# SharingRoutes

Routes for the sharing namespace. For Objective-C compatible routes see `DBSharingRoutes`.

---

## addFileMember

Adds specified members to a file.

**Scope:** `sharing.write`

```swift
@discardableResult public func addFileMember(
    file: String,
    members: [Sharing.MemberSelector],
    customMessage: String? = nil,
    quiet: Bool = false,
    accessLevel: Sharing.AccessLevel = .viewer,
    addMessageAsComment: Bool = false
) -> RpcRequest<ArraySerializer<Sharing.FileMemberActionResultSerializer>, Sharing.AddFileMemberErrorSerializer>
```

**Parameters:**
- `file` - File to which to add members.
- `members` - Members to add. Note that even an email address is given, this may result in a user being directly added to the membership if that email is the user's main account email.
- `customMessage` - Message to send to added members in their invitation.
- `quiet` - Whether added members should be notified via email and device notifications of their invitation.
- `accessLevel` - AccessLevel union object, describing what access level we want to give new members.
- `addMessageAsComment` - If the custom message should be added as a comment on the file.

**Returns:** `Array<Sharing.FileMemberActionResult>` on success, `Sharing.AddFileMemberError` on failure.

---

## addFolderMember

Allows an owner or editor (if the ACL update policy allows) of a shared folder to add another member. For the new member to get access to all the functionality for this folder, you will need to call mountFolder on their behalf.

**Scope:** `sharing.write`

```swift
@discardableResult public func addFolderMember(
    sharedFolderId: String,
    members: [Sharing.AddMember],
    quiet: Bool = false,
    customMessage: String? = nil
) -> RpcRequest<VoidSerializer, Sharing.AddFolderMemberErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `members` - The intended list of members to add. Added members will receive invites to join the shared folder.
- `quiet` - Whether added members should be notified via email and device notifications of their invite.
- `customMessage` - Optional message to display to added members in their invitation.

**Returns:** `Void` on success, `Sharing.AddFolderMemberError` on failure.

---

## checkJobStatus

Returns the status of an asynchronous job.

**Scope:** `sharing.write`

```swift
@discardableResult public func checkJobStatus(
    asyncJobId: String
) -> RpcRequest<Sharing.JobStatusSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Sharing.JobStatus` on success, `Async.PollError` on failure.

---

## checkRemoveMemberJobStatus

Returns the status of an asynchronous job for sharing a folder.

**Scope:** `sharing.write`

```swift
@discardableResult public func checkRemoveMemberJobStatus(
    asyncJobId: String
) -> RpcRequest<Sharing.RemoveMemberJobStatusSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Sharing.RemoveMemberJobStatus` on success, `Async.PollError` on failure.

---

## checkShareJobStatus

Returns the status of an asynchronous job for sharing a folder.

**Scope:** `sharing.write`

```swift
@discardableResult public func checkShareJobStatus(
    asyncJobId: String
) -> RpcRequest<Sharing.ShareFolderJobStatusSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Sharing.ShareFolderJobStatus` on success, `Async.PollError` on failure.

---

## createSharedLink

> **Deprecated:** createSharedLink is deprecated. Use createSharedLinkWithSettings.

Create a shared link. If a shared link already exists for the given path, that link is returned. Previously, it was technically possible to break a shared link by moving or renaming the corresponding file or folder. In the future, this will no longer be the case, so your app shouldn't rely on this behavior. Instead, if your app needs to revoke a shared link, use revokeSharedLink.

**Scope:** `sharing.write`

```swift
@discardableResult public func createSharedLink(
    path: String,
    shortUrl: Bool = false,
    pendingUpload: Sharing.PendingUploadMode? = nil
) -> RpcRequest<Sharing.PathLinkMetadataSerializer, Sharing.CreateSharedLinkErrorSerializer>
```

**Parameters:**
- `path` - The path to share.
- `shortUrl` - Whether to return a shortened URL.
- `pendingUpload` - If it's okay to share a path that does not yet exist, set this to either file in PendingUploadMode or folder in PendingUploadMode to indicate whether to assume it's a file or folder.

**Returns:** `Sharing.PathLinkMetadata` on success, `Sharing.CreateSharedLinkError` on failure.

---

## createSharedLinkWithSettings

Create a shared link with custom settings. If no settings are given then the default visibility is public_ in RequestedVisibility (The resolved visibility, though, may depend on other aspects such as team and shared folder settings).

**Scope:** `sharing.write`

```swift
@discardableResult public func createSharedLinkWithSettings(
    path: String,
    settings: Sharing.SharedLinkSettings? = nil
) -> RpcRequest<Sharing.SharedLinkMetadataSerializer, Sharing.CreateSharedLinkWithSettingsErrorSerializer>
```

**Parameters:**
- `path` - The path to be shared by the shared link.
- `settings` - The requested settings for the newly created shared link.

**Returns:** `Sharing.SharedLinkMetadata` on success, `Sharing.CreateSharedLinkWithSettingsError` on failure.

---

## getFileMetadata

Returns shared file metadata.

**Scope:** `sharing.read`

```swift
@discardableResult public func getFileMetadata(
    file: String,
    actions: [Sharing.FileAction]? = nil
) -> RpcRequest<Sharing.SharedFileMetadataSerializer, Sharing.GetFileMetadataErrorSerializer>
```

**Parameters:**
- `file` - The file to query.
- `actions` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions in SharedFileMetadata field describing the actions the authenticated user can perform on the file.

**Returns:** `Sharing.SharedFileMetadata` on success, `Sharing.GetFileMetadataError` on failure.

---

## getFileMetadataBatch

Returns shared file metadata.

**Scope:** `sharing.read`

```swift
@discardableResult public func getFileMetadataBatch(
    files: [String],
    actions: [Sharing.FileAction]? = nil
) -> RpcRequest<ArraySerializer<Sharing.GetFileMetadataBatchResultSerializer>, Sharing.SharingUserErrorSerializer>
```

**Parameters:**
- `files` - The files to query.
- `actions` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions in SharedFileMetadata field describing the actions the authenticated user can perform on the file.

**Returns:** `Array<Sharing.GetFileMetadataBatchResult>` on success, `Sharing.SharingUserError` on failure.

---

## getFolderMetadata

Returns shared folder metadata by its folder ID.

**Scope:** `sharing.read`

```swift
@discardableResult public func getFolderMetadata(
    sharedFolderId: String,
    actions: [Sharing.FolderAction]? = nil
) -> RpcRequest<Sharing.SharedFolderMetadataSerializer, Sharing.SharedFolderAccessErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `actions` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

