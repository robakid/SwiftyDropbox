# FileRequestsRoutes

Routes for the file_requests namespace. For Objective-C compatible routes see `DBFileRequestsRoutes`.

---

## count

Returns the total number of file requests owned by this user. Includes both open and closed file requests.

**Scope:** `file_requests.read`

```swift
func count() -> RpcRequest<FileRequests.CountFileRequestsResult, FileRequests.CountFileRequestsError>
```

**Returns:** `FileRequests.CountFileRequestsResult` on success, `FileRequests.CountFileRequestsError` on failure.

---

## create

Creates a file request for this user.

**Scope:** `file_requests.write`

```swift
func create(title: String, destination: String, deadline: FileRequests.FileRequestDeadline? = nil, open: Bool = true, description_: String? = nil) -> RpcRequest<FileRequests.FileRequest, FileRequests.CreateFileRequestError>
```

**Parameters:**
- `title` - The title of the file request. Must not be empty.
- `destination` - The path of the folder in the Dropbox where uploaded files will be sent. For apps with the app folder permission, this will be relative to the app folder.
- `deadline` - The deadline for the file request. Deadlines can only be set by Professional and Business accounts.
- `open` - Whether or not the file request should be open. If the file request is closed, it will not accept any file submissions, but it can be opened later.
- `description_` - A description of the file request.

**Returns:** `FileRequests.FileRequest` on success, `FileRequests.CreateFileRequestError` on failure.

---

## delete

Delete a batch of closed file requests.

**Scope:** `file_requests.write`

```swift
func delete(ids: [String]) -> RpcRequest<FileRequests.DeleteFileRequestsResult, FileRequests.DeleteFileRequestError>
```

**Parameters:**
- `ids` - List IDs of the file requests to delete.

**Returns:** `FileRequests.DeleteFileRequestsResult` on success, `FileRequests.DeleteFileRequestError` on failure.

---

## deleteAllClosed

Delete all closed file requests owned by this user.

**Scope:** `file_requests.write`

```swift
func deleteAllClosed() -> RpcRequest<FileRequests.DeleteAllClosedFileRequestsResult, FileRequests.DeleteAllClosedFileRequestsError>
```

**Returns:** `FileRequests.DeleteAllClosedFileRequestsResult` on success, `FileRequests.DeleteAllClosedFileRequestsError` on failure.

---

## get

Returns the specified file request.

**Scope:** `file_requests.read`

```swift
func get(id: String) -> RpcRequest<FileRequests.FileRequest, FileRequests.GetFileRequestError>
```

**Parameters:**
- `id` - The ID of the file request to retrieve.

**Returns:** `FileRequests.FileRequest` on success, `FileRequests.GetFileRequestError` on failure.

---

## list_

Returns a list of file requests owned by this user. For apps with the app folder permission, this will only return file requests with destinations in the app folder.

**Scope:** `file_requests.read`

```swift
func list_() -> RpcRequest<FileRequests.ListFileRequestsResult, FileRequests.ListFileRequestsError>
```

**Returns:** `FileRequests.ListFileRequestsResult` on success, `FileRequests.ListFileRequestsError` on failure.

---

## listV2

Returns a list of file requests owned by this user. For apps with the app folder permission, this will only return file requests with destinations in the app folder.

**Scope:** `file_requests.read`

```swift
func listV2(limit: UInt64 = 1_000) -> RpcRequest<FileRequests.ListFileRequestsV2Result, FileRequests.ListFileRequestsError>
```

**Parameters:**
- `limit` - The maximum number of file requests that should be returned per request.

**Returns:** `FileRequests.ListFileRequestsV2Result` on success, `FileRequests.ListFileRequestsError` on failure.

---

## listContinue

Once a cursor has been retrieved from `listV2`, use this to paginate through all file requests. The cursor must come from a previous call to `listV2` or `listContinue`.

**Scope:** `file_requests.read`

```swift
func listContinue(cursor: String) -> RpcRequest<FileRequests.ListFileRequestsV2Result, FileRequests.ListFileRequestsContinueError>
```

**Parameters:**
- `cursor` - The cursor returned by the previous API call specified in the endpoint description.

**Returns:** `FileRequests.ListFileRequestsV2Result` on success, `FileRequests.ListFileRequestsContinueError` on failure.

---

## update

Update a file request.

**Scope:** `file_requests.write`

```swift
func update(id: String, title: String? = nil, destination: String? = nil, deadline: FileRequests.UpdateFileRequestDeadline = .noUpdate, open: Bool? = nil, description_: String? = nil) -> RpcRequest<FileRequests.FileRequest, FileRequests.UpdateFileRequestError>
```

**Parameters:**
- `id` - The ID of the file request to update.
- `title` - The new title of the file request. Must not be empty.
- `destination` - The new path of the folder in the Dropbox where uploaded files will be sent. For apps with the app folder permission, this will be relative to the app folder.
- `deadline` - The new deadline for the file request. Deadlines can only be set by Professional and Business accounts.
- `open` - Whether to set this file request as open or closed.
- `description_` - The description of the file request.

**Returns:** `FileRequests.FileRequest` on success, `FileRequests.UpdateFileRequestError` on failure.
