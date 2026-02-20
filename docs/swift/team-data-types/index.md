# Team Data Types

Data types for the team namespace.

## DeviceSession

The DeviceSession struct

**Properties:**

- `sessionId: String` - The session id.
- `ipAddress: String?` - The IP address of the last activity from this session.
- `country: String?` - The country from which the last activity from this session was made.
- `created: Date?` - The time this session was created.
- `updated: Date?` - The time of the last activity from this session.

---

## ActiveWebSession

Information on active web sessions.

Extends `Team.DeviceSession`

**Properties:**

- `userAgent: String` - Information on the hosting device.
- `os: String` - Information on the hosting operating system.
- `browser: String` - Information on the browser used for this web session.
- `expires: Date?` - The time this session expires.

---

## AddSecondaryEmailResult

Result of trying to add a secondary email to a user. 'success' is the only value indicating that a secondary email was successfully added to a user. The other values explain the type of error that occurred, and include the email for which the error occurred.

**Cases:**

- `success` (SecondaryEmails.SecondaryEmail) - Describes a secondary email that was successfully added to a user.
- `unavailable` (String) - Secondary email is not available to be claimed by the user.
- `alreadyPending` (String) - Secondary email is already a pending email for the user.
- `alreadyOwnedByUser` (String) - Secondary email is already a verified email for the user.
- `reachedLimit` (String) - User already has the maximum number of secondary emails allowed.
- `transientError` (String) - A transient error occurred. Please try again later.
- `tooManyUpdates` (String) - An error occurred due to conflicting updates. Please try again later.
- `unknownError` (String) - An unknown error occurred.
- `rateLimited` (String) - Too many emails are being sent to this email address. Please try again later.
- `other` - An unspecified error.

---

## AddSecondaryEmailsArg

The AddSecondaryEmailsArg struct

**Properties:**

- `newSecondaryEmails: [Team.UserSecondaryEmailsArg]` - List of users and secondary emails to add.

---

## AddSecondaryEmailsError

Error returned when adding secondary emails fails.

**Cases:**

- `secondaryEmailsDisabled` - Secondary emails are disabled for the team.
- `tooManyEmails` - A maximum of 20 secondary emails can be added in a single call.
- `other` - An unspecified error.

---

## AddSecondaryEmailsResult

The AddSecondaryEmailsResult struct

**Properties:**

- `results: [Team.UserAddResult]` - List of users and secondary email results.

---

## AdminTier

Describes which team-related admin permissions a user has.

**Cases:**

- `teamAdmin` - User is an administrator of the team - has all permissions.
- `userManagementAdmin` - User can do most user provisioning, de-provisioning and management.
- `supportAdmin` - admin roles; these may display as support_admin.
- `memberOnly` - User is not an admin of the team.

---

## ApiApp

Information on linked third party applications.

**Properties:**

- `appId: String` - The application unique id.
- `appName: String` - The application name.
- `publisher: String?` - The application publisher name.
- `publisherUrl: String?` - The publisher's URL.
- `linked: Date?` - The time this application was linked.
- `isAppFolder: Bool` - Whether the linked application uses a dedicated folder.

---

## BaseDfbReport

Base report structure.

**Properties:**

- `startDate: String` - First date present in the results as 'YYYY-MM-DD' or None.

---

## BaseTeamFolderError

Base error that all errors for existing team folders should extend.

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.

---

## CustomQuotaError

Error returned when getting member custom quota.

**Cases:**

- `tooManyUsers` - A maximum of 1000 users can be set for a single call.
- `other` - An unspecified error.

---

## CustomQuotaResult

User custom quota.

**Cases:**

- `success` (Team.UserCustomQuotaResult) - User's custom quota.
- `invalidUser` (Team.UserSelectorArg) - Invalid user (not in team).
- `other` - An unspecified error.

---

## CustomQuotaUsersArg

The CustomQuotaUsersArg struct

**Properties:**

- `users: [Team.UserSelectorArg]` - List of users.

---

## DateRange

Input arguments that can be provided for most reports.

**Properties:**

- `startDate: Date?` - months ago.
- `endDate: Date?` - Optional ending date (exclusive).

---

## DateRangeError

Errors that can originate from problems in input arguments to reports.

**Cases:**

- `other` - An unspecified error.

---

## DeleteSecondaryEmailResult

Result of trying to delete a secondary email address. 'success' is the only value indicating that a secondary email was successfully deleted. The other values explain the type of error that occurred, and include the email for which the error occurred.

**Cases:**

- `success` (String) - The secondary email was successfully deleted.
- `notFound` (String) - The email address was not found for the user.
- `cannotRemovePrimary` (String) - The email address is the primary email address of the user, and cannot be removed.
- `other` - An unspecified error.

---

## DeleteSecondaryEmailsArg

The DeleteSecondaryEmailsArg struct

**Properties:**

- `emailsToDelete: [Team.UserSecondaryEmailsArg]` - List of users and their secondary emails to delete.

---

## DeleteSecondaryEmailsResult

The DeleteSecondaryEmailsResult struct

**Properties:**

- `results: [Team.UserDeleteResult]` - (no description)

---

## DesktopClientSession

Information about linked Dropbox desktop client sessions.

Extends `Team.DeviceSession`

**Properties:**

- `hostName: String` - Name of the hosting desktop.
- `clientType: Team.DesktopPlatform` - The Dropbox desktop client type.
- `clientVersion: String` - The Dropbox client version.
- `platform: String` - Information on the hosting platform.
- `isDeleteOnUnlinkSupported: Bool` - Whether it's possible to delete all of the account files upon unlinking.

---

## DesktopPlatform

The DesktopPlatform union

**Cases:**

- `windows` - Official Windows Dropbox desktop client.
- `mac` - Official Mac Dropbox desktop client.
- `linux` - Official Linux Dropbox desktop client.
- `other` - An unspecified error.

---

## DeviceSessionArg

The DeviceSessionArg struct

**Properties:**

- `sessionId: String` - The session id.
- `teamMemberId: String` - The unique id of the member owning the device.

---

## DevicesActive

Each of the items is an array of values, one value per day. The value is the number of devices active within a time window, ending with that day. If there is no data for a day, then the value will be None.

**Properties:**

- `windows: [UInt64?]` - Array of number of linked windows (desktop) clients with activity.
- `macos: [UInt64?]` - Array of number of linked mac (desktop) clients with activity.
- `linux: [UInt64?]` - Array of number of linked linus (desktop) clients with activity.
- `ios: [UInt64?]` - Array of number of linked ios devices with activity.
- `android: [UInt64?]` - Array of number of linked android devices with activity.
- `other: [UInt64?]` - Array of number of other linked devices (blackberry, windows phone, etc)  with activity.
- `total: [UInt64?]` - Array of total number of linked clients with activity.

---

## ExcludedUsersListArg

Excluded users list argument.

**Properties:**

- `limit: UInt32` - Number of results to return per call.

---

## ExcludedUsersListContinueArg

Excluded users list continue argument.

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of users.

---

## ExcludedUsersListContinueError

Excluded users list continue error.

**Cases:**

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## ExcludedUsersListError

Excluded users list error.

**Cases:**

- `listError` - An error occurred.
- `other` - An unspecified error.

---

## ExcludedUsersListResult

Excluded users list result.

**Properties:**

- `users: [Team.MemberProfile]` - (no description)
- `cursor: String?` - Pass the cursor into memberSpaceLimitsExcludedUsersListContinue to obtain additional excluded users.
- `hasMore: Bool` - memberSpaceLimitsExcludedUsersListContinue can retrieve them.

---

## ExcludedUsersUpdateArg

Argument of excluded users update operation. Should include a list of users to add/remove (according to endpoint), Maximum size of the list is 1000 users.

**Properties:**

- `users: [Team.UserSelectorArg]?` - List of users to be added/removed.

---

## ExcludedUsersUpdateError

Excluded users update error.

**Cases:**

- `usersNotInTeam` - At least one of the users is not part of your team.
- `tooManyUsers` - A maximum of 1000 users for each of addition/removal can be supplied.
- `other` - An unspecified error.

---

## ExcludedUsersUpdateResult

Excluded users update result.

**Properties:**

- `status: Team.ExcludedUsersUpdateStatus` - Update status.

---

## ExcludedUsersUpdateStatus

Excluded users update operation status.

**Cases:**

- `success` - Update successful.
- `other` - An unspecified error.

---

## Feature

A set of features that a Dropbox Business account may support.

**Cases:**

- `uploadApiRateLimit` - The number of upload API calls allowed per month.
- `hasTeamSharedDropbox` - Does this team have a shared team root.
- `hasTeamFileEvents` - Does this team have file events.
- `hasTeamSelectiveSync` - Does this team have team selective sync enabled.
- `other` - An unspecified error.

---

## FeatureValue

The values correspond to entries in Feature. You may get different value according to your Dropbox Business plan.

**Cases:**

- `uploadApiRateLimit` (Team.UploadApiRateLimitValue) - An unspecified error.
- `hasTeamSharedDropbox` (Team.HasTeamSharedDropboxValue) - An unspecified error.
- `hasTeamFileEvents` (Team.HasTeamFileEventsValue) - An unspecified error.
- `hasTeamSelectiveSync` (Team.HasTeamSelectiveSyncValue) - An unspecified error.
- `other` - An unspecified error.

---

## FeaturesGetValuesBatchArg

The FeaturesGetValuesBatchArg struct

**Properties:**

- `features: [Team.Feature]` - A list of features in Feature. If the list is empty, this route will return FeaturesGetValuesBatchError.

---

## FeaturesGetValuesBatchError

The FeaturesGetValuesBatchError union