**Returns:** `Sharing.SharedFolderMetadata` on success, `Sharing.SharedFolderAccessError` on failure.

---

## getSharedLinkFile (download to file)

Download the shared link's file from a user's Dropbox.

**Scope:** `sharing.read`

```swift
@discardableResult public func getSharedLinkFile(
    url: String,
    path: String? = nil,
    linkPassword: String? = nil,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Sharing.SharedLinkMetadataSerializer, Sharing.GetSharedLinkFileErrorSerializer>
```

**Parameters:**
- `url` - URL of the shared link.
- `path` - If the shared link is to a folder, this parameter can be used to retrieve the metadata for a specific file or sub-folder in this folder. A relative path should be used.
- `linkPassword` - If the shared link has a password, this parameter can be used.
- `overwrite` - A boolean to set behavior in the event of a naming conflict. `True` will overwrite conflicting file at destination. `False` will take no action (but if left unhandled in destination closure, an NSError will be thrown).
- `destination` - The location to write the download to.

**Returns:** `Sharing.SharedLinkMetadata` on success, `Sharing.GetSharedLinkFileError` on failure.

---

## getSharedLinkFile (download to memory)

Download the shared link's file from a user's Dropbox.

**Scope:** `sharing.read`

```swift
@discardableResult public func getSharedLinkFile(
    url: String,
    path: String? = nil,
    linkPassword: String? = nil
) -> DownloadRequestMemory<Sharing.SharedLinkMetadataSerializer, Sharing.GetSharedLinkFileErrorSerializer>
```

**Parameters:**
- `url` - URL of the shared link.
- `path` - If the shared link is to a folder, this parameter can be used to retrieve the metadata for a specific file or sub-folder in this folder. A relative path should be used.
- `linkPassword` - If the shared link has a password, this parameter can be used.

**Returns:** `Sharing.SharedLinkMetadata` on success, `Sharing.GetSharedLinkFileError` on failure.

---

## getSharedLinkMetadata

Get the shared link's metadata.

**Scope:** `sharing.read`

```swift
@discardableResult public func getSharedLinkMetadata(
    url: String,
    path: String? = nil,
    linkPassword: String? = nil
) -> RpcRequest<Sharing.SharedLinkMetadataSerializer, Sharing.SharedLinkErrorSerializer>
```

