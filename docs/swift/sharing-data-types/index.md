# Sharing Data Types

Data types for the sharing namespace.

---

## AccessInheritance

The access inheritance settings for the folder.

- `inherit` - The folder inherits its members from its parent folder.
- `noInherit` - The folder does not inherit its members from its parent folder.
- `other` - An unspecified error.

---

## AccessLevel

Defines the access levels for collaborators.

- `owner` - The collaborator is the owner of the shared folder. Owners can view and edit the shared folder as well as set the folder's policies using updateFolderPolicy.
- `editor` - The collaborator can both view and edit the shared folder.
- `viewer` - The collaborator can only view the shared folder.
- `viewerNoComment` - The collaborator can only view the shared folder and does not have any access to comments.
- `traverse` - The collaborator can only view the shared folder and does not have any access to comments or the ability to preview files.
- `noAccess` - The collaborator has no access to the shared folder. This is only used for updating access.
- `other` - An unspecified error.

---

## AclUpdatePolicy

Who can change a shared folder's access control list (ACL). In other words, who can add, remove, or change the privileges of members.

- `owner` - Only the owner can update the ACL.
- `editors` - Any editor can update the ACL. This may be further restricted to editors on the same team.
- `other` - An unspecified error.

---

## AddFileMemberArgs

Arguments for addFileMember.

- `file: String` - File to which to add members.
- `members: [Sharing.MemberSelector]` - Members to add. Note that even an email address is given, this may result in a user being directly added to the membership if that email is the user's main account email.
- `customMessage: String?` - Message to send to added members in their invitation.
- `quiet: Bool` - Whether added members should be notified via email and device notifications of their invitation.
- `accessLevel: Sharing.AccessLevel` - AccessLevel union object, describing what access level we want to give new members.
- `addMessageAsComment: Bool` - If the custom message should be added as a comment on the file.

---

## AddFileMemberError

Errors for addFileMember.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `rateLimit` - The user has reached the rate limit for requests. The string value may indicate a reason.
- `invalidComment` - The custom message did not pass comment permissions checks.
- `other` - An unspecified error.

---

## AddFolderMemberArg

The AddFolderMemberArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `members: [Sharing.AddMember]` - The intended list of members to add. Added members will receive invites to join the shared folder.
- `quiet: Bool` - Whether added members should be notified via email and device notifications of their invite.
- `customMessage: String?` - Optional message to display to added members in their invitation.

---

## AddFolderMemberError

The AddFolderMemberError union.

- `accessError(Sharing.SharedFolderAccessError)` - Unable to access shared folder.
- `emailUnverified` - The current user's e-mail address is unverified.
- `bannedMember` - The current user has been banned.
- `badMember(Sharing.AddMemberSelectorError)` - The value is the member selector argument that is problematic.
- `cantShareOutsideTeam` - Your team policy does not allow sharing outside of the team.
- `tooManyMembers(UInt64)` - The value is the pending invite limit for this shared folder.
- `tooManyPendingInvites(UInt64)` - The value is the pending invite limit for this shared folder.
- `rateLimit` - The current user has hit the limit of invites they can send per day.
- `tooManyInvitees` - The current user is trying to share with too many people at once.
- `insufficientPlan` - The current user's account doesn't support this action.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `invalidSharedFolder` - Invalid shared folder error.
- `other` - An unspecified error.

---

## AddMember

The member and type of access the member should have when added to a shared folder.

- `member: Sharing.MemberSelector` - The member to add to the shared folder.
- `accessLevel: Sharing.AccessLevel` - The access level for the new member.

---

## AddMemberSelectorError

The AddMemberSelectorError union.

- `automaticGroup` - Automatically created groups can only be added to team folders.
- `invalidDropboxId(String)` - The value is the ID that could not be identified.
- `invalidEmail(String)` - The value is the e-email address that is malformed.
- `unverifiedDropboxId(String)` - The value is the ID of the Dropbox user with an unverified e-mail address.
- `groupDeleted` - At least one of the specified groups in the file has been deleted.
- `groupNotOnTeam` - Sharing to a group that is not on the current user's team.
- `other` - An unspecified error.

---

## RequestedVisibility

The access permission that can be requested by the caller for the shared link. Note that the final resolved visibility of the shared link takes into account other aspects, such as team and shared folder settings.

- `public_` - Anyone who has received the link can access it. No login required.
- `teamOnly` - Only members of the same team can access the link. Login is required.
- `password` - A link-specific password is required to access the link. Login is not required.

---

## ResolvedVisibility

The actual access permissions values of shared links after taking into account user preferences and the team and shared folder settings.

- `public_` - Anyone who has received the link can access it. No login required.
- `teamOnly` - Only members of the same team can access the link. Login is required.
- `password` - A link-specific password is required to access the link. Login is not required.
- `teamAndPassword` - Only members of the same team who have the link-specific password can access the link.
- `sharedFolderOnly` - Only members of the shared folder containing the linked file can access the link. Login is required.
- `noOne` - The link merely points the user to the content, and does not grant additional rights to the user.
- `onlyYou` - Only the current user can view this link.
- `other` - An unspecified error.

---

## AlphaResolvedVisibility

Check documentation for ResolvedVisibility.

- `public_` - Anyone who has received the link can access it. No login required.
- `teamOnly` - Only members of the same team can access the link. Login is required.
- `password` - A link-specific password is required to access the link. Login is not required.
- `teamAndPassword` - Only members of the same team who have the link-specific password can access the link.
- `sharedFolderOnly` - Only members of the shared folder containing the linked file can access the link. Login is required.
- `noOne` - The link merely points the user to the content, and does not grant additional rights to the user.
- `onlyYou` - Only the current user can view this link.
- `other` - An unspecified error.

---

## AudienceExceptionContentInfo

Information about the content that has a link audience different than that of this folder.

- `name: String` - The name of the content.

---

## AudienceExceptions

The AudienceExceptions struct.

- `count: UInt32` - (no description)
- `exceptions: [Sharing.AudienceExceptionContentInfo]` - A truncated list of some of the content that is an exception.

---

## AudienceRestrictingSharedFolder

Information about the shared folder that prevents the link audience for this link from being more restrictive.

- `sharedFolderId: String` - The ID of the shared folder.
- `name: String` - The name of the shared folder.
- `audience: Sharing.LinkAudience` - The link audience of the shared folder.

---

## LinkMetadata

Metadata for a shared link. This can be either a PathLinkMetadata or CollectionLinkMetadata.

- `url: String` - URL of the shared link.
- `visibility: Sharing.Visibility` - Who can access the link.
- `expires: Date?` - Expiration time, if set. By default the link won't expire.

---

## CollectionLinkMetadata

Metadata for a collection-based shared link. Inherits from LinkMetadata.

---

## CreateSharedLinkArg

The CreateSharedLinkArg struct.

- `path: String` - The path to share.
- `shortUrl: Bool` - (no description)
- `pendingUpload: Sharing.PendingUploadMode?` - If it's okay to share a path that does not yet exist, set this to either file in PendingUploadMode or folder in PendingUploadMode to indicate whether to assume it's a file or folder.