**Cases:**

- `emptyFeaturesList` - At least one Feature must be included in the FeaturesGetValuesBatchArg.features list.
- `other` - An unspecified error.

---

## FeaturesGetValuesBatchResult

The FeaturesGetValuesBatchResult struct

**Properties:**

- `values: [Team.FeatureValue]` - (no description)

---

## GetActivityReport

Activity Report Result. Each of the items in the storage report is an array of values, one value per day. If there is no data for a day, then the value will be None.

Extends `Team.BaseDfbReport`

**Properties:**

- `adds: [UInt64?]` - Array of total number of adds by team members.
- `edits: [UInt64?]` - counted as a single edit.
- `deletes: [UInt64?]` - Array of total number of deletes by team members.
- `activeUsers28Day: [UInt64?]` - Array of the number of users who have been active in the last 28 days.
- `activeUsers7Day: [UInt64?]` - Array of the number of users who have been active in the last week.
- `activeUsers1Day: [UInt64?]` - Array of the number of users who have been active in the last day.
- `activeSharedFolders28Day: [UInt64?]` - Array of the number of shared folders with some activity in the last 28 days.
- `activeSharedFolders7Day: [UInt64?]` - Array of the number of shared folders with some activity in the last week.
- `activeSharedFolders1Day: [UInt64?]` - Array of the number of shared folders with some activity in the last day.
- `sharedLinksCreated: [UInt64?]` - Array of the number of shared links created.
- `sharedLinksViewedByTeam: [UInt64?]` - Array of the number of views by team users to shared links created by the team.
- `sharedLinksViewedByOutsideUser: [UInt64?]` - Array of the number of views by users outside of the team to shared links created by the team.
- `sharedLinksViewedByNotLoggedIn: [UInt64?]` - Array of the number of views by non-logged-in users to shared links created by the team.
- `sharedLinksViewedTotal: [UInt64?]` - Array of the total number of views to shared links created by the team.

---

## GetDevicesReport

Devices Report Result. Contains subsections for different time ranges of activity. Each of the items in each subsection of the storage report is an array of values, one value per day. If there is no data for a day, then the value will be None.

Extends `Team.BaseDfbReport`

**Properties:**

- `active1Day: Team.DevicesActive` - Report of the number of devices active in the last day.
- `active7Day: Team.DevicesActive` - Report of the number of devices active in the last 7 days.
- `active28Day: Team.DevicesActive` - Report of the number of devices active in the last 28 days.

---

## GetMembershipReport

Membership Report Result. Each of the items in the storage report is an array of values, one value per day. If there is no data for a day, then the value will be None.

Extends `Team.BaseDfbReport`

**Properties:**

- `teamSize: [UInt64?]` - Team size, for each day.
- `pendingInvites: [UInt64?]` - The number of pending invites to the team, for each day.
- `membersJoined: [UInt64?]` - The number of members that joined the team, for each day.
- `suspendedMembers: [UInt64?]` - The number of suspended team members, for each day.
- `licenses: [UInt64?]` - The total number of licenses the team has, for each day.

---

## GetStorageReport

Storage Report Result. Each of the items in the storage report is an array of values, one value per day. If there is no data for a day, then the value will be None.

Extends `Team.BaseDfbReport`

**Properties:**

- `totalUsage: [UInt64?]` - Sum of the shared, unshared, and datastore usages, for each day.
- `sharedUsage: [UInt64?]` - Array of the combined size (bytes) of team members' shared folders, for each day.
- `unsharedUsage: [UInt64?]` - Array of the combined size (bytes) of team members' root namespaces, for each day.
- `sharedFolders: [UInt64?]` - Array of the number of shared folders owned by team members, for each day.
- `memberStorageMap: [[Team.StorageBucket]]` - no data for a day, the storage summary will be empty.

---

## GroupAccessType

Role of a user in group.

**Cases:**

- `member` - User is a member of the group, but has no special permissions.
- `owner` - User can rename the group, and add/remove members.

---

## GroupCreateArg

The GroupCreateArg struct

**Properties:**

- `groupName: String` - Group name.
- `addCreatorAsOwner: Bool` - Automatically add the creator of the group.
- `groupExternalId: String?` - The creator of a team can associate an arbitrary external ID to the group.
- `groupManagementType: TeamCommon.GroupManagementType?` - Whether the team can be managed by selected users, or only by team admins.

---

## GroupCreateError

The GroupCreateError union

**Cases:**

- `groupNameAlreadyUsed` - The requested group name is already being used by another group.
- `groupNameInvalid` - Group name is empty or has invalid characters.
- `externalIdAlreadyInUse` - The requested external ID is already being used by another group.
- `systemManagedGroupDisallowed` - System-managed group cannot be manually created.
- `other` - An unspecified error.

---

## GroupSelectorError

Error that can be raised when GroupSelector is used.

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.

---

## GroupSelectorWithTeamGroupError

Error that can be raised when GroupSelector is used and team groups are disallowed from being used.

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.

---

## GroupDeleteError

The GroupDeleteError union

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `groupAlreadyDeleted` - This group has already been deleted.

---

## GroupFullInfo

Full description of a group.

Extends `TeamCommon.GroupSummary`

**Properties:**

- `members: [Team.GroupMemberInfo]?` - List of group members.
- `created: UInt64` - The group creation time as a UTC timestamp in milliseconds since the Unix epoch.

---

## GroupMemberInfo

Profile of group member, and role in group.

**Properties:**

- `profile: Team.MemberProfile` - Profile of group member.
- `accessType: Team.GroupAccessType` - The role that the user has in the group.

---

## GroupMemberSelector

Argument for selecting a group and a single user.

**Properties:**

- `group: Team.GroupSelector` - Specify a group.
- `user: Team.UserSelectorArg` - Identity of a user that is a member of group.

---

## GroupMemberSelectorError

Error that can be raised when GroupMemberSelector is used, and the user is required to be a member of the specified group.

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `memberNotInGroup` - The specified user is not a member of this group.

---

## GroupMemberSetAccessTypeError

The GroupMemberSetAccessTypeError union

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `memberNotInGroup` - The specified user is not a member of this group.
- `userCannotBeManagerOfCompanyManagedGroup` - A company managed group cannot be managed by a user.

---

## IncludeMembersArg

The IncludeMembersArg struct

**Properties:**

- `returnMembers: Bool` - members  to be returned in the response. This may take a long time for large groups.

---

## GroupMembersAddArg

The GroupMembersAddArg struct

Extends `Team.IncludeMembersArg`

**Properties:**

- `group: Team.GroupSelector` - Group to which users will be added.
- `members: [Team.MemberAccess]` - List of users to be added to the group.

---

## GroupMembersAddError

The GroupMembersAddError union

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `duplicateUser` - group.
- `groupNotInTeam` - Group is not in this team. You cannot add members to a group that is outside of your team.
- `membersNotInTeam` ([String]) - Business team, use the membersAdd endpoint.
- `usersNotFound` ([String]) - These users were not found in Dropbox.
- `userMustBeActiveToBeOwner` - A suspended user cannot be added to a group as owner in GroupAccessType.
- `userCannotBeManagerOfCompanyManagedGroup` ([String]) - A company-managed group cannot be managed by a user.

---

## GroupMembersChangeResult

Result returned by groupsMembersAdd and groupsMembersRemove.

**Properties:**

- `groupInfo: Team.GroupFullInfo` - The group info after member change operation has been performed.
- `asyncJobId: String` - async processing now happens automatically.

---

## GroupMembersRemoveArg

The GroupMembersRemoveArg struct

Extends `Team.IncludeMembersArg`

**Properties:**

- `group: Team.GroupSelector` - Group from which users will be removed.
- `users: [Team.UserSelectorArg]` - List of users to be removed from the group.

---

## GroupMembersSelectorError

Error that can be raised when GroupMembersSelector is used, and the users are required to be members of the specified group.

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `memberNotInGroup` - At least one of the specified users is not a member of the group.

---

## GroupMembersRemoveError

The GroupMembersRemoveError union

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `memberNotInGroup` - At least one of the specified users is not a member of the group.
- `groupNotInTeam` - Group is not in this team. You cannot remove members from a group that is outside of your team.
- `membersNotInTeam` ([String]) - These members are not part of your team.
- `usersNotFound` ([String]) - These users were not found in Dropbox.

---

## GroupMembersSelector

Argument for selecting a group and a list of users.

**Properties:**

- `group: Team.GroupSelector` - Specify a group.
- `users: Team.UsersSelectorArg` - A list of users that are members of group.

---

## GroupMembersSetAccessTypeArg

The GroupMembersSetAccessTypeArg struct

Extends `Team.GroupMemberSelector`

**Properties:**

- `accessType: Team.GroupAccessType` - New group access type the user will have.
- `returnMembers: Bool` - members  to be returned in the response. This may take a long time for large groups.

---

## GroupSelector

Argument for selecting a single group, either by group_id or by external group ID.

**Cases:**

- `groupId` (String) - Group ID.
- `groupExternalId` (String) - External ID of the group.

---

## GroupUpdateArgs

The GroupUpdateArgs struct

Extends `Team.IncludeMembersArg`

**Properties:**

- `group: Team.GroupSelector` - Specify a group.
- `newGroupName: String?` - Optional argument. Set group name to this if provided.
- `newGroupExternalId: String?` - If the argument is empty string, the group's external id will be cleared.
- `newGroupManagementType: TeamCommon.GroupManagementType?` - Set new group management type, if provided.

---

## GroupUpdateError

The GroupUpdateError union

**Cases:**