**Parameters:**
- `url` - URL of the shared link.
- `path` - If the shared link is to a folder, this parameter can be used to retrieve the metadata for a specific file or sub-folder in this folder. A relative path should be used.
- `linkPassword` - If the shared link has a password, this parameter can be used.

**Returns:** `Sharing.SharedLinkMetadata` on success, `Sharing.SharedLinkError` on failure.

---

## getSharedLinks

> **Deprecated:** getSharedLinks is deprecated. Use listSharedLinks.

Returns a list of LinkMetadata objects for this user, including collection links. If no path is given, returns a list of all shared links for the current user, including collection links, up to a maximum of 1000 links. If a non-empty path is given, returns a list of all shared links that allow access to the given path. Collection links are never returned in this case.

**Scope:** `sharing.read`

```swift
@discardableResult public func getSharedLinks(
    path: String? = nil
) -> RpcRequest<Sharing.GetSharedLinksResultSerializer, Sharing.GetSharedLinksErrorSerializer>
```

**Parameters:**
- `path` - See getSharedLinks description.

**Returns:** `Sharing.GetSharedLinksResult` on success, `Sharing.GetSharedLinksError` on failure.

---

## listFileMembers

Use to obtain the members who have been invited to a file, both inherited and uninherited members.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFileMembers(
    file: String,
    actions: [Sharing.MemberAction]? = nil,
    includeInherited: Bool = true,
    limit: UInt32 = 100
) -> RpcRequest<Sharing.SharedFileMembersSerializer, Sharing.ListFileMembersErrorSerializer>
```

**Parameters:**
- `file` - The file for which you want to see members.
- `actions` - The actions for which to return permissions on a member.
- `includeInherited` - Whether to include members who only have access from a parent shared folder.
- `limit` - Number of members to return max per query. Defaults to 100 if no limit is specified.

**Returns:** `Sharing.SharedFileMembers` on success, `Sharing.ListFileMembersError` on failure.

---

## listFileMembersBatch

Get members of multiple files at once. The arguments to this route are more limited, and the limit on query result size per file is more strict. To customize the results more, use the individual file endpoint. Inherited users and groups are not included in the result, and permissions are not returned for this endpoint.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFileMembersBatch(
    files: [String],
    limit: UInt32 = 10
) -> RpcRequest<ArraySerializer<Sharing.ListFileMembersBatchResultSerializer>, Sharing.SharingUserErrorSerializer>
```

**Parameters:**
- `files` - Files for which to return members.
- `limit` - Number of members to return max per query. Defaults to 10 if no limit is specified.

**Returns:** `Array<Sharing.ListFileMembersBatchResult>` on success, `Sharing.SharingUserError` on failure.

---

## listFileMembersContinue

Once a cursor has been retrieved from listFileMembers or listFileMembersBatch, use this to paginate through all shared file members.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFileMembersContinue(
    cursor: String
) -> RpcRequest<Sharing.SharedFileMembersSerializer, Sharing.ListFileMembersContinueErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor returned by your last call to listFileMembers, listFileMembersContinue, or listFileMembersBatch.

**Returns:** `Sharing.SharedFileMembers` on success, `Sharing.ListFileMembersContinueError` on failure.

---

## listFolderMembers

Returns shared folder membership by its folder ID.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFolderMembers(
    sharedFolderId: String,
    actions: [Sharing.MemberAction]? = nil,
    limit: UInt32 = 1_000
) -> RpcRequest<Sharing.SharedFolderMembersSerializer, Sharing.SharedFolderAccessErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `actions` - The actions for which to return permissions on a member.
- `limit` - Number of members to return max per query. Defaults to 1000 if no limit is specified.

**Returns:** `Sharing.SharedFolderMembers` on success, `Sharing.SharedFolderAccessError` on failure.

---

## listFolderMembersContinue

Once a cursor has been retrieved from listFolderMembers, use this to paginate through all shared folder members.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFolderMembersContinue(
    cursor: String
) -> RpcRequest<Sharing.SharedFolderMembersSerializer, Sharing.ListFolderMembersContinueErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor returned by your last call to listFolderMembers or listFolderMembersContinue.

**Returns:** `Sharing.SharedFolderMembers` on success, `Sharing.ListFolderMembersContinueError` on failure.

