# Paper Data Types

Data types for the paper namespace.

## AddMember

The AddMember struct.

**Properties:**
- `permissionLevel: Paper.PaperDocPermissionLevel` - Permission for the user.
- `member: Sharing.MemberSelector` - User which should be added to the Paper doc. Specify only email address or Dropbox account ID.

---

## RefPaperDoc

The RefPaperDoc struct.

**Properties:**
- `docId: String` - The Paper doc ID.

---

## AddPaperDocUser

The AddPaperDocUser struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `members: [Paper.AddMember]` - User which should be added to the Paper doc. Specify only email address or Dropbox account ID.
- `customMessage: String?` - A personal message that will be emailed to each successfully added member.
- `quiet: Bool` - Clients should set this to true if no email message shall be sent to added users.

---

## AddPaperDocUserMemberResult

Per-member result for docsUsersAdd.

**Properties:**
- `member: Sharing.MemberSelector` - One of specified input members.
- `result: Paper.AddPaperDocUserResult` - The outcome of the action on this member.

---

## AddPaperDocUserResult

The AddPaperDocUserResult union.

**Cases:**
- `success` - User was successfully added to the Paper doc.
- `unknownError` - Something unexpected happened when trying to add the user to the Paper doc.
- `sharingOutsideTeamDisabled` - The Paper doc can be shared only with team members.
- `dailyLimitReached` - The daily limit of how many users can be added to the Paper doc was reached.
- `userIsOwner` - Owner's permissions cannot be changed.
- `failedUserDataRetrieval` - User data could not be retrieved. Clients should retry.
- `permissionAlreadyGranted` - This user already has the correct permission to the Paper doc.
- `other` - An unspecified error.

---

## Cursor

The Cursor struct.

**Properties:**
- `value: String` - The actual cursor value.
- `expiration: Date?` - Expiration time of value. Some cursors might have expiration time assigned. This is a UTC value after which the cursor is no longer valid and the API starts returning an error. If cursor expires a new one needs to be obtained and pagination needs to be restarted.

---

## PaperApiBaseError

The PaperApiBaseError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.

---

## DocLookupError

The DocLookupError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.
- `docNotFound` - The required doc was not found.

---

## DocSubscriptionLevel

The subscription level of a Paper doc.

**Cases:**
- `default_` - No change email messages unless you're the creator.
- `ignore` - Ignored: Not shown in pad lists or activity and no email message is sent.
- `every` - Subscribed: Shown in pad lists and activity and change email messages are sent.
- `noEmail` - Unsubscribed: Shown in pad lists, but not in activity and no change email messages are sent.

---

## ExportFormat

The desired export format of the Paper doc.

**Cases:**
- `html` - The HTML export format.
- `markdown` - The markdown export format.
- `other` - An unspecified error.

---

## Folder

Data structure representing a Paper folder.

**Properties:**
- `id: String` - Paper folder ID. This ID uniquely identifies the folder.
- `name: String` - Paper folder name.

---

## FolderSharingPolicyType

The sharing policy of a Paper folder. The sharing policy of subfolders is inherited from the root folder.

**Cases:**
- `team` - Everyone in your team and anyone directly invited can access this folder.
- `inviteOnly` - Only people directly invited can access this folder.

---

## FolderSubscriptionLevel

The subscription level of a Paper folder.

**Cases:**
- `none` - Not shown in activity, no email messages.
- `activityOnly` - Shown in activity, no email messages.
- `dailyEmails` - Shown in activity, daily email messages.
- `weeklyEmails` - Shown in activity, weekly email messages.

---

## FoldersContainingPaperDoc

Metadata about Paper folders containing the specified Paper doc.

**Properties:**
- `folderSharingPolicyType: Paper.FolderSharingPolicyType?` - The sharing policy of the folder containing the Paper doc.
- `folders: [Paper.Folder]?` - The folder path. If present the first folder is the root folder.

---

## ImportFormat

The import format of the incoming data.

