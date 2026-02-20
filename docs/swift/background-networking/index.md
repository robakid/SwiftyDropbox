# Supporting Background Networking

Versions 10.0 and higher support iOS background networking from applications and their extensions.

## Initialization

To create a background client, provide a background session identifier. To use a shared container, specify that as well.

```swift
import SwiftyDropbox

DropboxClientsManager.setupWithAppKey(
    "<APP_KEY>",
    backgroundSessionIdentifier: "<BACKGROUND_SESSION_IDENTIFIER>",
    requestsToReconnect: { requestResults in
       // app code to handle results of completed requests
   }
)
```

If you're setting up a background client from an app extension, you'll need to specify a shared container identifier and configure an app group or keychain sharing appropriately.

```swift
DropboxClientsManager.setupWithAppKey(
    "<APP_KEY>",
    backgroundSessionIdentifier: "<BACKGROUND_SESSION_IDENTIFIER>"
    sharedContainerIdentifier: "<SHARED_CONTAINER_IDENTIFIER>",
    requestsToReconnect: { requestResults in
       // app code to handle results of completed requests
   }
)
```

Apps in an app group automatically have keychain sharing. App groups are required for using a shared container, which is necessary if your applications will be downloading files using background sessions in extensions. See:
- [Configuring App Groups](https://developer.apple.com/documentation/xcode/configuring-app-groups)
- [Configuring Keychain Sharing](https://developer.apple.com/documentation/xcode/configuring-keychain-sharing)

## Making requests

Make requests like you would with a foreground client.

```swift
let client = DropboxClientsManager.authorizedBackgroundClient!

client.files.download(path: path, overwrite: true, destination: destinationUrl) {
    if let result = response {
        print(result)
    }
}
```

## Customizing requests

Set background session related properties on requests for fine-grained control.

```swift
client.files.download(path: path, overwrite: true, destination: destinationUrl)
    .persistingString(string: "<DATA_AVAILABLE_ACROSS_APP_SESSIONS>")
    .settingEarliestBeginDate(date: .addingTimeInterval(fiveSeconds))
    .response { response, error in
{
    if let result = response {
        print(result)
    }
})
```

## Reconnecting to requests across app sessions

As background requests potentially span app sessions, the app will receive `AppDelegate.application(_:handleEventsForBackgroundURLSession:completionHandler:)` when woken to handle events. SwiftyDropbox can reconnect completion handlers to requests. The application must set up the `authorizedBackgroundClient` prior to attempting reconnection.

In the reconnection block you're receiving a heterogeneous collection of the routes requested on the background session. Handling the response will likely require context that must be persisted across sessions. You can use `.persistingString(string:)` and `.clientPersistedString` on request to store this context. Depending on your use case you may need to persist additional context in your application.

```swift
func application(_ application: UIApplication, handleEventsForBackgroundURLSession identifier: String, completionHandler: @escaping () -> Void) {
    DropboxClientsManager.handleEventsForBackgroundURLSession(
        with: identifier,
        creationInfos: [],
        completionHandler: completionHandler,
        requestsToReconnect: { requestResults in
            processReconnect(requestResults: requestResults)
        }
    )
}

func processReconnect(requestResults: ([Result<DropboxBaseRequestBox, ReconnectionError>])) {
    let successfulReturnedRequests = requestResults.compactMap { result -> DropboxBaseRequestBox? in
        switch result {
        case .success(let requestBox):
            return requestBox
        case .failure(let error):
            // handle error
            return nil
        }
    }

    for request in successfulReturnedRequests {
        switch request {
        case .download(let downloadRequest):
            downloadRequest.response { response, error in
                // handle response
            }
        case .upload(let uploadRequest):
            uploadRequest.response { response, error in
                // handle response
            }
        // or .downloadZip, .paperCreate, .getSharedLinkFile etc.
        default:
            // handle every case you expect to see, this should never be reached.
        }
    }
}
```

In the event that the requests originated from an App Extension, SwiftyDropbox must recreate the extension background client in order to reconnect the requests.

```swift
func application(_ application: UIApplication, handleEventsForBackgroundURLSession identifier: String, completionHandler: @escaping () -> Void) {
    let extensionCreationInfo: BackgroundExtensionSessionCreationInfo = .init(defaultInfo: .init(
        backgroundSessionIdentifier: "<EXTENSION_BACKGROUND_SESSION_IDENTIFIER>",
        sharedContainerIdentifier: "<EXTENSION_SHARED_CONTAINER_IDENTIFIER>"
    ))

    DropboxClientsManager.handleEventsForBackgroundURLSession(
        with: identifier,
        creationInfos: [extensionCreationInfo],
        completionHandler: completionHandler,
        requestsToReconnect: { requestResults in
            processReconnect(requestResults: requestResults)
        }
    )
}
```

## Debugging

Background sessions are difficult to debug. Both simulators and the Xcode debugger will cause the application to behave in meaningfully different ways -- verification of correct reconnection behavior should always take place on a physical device without the debugger connected. Logs to console can be viewed via **Xcode > Window > Devices and Simulators** and are a good bet for gaining insights here. Force quitting the application will disqualify it from continuing to do work in the background.

For a good discussion of this, see the [Apple Developer Forums thread](https://developer.apple.com/forums/thread/14855).

## Persistence

SwiftyDropbox tracks state and orchestrates reconnection by writing a JSON string to `URLSessionTask.taskDescription`, a property that `URLSession` itself persists across app sessions.

Above, in Customizing Requests, is an example of the ability of a client of SwiftyDropbox to persist its own arbitrary strings alongside SwiftyDropbox's private use of this field. This could be useful for storing the information needed to reconstruct a completion handler for a task after reconnection.

Depending on the needs of the application, this lightweight solution may be insufficient persistent bookkeeping, and the application may build independent private persistence mapping state to an id stored on the request. This could be useful in the event that a failure occurs where URLSession itself has lost track of the transfer and it must be recreated.

See the [Apple Developer Forums thread](https://developer.apple.com/forums/thread/11554) for further discussion.