- `groupNotFound` - No matching group found. No groups match the specified group ID.
- `other` - An unspecified error.
- `systemManagedGroupDisallowed` - This operation is not supported on system-managed groups.
- `groupNameAlreadyUsed` - The requested group name is already being used by another group.
- `groupNameInvalid` - Group name is empty or has invalid characters.
- `externalIdAlreadyInUse` - The requested external ID is already being used by another group.

---

## GroupsGetInfoError

The GroupsGetInfoError union

**Cases:**

- `groupNotOnTeam` - The group is not on your team.
- `other` - An unspecified error.

---

## GroupsGetInfoItem

The GroupsGetInfoItem union

**Cases:**

- `idNotFound` (String) - be a group ID, or an external ID, depending on how the method was called.
- `groupInfo` (Team.GroupFullInfo) - Info about a group.

---

## GroupsListArg

The GroupsListArg struct

**Properties:**

- `limit: UInt32` - Number of results to return per call.

---

## GroupsListContinueArg

The GroupsListContinueArg struct

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of groups.

---

## GroupsListContinueError

The GroupsListContinueError union

**Cases:**

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## GroupsListResult

The GroupsListResult struct

**Properties:**

- `groups: [TeamCommon.GroupSummary]` - (no description)
- `cursor: String` - Pass the cursor into groupsListContinue to obtain the additional groups.
- `hasMore: Bool` - groupsListContinue can retrieve them.

---

## GroupsMembersListArg

The GroupsMembersListArg struct

**Properties:**

- `group: Team.GroupSelector` - The group whose members are to be listed.
- `limit: UInt32` - Number of results to return per call.

---

## GroupsMembersListContinueArg

The GroupsMembersListContinueArg struct

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of groups.

---

## GroupsMembersListContinueError

The GroupsMembersListContinueError union

**Cases:**

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## GroupsMembersListResult

The GroupsMembersListResult struct

**Properties:**

- `members: [Team.GroupMemberInfo]` - (no description)
- `cursor: String` - Pass the cursor into groupsMembersListContinue to obtain additional group members.
- `hasMore: Bool` - groupsMembersListContinue can retrieve them.

---

## GroupsPollError

The GroupsPollError union

**Cases:**

- `invalidAsyncJobId` - The job ID is invalid.
- `internalError` - succeeded, and if not, try again. This should happen very rarely.
- `other` - An unspecified error.
- `accessDenied` - You are not allowed to poll this job.

---

## GroupsSelector

Argument for selecting a list of groups, either by group_ids, or external group IDs.

**Cases:**

- `groupIds` ([String]) - List of group IDs.
- `groupExternalIds` ([String]) - List of external IDs of groups.

---

## HasTeamFileEventsValue

The value for hasTeamFileEvents in Feature.

**Cases:**

- `enabled` (Bool) - Does this team have file events.
- `other` - An unspecified error.

---

## HasTeamSelectiveSyncValue

The value for hasTeamSelectiveSync in Feature.

**Cases:**

- `hasTeamSelectiveSync` (Bool) - Does this team have team selective sync enabled.
- `other` - An unspecified error.

---

## HasTeamSharedDropboxValue

The value for hasTeamSharedDropbox in Feature.

**Cases:**

- `hasTeamSharedDropbox` (Bool) - Does this team have a shared team root.
- `other` - An unspecified error.

---

## LegalHoldHeldRevisionMetadata

The LegalHoldHeldRevisionMetadata struct

**Properties:**

- `newFilename: String` - The held revision filename.
- `originalRevisionId: String` - The id of the held revision.
- `originalFilePath: String` - The original path of the held revision.
- `serverModified: Date` - The last time the file was modified on Dropbox.
- `authorMemberId: String` - The member id of the revision's author.
- `authorMemberStatus: Team.TeamMemberStatus` - The member status of the revision's author.
- `authorEmail: String` - The email address of the held revision author.
- `fileType: String` - The type of the held revision's file.
- `size: UInt64` - The file size in bytes.
- `contentHash: String` - Content hash https://www.dropbox.com/developers/reference/content-hash page.

---

## LegalHoldPolicy

The LegalHoldPolicy struct

**Properties:**

- `id: String` - The legal hold id.
- `name: String` - Policy name.
- `description_: String?` - A description of the legal hold policy.
- `activationTime: Date?` - The time at which the legal hold was activated.
- `members: Team.MembersInfo` - Team members IDs and number of permanently deleted members under hold.
- `status: Team.LegalHoldStatus` - The current state of the hold.
- `startDate: Date` - Start date of the legal hold policy.
- `endDate: Date?` - End date of the legal hold policy.

---

## LegalHoldStatus

The LegalHoldStatus union

**Cases:**

- `active` - The legal hold policy is active.
- `released` - The legal hold policy was released.
- `activating` - The legal hold policy is activating.
- `updating` - The legal hold policy is updating.
- `exporting` - The legal hold policy is exporting.
- `releasing` - The legal hold policy is releasing.
- `other` - An unspecified error.

---

## LegalHoldsError

The LegalHoldsError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.

---

## LegalHoldsGetPolicyArg

The LegalHoldsGetPolicyArg struct

**Properties:**

- `id: String` - The legal hold Id.

---

## LegalHoldsGetPolicyError

The LegalHoldsGetPolicyError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `legalHoldPolicyNotFound` - Legal hold policy does not exist for id in LegalHoldsGetPolicyArg.

---

## LegalHoldsListHeldRevisionResult

The LegalHoldsListHeldRevisionResult struct

**Properties:**

- `entries: [Team.LegalHoldHeldRevisionMetadata]` - List of file entries that under the hold.
- `cursor: String?` - /2/team/legal_holds/list_held_revisions/continue.
- `hasMore: Bool` - /legal_holds/list_held_revisions_continue.

---

## LegalHoldsListHeldRevisionsArg

The LegalHoldsListHeldRevisionsArg struct

**Properties:**

- `id: String` - The legal hold Id.

---

## LegalHoldsListHeldRevisionsContinueArg

The LegalHoldsListHeldRevisionsContinueArg struct

**Properties:**

- `id: String` - The legal hold Id.
- `cursor: String?` - more entries, the cursor will return none.

---

## LegalHoldsListHeldRevisionsContinueError

The LegalHoldsListHeldRevisionsContinueError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `transientError` - Temporary infrastructure failure, please retry.
- `reset` - cursor to obtain a new cursor.
- `other` - An unspecified error.

---

## LegalHoldsListHeldRevisionsError

The LegalHoldsListHeldRevisionsError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `transientError` - Temporary infrastructure failure, please retry.
- `legalHoldStillEmpty` - The legal hold is not holding any revisions yet.
- `inactiveLegalHold` - Trying to list revisions for an inactive legal hold.

---

## LegalHoldsListPoliciesArg

The LegalHoldsListPoliciesArg struct

**Properties:**

- `includeReleased: Bool` - Whether to return holds that were released.

---

## LegalHoldsListPoliciesError

The LegalHoldsListPoliciesError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `transientError` - Temporary infrastructure failure, please retry.

---

## LegalHoldsListPoliciesResult

The LegalHoldsListPoliciesResult struct

**Properties:**

- `policies: [Team.LegalHoldPolicy]` - (no description)

---

## LegalHoldsPolicyCreateArg

The LegalHoldsPolicyCreateArg struct

**Properties:**

- `name: String` - Policy name.
- `description_: String?` - A description of the legal hold policy.
- `members: [String]` - List of team member IDs added to the hold.
- `startDate: Date?` - start date of the legal hold policy.
- `endDate: Date?` - end date of the legal hold policy.

---

## LegalHoldsPolicyCreateError

The LegalHoldsPolicyCreateError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `startDateIsLaterThanEndDate` - Start date must be earlier than end date.
- `emptyMembersList` - The users list must have at least one user.
- `invalidMembers` - Some members in the members list are not valid to be placed under legal hold.
- `numberOfUsersOnHoldIsGreaterThanHoldLimitation` - You cannot add more than 5 users in a legal hold.
- `transientError` - Temporary infrastructure failure, please retry.
- `nameMustBeUnique` - The name provided is already in use by another legal hold.
- `teamExceededLegalHoldQuota` - Team exceeded legal hold quota.
- `invalidDate` - The provided date is invalid.

---

## LegalHoldsPolicyReleaseArg

The LegalHoldsPolicyReleaseArg struct

**Properties:**

- `id: String` - The legal hold Id.

---

## LegalHoldsPolicyReleaseError

The LegalHoldsPolicyReleaseError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `legalHoldPerformingAnotherOperation` - Legal hold is currently performing another operation.
- `legalHoldAlreadyReleasing` - Legal hold is currently performing a release or is already released.
- `legalHoldPolicyNotFound` - Legal hold policy does not exist for id in LegalHoldsPolicyReleaseArg.

---

## LegalHoldsPolicyUpdateArg

The LegalHoldsPolicyUpdateArg struct

**Properties:**

- `id: String` - The legal hold Id.
- `name: String?` - Policy new name.
- `description_: String?` - Policy new description.
- `members: [String]?` - List of team member IDs to apply the policy on.

---

## LegalHoldsPolicyUpdateError

The LegalHoldsPolicyUpdateError union

**Cases:**

- `unknownLegalHoldError` - There has been an unknown legal hold error.
- `insufficientPermissions` - You don't have permissions to perform this action.
- `other` - An unspecified error.
- `transientError` - Temporary infrastructure failure, please retry.
- `inactiveLegalHold` - Trying to release an inactive legal hold.
- `legalHoldPerformingAnotherOperation` - Legal hold is currently performing another operation.
- `invalidMembers` - Some members in the members list are not valid to be placed under legal hold.
- `numberOfUsersOnHoldIsGreaterThanHoldLimitation` - You cannot add more than 5 users in a legal hold.
- `emptyMembersList` - The users list must have at least one user.
- `nameMustBeUnique` - The name provided is already in use by another legal hold.
- `legalHoldPolicyNotFound` - Legal hold policy does not exist for id in LegalHoldsPolicyUpdateArg.