---

## CreateSharedLinkError

The CreateSharedLinkError union.

- `path(Files.LookupError)` - An unspecified error.
- `other` - An unspecified error.

---

## CreateSharedLinkWithSettingsArg

The CreateSharedLinkWithSettingsArg struct.

- `path: String` - The path to be shared by the shared link.
- `settings: Sharing.SharedLinkSettings?` - The requested settings for the newly created shared link.

---

## CreateSharedLinkWithSettingsError

The CreateSharedLinkWithSettingsError union.

- `path(Files.LookupError)` - An unspecified error.
- `emailNotVerified` - This user's email address is not verified. This functionality is only available on accounts with a verified email address.
- `sharedLinkAlreadyExists(Sharing.SharedLinkAlreadyExistsMetadata?)` - The shared link already exists. You can call listSharedLinks to get the existing link, or use the provided metadata if it is returned.
- `settingsError(Sharing.SharedLinkSettingsError)` - There is an error with the given settings.
- `accessDenied` - The user is not allowed to create a shared link to the specified file.

---

## SharedContentLinkMetadataBase

The SharedContentLinkMetadataBase struct.

- `accessLevel: Sharing.AccessLevel?` - The access level on the link for this file.
- `audienceOptions: [Sharing.LinkAudienceOption]` - The audience options that are available for the content.
- `audienceRestrictingSharedFolder: Sharing.AudienceRestrictingSharedFolder?` - The shared folder that prevents the link audience for this link from being more restrictive.
- `currentAudience: Sharing.LinkAudience` - The current audience of the link.
- `expiry: Date?` - Whether the link has an expiry set on it.
- `linkPermissions: [Sharing.LinkPermission]` - A list of permissions for actions you can perform on the link.
- `passwordProtected: Bool` - Whether the link is protected by a password.

---

## ExpectedSharedContentLinkMetadata

The expected metadata of a shared link for a file or folder when a link is first created for the content. Inherits from SharedContentLinkMetadataBase.

---

## FileAction

Sharing actions that may be taken on files.

- `disableViewerInfo` - Disable viewer information on the file.
- `editContents` - Change or edit contents of the file.
- `enableViewerInfo` - Enable viewer information on the file.
- `inviteViewer` - Add a member with view permissions.
- `inviteViewerNoComment` - Add a member with view permissions but no comment permissions.
- `inviteEditor` - Add a member with edit permissions.
- `unshare` - Stop sharing this file.
- `relinquishMembership` - Relinquish one's own membership to the file.
- `shareLink` - Use create_link instead.
- `createLink` - Create a shared link to the file.
- `createViewLink` - Create a shared link to the file (view only).
- `createEditLink` - Create a shared link to the file (view and edit).
- `other` - An unspecified error.

---

## FileErrorResult

The FileErrorResult union.

- `fileNotFoundError(String)` - File specified by id was not found.
- `invalidFileActionError(String)` - User does not have permission to take the specified action on the file.
- `permissionDeniedError(String)` - User does not have permission to access file specified by file.Id.
- `other` - An unspecified error.

---

## SharedLinkMetadata

The metadata of a shared link.

- `url: String` - URL of the shared link.
- `id: String?` - A unique identifier for the linked file.
- `name: String` - The linked file name (including extension). This never contains a slash.
- `expires: Date?` - Expiration time, if set. By default the link won't expire.
- `pathLower: String?` - The lowercased full path in the user's Dropbox. This always starts with a slash. This field will only be present only if the linked file is in the authenticated user's dropbox.
- `linkPermissions: Sharing.LinkPermissions` - The link's access permissions.
- `teamMemberInfo: Sharing.TeamMemberInfo?` - The team membership information of the link's owner. This field will only be present if the link's owner is a team member.
- `contentOwnerTeamInfo: Users.Team?` - The team information of the content's owner. This field will only be present if the content's owner is a team member and the content's owner team is different from the link's owner team.

---

## FileLinkMetadata

The metadata of a file shared link. Inherits from SharedLinkMetadata.

- `clientModified: Date` - The modification time set by the desktop client when the file was added to Dropbox.
- `serverModified: Date` - The last time the file was modified on Dropbox.
- `rev: String` - A unique identifier for the current revision of a file.
- `size: UInt64` - The file size in bytes.

---

## FileMemberActionError

The FileMemberActionError union.

- `invalidMember` - Specified member was not found.
- `noPermission` - User does not have permission to perform this action on this member.
- `accessError(Sharing.SharingFileAccessError)` - Specified file was invalid or user does not have access.
- `noExplicitAccess(Sharing.MemberAccessLevelResult)` - The action cannot be completed because the target member does not have explicit access to the file.
- `other` - An unspecified error.

---

## FileMemberActionIndividualResult

The FileMemberActionIndividualResult union.

- `success(Sharing.AccessLevel?)` - Member was successfully removed from this file. If AccessLevel is given, the member still has access via a parent shared folder.
- `memberError(Sharing.FileMemberActionError)` - User was not able to perform this action.

---

## FileMemberActionResult

Per-member result for addFileMember or changeFileMemberAccess.

- `member: Sharing.MemberSelector` - One of specified input members.
- `result: Sharing.FileMemberActionIndividualResult` - The outcome of the action on this member.

---

## FileMemberRemoveActionResult

The FileMemberRemoveActionResult union.

- `success(Sharing.MemberAccessLevelResult)` - Member was successfully removed from this file.
- `memberError(Sharing.FileMemberActionError)` - User was not able to remove this member.
- `other` - An unspecified error.

---

## FilePermission

Whether the user is allowed to take the sharing action on the file.

- `action: Sharing.FileAction` - The action that the user may wish to take on the file.
- `allow: Bool` - True if the user is allowed to take the action.
- `reason: Sharing.PermissionDeniedReason?` - The reason why the user is denied the permission. Not present if the action is allowed.

---

## FolderAction

Actions that may be taken on shared folders.

- `changeOptions` - Change folder options, such as who can be invited to join the folder.
- `disableViewerInfo` - Disable viewer information for this folder.
- `editContents` - Change or edit contents of the folder.
- `enableViewerInfo` - Enable viewer information on the folder.
- `inviteEditor` - Invite a user or group to join the folder with read and write permission.
- `inviteViewer` - Invite a user or group to join the folder with read permission.
- `inviteViewerNoComment` - Invite a user or group to join the folder with read permission but no comment permissions.
- `relinquishMembership` - Relinquish one's own membership in the folder.
- `unmount` - Unmount the folder.
- `unshare` - Stop sharing this folder.
- `leaveACopy` - Keep a copy of the contents upon leaving or being kicked from the folder.
- `shareLink` - Use create_link instead.
- `createLink` - Create a shared link for folder.
- `setAccessInheritance` - Set whether the folder inherits permissions from its parent.
- `other` - An unspecified error.

---

## FolderLinkMetadata