---

## listFolders

Return the list of all shared folders the current user has access to.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFolders(
    limit: UInt32 = 1_000,
    actions: [Sharing.FolderAction]? = nil
) -> RpcRequest<Sharing.ListFoldersResultSerializer, VoidSerializer>
```

**Parameters:**
- `limit` - The maximum number of results to return per request.
- `actions` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

**Returns:** `Sharing.ListFoldersResult` on success, `Void` on failure.

---

## listFoldersContinue

Once a cursor has been retrieved from listFolders, use this to paginate through all shared folders. The cursor must come from a previous call to listFolders or listFoldersContinue.

**Scope:** `sharing.read`

```swift
@discardableResult public func listFoldersContinue(
    cursor: String
) -> RpcRequest<Sharing.ListFoldersResultSerializer, Sharing.ListFoldersContinueErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor returned by the previous API call specified in the endpoint description.

**Returns:** `Sharing.ListFoldersResult` on success, `Sharing.ListFoldersContinueError` on failure.

---

## listMountableFolders

Return the list of all shared folders the current user can mount or unmount.

**Scope:** `sharing.read`

```swift
@discardableResult public func listMountableFolders(
    limit: UInt32 = 1_000,
    actions: [Sharing.FolderAction]? = nil
) -> RpcRequest<Sharing.ListFoldersResultSerializer, VoidSerializer>
```

**Parameters:**
- `limit` - The maximum number of results to return per request.
- `actions` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

**Returns:** `Sharing.ListFoldersResult` on success, `Void` on failure.

---

## listMountableFoldersContinue

Once a cursor has been retrieved from listMountableFolders, use this to paginate through all mountable shared folders. The cursor must come from a previous call to listMountableFolders or listMountableFoldersContinue.

**Scope:** `sharing.read`

```swift
@discardableResult public func listMountableFoldersContinue(
    cursor: String
) -> RpcRequest<Sharing.ListFoldersResultSerializer, Sharing.ListFoldersContinueErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor returned by the previous API call specified in the endpoint description.

**Returns:** `Sharing.ListFoldersResult` on success, `Sharing.ListFoldersContinueError` on failure.

---

## listReceivedFiles

Returns a list of all files shared with current user. Does not include files the user has received via shared folders, and does not include unclaimed invitations.

**Scope:** `sharing.read`

```swift
@discardableResult public func listReceivedFiles(
    limit: UInt32 = 100,
    actions: [Sharing.FileAction]? = nil
) -> RpcRequest<Sharing.ListFilesResultSerializer, Sharing.SharingUserErrorSerializer>
```

**Parameters:**
- `limit` - Number of files to return max per query. Defaults to 100 if no limit is specified.
- `actions` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions in SharedFileMetadata field describing the actions the authenticated user can perform on the file.

**Returns:** `Sharing.ListFilesResult` on success, `Sharing.SharingUserError` on failure.

---

## listReceivedFilesContinue

Get more results with a cursor from listReceivedFiles.

**Scope:** `sharing.read`

```swift
@discardableResult public func listReceivedFilesContinue(
    cursor: String
) -> RpcRequest<Sharing.ListFilesResultSerializer, Sharing.ListFilesContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Cursor in cursor in ListFilesResult.

**Returns:** `Sharing.ListFilesResult` on success, `Sharing.ListFilesContinueError` on failure.

---

## listSharedLinks

List shared links of this user. If no path is given, returns a list of all shared links for the current user. For members of business teams using team space and member folders, returns all shared links in the team member's home folder unless the team space ID is specified in the request header. For more information, refer to the Namespace Guide. If a non-empty path is given, returns a list of all shared links that allow access to the given path - direct links to the given path and links to parent folders of the given path. Links to parent folders can be suppressed by setting direct_only to true.

**Scope:** `sharing.read`

```swift
@discardableResult public func listSharedLinks(
    path: String? = nil,
    cursor: String? = nil,
    directOnly: Bool? = nil
) -> RpcRequest<Sharing.ListSharedLinksResultSerializer, Sharing.ListSharedLinksErrorSerializer>
```

**Parameters:**
- `path` - See listSharedLinks description.
- `cursor` - The cursor returned by your last call to listSharedLinks.
- `directOnly` - See listSharedLinks description.

**Returns:** `Sharing.ListSharedLinksResult` on success, `Sharing.ListSharedLinksError` on failure.

---

