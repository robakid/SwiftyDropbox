# Changes in Version 10.0.0

Version 10.0.0 of SwiftyDropbox differs significantly from version 9.2.0. It aims to support Objective-C, remove AlamoFire as a dependency, support background networking, replace fatal errors during serialization, add unit tests, and better support testing.

These additional features are the greatest differences, but even simple upgrades that don't utilize these new features should consider the other notable changes.

## Notable changes

- The destination to which a file is downloaded must now be specified at the time of the call. It's no longer possible to provide a closure that is evaluated after the request is complete.

- The older API for SSL certificate pinning, provided through AlamoFire, is no longer available. This version exposes the URLSession authentication challenge API. Additionally, the optional SessionDelegate from the previous version of the SDK has been removed without a direct replacement. If your workflows relied on these specific features in ways that are no longer implementable, please [let us know](https://github.com/dropbox/SwiftyDropbox/issues) so that we can better understand and address any potential issues.

- Serialization inconsistencies that used to cause fatal errors now are represented as errors piped through to the requests' completion handlers. It is up to the calling app to decide how to handle them.

- Carthage is no longer supported, please use Swift Package Manager or CocoaPods.

- SDK classes can no longer be subclassed. If this disrupts your usage, please [let us know](https://github.com/dropbox/SwiftyDropbox/issues).

- Due to the extensive nature of the rewrite and the introduction of new features in the new version of the SDK, when transitioning to the new version of the SDK it is important to perform thorough testing of your codebase. The significant changes and enhancements in the new version of the SDK may introduce subtle behavioral changes or edge cases that were not present in the previous version of the SDK.

## New features

For notes on Objective-C support see [Migrating from dropbox-sdk-obj-c](../objective-c#migrating-from-dropbox-sdk-obj-c).

The SDK's background networking support simplifies the reconnection of completion handlers to URLSession tasks. See [`TestSwiftyDropbox/DebugBackgroundSessionViewModel`](https://github.com/dropbox/SwiftyDropbox/tree/master/TestSwiftyDropbox/TestSwiftyDropbox_SwiftUI/iOS) for code that exercises various background networking scenarios. See [`TestSwiftDropbox/ActionRequestHandler`](https://github.com/dropbox/SwiftyDropbox/blob/master/TestSwiftyDropbox/TestSwiftyDropbox_ActionExtension/ActionRequestHandler.swift) for usage from an app extension.

## Testing support

Initialize a `DropboxClient` with a `MockDropboxTransportClient` to facilitate route response mocking in tests. Supply this client to your code under test, exercise the code, then pipe in responses as illustrated below and assert against your code's behavior.

```swift
let transportClient = MockDropboxTransportClient()

let client = DropboxClient(
    transportClient: transportClient
)

let feature = SystemUnderTest(client: client)

let json: [String: Any] = ["fileNames": ["first"]]

let request = transportClient.getLastRequest()

request.handleMockInput(.success(json: json))

XCTAssert(<state of feature>, <expected state>)
```
