# Objective-C

If you need to interact with the Dropbox SDK in Objective-C code there is an Objective-C compatibility layer for the SDK that can be used.

## Objective-C Compatibility Layer Distribution

### Swift Package Manager

The Objective-C compatibility layer is in the same package outlined in [SDK distribution](../sdk-distribution). After adding the package you will see a target named `SwiftyDropboxObjC` that can be added in the same way as the Swift SDK and used in its place.

### CocoaPods

For CocoaPods, in your Podfile, simply specify `SwiftyDropboxObjC` instead of (or in addition to) `SwiftyDropbox`.

```ruby
use_frameworks!

target '<YOUR_PROJECT_NAME>' do
    pod 'SwiftyDropboxObjC', '~> 10.2.4'
end
```

## Using the Objective-C Compatibility Layer

The Objective-C interface was built to mimic the Swift interface as closely as possible while still maintaining good Objective-C patterns and practices (for example full verbose names instead of the namespacing relied on in Swift). Other than the naming and some other small tweaks to accommodate Objective-C the usage of the SDK should be extremely similar in both languages, thus the instructions in this documentation should apply even when using Objective-C.

An example of the differences between Swift and Objective-C:

**Swift:**

```swift
import SwiftyDropbox

let userSelectArg = Team.UserSelectorArg.email("some@email.com")
DropboxClientsManager.team.membersGetInfo(members: [userSelectArg]).response { response, error in
    if let result = response {
        // Handle result
    } else {
        // Handle error
    }
}
```

**Objective-C:**

```objc
@import SwiftyDropboxObjC;

DBXTeamUserSelectorArgEmail *selector = [[DBXTeamUserSelectorArgEmail alloc] init:@"some@email.com"]
[[DBXDropboxClientsManager.authorizedTeamClient.team membersGetInfoWithMembers:@[selector]] responseWithCompletionHandler:^(NSArray<DBXTeamMembersGetInfoItem *> * _Nullable result, DBXTeamMembersGetInfoError * _Nullable routeError, DBXCallError * _Nullable error) {
    if (result) {
        // Handle result
    } else {
        // Handle error
    }
}];
```

## Migrating from dropbox-sdk-obj-c