The metadata of a folder shared link. Inherits from SharedLinkMetadata.

---

## FolderPermission

Whether the user is allowed to take the action on the shared folder.

- `action: Sharing.FolderAction` - The action that the user may wish to take on the folder.
- `allow: Bool` - True if the user is allowed to take the action.
- `reason: Sharing.PermissionDeniedReason?` - The reason why the user is denied the permission. Not present if the action is allowed.

---

## FolderPolicy

A set of policies governing membership and privileges for a shared folder.

- `memberPolicy: Sharing.MemberPolicy?` - Who can be a member of this shared folder, as set on the folder itself. This is not considering any policies set on any ancestor.
- `resolvedMemberPolicy: Sharing.MemberPolicy?` - Who can be a member of this shared folder, taking into account both the folder and the team-level policy.
- `aclUpdatePolicy: Sharing.AclUpdatePolicy` - Who can add and remove members from this shared folder.
- `sharedLinkPolicy: Sharing.SharedLinkPolicy` - The policy governing who can view shared links.
- `viewerInfoPolicy: Sharing.ViewerInfoPolicy?` - Who can enable/disable viewer info for this shared folder.

---

## GetFileMetadataArg

Arguments of getFileMetadata.

- `file: String` - The file to query.
- `actions: [Sharing.FileAction]?` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions field describing the actions the authenticated user can perform on the file.

---

## GetFileMetadataBatchArg

Arguments of getFileMetadataBatch.

- `files: [String]` - The files to query.
- `actions: [Sharing.FileAction]?` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions field describing the actions the authenticated user can perform on the file.

---

## GetFileMetadataBatchResult

Per file results of getFileMetadataBatch.

- `file: String` - This is the input file identifier corresponding to one of the files in GetFileMetadataBatchArg.
- `result: Sharing.GetFileMetadataIndividualResult` - The result for this particular file.

---

## GetFileMetadataError

The GetFileMetadataError union.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `other` - An unspecified error.

---

## GetFileMetadataIndividualResult

The GetFileMetadataIndividualResult union.

- `metadata(Sharing.SharedFileMetadata)` - The result for this file if it was successful.
- `accessError(Sharing.SharingFileAccessError)` - The result for this file if it was an error.
- `other` - An unspecified error.

---

## GetMetadataArgs

The GetMetadataArgs struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `actions: [Sharing.FolderAction]?` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

---

## SharedLinkError

The SharedLinkError union.

- `sharedLinkNotFound` - The shared link wasn't found.
- `sharedLinkAccessDenied` - The caller is not allowed to access this shared link.
- `unsupportedLinkType` - This type of link is not supported; use files instead.
- `other` - An unspecified error.

---

## GetSharedLinkFileError

The GetSharedLinkFileError union.

- `sharedLinkNotFound` - The shared link wasn't found.
- `sharedLinkAccessDenied` - The caller is not allowed to access this shared link.
- `unsupportedLinkType` - This type of link is not supported; use files instead.
- `other` - An unspecified error.
- `sharedLinkIsDirectory` - Directories cannot be retrieved by this endpoint.

---

## GetSharedLinkMetadataArg

The GetSharedLinkMetadataArg struct.

- `url: String` - URL of the shared link.
- `path: String?` - If the shared link is to a folder, this parameter can be used to retrieve the metadata for a specific file or sub-folder in this folder. A relative path should be used.
- `linkPassword: String?` - If the shared link has a password, this parameter can be used.

---

## GetSharedLinksArg

The GetSharedLinksArg struct.

- `path: String?` - See getSharedLinks description.

---

## GetSharedLinksError

The GetSharedLinksError union.

- `path(String?)` - An unspecified error.
- `other` - An unspecified error.

---

## GetSharedLinksResult

The GetSharedLinksResult struct.

- `links: [Sharing.LinkMetadata]` - Shared links applicable to the path argument.

---

## GroupInfo

The information about a group. Groups is a way to manage a list of users who need same access permission to the shared folder. Inherits from TeamCommon.GroupSummary.

- `groupType: TeamCommon.GroupType` - The type of group.
- `isMember: Bool` - If the current user is a member of the group.
- `isOwner: Bool` - If the current user is an owner of the group.
- `sameTeam: Bool` - If the group is owned by the current user's team.

---

## MembershipInfo

The information about a member of the shared content.

- `accessType: Sharing.AccessLevel` - The access type for this member. It contains inherited access type if the member has inherited permissions.
- `permissions: [Sharing.MemberPermission]?` - The permissions that requesting user has on this member.
- `initials: String?` - Never set.
- `isInherited: Bool` - True if the member has access from a parent folder.

---

## GroupMembershipInfo

The information about a group member of the shared content. Inherits from MembershipInfo.

- `group: Sharing.GroupInfo` - The information about the membership group.

---

## InsufficientPlan

The InsufficientPlan struct.

- `message: String` - A message to tell the user to upgrade in order to support expected action.
- `upsellUrl: String?` - A URL to send the user to in order to obtain the account type they need, e.g. upgrading.

---

## InsufficientQuotaAmounts

The InsufficientQuotaAmounts struct.

- `spaceNeeded: UInt64` - The amount of space needed to add the item (the size of the item).
- `spaceShortage: UInt64` - The amount of extra space needed to add the item.
- `spaceLeft: UInt64` - The amount of space left in the user's Dropbox, less than spaceNeeded.

---

## InviteeInfo

Information about the recipient of a shared content invitation.

- `email(String)` - E-mail address of invited user.
- `other` - An unspecified error.

---

## InviteeMembershipInfo

Information about an invited member of a shared content. Inherits from MembershipInfo.

- `invitee: Sharing.InviteeInfo` - Recipient of the invitation.
- `user: Sharing.UserInfo?` - The user this invitation is tied to, if available.

---

## JobError

Error occurred while performing an asynchronous job from unshareFolder or removeFolderMember.

- `unshareFolderError(Sharing.UnshareFolderError)` - Error occurred while performing unshareFolder action.
- `removeFolderMemberError(Sharing.RemoveFolderMemberError)` - Error occurred while performing removeFolderMember action.
- `relinquishFolderMembershipError(Sharing.RelinquishFolderMembershipError)` - Error occurred while performing relinquishFolderMembership action.
- `other` - An unspecified error.

---

## JobStatus

The JobStatus union.

- `inProgress` - The asynchronous job is still in progress.
- `complete` - The asynchronous job has finished.
- `failed(Sharing.JobError)` - The asynchronous job returned an error.

---

## LinkAccessLevel

The LinkAccessLevel union.

- `viewer` - Users who use the link can view and comment on the content.
- `editor` - Users who use the link can edit, view and comment on the content.
- `other` - An unspecified error.

---

## LinkAction

Actions that can be performed on a link.

- `changeAccessLevel` - Change the access level of the link.
- `changeAudience` - Change the audience of the link.
- `removeExpiry` - Remove the expiry date of the link.
- `removePassword` - Remove the password of the link.
- `setExpiry` - Set or change the expiry date of the link.
- `setPassword` - Set or change the password of the link.
- `other` - An unspecified error.