---

## ListMemberAppsArg

The ListMemberAppsArg struct

**Properties:**

- `teamMemberId: String` - The team member id.

---

## ListMemberAppsError

Error returned by linkedAppsListMemberLinkedApps.

**Cases:**

- `memberNotFound` - Member not found.
- `other` - An unspecified error.

---

## ListMemberAppsResult

The ListMemberAppsResult struct

**Properties:**

- `linkedApiApps: [Team.ApiApp]` - List of third party applications linked by this team member.

---

## ListMemberDevicesArg

The ListMemberDevicesArg struct

**Properties:**

- `teamMemberId: String` - The team's member id.
- `includeWebSessions: Bool` - Whether to list web sessions of the team's member.
- `includeDesktopClients: Bool` - Whether to list linked desktop devices of the team's member.
- `includeMobileClients: Bool` - Whether to list linked mobile devices of the team's member.

---

## ListMemberDevicesError

The ListMemberDevicesError union

**Cases:**

- `memberNotFound` - Member not found.
- `other` - An unspecified error.

---

## ListMemberDevicesResult

The ListMemberDevicesResult struct

**Properties:**

- `activeWebSessions: [Team.ActiveWebSession]?` - List of web sessions made by this team member.
- `desktopClientSessions: [Team.DesktopClientSession]?` - List of desktop clients used by this team member.
- `mobileClientSessions: [Team.MobileClientSession]?` - List of mobile client used by this team member.

---

## ListMembersAppsArg

Arguments for linkedAppsListMembersLinkedApps.

**Properties:**

- `cursor: String?` - to receive the next sub list of the team applications.

---

## ListMembersAppsError

Error returned by linkedAppsListMembersLinkedApps.

**Cases:**

- `reset` - cursor to obtain a new cursor.
- `other` - An unspecified error.

---

## ListMembersAppsResult

Information returned by linkedAppsListMembersLinkedApps.

**Properties:**

- `apps: [Team.MemberLinkedApps]` - The linked applications of each member of the team.
- `hasMore: Bool` - the rest.
- `cursor: String?` - Pass the cursor into linkedAppsListMembersLinkedApps to receive the next sub list of team's applications.

---

## ListMembersDevicesArg

The ListMembersDevicesArg struct

**Properties:**

- `cursor: String?` - receive the next sub list of team devices.
- `includeWebSessions: Bool` - Whether to list web sessions of the team members.
- `includeDesktopClients: Bool` - Whether to list desktop clients of the team members.
- `includeMobileClients: Bool` - Whether to list mobile clients of the team members.

---

## ListMembersDevicesError

The ListMembersDevicesError union

**Cases:**

- `reset` - obtain a new cursor.
- `other` - An unspecified error.

---

## ListMembersDevicesResult

The ListMembersDevicesResult struct

**Properties:**

- `devices: [Team.MemberDevices]` - The devices of each member of the team.
- `hasMore: Bool` - rest.
- `cursor: String?` - Pass the cursor into devicesListMembersDevices to receive the next sub list of team's devices.

---

## ListTeamAppsArg

Arguments for linkedAppsListTeamLinkedApps.

**Properties:**

- `cursor: String?` - receive the next sub list of the team applications.

---

## ListTeamAppsError

Error returned by linkedAppsListTeamLinkedApps.

**Cases:**

- `reset` - to obtain a new cursor.
- `other` - An unspecified error.

---

## ListTeamAppsResult

Information returned by linkedAppsListTeamLinkedApps.

**Properties:**

- `apps: [Team.MemberLinkedApps]` - The linked applications of each member of the team.
- `hasMore: Bool` - rest.
- `cursor: String?` - Pass the cursor into linkedAppsListTeamLinkedApps to receive the next sub list of team's applications.

---

## ListTeamDevicesArg

The ListTeamDevicesArg struct

**Properties:**

- `cursor: String?` - receive the next sub list of team devices.
- `includeWebSessions: Bool` - Whether to list web sessions of the team members.
- `includeDesktopClients: Bool` - Whether to list desktop clients of the team members.
- `includeMobileClients: Bool` - Whether to list mobile clients of the team members.

---

## ListTeamDevicesError

The ListTeamDevicesError union

**Cases:**

- `reset` - obtain a new cursor.
- `other` - An unspecified error.

---

## ListTeamDevicesResult

The ListTeamDevicesResult struct

**Properties:**

- `devices: [Team.MemberDevices]` - The devices of each member of the team.
- `hasMore: Bool` - rest.
- `cursor: String?` - Pass the cursor into devicesListTeamDevices to receive the next sub list of team's devices.

---

## MemberAccess

Specify access type a member should have when joined to a group.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of a user.
- `accessType: Team.GroupAccessType` - Access type.

---

## MemberAddArgBase

The MemberAddArgBase struct

**Properties:**

- `memberEmail: String` - (no description)
- `memberGivenName: String?` - Member's first name.
- `memberSurname: String?` - Member's last name.
- `memberExternalId: String?` - External ID for member.
- `memberPersistentId: String?` - Persistent ID for member. This field is only available to teams using persistent ID SAML configuration.
- `sendWelcomeEmail: Bool` - want to handle announcements themselves.
- `isDirectoryRestricted: Bool?` - Whether a user is directory restricted.

---

## MemberAddArg

The MemberAddArg struct

Extends `Team.MemberAddArgBase`

**Properties:**

- `role: Team.AdminTier` - (no description)

---

## MemberAddResultBase

The MemberAddResultBase union

**Cases:**

- `teamLicenseLimit` (String) - Team is already full. The organization has no available licenses.
- `freeTeamMemberLimitReached` (String) - Team is already full. The free team member limit has been reached.
- `userAlreadyOnTeam` (String) - of (including in recoverable state) or invited to the team.
- `userOnAnotherTeam` (String) - member or invited to another team.
- `userAlreadyPaired` (String) - User is already paired.
- `userMigrationFailed` (String) - User migration has failed.
- `duplicateExternalMemberId` (String) - A user with the given external member ID already exists on the team (including in recoverable state).
- `duplicateMemberPersistentId` (String) - A user with the given persistent ID already exists on the team (including in recoverable state).
- `persistentIdDisabled` (String) - more information.
- `userCreationFailed` (String) - User creation has failed.

---

## MemberAddResult

Describes the result of attempting to add a single user to the team. 'success' is the only value indicating that a user was indeed added to the team - the other values explain the type of failure that occurred, and include the email of the user for which the operation has failed.

**Cases:**

- `teamLicenseLimit` (String) - Team is already full. The organization has no available licenses.
- `freeTeamMemberLimitReached` (String) - Team is already full. The free team member limit has been reached.
- `userAlreadyOnTeam` (String) - of (including in recoverable state) or invited to the team.
- `userOnAnotherTeam` (String) - member or invited to another team.
- `userAlreadyPaired` (String) - User is already paired.
- `userMigrationFailed` (String) - User migration has failed.
- `duplicateExternalMemberId` (String) - A user with the given external member ID already exists on the team (including in recoverable state).
- `duplicateMemberPersistentId` (String) - A user with the given persistent ID already exists on the team (including in recoverable state).
- `persistentIdDisabled` (String) - more information.
- `userCreationFailed` (String) - User creation has failed.
- `success` (Team.TeamMemberInfo) - Describes a user that was successfully added to the team.

---

## MemberAddV2Arg

The MemberAddV2Arg struct

Extends `Team.MemberAddArgBase`

**Properties:**

- `roleIds: [String]?` - (no description)

---

## MemberAddV2Result

Describes the result of attempting to add a single user to the team. 'success' is the only value indicating that a user was indeed added to the team - the other values explain the type of failure that occurred, and include the email of the user for which the operation has failed.

**Cases:**

- `teamLicenseLimit` (String) - Team is already full. The organization has no available licenses.
- `freeTeamMemberLimitReached` (String) - Team is already full. The free team member limit has been reached.
- `userAlreadyOnTeam` (String) - of (including in recoverable state) or invited to the team.
- `userOnAnotherTeam` (String) - member or invited to another team.
- `userAlreadyPaired` (String) - User is already paired.
- `userMigrationFailed` (String) - User migration has failed.
- `duplicateExternalMemberId` (String) - A user with the given external member ID already exists on the team (including in recoverable state).
- `duplicateMemberPersistentId` (String) - A user with the given persistent ID already exists on the team (including in recoverable state).
- `persistentIdDisabled` (String) - more information.
- `userCreationFailed` (String) - User creation has failed.
- `success` (Team.TeamMemberInfoV2) - Describes a user that was successfully added to the team.
- `other` - An unspecified error.

---

## MemberDevices

Information on devices of a team's member.

**Properties:**

- `teamMemberId: String` - The member unique Id.
- `webSessions: [Team.ActiveWebSession]?` - List of web sessions made by this team member.
- `desktopClients: [Team.DesktopClientSession]?` - List of desktop clients by this team member.
- `mobileClients: [Team.MobileClientSession]?` - List of mobile clients by this team member.

---

## MemberLinkedApps

Information on linked applications of a team member.

**Properties:**

- `teamMemberId: String` - The member unique Id.
- `linkedApiApps: [Team.ApiApp]` - List of third party applications linked by this team member.

---

## MemberProfile

Basic member profile.

**Properties:**