If you previously integrated with [dropbox-sdk-obj-c](https://github.com/dropbox/dropbox-sdk-obj-c) migrating to the Swift SDK + Objective-C layer will require code changes but they should be relatively straightforward in most cases.

In order to maintain as consistent of an interface between Swift and Objective-C as possible in this SDK the interface did have to differ slightly from dropbox-sdk-obj-c. The primary differences are as follows:

### 1. Type names

Type names are derived from SwiftyDropbox types prefixed with `DBX`. There are generally some differences in naming from dropbox-sdk-obj-c, and with Swift's more granular access control some previously accessible types are now internal to the SDK only. See the [Common type migration reference](#common-type-migration-reference) below.

### 2. Function names

Some function names have changed slightly to be more verbose about arguments and/or to better match the Swift interface. In the following example note `createFolderV2` vs `createFolderV2WithPath` and `responseWithCompletionHandler` vs `setResponseBlock`:

**dropbox-sdk-obj-c:**

```objc
[[[DBClientsManager authorizedClient].filesRoutes createFolderV2:@"/some/folder/path"]
  setResponseBlock:^(DBFILESCreateFolderResult * _Nullable result, DBFILESCreateFolderError * _Nullable routeError, DBRequestError * _Nullable networkError) {
    // Handle response
}];
```

**SwiftyDropboxObjC:**

```objc
[[DBXDropboxClientsManager.authorizedClient.files createFolderV2WithPath:@"some/folder/path"] responseWithCompletionHandler:^(DBXFilesCreateFolderResult * _Nullable result, DBXFilesCreateFolderError * _Nullable routeError, DBXCallError * _Nullable error) {
    // Handle response
}];
```

### 3. Capitalization changes

Capitalization has changed on many classes.

| dropbox-sdk-obj-c | SwiftyDropboxObjC |
|---|---|
| `DBUSERSBasicAccount` | `DBXUsersBasicAccount` |

### 4. Enum representation

Representation of enums that are passed to or returned from the server are now explicitly typed in the class name:

**dropbox-sdk-obj-c:**

```objc
DBTEAMUserSelectorArg *userSelectArg = [[DBTEAMUserSelectorArg alloc] initWithEmail:@"some@email.com"];
```

**SwiftyDropboxObjC:**

```objc
DBXTeamUserSelectorArgEmail *userSelectArg = [[DBXTeamUserSelectorArgEmail alloc] init:@"some@email.com"];
```

### 5. Task auto-start

When working with tasks you no longer need to manually `start` the tasks. They are automatically started on creation.

### 6. Typed completion handlers

SwiftyDropbox relies on generics for typed completion handlers on Requests. This is not bridgeable to Objective-C. Instead, for each route there is an additional Request type with the correctly typed completion handler. E.g., `DownloadRequestFile<Files.FileMetadataSerializer, Files.DownloadErrorSerializer>` is represented in Objective-C as `DBXFilesDownloadDownloadRequestFile`.

## Common type migration reference

| dropbox-sdk-obj-c | SwiftyDropbox | SwiftyDropboxObjC |
|---|---|---|
| `DBAppClient` | `DropboxAppClient` | `DBXDropboxAppBase` |
| `DBClientsManager` | `DropboxClientsManager` | `DBXDropboxClientsManager` |
| `DBTeamClient` | `DropboxTeamClient` | `DBXDropboxTeamClient` |
| `DBUserClient` | `DropboxClient` | `DBXDropboxClient` |
| `DBRequestErrors` | `CallError` | `DBXCallError` |
| `DBRpcTask` | `RpcRequest` | `DBX<route-name>RpcRequest` |
| `DBUploadTask` | `UploadRequest` | `DBX<route-name>UploadRequest` |
| `DBDownloadUrlTask` | `DownloadRequestFile` | `DBX<route-name>DownloadRequestFile` |
| `DBDownloadDataTask` | `DownloadRequestMemory` | `DBX<route-name>DownloadRequestMemory` |
| `DBTransportBaseClient` / `DBTransportDefaultClient` | `DropboxTransportClientImpl` | `DBXDropboxTransportClient` |
| `DBTransportBaseHostnameConfig` | `BaseHosts` | `DBXBaseHosts` |
| `DBAccessTokenProvider` | `AccessTokenProvider` | `DBXAccessTokenProvider` |
| `DBLongLivedAccessTokenProvider` | `LongLivedAccessTokenProvider` | `DBXLongLivedAccessTokenProvider` |
| `DBShortLivedAccessTokenProvider` | `ShortLivedAccessTokenProvider` | `DBXShortLivedAccessTokenProvider` |
| `DBLoadingStatusDelegate` | `LoadingStatusDelegate` | `DBXLoadingStatusDelegate` |
| `DBOAuthManager` | `DropboxOAuthManager` | `DBXDropboxOAuthManager` |
| `DBAccessToken` | `DropboxAccessToken` | `DBXDropboxAccessToken` |
| `DBAccessTokenRefreshing` | `AccessTokenRefreshing` | `DBXAccessTokenRefreshing` |
| `DBOAuthResult` | `DropboxOAuthResult` | `DBXDropboxOAuthResult` |
| `DBOAuthResultCompletion` | `DropboxOAuthCompletion` | `(DBXDropboxOAuthResult?) -> Void` |
| `DBScopeRequest` | `ScopeRequest` | `DBXScopeRequest` |
| `DBSDKKeychain` | `SecureStorageAccess` | `DBXSecureStorageAccess` / `DBXSecureStorageAccessDefaultImpl` |
| `DBDelegate` | n/a | n/a |
| `DBGlobalErrorResponseHandler` | n/a | n/a |
| `DBSDKReachability` | n/a | n/a |
| `DBSessionData` | n/a | n/a |
| `DBTransportDefaultConfig` | n/a | n/a |
| `DBURLSessionTaskResponseBlockWrapper` | n/a | n/a |
| `DBURLSessionTaskWithTokenRefresh` | n/a | n/a |
| `DBOAuthPKCESession` | n/a | n/a |
| `DBOAuthTokenRequest` | n/a | n/a |
