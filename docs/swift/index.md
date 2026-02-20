# Dropbox Swift SDK

The Official Dropbox Swift SDK for integrating with Dropbox [API v2](https://www.dropbox.com/developers/documentation/http/documentation) on iOS or macOS.

Full API documentation is available [here](https://dropbox.github.io/SwiftyDropbox/api-docs/latest/).

> **Note:** Version 10.0.0 differs greatly from previous versions of the SDK. See [Changes in version 10.0.0](version-10-changes) and, if needed, [Migrating from dropbox-sdk-obj-c](objective-c#migrating-from-dropbox-sdk-obj-c).

## Routes

The SDK organizes API endpoints into route classes:

| Route Class | Description |
|---|---|
| [AccountRoutes](account-routes) | User account operations |
| [AuthRoutes](auth-routes) | Authentication operations |
| [CheckRoutes](check-routes) | API connectivity checks |
| [ContactsRoutes](contacts-routes) | Contact management |
| [FilePropertiesRoutes](file-properties-routes) | File property templates and groups |
| [FileRequestsRoutes](file-requests-routes) | File request management |
| [FilesRoutes](files-routes) | File and folder operations |
| [OpenidRoutes](openid-routes) | OpenID Connect operations |
| [PaperRoutes](paper-routes) | Paper document operations (deprecated) |
| [SharingRoutes](sharing-routes) | Sharing and collaboration |
| [TeamRoutes](team-routes) | Team management |
| [TeamLogRoutes](team-log-routes) | Team event logging and auditing |
| [UsersRoutes](users-routes) | User information |

## Data Types

Each namespace has associated data types (classes and enums) used as arguments, results, and errors:

| Namespace | Description |
|---|---|
| [Account](account-data-types) | Account-related types |
| [Async](async-data-types) | Asynchronous job types |
| [Auth](auth-data-types) | Authentication types |
| [Check](check-data-types) | Check/echo types |
| [Common](common-data-types) | Common shared types |
| [Contacts](contacts-data-types) | Contact types |
| [FileProperties](file-properties-data-types) | File property types |
| [FileRequests](file-requests-data-types) | File request types |
| [Files](files-data-types) | File and folder types |
| [Openid](openid-data-types) | OpenID types |
| [Paper](paper-data-types) | Paper document types |
| [SeenState](seen-state-data-types) | Seen state types |
| [Sharing](sharing-data-types) | Sharing types |
| [Team](team-data-types) | Team management types |
| [TeamCommon](team-common-data-types) | Common team types |
| [TeamLog](team-log-data-types) | Team logging types |
| [Users](users-data-types) | User types |