- `teamMemberId: String` - ID of user as a member of a team.
- `externalId: String?` - own IDs instead of Dropbox IDs like account_id or team_member_id.
- `accountId: String?` - A user's account identifier.
- `email: String` - Email address of user.
- `emailVerified: Bool` - Is true if the user's email is verified to be owned by the user.
- `secondaryEmails: [SecondaryEmails.SecondaryEmail]?` - Secondary emails of a user.
- `status: Team.TeamMemberStatus` - The user's status as a member of a specific team.
- `name: Users.Name` - Representations for a person's name.
- `membershipType: Team.TeamMembershipType` - team's shared quota).
- `invitedOn: Date?` - invited in TeamMemberStatus).
- `joinedOn: Date?` - The date and time the user joined as a member of a specific team.
- `suspendedOn: Date?` - suspended in TeamMemberStatus).
- `persistentId: String?` - authentication.
- `isDirectoryRestricted: Bool?` - Whether the user is a directory restricted user.
- `profilePhotoUrl: String?` - URL for the photo representing the user, if one is set.

---

## UserSelectorError

Error that can be returned whenever a struct derived from UserSelectorArg is used.

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.

---

## MemberSelectorError

The MemberSelectorError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.

---

## MembersAddArgBase

The MembersAddArgBase struct

**Properties:**

- `forceAsync: Bool` - Whether to force the add to happen asynchronously.

---

## MembersAddArg

The MembersAddArg struct

Extends `Team.MembersAddArgBase`

**Properties:**

- `newMembers: [Team.MemberAddArg]` - Details of new members to be added to the team.

---

## MembersAddJobStatus

The MembersAddJobStatus union

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` ([Team.MemberAddResult]) - was provided to membersAdd, a corresponding item is returned in this list.
- `failed` (String) - The asynchronous job returned an error. The string contains an error message.

---

## MembersAddJobStatusV2Result

The MembersAddJobStatusV2Result union

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` ([Team.MemberAddV2Result]) - was provided to membersAddV2, a corresponding item is returned in this list.
- `failed` (String) - The asynchronous job returned an error. The string contains an error message.
- `other` - An unspecified error.

---

## MembersAddLaunch

The MembersAddLaunch union

**Cases:**

- `asyncJobId` (String) - the status of the asynchronous job.
- `complete` ([Team.MemberAddResult]) - An unspecified error.

---

## MembersAddLaunchV2Result

The MembersAddLaunchV2Result union

**Cases:**

- `asyncJobId` (String) - the status of the asynchronous job.
- `complete` ([Team.MemberAddV2Result]) - An unspecified error.
- `other` - An unspecified error.

---

## MembersAddV2Arg

The MembersAddV2Arg struct

Extends `Team.MembersAddArgBase`

**Properties:**

- `newMembers: [Team.MemberAddV2Arg]` - Details of new members to be added to the team.

---

## MembersDeactivateBaseArg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user to remove/suspend/have their files moved.

---

## MembersDataTransferArg

The MembersDataTransferArg struct

Extends `Team.MembersDeactivateBaseArg`

**Properties:**

- `transferDestId: Team.UserSelectorArg` - Files from the deleted member account will be transferred to this user.
- `transferAdminId: Team.UserSelectorArg` - Errors during the transfer process will be sent via email to this user.

---

## MembersDeactivateArg

The MembersDeactivateArg struct

Extends `Team.MembersDeactivateBaseArg`

**Properties:**

- `wipeData: Bool` - If provided, controls if the user's data will be deleted on their linked devices.

---

## MembersDeactivateError

The MembersDeactivateError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.

---

## MembersDeleteProfilePhotoArg

The MembersDeleteProfilePhotoArg struct

**Properties:**

- `user: Team.UserSelectorArg` - Identity of the user whose profile photo will be deleted.

---

## MembersDeleteProfilePhotoError

The MembersDeleteProfilePhotoError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `setProfileDisallowed` - Modifying deleted users is not allowed.
- `other` - An unspecified error.

---

## MembersGetAvailableTeamMemberRolesResult

Available TeamMemberRole for the connected team. To be used with membersSetAdminPermissionsV2.

**Properties:**

- `roles: [Team.TeamMemberRole]` - Available roles.

---

## MembersGetInfoArgs

The MembersGetInfoArgs struct

**Properties:**

- `members: [Team.UserSelectorArg]` - List of team members.

---

## MembersGetInfoError

The MembersGetInfoError union

**Cases:**

- `other` - An unspecified error.

---

## MembersGetInfoItemBase

The MembersGetInfoItemBase union

**Cases:**

- `idNotFound` (String) - the method was called.

---

## MembersGetInfoItem

Describes a result obtained for a single user whose id was specified in the parameter of membersGetInfo.

**Cases:**

- `idNotFound` (String) - the method was called.
- `memberInfo` (Team.TeamMemberInfo) - Info about a team member.

---

## MembersGetInfoItemV2

Describes a result obtained for a single user whose id was specified in the parameter of membersGetInfoV2.

**Cases:**

- `idNotFound` (String) - the method was called.
- `memberInfo` (Team.TeamMemberInfoV2) - Info about a team member.
- `other` - An unspecified error.

---

## MembersGetInfoV2Arg

The MembersGetInfoV2Arg struct

**Properties:**

- `members: [Team.UserSelectorArg]` - List of team members.

---

## MembersGetInfoV2Result

The MembersGetInfoV2Result struct

**Properties:**

- `membersInfo: [Team.MembersGetInfoItemV2]` - List of team members info.

---

## MembersInfo

The MembersInfo struct

**Properties:**

- `teamMemberIds: [String]` - Team member IDs of the users under this hold.
- `permanentlyDeletedUsers: UInt64` - The number of permanently deleted users that were under this hold.

---

## MembersListArg

The MembersListArg struct

**Properties:**

- `limit: UInt32` - Number of results to return per call.
- `includeRemoved: Bool` - Whether to return removed members.

---

## MembersListContinueArg

The MembersListContinueArg struct

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of members.

---

## MembersListContinueError

The MembersListContinueError union

**Cases:**

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## MembersListError

The MembersListError union

**Cases:**

- `other` - An unspecified error.

---

## MembersListResult

The MembersListResult struct

**Properties:**

- `members: [Team.TeamMemberInfo]` - List of team members.
- `cursor: String` - Pass the cursor into membersListContinue to obtain the additional members.
- `hasMore: Bool` - membersListContinue can retrieve them.

---

## MembersListV2Result

The MembersListV2Result struct

**Properties:**

- `members: [Team.TeamMemberInfoV2]` - List of team members.
- `cursor: String` - Pass the cursor into membersListContinueV2 to obtain the additional members.
- `hasMore: Bool` - membersListContinueV2 can retrieve them.

---

## MembersRecoverArg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user to recover.

---

## MembersRecoverError

