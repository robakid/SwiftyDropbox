# FileRequests Data Types

Data types for the file_requests namespace.

## GeneralFileRequestsError

There is an error accessing the file requests functionality.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.

---

## CountFileRequestsError

There was an error counting the file requests.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.

---

## CountFileRequestsResult

Result for count.

**Properties:**
- `fileRequestCount: UInt64` - The number file requests owner by this user.

---

## CreateFileRequestArgs

Arguments for create.

**Properties:**
- `title: String` - The title of the file request. Must not be empty.
- `destination: String` - The path of the folder in the Dropbox where uploaded files will be sent. For apps with the app folder permission, this will be relative to the app folder.
- `deadline: FileRequests.FileRequestDeadline?` - The deadline for the file request. Deadlines can only be set by Professional and Business accounts.
- `open: Bool` - Whether or not the file request should be open. If the file request is closed, it will not accept any file submissions, but it can be opened later.
- `description_: String?` - A description of the file request.

---

## FileRequestError

There is an error with the file request.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.

---

## CreateFileRequestError

There was an error creating the file request.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.
- `invalidLocation` - File requests are not available on the specified folder.
- `rateLimit` - The user has reached the rate limit for creating file requests. The limit is currently 4000 file requests total.

---

## DeleteAllClosedFileRequestsError

There was an error deleting all closed file requests.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.

---

## DeleteAllClosedFileRequestsResult

Result for deleteAllClosed.

**Properties:**
- `fileRequests: [FileRequests.FileRequest]` - The file requests deleted for this user.

---

## DeleteFileRequestArgs

Arguments for delete.

**Properties:**
- `ids: [String]` - List IDs of the file requests to delete.

---

## DeleteFileRequestError

There was an error deleting these file requests.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.
- `fileRequestOpen` - One or more file requests currently open.

---

## DeleteFileRequestsResult

Result for delete.

**Properties:**
- `fileRequests: [FileRequests.FileRequest]` - The file requests deleted by the request.

---

## FileRequest

A file request for receiving files into the user's Dropbox account.

**Properties:**
- `id: String` - The ID of the file request.
- `url: String` - The URL of the file request.
- `title: String` - The title of the file request.
- `destination: String?` - The path of the folder in the Dropbox where uploaded files will be sent. This can be null if the destination was removed. For apps with the app folder permission, this will be relative to the app folder.
- `created: Date` - When this file request was created.
- `deadline: FileRequests.FileRequestDeadline?` - The deadline for this file request. Only set if the request has a deadline.
- `isOpen: Bool` - Whether or not the file request is open. If the file request is closed, it will not accept any more file submissions.
- `fileCount: Int64` - The number of files this file request has received.
- `description_: String?` - A description of the file request.

---

## FileRequestDeadline

The FileRequestDeadline struct.

**Properties:**
- `deadline: Date` - The deadline for this file request.
- `allowLateUploads: FileRequests.GracePeriod?` - If set, allow uploads after the deadline has passed. These uploads will be marked overdue.

---

## GetFileRequestArgs

Arguments for get.

**Properties:**
- `id: String` - The ID of the file request to retrieve.

---

## GetFileRequestError

There was an error retrieving the specified file request.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.

---

## GracePeriod

The GracePeriod union.

**Cases:**
- `oneDay` - One day grace period.
- `twoDays` - Two days grace period.
- `sevenDays` - Seven days grace period.
- `thirtyDays` - Thirty days grace period.
- `always` - Always allow late uploads.
- `other` - An unspecified error.

---

## ListFileRequestsArg

Arguments for listV2.

**Properties:**
- `limit: UInt64` - The maximum number of file requests that should be returned per request.

---

## ListFileRequestsContinueArg

The ListFileRequestsContinueArg struct.

**Properties:**
- `cursor: String` - The cursor returned by the previous API call specified in the endpoint description.

---

## ListFileRequestsContinueError

There was an error retrieving the file requests.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `invalidCursor` - The cursor is invalid.

---

## ListFileRequestsError

There was an error retrieving the file requests.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.

---

## ListFileRequestsResult

Result for list_.

**Properties:**
- `fileRequests: [FileRequests.FileRequest]` - The file requests owned by this user. Apps with the app folder permission will only see file requests in their app folder.

---

## ListFileRequestsV2Result

Result for listV2 and listContinue.

**Properties:**
- `fileRequests: [FileRequests.FileRequest]` - The file requests owned by this user. Apps with the app folder permission will only see file requests in their app folder.
- `cursor: String` - Pass the cursor into listContinue to obtain additional file requests.
- `hasMore: Bool` - Is true if there are additional file requests that have not been returned yet. An additional call to list/continue can retrieve them.

---

## UpdateFileRequestArgs

Arguments for update.

**Properties:**
- `id: String` - The ID of the file request to update.
- `title: String?` - The new title of the file request. Must not be empty.
- `destination: String?` - The new path of the folder in the Dropbox where uploaded files will be sent. For apps with the app folder permission, this will be relative to the app folder.
- `deadline: FileRequests.UpdateFileRequestDeadline` - The new deadline for the file request. Deadlines can only be set by Professional and Business accounts.
- `open: Bool?` - Whether to set this file request as open or closed.
- `description_: String?` - The description of the file request.

---

## UpdateFileRequestDeadline

The UpdateFileRequestDeadline union.

**Cases:**
- `noUpdate` - Do not change the file request's deadline.
- `update` - FileRequests.FileRequestDeadline?. If null, the file request's deadline is cleared.
- `other` - An unspecified error.

---

## UpdateFileRequestError

There is an error updating the file request.

**Cases:**
- `disabledForTeam` - This user's Dropbox Business team doesn't allow file requests.
- `other` - An unspecified error.
- `notFound` - This file request ID was not found.
- `notAFolder` - The specified path is not a folder.
- `appLacksAccess` - This file request is not accessible to this app. Apps with the app folder permission can only access file requests in their app folder.
- `noPermission` - This user doesn't have permission to access or modify this file request.
- `emailUnverified` - This user's email address is not verified. File requests are only available on accounts with a verified email address.
- `validationError` - There was an error validating the request. For example, the title was invalid, or there were disallowed characters in the destination path.
