# PaperRoutes

Routes for the paper namespace. For Objective-C compatible routes see `DBPaperRoutes`.

## docsArchive

> **Deprecated**

Marks the given Paper doc as archived. This action can be performed or undone by anyone with edit permissions to the doc. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsArchive(docId: String) -> RpcRequest<VoidSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.

**Returns:** `Void` on success, `Paper.DocLookupError` on failure.

---

## docsCreate (Data)

> **Deprecated**

Creates a new Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsCreate(
    importFormat: Paper.ImportFormat,
    parentFolderId: String? = nil,
    input: Data
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocCreateErrorSerializer>
```

**Parameters:**
- `importFormat` - The format of provided data.
- `parentFolderId` - The Paper folder ID where the Paper document should be created. The API user has to have write access to this folder or error is thrown.
- `input` - The file to upload, as an Data object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocCreateError` on failure.

---

## docsCreate (URL)

> **Deprecated**

Creates a new Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsCreate(
    importFormat: Paper.ImportFormat,
    parentFolderId: String? = nil,
    input: URL
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocCreateErrorSerializer>
```

**Parameters:**
- `importFormat` - The format of provided data.
- `parentFolderId` - The Paper folder ID where the Paper document should be created. The API user has to have write access to this folder or error is thrown.
- `input` - The file to upload, as an URL object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocCreateError` on failure.

---

## docsCreate (InputStream)

> **Deprecated**

Creates a new Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsCreate(
    importFormat: Paper.ImportFormat,
    parentFolderId: String? = nil,
    input: InputStream
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocCreateErrorSerializer>
```

**Parameters:**
- `importFormat` - The format of provided data.
- `parentFolderId` - The Paper folder ID where the Paper document should be created. The API user has to have write access to this folder or error is thrown.
- `input` - The file to upload, as an InputStream object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocCreateError` on failure.

---

## docsDownload (File)

> **Deprecated**

Exports and downloads Paper doc either as HTML or markdown. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.content.read`

```swift
@discardableResult public func docsDownload(
    docId: String,
    exportFormat: Paper.ExportFormat,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Paper.PaperDocExportResultSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `exportFormat` - The export format for the Paper doc.
- `overwrite` - A boolean to set behavior in the event of a naming conflict. `True` will overwrite conflicting file at destination. `False` will take no action (but if left unhandled in destination closure, an NSError will be thrown).
- `destination` - The location to write the download to.

**Returns:** `Paper.PaperDocExportResult` on success, `Paper.DocLookupError` on failure.

---

## docsDownload (Memory)

> **Deprecated**

Exports and downloads Paper doc either as HTML or markdown. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.content.read`

```swift
@discardableResult public func docsDownload(
    docId: String,
    exportFormat: Paper.ExportFormat
) -> DownloadRequestMemory<Paper.PaperDocExportResultSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `exportFormat` - The export format for the Paper doc.

**Returns:** `Paper.PaperDocExportResult` on success, `Paper.DocLookupError` on failure.

---

## docsFolderUsersList

> **Deprecated**

Lists the users who are explicitly invited to the Paper folder in which the Paper doc is contained. For private folders all users (including owner) shared on the folder are listed and for team folders all non-team users shared on the folder are returned. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsFolderUsersList(
    docId: String,
    limit: Int32 = 1_000
) -> RpcRequest<Paper.ListUsersOnFolderResponseSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `limit` - Size limit per batch. The maximum number of users that can be retrieved per batch is 1000. Higher value results in invalid arguments error.

**Returns:** `Paper.ListUsersOnFolderResponse` on success, `Paper.DocLookupError` on failure.

---

## docsFolderUsersListContinue

> **Deprecated**

Once a cursor has been retrieved from docsFolderUsersList, use this to paginate through all users on the Paper folder. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsFolderUsersListContinue(
    docId: String,
    cursor: String
) -> RpcRequest<Paper.ListUsersOnFolderResponseSerializer, Paper.ListUsersCursorErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `cursor` - The cursor obtained from docsFolderUsersList or docsFolderUsersListContinue. Allows for pagination.

**Returns:** `Paper.ListUsersOnFolderResponse` on success, `Paper.ListUsersCursorError` on failure.

---

## docsGetFolderInfo

> **Deprecated**

Retrieves folder information for the given Paper doc. This includes: folder sharing policy; permissions for subfolders are set by the top-level folder. Full 'filepath', i.e. the list of folders (both folderId and folderName) from the root folder to the folder directly containing the Paper doc. If the Paper doc is not in any folder (aka unfiled) the response will be empty. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsGetFolderInfo(docId: String) -> RpcRequest<Paper.FoldersContainingPaperDocSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.

**Returns:** `Paper.FoldersContainingPaperDoc` on success, `Paper.DocLookupError` on failure.

---

## docsList

> **Deprecated**

Return the list of all Paper docs according to the argument specifications. To iterate over through the full pagination, pass the cursor to docsListContinue. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.metadata.read`

```swift
@discardableResult public func docsList(
    filterBy: Paper.ListPaperDocsFilterBy = .docsAccessed,
    sortBy: Paper.ListPaperDocsSortBy = .accessed,
    sortOrder: Paper.ListPaperDocsSortOrder = .ascending,
    limit: Int32 = 1_000
) -> RpcRequest<Paper.ListPaperDocsResponseSerializer, VoidSerializer>
```

**Parameters:**
- `filterBy` - Allows user to specify how the Paper docs should be filtered.
- `sortBy` - Allows user to specify how the Paper docs should be sorted.
- `sortOrder` - Allows user to specify the sort order of the result.
- `limit` - Size limit per batch. The maximum number of docs that can be retrieved per batch is 1000. Higher value results in invalid arguments error.

**Returns:** `Paper.ListPaperDocsResponse` on success, `Void` on failure.

---

## docsListContinue

> **Deprecated**

Once a cursor has been retrieved from docsList, use this to paginate through all Paper doc. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.metadata.read`

```swift
@discardableResult public func docsListContinue(cursor: String) -> RpcRequest<Paper.ListPaperDocsResponseSerializer, Paper.ListDocsCursorErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor obtained from docsList or docsListContinue. Allows for pagination.

**Returns:** `Paper.ListPaperDocsResponse` on success, `Paper.ListDocsCursorError` on failure.

---

## docsPermanentlyDelete

> **Deprecated**

Permanently deletes the given Paper doc. This operation is final as the doc cannot be recovered. This action can be performed only by the doc owner. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.permanent_delete`

```swift
@discardableResult public func docsPermanentlyDelete(docId: String) -> RpcRequest<VoidSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.

**Returns:** `Void` on success, `Paper.DocLookupError` on failure.

---

## docsSharingPolicyGet

> **Deprecated**

Gets the default sharing policy for the given Paper doc. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsSharingPolicyGet(docId: String) -> RpcRequest<Paper.SharingPolicySerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.

**Returns:** `Paper.SharingPolicy` on success, `Paper.DocLookupError` on failure.

---

## docsSharingPolicySet

> **Deprecated**

Sets the default sharing policy for the given Paper doc. The default 'team_sharing_policy' can be changed only by teams, omit this field for personal accounts. The 'public_sharing_policy' policy can't be set to the value 'disabled' because this setting can be changed only via the team admin console. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.write`

```swift
@discardableResult public func docsSharingPolicySet(
    docId: String,
    sharingPolicy: Paper.SharingPolicy
) -> RpcRequest<VoidSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `sharingPolicy` - The default sharing policy to be set for the Paper doc.

**Returns:** `Void` on success, `Paper.DocLookupError` on failure.

---

## docsUpdate (Data)

> **Deprecated**

Updates an existing Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsUpdate(
    docId: String,
    docUpdatePolicy: Paper.PaperDocUpdatePolicy,
    revision: Int64,
    importFormat: Paper.ImportFormat,
    input: Data
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocUpdateErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `docUpdatePolicy` - The policy used for the current update call.
- `revision` - The latest doc revision. This value must match the head revision or an error code will be returned. This is to prevent colliding writes.
- `importFormat` - The format of provided data.
- `input` - The file to upload, as an Data object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocUpdateError` on failure.

---

## docsUpdate (URL)

> **Deprecated**

Updates an existing Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsUpdate(
    docId: String,
    docUpdatePolicy: Paper.PaperDocUpdatePolicy,
    revision: Int64,
    importFormat: Paper.ImportFormat,
    input: URL
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocUpdateErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `docUpdatePolicy` - The policy used for the current update call.
- `revision` - The latest doc revision. This value must match the head revision or an error code will be returned. This is to prevent colliding writes.
- `importFormat` - The format of provided data.
- `input` - The file to upload, as an URL object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocUpdateError` on failure.

---

## docsUpdate (InputStream)

> **Deprecated**

Updates an existing Paper doc with the provided content. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. This endpoint will be retired in September 2020. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for more information.

**Scope:** `files.content.write`

```swift
@discardableResult public func docsUpdate(
    docId: String,
    docUpdatePolicy: Paper.PaperDocUpdatePolicy,
    revision: Int64,
    importFormat: Paper.ImportFormat,
    input: InputStream
) -> UploadRequest<Paper.PaperDocCreateUpdateResultSerializer, Paper.PaperDocUpdateErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `docUpdatePolicy` - The policy used for the current update call.
- `revision` - The latest doc revision. This value must match the head revision or an error code will be returned. This is to prevent colliding writes.
- `importFormat` - The format of provided data.
- `input` - The file to upload, as an InputStream object.

**Returns:** `Paper.PaperDocCreateUpdateResult` on success, `Paper.PaperDocUpdateError` on failure.

---

## docsUsersAdd

> **Deprecated**

Allows an owner or editor to add users to a Paper doc or change their permissions using their email address or Dropbox account ID. The doc owner's permissions cannot be changed. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.write`

```swift
@discardableResult public func docsUsersAdd(
    docId: String,
    members: [Paper.AddMember],
    customMessage: String? = nil,
    quiet: Bool = false
) -> RpcRequest<ArraySerializer<Paper.AddPaperDocUserMemberResultSerializer>, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `members` - User which should be added to the Paper doc. Specify only email address or Dropbox account ID.
- `customMessage` - A personal message that will be emailed to each successfully added member.
- `quiet` - Clients should set this to true if no email message shall be sent to added users.

**Returns:** `Array<Paper.AddPaperDocUserMemberResult>` on success, `Paper.DocLookupError` on failure.

---

## docsUsersList

> **Deprecated**

Lists all users who visited the Paper doc or users with explicit access. This call excludes users who have been removed. The list is sorted by the date of the visit or the share date. The list will include both users, the explicitly shared ones as well as those who came in using the Paper url link. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsUsersList(
    docId: String,
    limit: Int32 = 1_000,
    filterBy: Paper.UserOnPaperDocFilter = .shared
) -> RpcRequest<Paper.ListUsersOnPaperDocResponseSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `limit` - Size limit per batch. The maximum number of users that can be retrieved per batch is 1000. Higher value results in invalid arguments error.
- `filterBy` - Specify this attribute if you want to obtain users that have already accessed the Paper doc.

**Returns:** `Paper.ListUsersOnPaperDocResponse` on success, `Paper.DocLookupError` on failure.

---

## docsUsersListContinue

> **Deprecated**

Once a cursor has been retrieved from docsUsersList, use this to paginate through all users on the Paper doc. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.read`

```swift
@discardableResult public func docsUsersListContinue(
    docId: String,
    cursor: String
) -> RpcRequest<Paper.ListUsersOnPaperDocResponseSerializer, Paper.ListUsersCursorErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `cursor` - The cursor obtained from docsUsersList or docsUsersListContinue. Allows for pagination.

**Returns:** `Paper.ListUsersOnPaperDocResponse` on success, `Paper.ListUsersCursorError` on failure.

---

## docsUsersRemove

> **Deprecated**

Allows an owner or editor to remove users from a Paper doc using their email address or Dropbox account ID. The doc owner cannot be removed. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `sharing.write`

```swift
@discardableResult public func docsUsersRemove(
    docId: String,
    member: Sharing.MemberSelector
) -> RpcRequest<VoidSerializer, Paper.DocLookupErrorSerializer>
```

**Parameters:**
- `docId` - The Paper doc ID.
- `member` - User which should be removed from the Paper doc. Specify only email address or Dropbox account ID.

**Returns:** `Void` on success, `Paper.DocLookupError` on failure.

---

## foldersCreate

> **Deprecated**

Create a new Paper folder with the provided info. Note that this endpoint will continue to work for content created by users on the older version of Paper. To check which version of Paper a user is on, use /users/features/get_values. If the paper_as_files feature is enabled, then the user is running the new version of Paper. Refer to the [Paper Migration Guide](https://www.dropbox.com/lp/developers/reference/paper-migration-guide) for migration information.

**Scope:** `files.content.write`

```swift
@discardableResult public func foldersCreate(
    name: String,
    parentFolderId: String? = nil,
    isTeamFolder: Bool? = nil
) -> RpcRequest<Paper.PaperFolderCreateResultSerializer, Paper.PaperFolderCreateErrorSerializer>
```

**Parameters:**
- `name` - The name of the new Paper folder.
- `parentFolderId` - The encrypted Paper folder Id where the new Paper folder should be created. The API user has to have write access to this folder or error is thrown. If not supplied, the new folder will be created at top level.
- `isTeamFolder` - Whether the folder to be created should be a team folder. This value will be ignored if parent_folder_id is supplied, as the new folder will inherit the type (private or team folder) from its parent. We will by default create a top-level private folder if both parent_folder_id and is_team_folder are not supplied.

**Returns:** `Paper.PaperFolderCreateResult` on success, `Paper.PaperFolderCreateError` on failure.