## modifySharedLinkSettings

Modify the shared link's settings. If the requested visibility conflict with the shared links policy of the team or the shared folder (in case the linked file is part of a shared folder) then the resolvedVisibility in LinkPermissions of the returned SharedLinkMetadata will reflect the actual visibility of the shared link and the requestedVisibility in LinkPermissions will reflect the requested visibility.

**Scope:** `sharing.write`

```swift
@discardableResult public func modifySharedLinkSettings(
    url: String,
    settings: Sharing.SharedLinkSettings,
    removeExpiration: Bool = false
) -> RpcRequest<Sharing.SharedLinkMetadataSerializer, Sharing.ModifySharedLinkSettingsErrorSerializer>
```

**Parameters:**
- `url` - URL of the shared link to change its settings.
- `settings` - Set of settings for the shared link.
- `removeExpiration` - If set to true, removes the expiration of the shared link.

**Returns:** `Sharing.SharedLinkMetadata` on success, `Sharing.ModifySharedLinkSettingsError` on failure.

---

## mountFolder

The current user mounts the designated folder. Mount a shared folder for a user after they have been added as a member. Once mounted, the shared folder will appear in their Dropbox.

**Scope:** `sharing.write`

```swift
@discardableResult public func mountFolder(
    sharedFolderId: String
) -> RpcRequest<Sharing.SharedFolderMetadataSerializer, Sharing.MountFolderErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID of the shared folder to mount.

**Returns:** `Sharing.SharedFolderMetadata` on success, `Sharing.MountFolderError` on failure.

---

## relinquishFileMembership

The current user relinquishes their membership in the designated file. Note that the current user may still have inherited access to this file through the parent folder.

**Scope:** `sharing.write`

```swift
@discardableResult public func relinquishFileMembership(
    file: String
) -> RpcRequest<VoidSerializer, Sharing.RelinquishFileMembershipErrorSerializer>
```

**Parameters:**
- `file` - The path or id for the file.

**Returns:** `Void` on success, `Sharing.RelinquishFileMembershipError` on failure.

---

## relinquishFolderMembership

The current user relinquishes their membership in the designated shared folder and will no longer have access to the folder. A folder owner cannot relinquish membership in their own folder. This will run synchronously if leave_a_copy is false, and asynchronously if leave_a_copy is true.

**Scope:** `sharing.write`

```swift
@discardableResult public func relinquishFolderMembership(
    sharedFolderId: String,
    leaveACopy: Bool = false
) -> RpcRequest<Async.LaunchEmptyResultSerializer, Sharing.RelinquishFolderMembershipErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `leaveACopy` - Keep a copy of the folder's contents upon relinquishing membership. This must be set to false when the folder is within a team folder or another shared folder.

**Returns:** `Async.LaunchEmptyResult` on success, `Sharing.RelinquishFolderMembershipError` on failure.

---

## removeFileMember

> **Deprecated:** removeFileMember is deprecated. Use removeFileMember2.

Identical to remove_file_member_2 but with less information returned.

**Scope:** `sharing.write`

```swift
@discardableResult public func removeFileMember(
    file: String,
    member: Sharing.MemberSelector
) -> RpcRequest<Sharing.FileMemberActionIndividualResultSerializer, Sharing.RemoveFileMemberErrorSerializer>
```

**Parameters:**
- `file` - File from which to remove members.
- `member` - Member to remove from this file. Note that even if an email is specified, it may result in the removal of a user (not an invitee) if the user's main account corresponds to that email address.

**Returns:** `Sharing.FileMemberActionIndividualResult` on success, `Sharing.RemoveFileMemberError` on failure.

---

## removeFileMember2

Removes a specified member from the file.

**Scope:** `sharing.write`

```swift
@discardableResult public func removeFileMember2(
    file: String,
    member: Sharing.MemberSelector
) -> RpcRequest<Sharing.FileMemberRemoveActionResultSerializer, Sharing.RemoveFileMemberErrorSerializer>
```

**Parameters:**
- `file` - File from which to remove members.
- `member` - Member to remove from this file. Note that even if an email is specified, it may result in the removal of a user (not an invitee) if the user's main account corresponds to that email address.

**Returns:** `Sharing.FileMemberRemoveActionResult` on success, `Sharing.RemoveFileMemberError` on failure.

---

## removeFolderMember

Allows an owner or editor (if the ACL update policy allows) of a shared folder to remove another member.