**Cases:**
- `html` - The provided data is interpreted as standard HTML.
- `markdown` - The provided data is interpreted as markdown. The first line of the provided document will be used as the doc title.
- `plainText` - The provided data is interpreted as plain text. The first line of the provided document will be used as the doc title.
- `other` - An unspecified error.

---

## InviteeInfoWithPermissionLevel

The InviteeInfoWithPermissionLevel struct.

**Properties:**
- `invitee: Sharing.InviteeInfo` - Email address invited to the Paper doc.
- `permissionLevel: Paper.PaperDocPermissionLevel` - Permission level for the invitee.

---

## ListDocsCursorError

The ListDocsCursorError union.

**Cases:**
- `cursorError` - Paper.PaperApiCursorError
- `other` - An unspecified error.

---

## ListPaperDocsArgs

The ListPaperDocsArgs struct.

**Properties:**
- `filterBy: Paper.ListPaperDocsFilterBy` - Allows user to specify how the Paper docs should be filtered.
- `sortBy: Paper.ListPaperDocsSortBy` - Allows user to specify how the Paper docs should be sorted.
- `sortOrder: Paper.ListPaperDocsSortOrder` - Allows user to specify the sort order of the result.
- `limit: Int32` - Size limit per batch. The maximum number of docs that can be retrieved per batch is 1000. Higher value results in invalid arguments error.

---

## ListPaperDocsContinueArgs

The ListPaperDocsContinueArgs struct.

**Properties:**
- `cursor: String` - The cursor obtained from docsList or docsListContinue. Allows for pagination.

---

## ListPaperDocsFilterBy

The ListPaperDocsFilterBy union.

**Cases:**
- `docsAccessed` - Fetches all Paper doc IDs that the user has ever accessed.
- `docsCreated` - Fetches only the Paper doc IDs that the user has created.
- `other` - An unspecified error.

---

## ListPaperDocsResponse

The ListPaperDocsResponse struct.

**Properties:**
- `docIds: [String]` - The list of Paper doc IDs that can be used to access the given Paper docs or supplied to other API methods. The list is sorted in the order specified by the initial call to docsList.
- `cursor: Paper.Cursor` - Pass the cursor into docsListContinue to paginate through all files. The cursor preserves all properties as specified in the original call to docsList.
- `hasMore: Bool` - Will be set to True if a subsequent call with the provided cursor to docsListContinue returns immediately with some results.

---

## ListPaperDocsSortBy

The ListPaperDocsSortBy union.

**Cases:**
- `accessed` - Sorts the Paper docs by the time they were last accessed.
- `modified` - Sorts the Paper docs by the time they were last modified.
- `created` - Sorts the Paper docs by the creation time.
- `other` - An unspecified error.

---

## ListPaperDocsSortOrder

The ListPaperDocsSortOrder union.

**Cases:**
- `ascending` - Sorts the search result in ascending order.
- `descending` - Sorts the search result in descending order.
- `other` - An unspecified error.

---

## ListUsersCursorError

The ListUsersCursorError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.
- `docNotFound` - The required doc was not found.
- `cursorError` - Paper.PaperApiCursorError

---

## ListUsersOnFolderArgs

The ListUsersOnFolderArgs struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `limit: Int32` - Size limit per batch. The maximum number of users that can be retrieved per batch is 1000. Higher value results in invalid arguments error.

---

## ListUsersOnFolderContinueArgs

The ListUsersOnFolderContinueArgs struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `cursor: String` - The cursor obtained from docsFolderUsersList or docsFolderUsersListContinue. Allows for pagination.

---

## ListUsersOnFolderResponse

The ListUsersOnFolderResponse struct.

**Properties:**
- `invitees: [Sharing.InviteeInfo]` - List of email addresses that are invited on the Paper folder.
- `users: [Sharing.UserInfo]` - List of users that are invited on the Paper folder.
- `cursor: Paper.Cursor` - Pass the cursor into docsFolderUsersListContinue to paginate through all users. The cursor preserves all properties as specified in the original call to docsFolderUsersList.
- `hasMore: Bool` - Will be set to True if a subsequent call with the provided cursor to docsFolderUsersListContinue returns immediately with some results.

