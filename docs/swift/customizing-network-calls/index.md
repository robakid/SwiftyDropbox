# Customizing Network Calls

## Configure network client

It is possible to configure the networking client used by the SDK to make API requests. You can supply custom fields like a custom user agent or custom session configurations, or a custom auth challenge handler. See below:

**iOS**

```swift
import SwiftyDropbox

let transportClient = DropboxTransportClientImpl(accessToken: "<MY_ACCESS_TOKEN>",
                                             baseHosts: nil,
                                             userAgent: "CustomUserAgent",
                                             selectUser: nil,
                                             sessionConfiguration: mySessionConfiguration,
                                             longpollSessionConfiguration: myLongpollSessionConfiguration,
                                             authChallengeHandler: nil)

DropboxClientsManager.setupWithAppKey("<APP_KEY>", transportClient: transportClient)
```

**macOS**

```swift
import SwiftyDropbox

let transportClient = DropboxTransportClientImpl(accessToken: "<MY_ACCESS_TOKEN>",
                                             baseHosts: nil,
                                             userAgent: "CustomUserAgent",
                                             selectUser: nil,
                                             sessionConfiguration: mySessionConfiguration,
                                             longpollSessionConfiguration: myLongpollSessionConfiguration,
                                             authChallengeHandler: nil)

DropboxClientsManager.setupWithAppKeyDesktop("<APP_KEY>", transportClient: transportClient)
```

## Specify API call response queue

By default, response/progress handler code runs on the main thread. You can set a custom response queue for each API call that you make via the `response` method, in the event you want your response/progress handler code to run on a different thread:

```swift
let client = DropboxClientsManager.authorizedClient!

client.files.listFolder(path: "").response(queue: DispatchQueue(label: "MyCustomSerialQueue")) { response, error in
    if let result = response {
        print(Thread.current)  // Output: <NSThread: 0x61000007bec0>{number = 4, name = (null)}
        print(Thread.main)     // Output: <NSThread: 0x608000070100>{number = 1, name = (null)}
        print(result)
    }
}
```

## Mock API responses in tests

When testing code that depends upon the SDK, it can be useful to mock arbitrary API responses from JSON fixtures. We recommend using dependency injection rather than accessing the client via the convenience singletons. Note that the mocks are not public, they are only available in tests when SwiftyDropbox is imported using the `@testable` attribute.

```swift
@testable import SwiftyDropbox

let transportClient = MockDropboxTransportClient()
let dropboxClient = DropboxClient(transportClient: transportClient)

// your feature under test
let commentClient = CommentClient(apiClient: dropboxClient)

let expectation = expectation(description: "added comment")

// function of your feature that relies upon Dropbox api response
commentClient.addComment(
    forIdentifier: identifier,
    commentId: "pendingCommentId",
    threadId: nil,
    message: "hello world",
    mentions: [],
    annotation: nil
) { result in
    XCTAssertEqual(result.commentId, "thread-1")
    XCTAssertNil(result.error)
    addCommentExpectation.fulfill()
}

let mockInput: MockInput = .success(
    json: ["id": "thread-1", "status": 1]
)

let request = try XCTUnwrap(transportClient.getLastRequest())
try request.handleMockInput(mockInput)

wait(for: [expectation], timeout: 1.0)
```