**Scope:** `sharing.write`

```swift
@discardableResult public func removeFolderMember(
    sharedFolderId: String,
    member: Sharing.MemberSelector,
    leaveACopy: Bool
) -> RpcRequest<Async.LaunchResultBaseSerializer, Sharing.RemoveFolderMemberErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `member` - The member to remove from the folder.
- `leaveACopy` - If true, the removed user will keep their copy of the folder after it's unshared, assuming it was mounted. Otherwise, it will be removed from their Dropbox. This must be set to false when removing a group, or when the folder is within a team folder or another shared folder.

**Returns:** `Async.LaunchResultBase` on success, `Sharing.RemoveFolderMemberError` on failure.

---

## revokeSharedLink

Revoke a shared link. Note that even after revoking a shared link to a file, the file may be accessible if there are shared links leading to any of the file parent folders. To list all shared links that enable access to a specific file, you can use the listSharedLinks with the file as the path in ListSharedLinksArg argument.

**Scope:** `sharing.write`

```swift
@discardableResult public func revokeSharedLink(
    url: String
) -> RpcRequest<VoidSerializer, Sharing.RevokeSharedLinkErrorSerializer>
```

**Parameters:**
- `url` - URL of the shared link.

**Returns:** `Void` on success, `Sharing.RevokeSharedLinkError` on failure.

---

## setAccessInheritance

Change the inheritance policy of an existing Shared Folder. Only permitted for shared folders in a shared team root. If a asyncJobId in ShareFolderLaunch is returned, you'll need to call checkShareJobStatus until the action completes to get the metadata for the folder.

**Scope:** `sharing.write`

```swift
@discardableResult public func setAccessInheritance(
    sharedFolderId: String,
    accessInheritance: Sharing.AccessInheritance = .inherit
) -> RpcRequest<Sharing.ShareFolderLaunchSerializer, Sharing.SetAccessInheritanceErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `accessInheritance` - The access inheritance settings for the folder.

**Returns:** `Sharing.ShareFolderLaunch` on success, `Sharing.SetAccessInheritanceError` on failure.

---

## shareFolder

Share a folder with collaborators. Most sharing will be completed synchronously. Large folders will be completed asynchronously. To make testing the async case repeatable, set `ShareFolderArg.force_async`. If a asyncJobId in ShareFolderLaunch is returned, you'll need to call checkShareJobStatus until the action completes to get the metadata for the folder.

**Scope:** `sharing.write`

```swift
@discardableResult public func shareFolder(
    path: String,
    aclUpdatePolicy: Sharing.AclUpdatePolicy? = nil,
    forceAsync: Bool = false,
    memberPolicy: Sharing.MemberPolicy? = nil,
    sharedLinkPolicy: Sharing.SharedLinkPolicy? = nil,
    viewerInfoPolicy: Sharing.ViewerInfoPolicy? = nil,
    accessInheritance: Sharing.AccessInheritance = .inherit,
    actions: [Sharing.FolderAction]? = nil,
    linkSettings: Sharing.LinkSettings? = nil
) -> RpcRequest<Sharing.ShareFolderLaunchSerializer, Sharing.ShareFolderErrorSerializer>
```

**Parameters:**
- `path` - The path of the folder to share.
- `aclUpdatePolicy` - Who can add and remove members of this shared folder.
- `forceAsync` - Whether to force the share to happen asynchronously.
- `memberPolicy` - Who can be a member of this shared folder. Only applicable if the current user is on a team.
- `sharedLinkPolicy` - The policy to apply to shared links created for content inside this shared folder.
- `viewerInfoPolicy` - Who can enable/disable viewer info for this shared folder.
- `accessInheritance` - The access inheritance settings for the folder.
- `actions` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.
- `linkSettings` - Settings on the link for this folder.

**Returns:** `Sharing.ShareFolderLaunch` on success, `Sharing.ShareFolderError` on failure.

---

## transferFolder

Transfer ownership of a shared folder to a member of the shared folder. User must have owner in AccessLevel access to the shared folder to perform a transfer.

**Scope:** `sharing.write`

```swift
@discardableResult public func transferFolder(
    sharedFolderId: String,
    toDropboxId: String
) -> RpcRequest<VoidSerializer, Sharing.TransferFolderErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `toDropboxId` - A account or team member ID to transfer ownership to.

**Returns:** `Void` on success, `Sharing.TransferFolderError` on failure.

---

## unmountFolder

The current user unmounts the designated folder. They can re-mount the folder at a later time using mountFolder.

**Scope:** `sharing.write`

```swift
@discardableResult public func unmountFolder(
    sharedFolderId: String
) -> RpcRequest<VoidSerializer, Sharing.UnmountFolderErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.