---

## ListUsersOnPaperDocArgs

The ListUsersOnPaperDocArgs struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `limit: Int32` - Size limit per batch. The maximum number of users that can be retrieved per batch is 1000. Higher value results in invalid arguments error.
- `filterBy: Paper.UserOnPaperDocFilter` - Specify this attribute if you want to obtain users that have already accessed the Paper doc.

---

## ListUsersOnPaperDocContinueArgs

The ListUsersOnPaperDocContinueArgs struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `cursor: String` - The cursor obtained from docsUsersList or docsUsersListContinue. Allows for pagination.

---

## ListUsersOnPaperDocResponse

The ListUsersOnPaperDocResponse struct.

**Properties:**
- `invitees: [Paper.InviteeInfoWithPermissionLevel]` - List of email addresses with their respective permission levels that are invited on the Paper doc.
- `users: [Paper.UserInfoWithPermissionLevel]` - List of users with their respective permission levels that are invited on the Paper folder.
- `docOwner: Sharing.UserInfo` - The Paper doc owner. This field is populated on every single response.
- `cursor: Paper.Cursor` - Pass the cursor into docsUsersListContinue to paginate through all users. The cursor preserves all properties as specified in the original call to docsUsersList.
- `hasMore: Bool` - Will be set to True if a subsequent call with the provided cursor to docsUsersListContinue returns immediately with some results.

---

## PaperApiCursorError

The PaperApiCursorError union.

**Cases:**
- `expiredCursor` - The provided cursor is expired.
- `invalidCursor` - The provided cursor is invalid.
- `wrongUserInCursor` - The provided cursor contains invalid user.
- `reset` - Indicates that the cursor has been invalidated. Call the corresponding non-continue endpoint to obtain a new cursor.
- `other` - An unspecified error.

---

## PaperDocCreateArgs

The PaperDocCreateArgs struct.

**Properties:**
- `parentFolderId: String?` - The Paper folder ID where the Paper document should be created. The API user has to have write access to this folder or error is thrown.
- `importFormat: Paper.ImportFormat` - The format of provided data.

---

## PaperDocCreateError

The PaperDocCreateError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.
- `contentMalformed` - The provided content was malformed and cannot be imported to Paper.
- `folderNotFound` - The specified Paper folder cannot be found.
- `docLengthExceeded` - The newly created Paper doc would be too large. Please split the content into multiple docs.
- `imageSizeExceeded` - The imported document contains an image that is too large. The current limit is 1MB. This only applies to HTML with data URI.

---

## PaperDocCreateUpdateResult

The PaperDocCreateUpdateResult struct.

**Properties:**
- `docId: String` - Doc ID of the newly created doc.
- `revision: Int64` - The Paper doc revision. Simply an ever increasing number.
- `title: String` - The Paper doc title.

---

## PaperDocExport

The PaperDocExport struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `exportFormat: Paper.ExportFormat` - The export format.

---

## PaperDocExportResult

The PaperDocExportResult struct.

**Properties:**
- `owner: String` - The Paper doc owner's email address.
- `title: String` - The Paper doc title.
- `revision: Int64` - The Paper doc revision. Simply an ever increasing number.
- `mimeType: String` - MIME type of the export. This corresponds to ExportFormat specified in the request.

---

## PaperDocPermissionLevel

The PaperDocPermissionLevel union.

**Cases:**
- `edit` - User will be granted edit permissions.
- `viewAndComment` - User will be granted view and comment permissions.
- `other` - An unspecified error.

---

## PaperDocSharingPolicy

The PaperDocSharingPolicy struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `sharingPolicy: Paper.SharingPolicy` - The default sharing policy to be set for the Paper doc.

---

## PaperDocUpdateArgs

The PaperDocUpdateArgs struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `docUpdatePolicy: Paper.PaperDocUpdatePolicy` - The policy used for the current update call.
- `revision: Int64` - The latest doc revision. This value must match the head revision or an error code will be returned. This is to prevent colliding writes.
- `importFormat: Paper.ImportFormat` - The format of provided data.