---

## LinkAudience

The LinkAudience union.

- `public_` - Link is accessible by anyone.
- `team` - Link is accessible only by team members.
- `noOne` - The link can be used by no one. The link merely points the user to the content, and does not grant additional rights to the user.
- `password` - A link-specific password is required to access the link.
- `members` - Link is accessible only by members of the content.
- `other` - An unspecified error.

---

## VisibilityPolicyDisallowedReason

The VisibilityPolicyDisallowedReason union.

- `deleteAndRecreate` - The user needs to delete and recreate the link to change the visibility policy.
- `restrictedBySharedFolder` - The parent shared folder restricts sharing of links outside the shared folder.
- `restrictedByTeam` - The team policy prevents links being shared outside the team.
- `userNotOnTeam` - The user needs to be on a team to set this policy.
- `userAccountType` - The user is a basic user or is on a limited team.
- `permissionDenied` - The user does not have permission.
- `other` - An unspecified error.

---

## LinkAudienceDisallowedReason

Check documentation for VisibilityPolicyDisallowedReason.

- `deleteAndRecreate` - The user needs to delete and recreate the link to change the visibility policy.
- `restrictedBySharedFolder` - The parent shared folder restricts sharing of links outside the shared folder.
- `restrictedByTeam` - The team policy prevents links being shared outside the team.
- `userNotOnTeam` - The user needs to be on a team to set this policy.
- `userAccountType` - The user is a basic user or is on a limited team.
- `permissionDenied` - The user does not have permission.
- `other` - An unspecified error.

---

## LinkAudienceOption

The LinkAudienceOption struct.

- `audience: Sharing.LinkAudience` - Specifies who can access the link.
- `allowed: Bool` - Whether the user calling this API can select this audience option.
- `disallowedReason: Sharing.LinkAudienceDisallowedReason?` - If allowed is false, this will provide the reason that the user is not permitted to set the visibility to this policy.

---

## LinkExpiry

The LinkExpiry union.

- `removeExpiry` - Remove the currently set expiry for the link.
- `setExpiry(Date)` - Set a new expiry or change an existing expiry.
- `other` - An unspecified error.

---

## LinkPassword

The LinkPassword union.

- `removePassword` - Remove the currently set password for the link.
- `setPassword(String)` - Set a new password or change an existing password.
- `other` - An unspecified error.

---

## LinkPermission

The LinkPermission struct.

- `action: Sharing.LinkAction` - (no description)
- `allow: Bool` - (no description)
- `reason: Sharing.PermissionDeniedReason?` - (no description)

---

## LinkPermissions

The LinkPermissions struct.