The MembersRecoverError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userUnrecoverable` - The user is not recoverable.
- `userNotInTeam` - The user is not a member of the team.
- `teamLicenseLimit` - Team is full. The organization has no available licenses.
- `other` - An unspecified error.

---

## MembersRemoveArg

The MembersRemoveArg struct

Extends `Team.MembersDeactivateArg`

**Properties:**

- `transferDestId: Team.UserSelectorArg?` - If provided, files from the deleted member account will be transferred to this user.
- `transferAdminId: Team.UserSelectorArg?` - argument was provided, then this argument must be provided as well.
- `keepAccount: Bool` - the account the argument wipeData should be set to false.
- `retainTeamShares: Bool` - relationships, the arguments wipeData should be set to false and keepAccount should be set to true.

---

## MembersTransferFilesError

The MembersTransferFilesError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.
- `removedAndTransferDestShouldDiffer` - Expected removed user and transfer_dest user to be different.
- `removedAndTransferAdminShouldDiffer` - Expected removed user and transfer_admin user to be different.
- `transferDestUserNotFound` - No matching user found for the argument transfer_dest_id.
- `transferDestUserNotInTeam` - The provided transfer_dest_id does not exist on this team.
- `transferAdminUserNotInTeam` - The provided transfer_admin_id does not exist on this team.
- `transferAdminUserNotFound` - No matching user found for the argument transfer_admin_id.
- `unspecifiedTransferAdminId` - The transfer_admin_id argument must be provided when file transfer is requested.
- `transferAdminIsNotAdmin` - Specified transfer_admin user is not a team admin.
- `recipientNotVerified` - The recipient user's email is not verified.

---

## MembersRemoveError

The MembersRemoveError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.
- `removedAndTransferDestShouldDiffer` - Expected removed user and transfer_dest user to be different.
- `removedAndTransferAdminShouldDiffer` - Expected removed user and transfer_admin user to be different.
- `transferDestUserNotFound` - No matching user found for the argument transfer_dest_id.
- `transferDestUserNotInTeam` - The provided transfer_dest_id does not exist on this team.
- `transferAdminUserNotInTeam` - The provided transfer_admin_id does not exist on this team.
- `transferAdminUserNotFound` - No matching user found for the argument transfer_admin_id.
- `unspecifiedTransferAdminId` - The transfer_admin_id argument must be provided when file transfer is requested.
- `transferAdminIsNotAdmin` - Specified transfer_admin user is not a team admin.
- `recipientNotVerified` - The recipient user's email is not verified.
- `removeLastAdmin` - The user is the last admin of the team, so it cannot be removed from it.
- `cannotKeepAccountAndTransfer` - Cannot keep account and transfer the data to another user at the same time.
- `cannotKeepAccountAndDeleteData` - be set to false.
- `emailAddressTooLongToBeDisabled` - The email address of the user is too long to be disabled.
- `cannotKeepInvitedUserAccount` - Cannot keep account of an invited user.
- `cannotRetainSharesWhenDataWiped` - wipe_data should be set to false.
- `cannotRetainSharesWhenNoAccountKept` - true.
- `cannotRetainSharesWhenTeamExternalSharingOff` - for the user.
- `cannotKeepAccount` - Only a team admin, can convert this account to a Basic account.
- `cannotKeepAccountUnderLegalHold` - need to remove them from the hold.
- `cannotKeepAccountRequiredToSignTos` - of service.

---

## MembersSendWelcomeError

The MembersSendWelcomeError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.

---

## MembersSetPermissions2Arg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user whose role will be set.
- `newRoles: [String]?` - allowed.

---

## MembersSetPermissions2Error

The MembersSetPermissions2Error union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `lastAdmin` - Cannot remove the admin setting of the last admin.
- `userNotInTeam` - The user is not a member of the team.
- `cannotSetPermissions` - Cannot remove/grant permissions. This can happen if the team member is suspended.
- `roleNotFound` - No matching role found. At least one of the provided new_roles does not exist on this team.
- `other` - An unspecified error.

---

## MembersSetPermissions2Result

The MembersSetPermissions2Result struct

**Properties:**

- `teamMemberId: String` - The member ID of the user to which the change was applied.
- `roles: [Team.TeamMemberRole]?` - The roles after the change. Empty in case the user become a non-admin.

---

## MembersSetPermissionsArg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user whose role will be set.
- `newRole: Team.AdminTier` - The new role of the member.

---

## MembersSetPermissionsError

The MembersSetPermissionsError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `lastAdmin` - Cannot remove the admin setting of the last admin.
- `userNotInTeam` - The user is not a member of the team.
- `cannotSetPermissions` - Cannot remove/grant permissions.
- `teamLicenseLimit` - Team is full. The organization has no available licenses.
- `other` - An unspecified error.

---

## MembersSetPermissionsResult

The MembersSetPermissionsResult struct

**Properties:**

- `teamMemberId: String` - The member ID of the user to which the change was applied.
- `role: Team.AdminTier` - The role after the change.

---

## MembersSetProfileArg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account. At least one of new_email, new_external_id, new_given_name, and/or new_surname must be provided.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user whose profile will be set.
- `newEmail: String?` - New email for member.
- `newExternalId: String?` - New external ID for member.
- `newGivenName: String?` - New given name for member.
- `newSurname: String?` - New surname for member.
- `newPersistentId: String?` - New persistent ID. This field only available to teams using persistent ID SAML configuration.
- `newIsDirectoryRestricted: Bool?` - New value for whether the user is a directory restricted user.

---

## MembersSetProfileError

The MembersSetProfileError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `externalIdAndNewExternalIdUnsafe` - It is unsafe to use both external_id and new_external_id.
- `noNewDataSpecified` - None of new_email, new_given_name, new_surname, or new_external_id are specified.
- `emailReservedForOtherUser` - Email is already reserved for another user.
- `externalIdUsedByOtherUser` - The external ID is already in use by another team member.
- `setProfileDisallowed` - Modifying deleted users is not allowed.
- `paramCannotBeEmpty` - Parameter new_email cannot be empty.
- `persistentIdDisabled` - more information.
- `persistentIdUsedByOtherUser` - The persistent ID is already in use by another team member.
- `directoryRestrictedOff` - Directory Restrictions option is not available.
- `other` - An unspecified error.

---

## MembersSetProfilePhotoArg

The MembersSetProfilePhotoArg struct

**Properties:**

- `user: Team.UserSelectorArg` - Identity of the user whose profile photo will be set.
- `photo: Account.PhotoSourceArg` - Image to set as the member's new profile photo.

---

## MembersSetProfilePhotoError

The MembersSetProfilePhotoError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `setProfileDisallowed` - Modifying deleted users is not allowed.
- `photoError` (Account.SetProfilePhotoError) - An unspecified error.
- `other` - An unspecified error.

---

## MembersSuspendError

The MembersSuspendError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.
- `suspendInactiveUser` - The user is not active, so it cannot be suspended.
- `suspendLastAdmin` - The user is the last admin of the team, so it cannot be suspended.
- `teamLicenseLimit` - Team is full. The organization has no available licenses.

---

## MembersTransferFormerMembersFilesError

The MembersTransferFormerMembersFilesError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.
- `removedAndTransferDestShouldDiffer` - Expected removed user and transfer_dest user to be different.
- `removedAndTransferAdminShouldDiffer` - Expected removed user and transfer_admin user to be different.
- `transferDestUserNotFound` - No matching user found for the argument transfer_dest_id.
- `transferDestUserNotInTeam` - The provided transfer_dest_id does not exist on this team.
- `transferAdminUserNotInTeam` - The provided transfer_admin_id does not exist on this team.
- `transferAdminUserNotFound` - No matching user found for the argument transfer_admin_id.
- `unspecifiedTransferAdminId` - The transfer_admin_id argument must be provided when file transfer is requested.
- `transferAdminIsNotAdmin` - Specified transfer_admin user is not a team admin.
- `recipientNotVerified` - The recipient user's email is not verified.
- `userDataIsBeingTransferred` - The user's data is being transferred. Please wait some time before retrying.
- `userNotRemoved` - No matching removed user found for the argument user.
- `userDataCannotBeTransferred` - User files aren't transferable anymore.
- `userDataAlreadyTransferred` - User's data has already been transferred to another user.

---

## MembersUnsuspendArg

Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Properties:**

- `user: Team.UserSelectorArg` - Identity of user to unsuspend.

---

## MembersUnsuspendError

The MembersUnsuspendError union

**Cases:**

- `userNotFound` - No matching user found. The provided team_member_id, email, or external_id does not exist on this team.
- `userNotInTeam` - The user is not a member of the team.
- `other` - An unspecified error.
- `unsuspendNonSuspendedMember` - The user is unsuspended, so it cannot be unsuspended again.
- `teamLicenseLimit` - Team is full. The organization has no available licenses.

---

## MobileClientPlatform

The MobileClientPlatform union

**Cases:**

- `iphone` - Official Dropbox iPhone client.
- `ipad` - Official Dropbox iPad client.
- `android` - Official Dropbox Android client.
- `windowsPhone` - Official Dropbox Windows phone client.
- `blackberry` - Official Dropbox Blackberry client.
- `other` - An unspecified error.

---

## MobileClientSession

Information about linked Dropbox mobile client sessions.

Extends `Team.DeviceSession`

**Properties:**

- `deviceName: String` - The device name.
- `clientType: Team.MobileClientPlatform` - The mobile application type.
- `clientVersion: String?` - The dropbox client version.
- `osVersion: String?` - The hosting OS version.
- `lastCarrier: String?` - last carrier used by the device.

---

## NamespaceMetadata

Properties of a namespace.

**Properties:**

- `name: String` - The name of this namespace.
- `namespaceId: String` - The ID of this namespace.
- `namespaceType: Team.NamespaceType` - The type of this namespace.
- `teamMemberId: String?` - present.

---

## NamespaceType

The NamespaceType union

**Cases:**

- `appFolder` - App sandbox folder.
- `sharedFolder` - Shared folder.
- `teamFolder` - Top-level team-owned folder.
- `teamMemberFolder` - Team member's home folder.
- `other` - An unspecified error.

---

## RemoveCustomQuotaResult

User result for setting member custom quota.

**Cases:**

- `success` (Team.UserSelectorArg) - Successfully removed user.
- `invalidUser` (Team.UserSelectorArg) - Invalid user (not in team).
- `other` - An unspecified error.

---

## RemovedStatus

The RemovedStatus struct

**Properties:**

- `isRecoverable: Bool` - True if the removed team member is recoverable.
- `isDisconnected: Bool` - True if the team member's account was converted to individual account.

---

## ResendSecondaryEmailResult

Result of trying to resend verification email to a secondary email address. 'success' is the only value indicating that a verification email was successfully sent. The other values explain the type of error that occurred, and include the email for which the error occurred.

**Cases:**

- `success` (String) - A verification email was successfully sent to the secondary email address.
- `notPending` (String) - This secondary email address is not pending for the user.
- `rateLimited` (String) - Too many emails are being sent to this email address. Please try again later.
- `other` - An unspecified error.

---

## ResendVerificationEmailArg

The ResendVerificationEmailArg struct

**Properties:**

- `emailsToResend: [Team.UserSecondaryEmailsArg]` - List of users and secondary emails to resend verification emails to.

---

## ResendVerificationEmailResult

List of users and resend results.

**Properties:**

- `results: [Team.UserResendResult]` - (no description)

---

## RevokeDesktopClientArg

The RevokeDesktopClientArg struct

Extends `Team.DeviceSessionArg`

**Properties:**

- `deleteOnUnlink: Bool` - will be made the next time the client access the account).

---

## RevokeDeviceSessionArg

The RevokeDeviceSessionArg union

**Cases:**

- `webSession` (Team.DeviceSessionArg) - End an active session.
- `desktopClient` (Team.RevokeDesktopClientArg) - Unlink a linked desktop device.
- `mobileClient` (Team.DeviceSessionArg) - Unlink a linked mobile device.

---

## RevokeDeviceSessionBatchArg

The RevokeDeviceSessionBatchArg struct

**Properties:**

- `revokeDevices: [Team.RevokeDeviceSessionArg]` - (no description)

---

## RevokeDeviceSessionBatchError

The RevokeDeviceSessionBatchError union

**Cases:**

- `other` - An unspecified error.

---

## RevokeDeviceSessionBatchResult

The RevokeDeviceSessionBatchResult struct

**Properties:**

- `revokeDevicesStatus: [Team.RevokeDeviceSessionStatus]` - (no description)

---

## RevokeDeviceSessionError

The RevokeDeviceSessionError union

**Cases:**

- `deviceSessionNotFound` - Device session not found.
- `memberNotFound` - Member not found.
- `other` - An unspecified error.

---

## RevokeDeviceSessionStatus

The RevokeDeviceSessionStatus struct

**Properties:**

- `success: Bool` - Result of the revoking request.
- `errorType: Team.RevokeDeviceSessionError?` - The error cause in case of a failure.

---

## RevokeLinkedApiAppArg

The RevokeLinkedApiAppArg struct

**Properties:**

- `appId: String` - The application's unique id.
- `teamMemberId: String` - The unique id of the member owning the device.
- `keepAppFolder: Bool` - be kept.

---

## RevokeLinkedApiAppBatchArg

The RevokeLinkedApiAppBatchArg struct

**Properties:**

- `revokeLinkedApp: [Team.RevokeLinkedApiAppArg]` - (no description)

---

## RevokeLinkedAppBatchError

Error returned by linkedAppsRevokeLinkedAppBatch.

**Cases:**

- `other` - An unspecified error.

---

## RevokeLinkedAppBatchResult

The RevokeLinkedAppBatchResult struct

**Properties:**

- `revokeLinkedAppStatus: [Team.RevokeLinkedAppStatus]` - (no description)

---

## RevokeLinkedAppError

Error returned by linkedAppsRevokeLinkedApp.

**Cases:**

- `appNotFound` - Application not found.
- `memberNotFound` - Member not found.
- `appFolderRemovalNotSupported` - App folder removal is not supported.
- `other` - An unspecified error.

---

## RevokeLinkedAppStatus

The RevokeLinkedAppStatus struct

**Properties:**

- `success: Bool` - Result of the revoking request.
- `errorType: Team.RevokeLinkedAppError?` - The error cause in case of a failure.

---

## SetCustomQuotaArg

The SetCustomQuotaArg struct

**Properties:**

- `usersAndQuotas: [Team.UserCustomQuotaArg]` - List of users and their custom quotas.

---

## SetCustomQuotaError

Error returned when setting member custom quota.

**Cases:**

- `tooManyUsers` - A maximum of 1000 users can be set for a single call.
- `other` - An unspecified error.
- `someUsersAreExcluded` - Some of the users are on the excluded users list and can't have custom quota set.

---

## SharingAllowlistAddArgs

Structure representing Approve List entries. Domain and emails are supported. At least one entry of any supported type is required.

**Properties:**

- `domains: [String]?` - List of domains represented by valid string representation (RFC-1034/5).
- `emails: [String]?` - List of emails represented by valid string representation (RFC-5322/822).

---

## SharingAllowlistAddError

The SharingAllowlistAddError union

**Cases:**

- `malformedEntry` (String) - One of provided values is not valid.
- `noEntriesProvided` - Neither single domain nor email provided.
- `tooManyEntriesProvided` - Too many entries provided within one call.
- `teamLimitReached` - Team entries limit reached.
- `unknownError` - Unknown error.
- `entriesAlreadyExist` (String) - Entries already exists.
- `other` - An unspecified error.

---

## SharingAllowlistAddResponse

This struct is empty. The comment here is intentionally emitted to avoid indentation issues with Stone.

---

## SharingAllowlistListArg

The SharingAllowlistListArg struct

**Properties:**

- `limit: UInt32` - The number of entries to fetch at one time.

---

## SharingAllowlistListContinueArg

The SharingAllowlistListContinueArg struct

**Properties:**

- `cursor: String` - The cursor returned from a previous call to sharingAllowlistList or sharingAllowlistListContinue.

---

## SharingAllowlistListContinueError

The SharingAllowlistListContinueError union

**Cases:**

- `invalidCursor` - Provided cursor is not valid.
- `other` - An unspecified error.

---

## SharingAllowlistListError

This struct is empty. The comment here is intentionally emitted to avoid indentation issues with Stone.

---

## SharingAllowlistListResponse

The SharingAllowlistListResponse struct

**Properties:**

- `domains: [String]` - List of domains represented by valid string representation (RFC-1034/5).
- `emails: [String]` - List of emails represented by valid string representation (RFC-5322/822).
- `cursor: String` - If this is nonempty, there are more entries that can be fetched with sharingAllowlistListContinue.
- `hasMore: Bool` - if true indicates that more entries can be fetched with sharingAllowlistListContinue.

---

## SharingAllowlistRemoveArgs

The SharingAllowlistRemoveArgs struct

**Properties:**

- `domains: [String]?` - List of domains represented by valid string representation (RFC-1034/5).
- `emails: [String]?` - List of emails represented by valid string representation (RFC-5322/822).

---

## SharingAllowlistRemoveError

The SharingAllowlistRemoveError union

**Cases:**

- `malformedEntry` (String) - One of provided values is not valid.
- `entriesDoNotExist` (String) - One or more provided values do not exist.
- `noEntriesProvided` - Neither single domain nor email provided.
- `tooManyEntriesProvided` - Too many entries provided within one call.
- `unknownError` - Unknown error.
- `other` - An unspecified error.

---

## SharingAllowlistRemoveResponse

This struct is empty. The comment here is intentionally emitted to avoid indentation issues with Stone.

---

## StorageBucket

Describes the number of users in a specific storage bucket.

**Properties:**

- `bucket: String` - The name of the storage bucket. For example, '1G' is a bucket of users with storage size up to 1 Giga.
- `users: UInt64` - The number of people whose storage is in the range of this storage bucket.

---

## TeamFolderAccessError

The TeamFolderAccessError union

**Cases:**

- `invalidTeamFolderId` - The team folder ID is invalid.
- `noAccess` - The authenticated app does not have permission to manage that team folder.
- `other` - An unspecified error.

---

## TeamFolderActivateError

The TeamFolderActivateError union

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.

---

## TeamFolderIdArg

The TeamFolderIdArg struct

**Properties:**

- `teamFolderId: String` - The ID of the team folder.

---

## TeamFolderArchiveArg

The TeamFolderArchiveArg struct

Extends `Team.TeamFolderIdArg`

**Properties:**

- `forceAsyncOff: Bool` - Whether to force the archive to happen synchronously.

---

## TeamFolderArchiveError

The TeamFolderArchiveError union

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.

---

## TeamFolderArchiveJobStatus

The TeamFolderArchiveJobStatus union

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (Team.TeamFolderMetadata) - The archive job has finished. The value is the metadata for the resulting team folder.
- `failed` (Team.TeamFolderArchiveError) - Error occurred while performing an asynchronous job from teamFolderArchive.

---

## TeamFolderArchiveLaunch

The TeamFolderArchiveLaunch union

**Cases:**

- `asyncJobId` (String) - the status of the asynchronous job.
- `complete` (Team.TeamFolderMetadata) - An unspecified error.

---

## TeamFolderCreateArg

The TeamFolderCreateArg struct

**Properties:**

- `name: String` - Name for the new team folder.
- `syncSetting: Files.SyncSettingArg?` - The sync setting to apply to this team folder. Only permitted if the team has team selective sync enabled.

---

## TeamFolderCreateError

The TeamFolderCreateError union

**Cases:**

- `invalidFolderName` - The provided name cannot be used.
- `folderNameAlreadyUsed` - There is already a team folder with the provided name.
- `folderNameReserved` - The provided name cannot be used because it is reserved.
- `syncSettingsError` (Files.SyncSettingsError) - An error occurred setting the sync settings.
- `other` - An unspecified error.

---

## TeamFolderGetInfoItem

The TeamFolderGetInfoItem union

**Cases:**

- `idNotFound` (String) - An ID that was provided as a parameter to teamFolderGetInfo did not match any of the team's team folders.
- `teamFolderMetadata` (Team.TeamFolderMetadata) - Properties of a team folder.

---

## TeamFolderIdListArg

The TeamFolderIdListArg struct

**Properties:**

- `teamFolderIds: [String]` - The list of team folder IDs.

---

## TeamFolderInvalidStatusError

The TeamFolderInvalidStatusError union

**Cases:**

- `active` - The folder is active and the operation did not succeed.
- `archived` - The folder is archived and the operation did not succeed.
- `archiveInProgress` - The folder is being archived and the operation did not succeed.
- `other` - An unspecified error.

---

## TeamFolderListArg

The TeamFolderListArg struct

**Properties:**

- `limit: UInt32` - The maximum number of results to return per request.

---

## TeamFolderListContinueArg

The TeamFolderListContinueArg struct

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of team folders.

---

## TeamFolderListContinueError

The TeamFolderListContinueError union

**Cases:**

- `invalidCursor` - The cursor is invalid.
- `other` - An unspecified error.

---

## TeamFolderListError

The TeamFolderListError struct

**Properties:**

- `accessError: Team.TeamFolderAccessError` - (no description)

---

## TeamFolderListResult

Result for teamFolderList and teamFolderListContinue.

**Properties:**

- `teamFolders: [Team.TeamFolderMetadata]` - List of all team folders in the authenticated team.
- `cursor: String` - Pass the cursor into teamFolderListContinue to obtain additional team folders.
- `hasMore: Bool` - teamFolderListContinue can retrieve them.

---

## TeamFolderMetadata

Properties of a team folder.

**Properties:**

- `teamFolderId: String` - The ID of the team folder.
- `name: String` - The name of the team folder.
- `status: Team.TeamFolderStatus` - The status of the team folder.
- `isTeamSharedDropbox: Bool` - True if this team folder is a shared team root.
- `syncSetting: Files.SyncSetting` - The sync setting applied to this team folder.
- `contentSyncSettings: [Files.ContentSyncSetting]` - Sync settings applied to contents of this team folder.

---

## TeamFolderPermanentlyDeleteError

The TeamFolderPermanentlyDeleteError union

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.

---

## TeamFolderRenameArg

The TeamFolderRenameArg struct

Extends `Team.TeamFolderIdArg`

**Properties:**

- `name: String` - New team folder name.

---

## TeamFolderRenameError

The TeamFolderRenameError union

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.
- `invalidFolderName` - The provided folder name cannot be used.
- `folderNameAlreadyUsed` - There is already a team folder with the same name.
- `folderNameReserved` - The provided name cannot be used because it is reserved.

---

## TeamFolderStatus

The TeamFolderStatus union

**Cases:**

- `active` - The team folder and sub-folders are available to all members.
- `archived` - The team folder is not accessible outside of the team folder manager.
- `archiveInProgress` - The team folder is not accessible outside of the team folder manager.
- `other` - An unspecified error.

---

## TeamFolderTeamSharedDropboxError

The TeamFolderTeamSharedDropboxError union

**Cases:**

- `disallowed` - This action is not allowed for a shared team root.
- `other` - An unspecified error.

---

## TeamFolderUpdateSyncSettingsArg

The TeamFolderUpdateSyncSettingsArg struct

Extends `Team.TeamFolderIdArg`

**Properties:**

- `syncSetting: Files.SyncSettingArg?` - root.
- `contentSyncSettings: [Files.ContentSyncSettingArg]?` - Sync settings to apply to contents of this team folder.

---

## TeamFolderUpdateSyncSettingsError

The TeamFolderUpdateSyncSettingsError union

**Cases:**

- `accessError` (Team.TeamFolderAccessError) - An unspecified error.
- `statusError` (Team.TeamFolderInvalidStatusError) - An unspecified error.
- `teamSharedDropboxError` (Team.TeamFolderTeamSharedDropboxError) - An unspecified error.
- `other` - An unspecified error.
- `syncSettingsError` (Files.SyncSettingsError) - An error occurred setting the sync settings.

---

## TeamGetInfoResult

The TeamGetInfoResult struct

**Properties:**

- `name: String` - The name of the team.
- `teamId: String` - The ID of the team.
- `numLicensedUsers: UInt32` - The number of licenses available to the team.
- `numProvisionedUsers: UInt32` - The number of accounts that have been invited or are already active members of the team.
- `numUsedLicenses: UInt32` - The number of licenses used on the team.
- `policies: TeamPolicies.TeamMemberPolicies` - (no description)

---

## TeamMemberInfo

Information about a team member.

**Properties:**

- `profile: Team.TeamMemberProfile` - Profile of a user as a member of a team.
- `role: Team.AdminTier` - The user's role in the team.

---

## TeamMemberInfoV2

Information about a team member.

**Properties:**

- `profile: Team.TeamMemberProfile` - Profile of a user as a member of a team.
- `roles: [Team.TeamMemberRole]?` - The user's roles in the team.

---

## TeamMemberInfoV2Result

Information about a team member, after the change, like at membersSetProfileV2.

**Properties:**

- `memberInfo: Team.TeamMemberInfoV2` - Member info, after the change.

---

## TeamMemberProfile

Profile of a user as a member of a team.

Extends `Team.MemberProfile`

**Properties:**

- `groups: [String]` - List of group IDs of groups that the user belongs to.
- `memberFolderId: String` - The namespace id of the user's root folder.

---

## TeamMemberRole

A role which can be attached to a team member. This replaces AdminTier; each AdminTier corresponds to a new TeamMemberRole with a matching name.

**Properties:**

- `roleId: String` - A string containing encoded role ID. For roles defined by Dropbox, this is the same across all teams.
- `name: String` - The role display name.
- `description_: String` - Role description. Describes which permissions come with this role.

---

## TeamMemberStatus

The user's status as a member of a specific team.

**Cases:**

- `active` - User has successfully joined the team.
- `invited` - User has been invited to a team, but has not joined the team yet.
- `suspended` - team member.
- `removed` (Team.RemovedStatus) - members/list.

---

## TeamMembershipType

The TeamMembershipType union

**Cases:**

- `full` - User uses a license and has full access to team resources like the shared quota.
- `limited` - User does not have access to the shared quota and team admins have restricted administrative control.

---

## TeamNamespacesListArg

The TeamNamespacesListArg struct

**Properties:**

- `limit: UInt32` - Specifying a value here has no effect.

---

## TeamNamespacesListContinueArg

The TeamNamespacesListContinueArg struct

**Properties:**

- `cursor: String` - Indicates from what point to get the next set of team-accessible namespaces.

---

## TeamNamespacesListError

The TeamNamespacesListError union

**Cases:**

- `invalidArg` - Argument passed in is invalid.
- `other` - An unspecified error.

---

## TeamNamespacesListContinueError

The TeamNamespacesListContinueError union

**Cases:**

- `invalidArg` - Argument passed in is invalid.
- `other` - An unspecified error.
- `invalidCursor` - The cursor is invalid.

---

## TeamNamespacesListResult

Result for namespacesList.

**Properties:**

- `namespaces: [Team.NamespaceMetadata]` - List of all namespaces the team can access.
- `cursor: String` - may be returned.
- `hasMore: Bool` - Is true if there are additional namespaces that have not been returned yet.

---

## TeamReportFailureReason

The TeamReportFailureReason union

**Cases:**

- `temporaryError` - We couldn't create the report, but we think this was a fluke. Everything should work if you try it again.
- `manyReportsAtOnce` - Too many other reports are being created right now. Try creating this report again once the others finish.
- `tooMuchData` - We couldn't create the report. Try creating the report again with less data.
- `other` - An unspecified error.

---

## TokenGetAuthenticatedAdminError

Error returned by tokenGetAuthenticatedAdmin.

**Cases:**

- `mappingNotFound` - created. Consider re-authorizing a new access token to record its authenticating admin.
- `adminNotActive` - team admin.
- `other` - An unspecified error.

---

## TokenGetAuthenticatedAdminResult

Results for tokenGetAuthenticatedAdmin.

**Properties:**

- `adminProfile: Team.TeamMemberProfile` - The admin who authorized the token.

---

## UploadApiRateLimitValue

The value for uploadApiRateLimit in Feature.

**Cases:**

- `unlimited` - unlimited monthly upload api quota.
- `limit` (UInt32) - The number of upload API calls allowed per month.
- `other` - An unspecified error.

---

## UserAddResult

Result of trying to add secondary emails to a user. 'success' is the only value indicating that a user was successfully retrieved for adding secondary emails. The other values explain the type of error that occurred, and include the user for which the error occurred.

**Cases:**

- `success` (Team.UserSecondaryEmailsResult) - Describes a user and the results for each attempt to add a secondary email.
- `invalidUser` (Team.UserSelectorArg) - Specified user is not a valid target for adding secondary emails.
- `unverified` (Team.UserSelectorArg) - Secondary emails can only be added to verified users.
- `placeholderUser` (Team.UserSelectorArg) - Secondary emails cannot be added to placeholder users.
- `other` - An unspecified error.

---

## UserCustomQuotaArg

User and their required custom quota in GB (1 TB = 1024 GB).

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `quotaGb: UInt32` - (no description)

---

## UserCustomQuotaResult

User and their custom quota in GB (1 TB = 1024 GB).  No quota returns if the user has no custom quota set.

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `quotaGb: UInt32?` - (no description)

---

## UserDeleteEmailsResult

The UserDeleteEmailsResult struct

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `results: [Team.DeleteSecondaryEmailResult]` - (no description)

---

## UserDeleteResult

Result of trying to delete a user's secondary emails. 'success' is the only value indicating that a user was successfully retrieved for deleting secondary emails. The other values explain the type of error that occurred, and include the user for which the error occurred.

**Cases:**

- `success` (Team.UserDeleteEmailsResult) - Describes a user and the results for each attempt to delete a secondary email.
- `invalidUser` (Team.UserSelectorArg) - Specified user is not a valid target for deleting secondary emails.
- `other` - An unspecified error.

---

## UserResendEmailsResult

The UserResendEmailsResult struct

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `results: [Team.ResendSecondaryEmailResult]` - (no description)

---

## UserResendResult

Result of trying to resend verification emails to a user. 'success' is the only value indicating that a user was successfully retrieved for sending verification emails. The other values explain the type of error that occurred, and include the user for which the error occurred.

**Cases:**

- `success` (Team.UserResendEmailsResult) - Describes a user and the results for each attempt to resend verification emails.
- `invalidUser` (Team.UserSelectorArg) - Specified user is not a valid target for resending verification emails.
- `other` - An unspecified error.

---

## UserSecondaryEmailsArg

User and a list of secondary emails.

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `secondaryEmails: [String]` - (no description)

---

## UserSecondaryEmailsResult

The UserSecondaryEmailsResult struct

**Properties:**

- `user: Team.UserSelectorArg` - (no description)
- `results: [Team.AddSecondaryEmailResult]` - (no description)

---

## UserSelectorArg

Argument for selecting a single user, either by team_member_id, external_id or email.

**Cases:**

- `teamMemberId` (String) - An unspecified error.
- `externalId` (String) - An unspecified error.
- `email` (String) - An unspecified error.

---

## UsersSelectorArg

Argument for selecting a list of users, either by team_member_ids, external_ids or emails.

**Cases:**

- `teamMemberIds` ([String]) - List of member IDs.
- `externalIds` ([String]) - List of external user IDs.
- `emails` ([String]) - List of email addresses.