---

## PaperDocUpdateError

The PaperDocUpdateError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.
- `docNotFound` - The required doc was not found.
- `contentMalformed` - The provided content was malformed and cannot be imported to Paper.
- `revisionMismatch` - The provided revision does not match the document head.
- `docLengthExceeded` - The newly created Paper doc would be too large, split the content into multiple docs.
- `imageSizeExceeded` - The imported document contains an image that is too large. The current limit is 1MB. This only applies to HTML with data URI.
- `docArchived` - This operation is not allowed on archived Paper docs.
- `docDeleted` - This operation is not allowed on deleted Paper docs.

---

## PaperDocUpdatePolicy

The PaperDocUpdatePolicy union.

**Cases:**
- `append` - The content will be appended to the doc.
- `prepend` - The content will be prepended to the doc. The doc title will not be affected.
- `overwriteAll` - The document will be overwritten at the head with the provided content.
- `other` - An unspecified error.

---

## PaperFolderCreateArg

The PaperFolderCreateArg struct.

**Properties:**
- `name: String` - The name of the new Paper folder.
- `parentFolderId: String?` - The encrypted Paper folder Id where the new Paper folder should be created. The API user has to have write access to this folder or error is thrown. If not supplied, the new folder will be created at top level.
- `isTeamFolder: Bool?` - Whether the folder to be created should be a team folder. This value will be ignored if parent_folder_id is supplied, as the new folder will inherit the type (private or team folder) from its parent.

---

## PaperFolderCreateError

The PaperFolderCreateError union.

**Cases:**
- `insufficientPermissions` - Your account does not have permissions to perform this action. This may be due to it only having access to Paper as files in the Dropbox filesystem.
- `other` - An unspecified error.
- `folderNotFound` - The specified parent Paper folder cannot be found.
- `invalidFolderId` - The folder id cannot be decrypted to valid folder id.

---

## PaperFolderCreateResult

The PaperFolderCreateResult struct.

**Properties:**
- `folderId: String` - Folder ID of the newly created folder.

---

## RemovePaperDocUser

The RemovePaperDocUser struct. Inherits from RefPaperDoc.

**Properties:**
- `docId: String` - The Paper doc ID (inherited).
- `member: Sharing.MemberSelector` - User which should be removed from the Paper doc. Specify only email address or Dropbox account ID.

---

## SharingPolicy

Sharing policy of Paper doc.

**Properties:**
- `publicSharingPolicy: Paper.SharingPublicPolicyType?` - This value applies to the non-team members.
- `teamSharingPolicy: Paper.SharingTeamPolicyType?` - This value applies to the team members only. The value is null for all personal accounts.

---

## SharingTeamPolicyType

The sharing policy type of the Paper doc.

**Cases:**
- `peopleWithLinkCanEdit` - Users who have a link to this doc can edit it.
- `peopleWithLinkCanViewAndComment` - Users who have a link to this doc can view and comment on it.
- `inviteOnly` - Users must be explicitly invited to this doc.

---

## SharingPublicPolicyType

The SharingPublicPolicyType union.

**Cases:**
- `peopleWithLinkCanEdit` - Users who have a link to this doc can edit it.
- `peopleWithLinkCanViewAndComment` - Users who have a link to this doc can view and comment on it.
- `inviteOnly` - Users must be explicitly invited to this doc.
- `disabled` - Value used to indicate that doc sharing is enabled only within team.

---

## UserInfoWithPermissionLevel

The UserInfoWithPermissionLevel struct.

**Properties:**
- `user: Sharing.UserInfo` - User shared on the Paper doc.
- `permissionLevel: Paper.PaperDocPermissionLevel` - Permission level for the user.

---

## UserOnPaperDocFilter

The UserOnPaperDocFilter union.

**Cases:**
- `visited` - All users who have visited the Paper doc.
- `shared` - All users who are shared on the Paper doc. This includes all users who have visited the Paper doc as well as those who have not.
- `other` - An unspecified error.