- `resolvedVisibility: Sharing.ResolvedVisibility?` - The current visibility of the link after considering the shared links policies of the the team (in case the link's owner is part of a team) and the shared folder (in case the linked file is part of a shared folder).
- `requestedVisibility: Sharing.RequestedVisibility?` - The shared link's requested visibility.
- `canRevoke: Bool` - Whether the caller can revoke the shared link.
- `revokeFailureReason: Sharing.SharedLinkAccessFailureReason?` - The failure reason for revoking the link.
- `effectiveAudience: Sharing.LinkAudience?` - The type of audience who can benefit from the access level specified by the `link_access_level` field.
- `linkAccessLevel: Sharing.LinkAccessLevel?` - The access level that the link will grant to its users.
- `visibilityPolicies: [Sharing.VisibilityPolicy]` - A list of policies that the user might be able to set for the visibility.
- `canSetExpiry: Bool?` - Whether the user can set the expiry settings of the link.
- `canRemoveExpiry: Bool?` - Whether the user can remove the expiry of the link.
- `allowDownload: Bool?` - Whether the link can be used for downloads.
- `canAllowDownload: Bool?` - Whether the user can allow downloads via the link.
- `canDisallowDownload: Bool?` - Whether the user can disallow downloads via the link.
- `allowComments: Bool?` - Whether comments are enabled for the linked file.
- `teamRestrictsComments: Bool?` - Whether the team has disabled commenting globally.

---

## LinkSettings

Settings that apply to a link.

- `accessLevel: Sharing.AccessLevel?` - The access level on the link for this file.
- `audience: Sharing.LinkAudience?` - The type of audience on the link for this file.
- `expiry: Sharing.LinkExpiry?` - An expiry timestamp to set on a link.
- `password: Sharing.LinkPassword?` - The password for the link.

---

## ListFileMembersArg

Arguments for listFileMembers.

- `file: String` - The file for which you want to see members.
- `actions: [Sharing.FileAction]?` - The actions for which to return permissions on a member.
- `includeInherited: Bool` - Whether to include members who only have access from a parent shared folder.
- `limit: UInt32` - Number of members to return max per query.

---

## ListFileMembersBatchArg

Arguments for listFileMembersBatch.

- `files: [String]` - Files for which to return members.
- `limit: UInt32` - Number of members to return max per query.

---

## ListFileMembersBatchResult

Per-file result for listFileMembersBatch.

- `file: String` - This is the input file identifier.
- `result: Sharing.ListFileMembersIndividualResult` - The result for this particular file.

---

## ListFileMembersContinueArg

Arguments for listFileMembersContinue.

- `cursor: String` - The cursor returned by your last call to listFileMembers, listFileMembersContinue, or listFileMembersBatch.

---

## ListFileMembersContinueError

Error for listFileMembersContinue.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## ListFileMembersCountResult

The ListFileMembersCountResult struct.

- `members: Sharing.SharedFileMembers` - A list of members on this file.
- `memberCount: UInt32` - The number of members on this file. This does not include inherited members.

---

## ListFileMembersError

Error for listFileMembers.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `other` - An unspecified error.

---

## ListFileMembersIndividualResult

The ListFileMembersIndividualResult union.

- `result(Sharing.ListFileMembersCountResult)` - The results of the query for this file if it was successful.
- `accessError(Sharing.SharingFileAccessError)` - The result of the query for this file if it was an error.
- `other` - An unspecified error.

---

## ListFilesArg

Arguments for listReceivedFiles.

- `limit: UInt32` - Number of files to return max per query.
- `actions: [Sharing.FileAction]?` - A list of `FileAction`s corresponding to `FilePermission`s that should appear in the response's permissions field.

---

## ListFilesContinueArg

Arguments for listReceivedFilesContinue.

- `cursor: String` - Cursor in cursor returned by listReceivedFiles or listReceivedFilesContinue.

---

## ListFilesContinueError

Error results for listReceivedFilesContinue.

- `userError(Sharing.SharingUserError)` - User account had a problem.
- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## ListFilesResult

Success results for listReceivedFiles.

- `entries: [Sharing.SharedFileMetadata]` - Information about the files shared with current user.
- `cursor: String?` - Cursor used to obtain additional shared files.

---

## ListFolderMembersCursorArg

The ListFolderMembersCursorArg struct.

- `actions: [Sharing.MemberAction]?` - This is a list indicating whether each returned member will include a boolean value allow that describes whether the current user can perform the MemberAction on the member.
- `limit: UInt32` - The maximum number of results that include members, groups and invitees to return per request.

---

## ListFolderMembersArgs

The ListFolderMembersArgs struct. Inherits from ListFolderMembersCursorArg.

- `sharedFolderId: String` - The ID for the shared folder.

---

## ListFolderMembersContinueArg

The ListFolderMembersContinueArg struct.

- `cursor: String` - The cursor returned by your last call to listFolderMembers or listFolderMembersContinue.

---

## ListFolderMembersContinueError

The ListFolderMembersContinueError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## ListFoldersArgs

The ListFoldersArgs struct.

- `limit: UInt32` - The maximum number of results to return per request.
- `actions: [Sharing.FolderAction]?` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions field.

---

## ListFoldersContinueArg

The ListFoldersContinueArg struct.

- `cursor: String` - The cursor returned by your last call to listFolders or listFoldersContinue.

---

## ListFoldersContinueError

The ListFoldersContinueError union.

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## ListFoldersResult

Result for listFolders or listMountableFolders, depending on which endpoint was requested.

- `entries: [Sharing.SharedFolderMetadata]` - List of all shared folders the authenticated user has access to.
- `cursor: String?` - Present if there are additional shared folders that have not been returned yet.

---

## ListSharedLinksArg

The ListSharedLinksArg struct.

- `path: String?` - See listSharedLinks description.
- `cursor: String?` - The cursor returned by your last call to listSharedLinks.
- `directOnly: Bool?` - See listSharedLinks description.

---

## ListSharedLinksError

The ListSharedLinksError union.

- `path(Files.LookupError)` - An unspecified error.
- `reset` - Indicates that the cursor has been invalidated.
- `other` - An unspecified error.

---

## ListSharedLinksResult

The ListSharedLinksResult struct.

- `links: [Sharing.SharedLinkMetadata]` - Shared links applicable to the path argument.
- `hasMore: Bool` - Is true if there are additional shared links that have not been returned yet.
- `cursor: String?` - Pass the cursor into listSharedLinks to obtain the additional links.

---

## MemberAccessLevelResult

Contains information about a member's access level.

- `accessLevel: Sharing.AccessLevel?` - The member still has this level of access to the content through a parent shared folder.
- `warning: String?` - A localized string with additional information about why the user has this access level to the content.
- `accessDetails: [Sharing.ParentFolderAccessInfo]?` - The parent folders that a member has access to.

---

## MemberAction

Actions that may be taken on members of a shared folder.

- `leaveACopy` - Allow the member to keep a copy of the folder when removing.
- `makeEditor` - Make the member an editor of the folder.
- `makeOwner` - Make the member an owner of the folder.
- `makeViewer` - Make the member a viewer of the folder.
- `makeViewerNoComment` - Make the member a viewer of the folder without commenting permissions.
- `removeMember` - Remove the member from the folder.
- `other` - An unspecified error.

---

## MemberPermission

Whether the user is allowed to take the action on the associated member.

- `action: Sharing.MemberAction` - The action that the user may wish to take on the member.
- `allow: Bool` - True if the user is allowed to take the action.
- `reason: Sharing.PermissionDeniedReason?` - The reason why the user is denied the permission. Not present if the action is allowed.

---

## MemberPolicy

Policy governing who can be a member of a shared folder. Only applicable to folders owned by a user on a team.

- `team` - Only a teammate can become a member.
- `anyone` - Anyone can become a member.
- `other` - An unspecified error.

---

## MemberSelector

Includes different ways to identify a member of a shared folder.

- `dropboxId(String)` - Dropbox account, team member, or group ID of member.
- `email(String)` - E-mail address of member.
- `other` - An unspecified error.

---

## ModifySharedLinkSettingsArgs

The ModifySharedLinkSettingsArgs struct.

- `url: String` - URL of the shared link to change its settings.
- `settings: Sharing.SharedLinkSettings` - Set of settings for the shared link.
- `removeExpiration: Bool` - If set to true, removes the expiration of the shared link.

---

## ModifySharedLinkSettingsError

The ModifySharedLinkSettingsError union.

- `sharedLinkNotFound` - The shared link wasn't found.
- `sharedLinkAccessDenied` - The caller is not allowed to access this shared link.
- `unsupportedLinkType` - This type of link is not supported; use files instead.
- `other` - An unspecified error.
- `settingsError(Sharing.SharedLinkSettingsError)` - There is an error with the given settings.
- `emailNotVerified` - The caller's email should be verified.

---

## MountFolderArg

The MountFolderArg struct.

- `sharedFolderId: String` - The ID of the shared folder to mount.

---

## MountFolderError

The MountFolderError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `insideSharedFolder` - Mounting would cause a shared folder to be inside another, which is disallowed.
- `insufficientQuota(Sharing.InsufficientQuotaAmounts)` - The current user does not have enough space to mount the shared folder.
- `alreadyMounted` - The shared folder is already mounted.
- `noPermission` - The current user does not have permission to perform this action.
- `notMountable` - The shared folder is not mountable.
- `other` - An unspecified error.

---

## ParentFolderAccessInfo

Contains information about a parent folder's access to a member.

- `folderName: String` - Display name for the folder.
- `sharedFolderId: String` - The identifier of the parent shared folder.
- `permissions: [Sharing.MemberPermission]` - The user's permissions for the parent shared folder.
- `path: String` - The full path to the parent shared folder relative to the acting user's root.

---

## PathLinkMetadata

Metadata for a path-based shared link. Inherits from LinkMetadata.

- `path: String` - Path in user's Dropbox.

---

## PendingUploadMode

Flag to indicate pending upload default.

- `file` - Assume pending uploads are files.
- `folder` - Assume pending uploads are folders.

---

## PermissionDeniedReason

Possible reasons the user is denied a permission.

- `userNotSameTeamAsOwner` - User is not on the same team as the folder owner.
- `userNotAllowedByOwner` - User is prohibited by the owner from taking the action.
- `targetIsIndirectMember` - Target is indirectly a member of the folder.
- `targetIsOwner` - Target is the owner of the folder.
- `targetIsSelf` - Target is the user itself.
- `targetNotActive` - Target is not an active member of the team.
- `folderIsLimitedTeamFolder` - Folder is team folder for a limited team.
- `ownerNotOnTeam` - The content owner needs to be on a Dropbox team to perform this action.
- `permissionDenied` - The user does not have permission to perform this action on the link.
- `restrictedByTeam` - The user's team policy prevents performing this action on the link.
- `userAccountType` - The user's account type does not support this action.
- `userNotOnTeam` - The user needs to be on a Dropbox team to perform this action.
- `folderIsInsideSharedFolder` - Folder is inside of another shared folder.
- `restrictedByParentFolder` - Policy cannot be changed due to restrictions from parent folder.
- `insufficientPlan(Sharing.InsufficientPlan)` - An unspecified error.
- `other` - An unspecified error.

---

## RelinquishFileMembershipArg

The RelinquishFileMembershipArg struct.

- `file: String` - The path or id for the file.

---

## RelinquishFileMembershipError

The RelinquishFileMembershipError union.

- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `groupAccess` - The current user has access to the shared file via a group. You can't relinquish membership to a file shared via groups.
- `noPermission` - The current user does not have permission to perform this action.
- `other` - An unspecified error.

---

## RelinquishFolderMembershipArg

The RelinquishFolderMembershipArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `leaveACopy: Bool` - Keep a copy of the folder's contents upon relinquishing membership.

---

## RelinquishFolderMembershipError

The RelinquishFolderMembershipError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `folderOwner` - The current user is the owner of the shared folder. Owners cannot relinquish membership to their own folders.
- `mounted` - The shared folder is currently mounted.
- `groupAccess` - The current user has access to the shared folder via a group.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `noExplicitAccess` - The current user only has inherited access to the shared folder.
- `other` - An unspecified error.

---

## RemoveFileMemberArg

Arguments for removeFileMember2.

- `file: String` - File from which to remove members.
- `member: Sharing.MemberSelector` - Member to remove from this file.

---

## RemoveFileMemberError

Errors for removeFileMember2.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `noExplicitAccess(Sharing.MemberAccessLevelResult)` - This member does not have explicit access to the file and therefore cannot be removed.
- `other` - An unspecified error.

---

## RemoveFolderMemberArg

The RemoveFolderMemberArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `member: Sharing.MemberSelector` - The member to remove from the folder.
- `leaveACopy: Bool` - If true, the removed user will keep their copy of the folder after it's unshared, assuming it was mounted. Otherwise, it will be removed from their Dropbox.

---

## RemoveFolderMemberError

The RemoveFolderMemberError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `memberError(Sharing.SharedFolderMemberError)` - An unspecified error.
- `folderOwner` - The target user is the owner of the shared folder. You can't remove this user until you transfer ownership to another member.
- `groupAccess` - The target user has access to the shared folder via a group.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `tooManyFiles` - This shared folder has too many files for leaving a copy.
- `other` - An unspecified error.

---

## RemoveMemberJobStatus

The RemoveMemberJobStatus union.

- `inProgress` - The asynchronous job is still in progress.
- `complete(Sharing.MemberAccessLevelResult)` - Removing the folder member has finished.
- `failed(Sharing.RemoveFolderMemberError)` - An unspecified error.

---

## RequestedLinkAccessLevel

The RequestedLinkAccessLevel union.

- `viewer` - Users who use the link can view and comment on the content.
- `editor` - Users who use the link can edit, view and comment on the content. Note, editing permissions are not supported for all file types.
- `max` - Request for the maximum access level you can set the link to.
- `default_` - Request for the default access level the user has set.
- `other` - An unspecified error.

---

## RevokeSharedLinkArg

The RevokeSharedLinkArg struct.

- `url: String` - URL of the shared link.

---

## RevokeSharedLinkError

The RevokeSharedLinkError union.

- `sharedLinkNotFound` - The shared link wasn't found.
- `sharedLinkAccessDenied` - The caller is not allowed to access this shared link.
- `unsupportedLinkType` - This type of link is not supported; use files instead.
- `other` - An unspecified error.
- `sharedLinkMalformed` - Shared link is malformed.

---

## SetAccessInheritanceArg

The SetAccessInheritanceArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `accessInheritance: Sharing.AccessInheritance` - The access inheritance settings for the folder.

---

## SetAccessInheritanceError

The SetAccessInheritanceError union.

- `accessError(Sharing.SharedFolderAccessError)` - Unable to access shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `other` - An unspecified error.

---

## ShareFolderArgBase

The ShareFolderArgBase struct.

- `path: String` - The path or the file id to the folder to share. If it does not exist, then a new one is created.
- `aclUpdatePolicy: Sharing.AclUpdatePolicy?` - Who can add and remove members of this shared folder.
- `forceAsync: Bool` - Whether to force the share to happen asynchronously.
- `memberPolicy: Sharing.MemberPolicy?` - Who can be a member of this shared folder. Only applicable if the current user is on a team.
- `sharedLinkPolicy: Sharing.SharedLinkPolicy?` - The policy to apply to shared links created for content inside this shared folder.
- `viewerInfoPolicy: Sharing.ViewerInfoPolicy?` - Who can enable/disable viewer info for this shared folder.
- `accessInheritance: Sharing.AccessInheritance` - The access inheritance settings for the folder.

---

## ShareFolderArg

The ShareFolderArg struct. Inherits from ShareFolderArgBase.

- `actions: [Sharing.FolderAction]?` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions field.
- `linkSettings: Sharing.LinkSettings?` - Settings on the link for this folder.

---

## ShareFolderErrorBase

The ShareFolderErrorBase union.

- `emailUnverified` - This user's email address is not verified.
- `badPath(Sharing.SharePathError)` - The path is not valid.
- `teamPolicyDisallowsMemberPolicy` - Team policy is more restrictive than memberPolicy in ShareFolderArg.
- `disallowedSharedLinkPolicy` - The current account is not allowed to select the specified sharedLinkPolicy in ShareFolderArg.
- `other` - An unspecified error.

---

## ShareFolderError

The ShareFolderError union.

- `emailUnverified` - This user's email address is not verified.
- `badPath(Sharing.SharePathError)` - The path is not valid.
- `teamPolicyDisallowsMemberPolicy` - Team policy is more restrictive than memberPolicy in ShareFolderArg.
- `disallowedSharedLinkPolicy` - The current account is not allowed to select the specified sharedLinkPolicy in ShareFolderArg.
- `other` - An unspecified error.
- `noPermission` - The current user does not have permission to perform this action.

---

## ShareFolderJobStatus

The ShareFolderJobStatus union.

- `inProgress` - The asynchronous job is still in progress.
- `complete(Sharing.SharedFolderMetadata)` - The share job has finished.
- `failed(Sharing.ShareFolderError)` - An unspecified error.

---

## ShareFolderLaunch

The ShareFolderLaunch union.

- `asyncJobId(String)` - This response indicates that the processing is asynchronous.
- `complete(Sharing.SharedFolderMetadata)` - An unspecified error.

---

## SharePathError

The SharePathError union.

- `isFile` - A file is at the specified path.
- `insideSharedFolder` - We do not support sharing a folder inside a shared folder.
- `containsSharedFolder` - We do not support shared folders that contain shared folders.
- `containsAppFolder` - We do not support shared folders that contain app folders.
- `containsTeamFolder` - We do not support shared folders that contain team folders.
- `isAppFolder` - We do not support sharing an app folder.
- `insideAppFolder` - We do not support sharing a folder inside an app folder.
- `isPublicFolder` - A public folder can't be shared this way.
- `insidePublicFolder` - A folder inside a public folder can't be shared this way.
- `alreadyShared(Sharing.SharedFolderMetadata)` - Folder is already shared.
- `invalidPath` - Path is not valid.
- `isOsxPackage` - We do not support sharing a Mac OS X package.
- `insideOsxPackage` - We do not support sharing a folder inside a Mac OS X package.
- `other` - An unspecified error.

---

## SharedContentLinkMetadata

The SharedContentLinkMetadata struct. Inherits from SharedContentLinkMetadataBase.

- `audienceExceptions: Sharing.AudienceExceptions?` - The content inside this folder with link audience different than this folder's.
- `url: String` - The URL of the link.

---

## SharedFileMembers

Shared file user, group, and invitee membership.

- `users: [Sharing.UserFileMembershipInfo]` - The list of user members of the shared file.
- `groups: [Sharing.GroupMembershipInfo]` - The list of group members of the shared file.
- `invitees: [Sharing.InviteeMembershipInfo]` - The list of invited members of a file, but have not logged in and claimed this.
- `cursor: String?` - Present if there are additional shared file members that have not been returned yet.

---

## SharedFileMetadata

Properties of the shared file.

- `id: String?` - The ID of the file.
- `name: String` - The name of this file.
- `policy: Sharing.FolderPolicy` - Policies governing this shared file.
- `previewUrl: String` - URL for displaying a web preview of the shared file.
- `accessType: Sharing.AccessLevel?` - The current user's access level for this shared file.
- `expectedLinkMetadata: Sharing.ExpectedSharedContentLinkMetadata?` - The expected metadata of the link associated for the file when it is first shared.
- `linkMetadata: Sharing.SharedContentLinkMetadata?` - The metadata of the link associated for the file.
- `ownerDisplayNames: [String]?` - The display names of the users that own the file.
- `ownerTeam: Users.Team?` - The team that owns the file.
- `parentSharedFolderId: String?` - The ID of the parent shared folder.
- `pathDisplay: String?` - The cased path to be used for display purposes only.
- `pathLower: String?` - The lower-case full path of this file.
- `permissions: [Sharing.FilePermission]?` - The sharing permissions that requesting user has on this file.
- `timeInvited: Date?` - Timestamp indicating when the current user was invited to this shared file.

---

## SharedFolderAccessError

There is an error accessing the shared folder.

- `invalidId` - This shared folder ID is invalid.
- `notAMember` - The user is not a member of the shared folder thus cannot access it.
- `emailUnverified` - Never set.
- `unmounted` - The shared folder is unmounted.
- `other` - An unspecified error.

---

## SharedFolderMemberError

The SharedFolderMemberError union.

- `invalidDropboxId` - The target dropbox_id is invalid.
- `notAMember` - The target dropbox_id is not a member of the shared folder.
- `noExplicitAccess(Sharing.MemberAccessLevelResult)` - The target member only has inherited access to the shared folder.
- `other` - An unspecified error.

---

## SharedFolderMembers

Shared folder user and group membership.

- `users: [Sharing.UserMembershipInfo]` - The list of user members of the shared folder.
- `groups: [Sharing.GroupMembershipInfo]` - The list of group members of the shared folder.
- `invitees: [Sharing.InviteeMembershipInfo]` - The list of invitees to the shared folder.
- `cursor: String?` - Present if there are additional shared folder members that have not been returned yet.

---

## SharedFolderMetadataBase

Properties of the shared folder.

- `accessType: Sharing.AccessLevel` - The current user's access level for this shared folder.
- `isInsideTeamFolder: Bool` - Whether this folder is inside of a team folder.
- `isTeamFolder: Bool` - Whether this folder is a team folder.
- `ownerDisplayNames: [String]?` - The display names of the users that own the file.
- `ownerTeam: Users.Team?` - The team that owns the file.
- `parentSharedFolderId: String?` - The ID of the parent shared folder.
- `pathDisplay: String?` - The cased path to be used for display purposes only.
- `pathLower: String?` - The lower-case full path of this folder.
- `parentFolderName: String?` - Display name for the parent folder.

---

## SharedFolderMetadata

The metadata which includes basic information about the shared folder. Inherits from SharedFolderMetadataBase.

- `linkMetadata: Sharing.SharedContentLinkMetadata?` - The metadata of the shared content link to this shared folder.
- `name: String` - The name of the this shared folder.
- `permissions: [Sharing.FolderPermission]?` - Actions the current user may perform on the folder and its contents.
- `policy: Sharing.FolderPolicy` - Policies governing this shared folder.
- `previewUrl: String` - URL for displaying a web preview of the shared folder.
- `sharedFolderId: String` - The ID of the shared folder.
- `timeInvited: Date` - Timestamp indicating when the current user was invited to this shared folder.
- `accessInheritance: Sharing.AccessInheritance` - Whether the folder inherits its members from its parent.

---

## SharedLinkAccessFailureReason

The SharedLinkAccessFailureReason union.

- `loginRequired` - User is not logged in.
- `emailVerifyRequired` - User's email is not verified.
- `passwordRequired` - The link is password protected.
- `teamOnly` - Access is allowed for team members only.
- `ownerOnly` - Access is allowed for the shared link's owner only.
- `other` - An unspecified error.

---

## SharedLinkAlreadyExistsMetadata

The SharedLinkAlreadyExistsMetadata union.

- `metadata(Sharing.SharedLinkMetadata)` - An unspecified error.
- `other` - An unspecified error.

---

## SharedLinkPolicy

Who can view shared links in this folder.

- `anyone` - Links can be shared with anyone.
- `team` - Links can be shared with anyone on the same team as the owner.
- `members` - Links can only be shared among members of the shared folder.
- `other` - An unspecified error.

---

## SharedLinkSettings

The SharedLinkSettings struct.

- `requestedVisibility: Sharing.RequestedVisibility?` - The requested access for this shared link.
- `linkPassword: String?` - If requestedVisibility is password this is needed to specify the password to access the link.
- `expires: Date?` - Expiration time of the shared link.
- `audience: Sharing.LinkAudience?` - The new audience who can benefit from the access level specified by the link's access level.
- `access: Sharing.RequestedLinkAccessLevel?` - Requested access level you want the audience to gain from this link.

---

## SharedLinkSettingsError

The SharedLinkSettingsError union.

- `invalidSettings` - The given settings are invalid (for example, all attributes of the SharedLinkSettings are empty, the requested visibility is password but the linkPassword is missing, etc.).
- `notAuthorized` - User is not allowed to modify the settings of this link.

---

## SharingFileAccessError

User could not access this file.

- `noPermission` - Current user does not have sufficient privileges to perform the desired action.
- `invalidFile` - File specified was not found.
- `isFolder` - A folder can't be shared this way. Use folder sharing or a shared link instead.
- `insidePublicFolder` - A file inside a public folder can't be shared this way.
- `insideOsxPackage` - A Mac OS X package can't be shared this way.
- `other` - An unspecified error.

---

## SharingUserError

User account had a problem preventing this action.

- `emailUnverified` - The current user must verify the account e-mail address before performing this action.
- `other` - An unspecified error.

---

## TeamMemberInfo

Information about a team member.

- `teamInfo: Users.Team` - Information about the member's team.
- `displayName: String` - The display name of the user.
- `memberId: String?` - ID of user as a member of a team. This field will only be present if the member is in the same team as current user.

---

## TransferFolderArg

The TransferFolderArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `toDropboxId: String` - A account or team member ID to transfer ownership to.

---

## TransferFolderError

The TransferFolderError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `invalidDropboxId` - The toDropboxId argument is invalid.
- `newOwnerNotAMember` - The new designated owner is not currently a member of the shared folder.
- `newOwnerUnmounted` - The new designated owner has not added the folder to their Dropbox.
- `newOwnerEmailUnverified` - The new designated owner's e-mail address is unverified.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `other` - An unspecified error.

---

## UnmountFolderArg

The UnmountFolderArg struct.

- `sharedFolderId: String` - The ID for the shared folder.

---

## UnmountFolderError

The UnmountFolderError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `noPermission` - The current user does not have permission to perform this action.
- `notUnmountable` - The shared folder can't be unmounted. One example where this can occur is when the shared folder's parent folder is also a shared folder that resides in the current user's Dropbox.
- `other` - An unspecified error.

---

## UnshareFileArg

Arguments for unshareFile.

- `file: String` - The file to unshare.

---

## UnshareFileError

Error result for unshareFile.

- `userError(Sharing.SharingUserError)` - An unspecified error.
- `accessError(Sharing.SharingFileAccessError)` - An unspecified error.
- `other` - An unspecified error.

---

## UnshareFolderArg

The UnshareFolderArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `leaveACopy: Bool` - If true, members of this shared folder will get a copy of this folder after it's unshared. Otherwise, it will be removed from their Dropbox. The current user, who is an owner, will always retain their copy.

---

## UnshareFolderError

The UnshareFolderError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `noPermission` - The current user does not have permission to perform this action.
- `tooManyFiles` - This shared folder has too many files to be unshared.
- `other` - An unspecified error.

---

## UpdateFileMemberArgs

Arguments for updateFileMember.

- `file: String` - File for which we are changing a member's access.
- `member: Sharing.MemberSelector` - The member whose access we are changing.
- `accessLevel: Sharing.AccessLevel` - The new access level for the member.

---

## UpdateFolderMemberArg

The UpdateFolderMemberArg struct.

- `sharedFolderId: String` - The ID for the shared folder.
- `member: Sharing.MemberSelector` - The member of the shared folder to update. Only the dropboxId in MemberSelector may be set at this time.
- `accessLevel: Sharing.AccessLevel` - The new access level for member. owner in AccessLevel is disallowed.

---

## UpdateFolderMemberError

The UpdateFolderMemberError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `memberError(Sharing.SharedFolderMemberError)` - An unspecified error.
- `noExplicitAccess(Sharing.AddFolderMemberError)` - If updating the access type required the member to be added to the shared folder and there was an error when adding the member.
- `insufficientPlan` - The current user's account doesn't support this action.
- `noPermission` - The current user does not have permission to perform this action.
- `other` - An unspecified error.

---

## UpdateFolderPolicyArg

If any of the policies are unset, then they retain their current setting.

- `sharedFolderId: String` - The ID for the shared folder.
- `memberPolicy: Sharing.MemberPolicy?` - Who can be a member of this shared folder. Only applicable if the current user is on a team.
- `aclUpdatePolicy: Sharing.AclUpdatePolicy?` - Who can add and remove members of this shared folder.
- `viewerInfoPolicy: Sharing.ViewerInfoPolicy?` - Who can enable/disable viewer info for this shared folder.
- `sharedLinkPolicy: Sharing.SharedLinkPolicy?` - The policy to apply to shared links created for content inside this shared folder.
- `linkSettings: Sharing.LinkSettings?` - Settings on the link for this folder.
- `actions: [Sharing.FolderAction]?` - A list of `FolderAction`s corresponding to `FolderPermission`s that should appear in the response's permissions in SharedFolderMetadata field describing the actions the authenticated user can perform on the folder.

---

## UpdateFolderPolicyError

The UpdateFolderPolicyError union.

- `accessError(Sharing.SharedFolderAccessError)` - An unspecified error.
- `notOnTeam` - memberPolicy in UpdateFolderPolicyArg was set even though user is not on a team.
- `teamPolicyDisallowsMemberPolicy` - Team policy is more restrictive than memberPolicy in ShareFolderArg.
- `disallowedSharedLinkPolicy` - The current account is not allowed to select the specified sharedLinkPolicy in ShareFolderArg.
- `noPermission` - The current user does not have permission to perform this action.
- `teamFolder` - This action cannot be performed on a team shared folder.
- `other` - An unspecified error.

---

## UserMembershipInfo

The information about a user member of the shared content. Inherits from MembershipInfo.

- `user: Sharing.UserInfo` - The account information for the membership user.

---

## UserFileMembershipInfo

The information about a user member of the shared content with an appended last seen timestamp. Inherits from UserMembershipInfo.

- `timeLastSeen: Date?` - The UTC timestamp of when the user has last seen the content. Only populated if the user has seen the content and the caller has a plan that includes viewer history.
- `platformType: SeenState.PlatformType?` - The platform on which the user has last seen the content, or unknown.

---

## UserInfo

Basic information about a user. Use usersAccount and usersAccountBatch to obtain more detailed information.

- `accountId: String` - The account ID of the user.
- `email: String` - Email address of user.
- `displayName: String` - The display name of the user.
- `sameTeam: Bool` - If the user is in the same team as current user.
- `teamMemberId: String?` - The team member ID of the shared folder member. Only present if sameTeam is true.

---

## ViewerInfoPolicy

The ViewerInfoPolicy union.

- `enabled` - Viewer information is available on this file.
- `disabled` - Viewer information is disabled on this file.
- `other` - An unspecified error.

---

## Visibility

Who can access a shared link. The most open visibility is public_. The default depends on many aspects, such as team and user preferences and shared folder settings.

- `public_` - Anyone who has received the link can access it. No login required.
- `teamOnly` - Only members of the same team can access the link. Login is required.
- `password` - A link-specific password is required to access the link. Login is not required.
- `teamAndPassword` - Only members of the same team who have the link-specific password can access the link.
- `sharedFolderOnly` - Only members of the shared folder containing the linked file can access the link. Login is required.
- `other` - An unspecified error.

---

## VisibilityPolicy

The VisibilityPolicy struct.

- `policy: Sharing.RequestedVisibility` - This is the value to submit when saving the visibility setting.
- `resolvedPolicy: Sharing.AlphaResolvedVisibility` - This is what the effective policy would be, if you selected this option. The resolved policy is obtained after considering external effects such as shared folder settings and team policy. This value is guaranteed to be provided.
- `allowed: Bool` - Whether the user is permitted to set the visibility to this policy.
- `disallowedReason: Sharing.VisibilityPolicyDisallowedReason?` - If allowed is false, this will provide the reason that the user is not permitted to set the visibility to this policy.