**Returns:** `Void` on success, `Sharing.UnmountFolderError` on failure.

---

## unshareFile

Remove all members from this file. Does not remove inherited members.

**Scope:** `sharing.write`

```swift
@discardableResult public func unshareFile(
    file: String
) -> RpcRequest<VoidSerializer, Sharing.UnshareFileErrorSerializer>
```

**Parameters:**
- `file` - The file to unshare.

**Returns:** `Void` on success, `Sharing.UnshareFileError` on failure.

---

## unshareFolder

Allows a shared folder owner to unshare the folder. You'll need to call checkJobStatus to determine if the action has completed successfully.

**Scope:** `sharing.write`

```swift
@discardableResult public func unshareFolder(
    sharedFolderId: String,
    leaveACopy: Bool = false
) -> RpcRequest<Async.LaunchEmptyResultSerializer, Sharing.UnshareFolderErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `leaveACopy` - If true, members of this shared folder will get a copy of this folder after it's unshared. Otherwise, it will be removed from their Dropbox. The current user, who is an owner, will always retain their copy.

**Returns:** `Async.LaunchEmptyResult` on success, `Sharing.UnshareFolderError` on failure.

---

## updateFileMember

Changes a member's access on a shared file.

**Scope:** `sharing.write`

```swift
@discardableResult public func updateFileMember(
    file: String,
    member: Sharing.MemberSelector,
    accessLevel: Sharing.AccessLevel
) -> RpcRequest<Sharing.MemberAccessLevelResultSerializer, Sharing.FileMemberActionErrorSerializer>
```

**Parameters:**
- `file` - File for which we are changing a member's access.
- `member` - The member whose access we are changing.
- `accessLevel` - The new access level for the member.

**Returns:** `Sharing.MemberAccessLevelResult` on success, `Sharing.FileMemberActionError` on failure.

---

## updateFolderMember

Allows an owner or editor of a shared folder to update another member's permissions.

**Scope:** `sharing.write`

```swift
@discardableResult public func updateFolderMember(
    sharedFolderId: String,
    member: Sharing.MemberSelector,
    accessLevel: Sharing.AccessLevel
) -> RpcRequest<Sharing.MemberAccessLevelResultSerializer, Sharing.UpdateFolderMemberErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `member` - The member of the shared folder to update. Only the dropboxId in MemberSelector may be set at this time.
- `accessLevel` - The new access level for member. owner in AccessLevel is disallowed.

**Returns:** `Sharing.MemberAccessLevelResult` on success, `Sharing.UpdateFolderMemberError` on failure.

---

## updateFolderPolicy

Update the sharing policies for a shared folder. User must have owner in AccessLevel access to the shared folder to update its policies.

**Scope:** `sharing.write`

```swift
@discardableResult public func updateFolderPolicy(
    sharedFolderId: String,
    memberPolicy: Sharing.MemberPolicy? = nil,
    aclUpdatePolicy: Sharing.AclUpdatePolicy? = nil,
    viewerInfoPolicy: Sharing.ViewerInfoPolicy? = nil,
    sharedLinkPolicy: Sharing.SharedLinkPolicy? = nil,
    linkSettings: Sharing.LinkSettings? = nil,
    actions: [Sharing.FolderAction]? = nil
) -> RpcRequest<Sharing.SharedFolderMetadataSerializer, Sharing.UpdateFolderPolicyErrorSerializer>
```

**Parameters:**
- `sharedFolderId` - The ID for the shared folder.
- `memberPolicy` - Who can be a member of this shared folder. Only applicable if the current user is on a team.
- `aclUpdatePolicy` - Who can add and remove members of this shared folder.
- `viewerInfoPolicy` - Who can enable/disable viewer info for this shared folder.
- `sharedLinkPolicy` - The policy to apply to shared links created for content inside this shared folder. The current user must be on a team to set this policy to members in SharedLinkPolicy.
- `linkSettings` - Settings on the link for this folder.
- `actions` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

**Returns:** `Sharing.SharedFolderMetadata` on success, `Sharing.UpdateFolderPolicyError` on failure.

---
