# TeamRoutes

Routes for the team namespace.

---

## devicesListMemberDevices

List all device sessions of a team's member.

**Scope:** `sessions.list`

```swift
@discardableResult public func devicesListMemberDevices(
    teamMemberId: String,
    includeWebSessions: Bool = true,
    includeDesktopClients: Bool = true,
    includeMobileClients: Bool = true
) -> RpcRequest<Team.ListMemberDevicesResultSerializer, Team.ListMemberDevicesErrorSerializer>
```

**Parameters:**
- `teamMemberId` - The team's member id.
- `includeWebSessions` - Whether to list web sessions of the team's member.
- `includeDesktopClients` - Whether to list linked desktop devices of the team's member.
- `includeMobileClients` - Whether to list linked mobile devices of the team's member.

**Returns:** `Team.ListMemberDevicesResult` on success, `Team.ListMemberDevicesError` on failure.

---

## devicesListMembersDevices

List all device sessions of a team. Permission : Team member file access.

**Scope:** `sessions.list`

```swift
@discardableResult public func devicesListMembersDevices(
    cursor: String? = nil,
    includeWebSessions: Bool = true,
    includeDesktopClients: Bool = true,
    includeMobileClients: Bool = true
) -> RpcRequest<Team.ListMembersDevicesResultSerializer, Team.ListMembersDevicesErrorSerializer>
```

**Parameters:**
- `cursor` - At the first call to the devicesListMembersDevices the cursor shouldn't be passed. Then, if the result of the call includes a cursor, the following requests should include the received cursors in order to receive the next sub list of team devices.
- `includeWebSessions` - Whether to list web sessions of the team members.
- `includeDesktopClients` - Whether to list desktop clients of the team members.
- `includeMobileClients` - Whether to list mobile clients of the team members.

**Returns:** `Team.ListMembersDevicesResult` on success, `Team.ListMembersDevicesError` on failure.

---

## devicesListTeamDevices

List all device sessions of a team. Permission : Team member file access.

> **Deprecated:** Use `devicesListMembersDevices` instead.

**Scope:** `sessions.list`

```swift
@discardableResult public func devicesListTeamDevices(
    cursor: String? = nil,
    includeWebSessions: Bool = true,
    includeDesktopClients: Bool = true,
    includeMobileClients: Bool = true
) -> RpcRequest<Team.ListTeamDevicesResultSerializer, Team.ListTeamDevicesErrorSerializer>
```

**Parameters:**
- `cursor` - At the first call to the devicesListTeamDevices the cursor shouldn't be passed. Then, if the result of the call includes a cursor, the following requests should include the received cursors in order to receive the next sub list of team devices.
- `includeWebSessions` - Whether to list web sessions of the team members.
- `includeDesktopClients` - Whether to list desktop clients of the team members.
- `includeMobileClients` - Whether to list mobile clients of the team members.

**Returns:** `Team.ListTeamDevicesResult` on success, `Team.ListTeamDevicesError` on failure.

---

## devicesRevokeDeviceSession

Revoke a device session of a team's member.

**Scope:** `sessions.modify`

```swift
@discardableResult public func devicesRevokeDeviceSession(
    revokeDeviceSessionArg: Team.RevokeDeviceSessionArg
) -> RpcRequest<VoidSerializer, Team.RevokeDeviceSessionErrorSerializer>
```

**Parameters:**
- `revokeDeviceSessionArg` - The RevokeDeviceSessionArg union.

**Returns:** `Void` on success, `Team.RevokeDeviceSessionError` on failure.

---

## devicesRevokeDeviceSessionBatch

Revoke a list of device sessions of team members.

**Scope:** `sessions.modify`

```swift
@discardableResult public func devicesRevokeDeviceSessionBatch(
    revokeDevices: [Team.RevokeDeviceSessionArg]
) -> RpcRequest<Team.RevokeDeviceSessionBatchResultSerializer, Team.RevokeDeviceSessionBatchErrorSerializer>
```

**Parameters:**
- `revokeDevices` - List of device sessions to revoke.

**Returns:** `Team.RevokeDeviceSessionBatchResult` on success, `Team.RevokeDeviceSessionBatchError` on failure.

---

## featuresGetValues

Get the values for one or more featues. This route allows you to check your account's capability for what feature you can access or what value you have for certain features. Permission : Team information.

**Scope:** `team_info.read`

```swift
@discardableResult public func featuresGetValues(
    features: [Team.Feature]
) -> RpcRequest<Team.FeaturesGetValuesBatchResultSerializer, Team.FeaturesGetValuesBatchErrorSerializer>
```

**Parameters:**
- `features` - A list of features in Feature. If the list is empty, this route will return FeaturesGetValuesBatchError.

**Returns:** `Team.FeaturesGetValuesBatchResult` on success, `Team.FeaturesGetValuesBatchError` on failure.

---

## getInfo

Retrieves information about a team.

**Scope:** `team_info.read`

```swift
@discardableResult public func getInfo() -> RpcRequest<Team.TeamGetInfoResultSerializer, VoidSerializer>
```

**Parameters:**

None.

**Returns:** `Team.TeamGetInfoResult` on success, `Void` on failure.

---

## groupsCreate

Creates a new, empty group, with a requested name. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsCreate(
    groupName: String,
    addCreatorAsOwner: Bool = false,
    groupExternalId: String? = nil,
    groupManagementType: TeamCommon.GroupManagementType? = nil
) -> RpcRequest<Team.GroupFullInfoSerializer, Team.GroupCreateErrorSerializer>
```

**Parameters:**
- `groupName` - Group name.
- `addCreatorAsOwner` - Automatically add the creator of the group.
- `groupExternalId` - The creator of a team can associate an arbitrary external ID to the group.
- `groupManagementType` - Whether the team can be managed by selected users, or only by team admins.

**Returns:** `Team.GroupFullInfo` on success, `Team.GroupCreateError` on failure.

---

## groupsDelete

Deletes a group. The group is deleted immediately. However the revoking of group-owned resources may take additional time. Use the groupsJobStatusGet to determine whether this process has completed. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsDelete(
    groupSelector: Team.GroupSelector
) -> RpcRequest<Async.LaunchEmptyResultSerializer, Team.GroupDeleteErrorSerializer>
```

**Parameters:**
- `groupSelector` - Argument for selecting a single group, either by group_id or by external group ID.

**Returns:** `Async.LaunchEmptyResult` on success, `Team.GroupDeleteError` on failure.

---

## groupsGetInfo

Retrieves information about one or more groups. Note that the optional field members in GroupFullInfo is not returned for system-managed groups. Permission : Team Information.

**Scope:** `groups.read`

```swift
@discardableResult public func groupsGetInfo(
    groupsSelector: Team.GroupsSelector
) -> RpcRequest<ArraySerializer<Team.GroupsGetInfoItemSerializer>, Team.GroupsGetInfoErrorSerializer>
```

**Parameters:**
- `groupsSelector` - Argument for selecting a list of groups, either by group_ids, or external group IDs.

**Returns:** `Array<Team.GroupsGetInfoItem>` on success, `Team.GroupsGetInfoError` on failure.

---

## groupsJobStatusGet

Once an async_job_id is returned from groupsDelete, groupsMembersAdd, or groupsMembersRemove use this method to poll the status of granting/revoking group members' access to group-owned resources. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsJobStatusGet(
    asyncJobId: String
) -> RpcRequest<Async.PollEmptyResultSerializer, Team.GroupsPollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Async.PollEmptyResult` on success, `Team.GroupsPollError` on failure.

---

## groupsList

Lists groups on a team. Permission : Team Information.

**Scope:** `groups.read`

```swift
@discardableResult public func groupsList(
    limit: UInt32 = 1_000
) -> RpcRequest<Team.GroupsListResultSerializer, VoidSerializer>
```

**Parameters:**
- `limit` - Number of results to return per call.

**Returns:** `Team.GroupsListResult` on success, `Void` on failure.

---

## groupsListContinue

Once a cursor has been retrieved from groupsList, use this to paginate through all groups. Permission : Team Information.

**Scope:** `groups.read`

```swift
@discardableResult public func groupsListContinue(
    cursor: String
) -> RpcRequest<Team.GroupsListResultSerializer, Team.GroupsListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of groups.

**Returns:** `Team.GroupsListResult` on success, `Team.GroupsListContinueError` on failure.

---

## groupsMembersAdd

Adds members to a group. The members are added immediately. However the granting of group-owned resources may take additional time. Use the groupsJobStatusGet to determine whether this process has completed. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsMembersAdd(
    group: Team.GroupSelector,
    members: [Team.MemberAccess],
    returnMembers: Bool = true
) -> RpcRequest<Team.GroupMembersChangeResultSerializer, Team.GroupMembersAddErrorSerializer>
```

**Parameters:**
- `group` - Group to which users will be added.
- `members` - List of users to be added to the group.
- `returnMembers` - Whether to return the list of members in the group.

**Returns:** `Team.GroupMembersChangeResult` on success, `Team.GroupMembersAddError` on failure.

---

## groupsMembersList

Lists members of a group. Permission : Team Information.

**Scope:** `groups.read`

```swift
@discardableResult public func groupsMembersList(
    group: Team.GroupSelector,
    limit: UInt32 = 1_000
) -> RpcRequest<Team.GroupsMembersListResultSerializer, Team.GroupSelectorErrorSerializer>
```

**Parameters:**
- `group` - The group whose members are to be listed.
- `limit` - Number of results to return per call.

**Returns:** `Team.GroupsMembersListResult` on success, `Team.GroupSelectorError` on failure.

---

## groupsMembersListContinue

Once a cursor has been retrieved from groupsMembersList, use this to paginate through all members of the group. Permission : Team information.

**Scope:** `groups.read`

```swift
@discardableResult public func groupsMembersListContinue(
    cursor: String
) -> RpcRequest<Team.GroupsMembersListResultSerializer, Team.GroupsMembersListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of groups.

**Returns:** `Team.GroupsMembersListResult` on success, `Team.GroupsMembersListContinueError` on failure.

---

## groupsMembersRemove

Removes members from a group. The members are removed immediately. However the revoking of group-owned resources may take additional time. Use the groupsJobStatusGet to determine whether this process has completed. This method permits removing the only owner of a group, even in cases where this is not possible via the web client. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsMembersRemove(
    group: Team.GroupSelector,
    users: [Team.UserSelectorArg],
    returnMembers: Bool = true
) -> RpcRequest<Team.GroupMembersChangeResultSerializer, Team.GroupMembersRemoveErrorSerializer>
```

**Parameters:**
- `group` - Group from which users will be removed.
- `users` - List of users to be removed from the group.
- `returnMembers` - Whether to return the list of members in the group.

**Returns:** `Team.GroupMembersChangeResult` on success, `Team.GroupMembersRemoveError` on failure.

---

## groupsMembersSetAccessType

Sets a member's access type in a group. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsMembersSetAccessType(
    group: Team.GroupSelector,
    user: Team.UserSelectorArg,
    accessType: Team.GroupAccessType,
    returnMembers: Bool = true
) -> RpcRequest<ArraySerializer<Team.GroupsGetInfoItemSerializer>, Team.GroupMemberSetAccessTypeErrorSerializer>
```

**Parameters:**
- `group` - The group in which the member's access type will be set.
- `user` - The user whose access type will be changed.
- `accessType` - New group access type the user will have.
- `returnMembers` - Whether to return the list of members in the group. Note that the default value will cause all the group members to be returned in the response. This may take a long time for large groups.

**Returns:** `Array<Team.GroupsGetInfoItem>` on success, `Team.GroupMemberSetAccessTypeError` on failure.

---

## groupsUpdate

Updates a group's name and/or external ID. Permission : Team member management.

**Scope:** `groups.write`

```swift
@discardableResult public func groupsUpdate(
    group: Team.GroupSelector,
    returnMembers: Bool = true,
    newGroupName: String? = nil,
    newGroupExternalId: String? = nil,
    newGroupManagementType: TeamCommon.GroupManagementType? = nil
) -> RpcRequest<Team.GroupFullInfoSerializer, Team.GroupUpdateErrorSerializer>
```

**Parameters:**
- `group` - Specify a group.
- `returnMembers` - Whether to return the list of members in the group.
- `newGroupName` - Optional argument. Set group name to this if provided.
- `newGroupExternalId` - Optional argument. New group external ID. If the argument is None, the group's external_id won't be updated. If the argument is empty string, the group's external id will be cleared.
- `newGroupManagementType` - Set new group management type, if provided.

**Returns:** `Team.GroupFullInfo` on success, `Team.GroupUpdateError` on failure.

---

## legalHoldsCreatePolicy

Creates new legal hold policy. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsCreatePolicy(
    name: String,
    members: [String],
    description_: String? = nil,
    startDate: Date? = nil,
    endDate: Date? = nil
) -> RpcRequest<Team.LegalHoldPolicySerializer, Team.LegalHoldsPolicyCreateErrorSerializer>
```

**Parameters:**
- `name` - Policy name.
- `members` - List of team member IDs added to the hold.
- `description_` - A description of the legal hold policy.
- `startDate` - Start date of the legal hold policy.
- `endDate` - End date of the legal hold policy.

**Returns:** `Team.LegalHoldPolicy` on success, `Team.LegalHoldsPolicyCreateError` on failure.

---

## legalHoldsGetPolicy

Gets a legal hold by Id. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsGetPolicy(
    id: String
) -> RpcRequest<Team.LegalHoldPolicySerializer, Team.LegalHoldsGetPolicyErrorSerializer>
```

**Parameters:**
- `id` - The legal hold Id.

**Returns:** `Team.LegalHoldPolicy` on success, `Team.LegalHoldsGetPolicyError` on failure.

---

## legalHoldsListHeldRevisions

List the file metadata that's under the hold. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsListHeldRevisions(
    id: String
) -> RpcRequest<Team.LegalHoldsListHeldRevisionResultSerializer, Team.LegalHoldsListHeldRevisionsErrorSerializer>
```

**Parameters:**
- `id` - The legal hold Id.

**Returns:** `Team.LegalHoldsListHeldRevisionResult` on success, `Team.LegalHoldsListHeldRevisionsError` on failure.

---

## legalHoldsListHeldRevisionsContinue

Continue listing the file metadata that's under the hold. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsListHeldRevisionsContinue(
    id: String,
    cursor: String? = nil
) -> RpcRequest<Team.LegalHoldsListHeldRevisionResultSerializer, Team.LegalHoldsListHeldRevisionsErrorSerializer>
```

**Parameters:**
- `id` - The legal hold Id.
- `cursor` - The cursor idicates where to continue reading file metadata entries for the next API call. When there are no more entries, the cursor will return none.

**Returns:** `Team.LegalHoldsListHeldRevisionResult` on success, `Team.LegalHoldsListHeldRevisionsError` on failure.

---

## legalHoldsListPolicies

Lists legal holds on a team. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsListPolicies(
    includeReleased: Bool = false
) -> RpcRequest<Team.LegalHoldsListPoliciesResultSerializer, Team.LegalHoldsListPoliciesErrorSerializer>
```

**Parameters:**
- `includeReleased` - Whether to return holds that were released.

**Returns:** `Team.LegalHoldsListPoliciesResult` on success, `Team.LegalHoldsListPoliciesError` on failure.

---

## legalHoldsReleasePolicy

Releases a legal hold by Id. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsReleasePolicy(
    id: String
) -> RpcRequest<VoidSerializer, Team.LegalHoldsPolicyReleaseErrorSerializer>
```

**Parameters:**
- `id` - The legal hold Id.

**Returns:** `Void` on success, `Team.LegalHoldsPolicyReleaseError` on failure.

---

## legalHoldsUpdatePolicy

Updates a legal hold. Note: Legal Holds is a paid add-on. Not all teams have the feature. Permission : Team member file access.

**Scope:** `team_data.governance.write`

```swift
@discardableResult public func legalHoldsUpdatePolicy(
    id: String,
    name: String? = nil,
    description_: String? = nil,
    members: [String]? = nil
) -> RpcRequest<Team.LegalHoldPolicySerializer, Team.LegalHoldsPolicyUpdateErrorSerializer>
```

**Parameters:**
- `id` - The legal hold Id.
- `name` - Policy new name.
- `description_` - Policy new description.
- `members` - List of team member IDs to apply the policy on.

**Returns:** `Team.LegalHoldPolicy` on success, `Team.LegalHoldsPolicyUpdateError` on failure.

---

## linkedAppsListMemberLinkedApps

List all linked applications of the team member. Note, this endpoint does not list any team-linked applications.

**Scope:** `sessions.list`

```swift
@discardableResult public func linkedAppsListMemberLinkedApps(
    teamMemberId: String
) -> RpcRequest<Team.ListMemberAppsResultSerializer, Team.ListMemberAppsErrorSerializer>
```

**Parameters:**
- `teamMemberId` - The team member id.

**Returns:** `Team.ListMemberAppsResult` on success, `Team.ListMemberAppsError` on failure.

---

## linkedAppsListMembersLinkedApps

List all applications linked to the team members' accounts. Note, this endpoint does not list any team-linked applications.

**Scope:** `sessions.list`

```swift
@discardableResult public func linkedAppsListMembersLinkedApps(
    cursor: String? = nil
) -> RpcRequest<Team.ListMembersAppsResultSerializer, Team.ListMembersAppsErrorSerializer>
```

**Parameters:**
- `cursor` - At the first call to the linkedAppsListMembersLinkedApps the cursor shouldn't be passed. Then, if the result of the call includes a cursor, the following requests should include the received cursors in order to receive the next sub list of the team applications.

**Returns:** `Team.ListMembersAppsResult` on success, `Team.ListMembersAppsError` on failure.

---

## linkedAppsListTeamLinkedApps

List all applications linked to the team members' accounts. Note, this endpoint doesn't list any team-linked applications.

> **Deprecated:** Use `linkedAppsListMembersLinkedApps` instead.

**Scope:** `sessions.list`

```swift
@discardableResult public func linkedAppsListTeamLinkedApps(
    cursor: String? = nil
) -> RpcRequest<Team.ListTeamAppsResultSerializer, Team.ListTeamAppsErrorSerializer>
```

**Parameters:**
- `cursor` - At the first call to the linkedAppsListTeamLinkedApps the cursor shouldn't be passed. Then, if the result of the call includes a cursor, the following requests should include the received cursors in order to receive the next sub list of the team applications.

**Returns:** `Team.ListTeamAppsResult` on success, `Team.ListTeamAppsError` on failure.

---

## linkedAppsRevokeLinkedApp

Revoke a linked application of the team member.

**Scope:** `sessions.modify`

```swift
@discardableResult public func linkedAppsRevokeLinkedApp(
    appId: String,
    teamMemberId: String,
    keepAppFolder: Bool = true
) -> RpcRequest<VoidSerializer, Team.RevokeLinkedAppErrorSerializer>
```

**Parameters:**
- `appId` - The application's unique id.
- `teamMemberId` - The unique id of the member owning the device.
- `keepAppFolder` - This flag is not longer supported, the application dedicated folder (in case the application uses one) will be kept.

**Returns:** `Void` on success, `Team.RevokeLinkedAppError` on failure.

---

## linkedAppsRevokeLinkedAppBatch

Revoke a list of linked applications of the team members.

**Scope:** `sessions.modify`

```swift
@discardableResult public func linkedAppsRevokeLinkedAppBatch(
    revokeLinkedApp: [Team.RevokeLinkedApiAppArg]
) -> RpcRequest<Team.RevokeLinkedAppBatchResultSerializer, Team.RevokeLinkedAppBatchErrorSerializer>
```

**Parameters:**
- `revokeLinkedApp` - List of linked applications to revoke.

**Returns:** `Team.RevokeLinkedAppBatchResult` on success, `Team.RevokeLinkedAppBatchError` on failure.

---

## memberSpaceLimitsExcludedUsersAdd

Add users to member space limits excluded users list.

**Scope:** `members.write`

```swift
@discardableResult public func memberSpaceLimitsExcludedUsersAdd(
    users: [Team.UserSelectorArg]? = nil
) -> RpcRequest<Team.ExcludedUsersUpdateResultSerializer, Team.ExcludedUsersUpdateErrorSerializer>
```

**Parameters:**
- `users` - List of users to be added/removed.

**Returns:** `Team.ExcludedUsersUpdateResult` on success, `Team.ExcludedUsersUpdateError` on failure.

---

## memberSpaceLimitsExcludedUsersList

List member space limits excluded users.

**Scope:** `members.read`

```swift
@discardableResult public func memberSpaceLimitsExcludedUsersList(
    limit: UInt32 = 1_000
) -> RpcRequest<Team.ExcludedUsersListResultSerializer, Team.ExcludedUsersListErrorSerializer>
```

**Parameters:**
- `limit` - Number of results to return per call.

**Returns:** `Team.ExcludedUsersListResult` on success, `Team.ExcludedUsersListError` on failure.

---

## memberSpaceLimitsExcludedUsersListContinue

Continue listing member space limits excluded users.

**Scope:** `members.read`

```swift
@discardableResult public func memberSpaceLimitsExcludedUsersListContinue(
    cursor: String
) -> RpcRequest<Team.ExcludedUsersListResultSerializer, Team.ExcludedUsersListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of users.

**Returns:** `Team.ExcludedUsersListResult` on success, `Team.ExcludedUsersListContinueError` on failure.

---

## memberSpaceLimitsExcludedUsersRemove

Remove users from member space limits excluded users list.

**Scope:** `members.write`

```swift
@discardableResult public func memberSpaceLimitsExcludedUsersRemove(
    users: [Team.UserSelectorArg]? = nil
) -> RpcRequest<Team.ExcludedUsersUpdateResultSerializer, Team.ExcludedUsersUpdateErrorSerializer>
```

**Parameters:**
- `users` - List of users to be added/removed.

**Returns:** `Team.ExcludedUsersUpdateResult` on success, `Team.ExcludedUsersUpdateError` on failure.

---

## memberSpaceLimitsGetCustomQuota

Get users custom quota. A maximum of 1000 members can be specified in a single call. Note: to apply a custom space limit, a team admin needs to set a member space limit for the team first. (the team admin can check the settings here: https://www.dropbox.com/team/admin/settings/space).

**Scope:** `members.read`

```swift
@discardableResult public func memberSpaceLimitsGetCustomQuota(
    users: [Team.UserSelectorArg]
) -> RpcRequest<ArraySerializer<Team.CustomQuotaResultSerializer>, Team.CustomQuotaErrorSerializer>
```

**Parameters:**
- `users` - List of users.

**Returns:** `Array<Team.CustomQuotaResult>` on success, `Team.CustomQuotaError` on failure.

---

## memberSpaceLimitsRemoveCustomQuota

Remove users custom quota. A maximum of 1000 members can be specified in a single call. Note: to apply a custom space limit, a team admin needs to set a member space limit for the team first. (the team admin can check the settings here: https://www.dropbox.com/team/admin/settings/space).

**Scope:** `members.write`

```swift
@discardableResult public func memberSpaceLimitsRemoveCustomQuota(
    users: [Team.UserSelectorArg]
) -> RpcRequest<ArraySerializer<Team.RemoveCustomQuotaResultSerializer>, Team.CustomQuotaErrorSerializer>
```

**Parameters:**
- `users` - List of users.

**Returns:** `Array<Team.RemoveCustomQuotaResult>` on success, `Team.CustomQuotaError` on failure.

---

## memberSpaceLimitsSetCustomQuota

Set users custom quota. Custom quota has to be at least 15GB. A maximum of 1000 members can be specified in a single call. Note: to apply a custom space limit, a team admin needs to set a member space limit for the team first. (the team admin can check the settings here: https://www.dropbox.com/team/admin/settings/space).

**Scope:** `members.read`

```swift
@discardableResult public func memberSpaceLimitsSetCustomQuota(
    usersAndQuotas: [Team.UserCustomQuotaArg]
) -> RpcRequest<ArraySerializer<Team.CustomQuotaResultSerializer>, Team.SetCustomQuotaErrorSerializer>
```

**Parameters:**
- `usersAndQuotas` - List of users and their custom quotas.

**Returns:** `Array<Team.CustomQuotaResult>` on success, `Team.SetCustomQuotaError` on failure.

---

## membersAdd

Adds members to a team. Permission : Team member management. A maximum of 20 members can be specified in a single call. If no Dropbox account exists with the email address specified, a new Dropbox account will be created with the given email address, and that account will be invited to the team. If a personal Dropbox account exists with the email address specified in the call, this call will create a placeholder Dropbox account for the user on the team and send an email inviting the user to migrate their existing personal account onto the team. Team member management apps are required to set an initial given_name and surname for a user to use in the team invitation and for 'Perform as team member' actions taken on the user before they become 'active'.

**Scope:** `members.write`

```swift
@discardableResult public func membersAdd(
    newMembers: [Team.MemberAddArg],
    forceAsync: Bool = false
) -> RpcRequest<Team.MembersAddLaunchSerializer, VoidSerializer>
```

**Parameters:**
- `newMembers` - Details of new members to be added to the team.
- `forceAsync` - Whether to force the add to happen asynchronously.

**Returns:** `Team.MembersAddLaunch` on success, `Void` on failure.

---

## membersAddV2

Adds members to a team. Permission : Team member management. A maximum of 20 members can be specified in a single call. If no Dropbox account exists with the email address specified, a new Dropbox account will be created with the given email address, and that account will be invited to the team. If a personal Dropbox account exists with the email address specified in the call, this call will create a placeholder Dropbox account for the user on the team and send an email inviting the user to migrate their existing personal account onto the team. Team member management apps are required to set an initial given_name and surname for a user to use in the team invitation and for 'Perform as team member' actions taken on the user before they become 'active'.

**Scope:** `members.write`

```swift
@discardableResult public func membersAddV2(
    newMembers: [Team.MemberAddV2Arg],
    forceAsync: Bool = false
) -> RpcRequest<Team.MembersAddLaunchV2ResultSerializer, VoidSerializer>
```

**Parameters:**
- `newMembers` - Details of new members to be added to the team.
- `forceAsync` - Whether to force the add to happen asynchronously.

**Returns:** `Team.MembersAddLaunchV2Result` on success, `Void` on failure.

---

## membersAddJobStatusGet

Once an async_job_id is returned from membersAdd, use this to poll the status of the asynchronous request. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersAddJobStatusGet(
    asyncJobId: String
) -> RpcRequest<Team.MembersAddJobStatusSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Team.MembersAddJobStatus` on success, `Async.PollError` on failure.

---

## membersAddJobStatusGetV2

Once an async_job_id is returned from membersAddV2, use this to poll the status of the asynchronous request. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersAddJobStatusGetV2(
    asyncJobId: String
) -> RpcRequest<Team.MembersAddJobStatusV2ResultSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Team.MembersAddJobStatusV2Result` on success, `Async.PollError` on failure.

---

## membersDeleteProfilePhoto

Deletes a team member's profile photo. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersDeleteProfilePhoto(
    user: Team.UserSelectorArg
) -> RpcRequest<Team.TeamMemberInfoSerializer, Team.MembersDeleteProfilePhotoErrorSerializer>
```

**Parameters:**
- `user` - Identity of the user whose profile photo will be deleted.

**Returns:** `Team.TeamMemberInfo` on success, `Team.MembersDeleteProfilePhotoError` on failure.

---

## membersDeleteProfilePhotoV2

Deletes a team member's profile photo. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersDeleteProfilePhotoV2(
    user: Team.UserSelectorArg
) -> RpcRequest<Team.TeamMemberInfoV2ResultSerializer, Team.MembersDeleteProfilePhotoErrorSerializer>
```

**Parameters:**
- `user` - Identity of the user whose profile photo will be deleted.

**Returns:** `Team.TeamMemberInfoV2Result` on success, `Team.MembersDeleteProfilePhotoError` on failure.

---

## membersGetAvailableTeamMemberRoles

Get available TeamMemberRoles for the connected team. To be used with membersSetAdminPermissionsV2. Permission : Team member management.

**Scope:** `members.read`

```swift
@discardableResult public func membersGetAvailableTeamMemberRoles()
    -> RpcRequest<Team.MembersGetAvailableTeamMemberRolesResultSerializer, VoidSerializer>
```

**Parameters:**

None.

**Returns:** `Team.MembersGetAvailableTeamMemberRolesResult` on success, `Void` on failure.

---

## membersGetInfo

Returns information about multiple team members. Permission : Team information. This endpoint will return idNotFound in MembersGetInfoItem, for IDs (or emails) that cannot be matched to a valid team member.

**Scope:** `members.read`

```swift
@discardableResult public func membersGetInfo(
    members: [Team.UserSelectorArg]
) -> RpcRequest<ArraySerializer<Team.MembersGetInfoItemSerializer>, Team.MembersGetInfoErrorSerializer>
```

**Parameters:**
- `members` - List of team members.

**Returns:** `Array<Team.MembersGetInfoItem>` on success, `Team.MembersGetInfoError` on failure.

---

## membersGetInfoV2

Returns information about multiple team members. Permission : Team information. This endpoint will return idNotFound in MembersGetInfoItem, for IDs (or emails) that cannot be matched to a valid team member.

**Scope:** `members.read`

```swift
@discardableResult public func membersGetInfoV2(
    members: [Team.UserSelectorArg]
) -> RpcRequest<Team.MembersGetInfoV2ResultSerializer, Team.MembersGetInfoErrorSerializer>
```

**Parameters:**
- `members` - List of team members.

**Returns:** `Team.MembersGetInfoV2Result` on success, `Team.MembersGetInfoError` on failure.

---

## membersList

Lists members of a team. Permission : Team information.

**Scope:** `members.read`

```swift
@discardableResult public func membersList(
    limit: UInt32 = 1_000,
    includeRemoved: Bool = false
) -> RpcRequest<Team.MembersListResultSerializer, Team.MembersListErrorSerializer>
```

**Parameters:**
- `limit` - Number of results to return per call.
- `includeRemoved` - Whether to return removed members.

**Returns:** `Team.MembersListResult` on success, `Team.MembersListError` on failure.

---

## membersListV2

Lists members of a team. Permission : Team information.

**Scope:** `members.read`

```swift
@discardableResult public func membersListV2(
    limit: UInt32 = 1_000,
    includeRemoved: Bool = false
) -> RpcRequest<Team.MembersListV2ResultSerializer, Team.MembersListErrorSerializer>
```

**Parameters:**
- `limit` - Number of results to return per call.
- `includeRemoved` - Whether to return removed members.

**Returns:** `Team.MembersListV2Result` on success, `Team.MembersListError` on failure.

---

## membersListContinue

Once a cursor has been retrieved from membersList, use this to paginate through all team members. Permission : Team information.

**Scope:** `members.read`

```swift
@discardableResult public func membersListContinue(
    cursor: String
) -> RpcRequest<Team.MembersListResultSerializer, Team.MembersListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of members.

**Returns:** `Team.MembersListResult` on success, `Team.MembersListContinueError` on failure.

---

## membersListContinueV2

Once a cursor has been retrieved from membersListV2, use this to paginate through all team members. Permission : Team information.

**Scope:** `members.read`

```swift
@discardableResult public func membersListContinueV2(
    cursor: String
) -> RpcRequest<Team.MembersListV2ResultSerializer, Team.MembersListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of members.

**Returns:** `Team.MembersListV2Result` on success, `Team.MembersListContinueError` on failure.

---

## membersMoveFormerMemberFiles

Moves removed member's files to a different member. This endpoint initiates an asynchronous job. To obtain the final result of the job, the client should periodically poll membersMoveFormerMemberFilesJobStatusCheck. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersMoveFormerMemberFiles(
    user: Team.UserSelectorArg,
    transferDestId: Team.UserSelectorArg,
    transferAdminId: Team.UserSelectorArg
) -> RpcRequest<Async.LaunchEmptyResultSerializer, Team.MembersTransferFormerMembersFilesErrorSerializer>
```

**Parameters:**
- `user` - The user whose files will be moved.
- `transferDestId` - Files from the deleted member account will be transferred to this user.
- `transferAdminId` - Errors during the transfer process will be sent via email to this user.

**Returns:** `Async.LaunchEmptyResult` on success, `Team.MembersTransferFormerMembersFilesError` on failure.

---

## membersMoveFormerMemberFilesJobStatusCheck

Once an async_job_id is returned from membersMoveFormerMemberFiles, use this to poll the status of the asynchronous request. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersMoveFormerMemberFilesJobStatusCheck(
    asyncJobId: String
) -> RpcRequest<Async.PollEmptyResultSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Async.PollEmptyResult` on success, `Async.PollError` on failure.

---

## membersRecover

Recover a deleted member. Permission : Team member management. Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Scope:** `members.delete`

```swift
@discardableResult public func membersRecover(
    user: Team.UserSelectorArg
) -> RpcRequest<VoidSerializer, Team.MembersRecoverErrorSerializer>
```

**Parameters:**
- `user` - Identity of user to recover.

**Returns:** `Void` on success, `Team.MembersRecoverError` on failure.

---

## membersRemove

Removes a member from a team. Permission : Team member management. Exactly one of team_member_id, email, or external_id must be provided to identify the user account. Accounts can be recovered via membersRecover for a 7 day period or until the account has been permanently deleted or transferred to another account (whichever comes first). Calling membersAdd while a user is still recoverable on your team will return with userAlreadyOnTeam in MemberAddResult. Accounts can have their files transferred via the admin console for a limited time, based on the version history length associated with the team (180 days for most teams). This endpoint may initiate an asynchronous job. To obtain the final result of the job, the client should periodically poll membersRemoveJobStatusGet.

**Scope:** `members.delete`

```swift
@discardableResult public func membersRemove(
    user: Team.UserSelectorArg,
    wipeData: Bool = true,
    transferDestId: Team.UserSelectorArg? = nil,
    transferAdminId: Team.UserSelectorArg? = nil,
    keepAccount: Bool = false,
    retainTeamShares: Bool = false
) -> RpcRequest<Async.LaunchEmptyResultSerializer, Team.MembersRemoveErrorSerializer>
```

**Parameters:**
- `user` - The user to remove from the team.
- `wipeData` - If provided, controls if the user's data will be deleted on their linked devices.
- `transferDestId` - If provided, files from the deleted member account will be transferred to this user.
- `transferAdminId` - If provided, errors during the transfer process will be sent via email to this user. If the transfer_dest_id argument was provided, then this argument must be provided as well.
- `keepAccount` - Downgrade the member to a Basic account. The user will retain the email address associated with their Dropbox account and data in their account that is not restricted to team members. In order to keep the account the argument wipeData should be set to false.
- `retainTeamShares` - If provided, allows removed users to keep access to Dropbox folders (not Dropbox Paper folders) already explicitly shared with them (not via a group) when they are downgraded to a Basic account. Users will not retain access to folders that do not allow external sharing. In order to keep the sharing relationships, the arguments wipeData should be set to false and keepAccount should be set to true.

**Returns:** `Async.LaunchEmptyResult` on success, `Team.MembersRemoveError` on failure.

---

## membersRemoveJobStatusGet

Once an async_job_id is returned from membersRemove, use this to poll the status of the asynchronous request. Permission : Team member management.

**Scope:** `members.delete`

```swift
@discardableResult public func membersRemoveJobStatusGet(
    asyncJobId: String
) -> RpcRequest<Async.PollEmptyResultSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Async.PollEmptyResult` on success, `Async.PollError` on failure.

---

## membersSecondaryEmailsAdd

Add secondary emails to users. Permission : Team member management. Emails that are on verified domains will be verified automatically. For each email address not on a verified domain a verification email will be sent.

**Scope:** `members.write`

```swift
@discardableResult public func membersSecondaryEmailsAdd(
    newSecondaryEmails: [Team.UserSecondaryEmailsArg]
) -> RpcRequest<Team.AddSecondaryEmailsResultSerializer, Team.AddSecondaryEmailsErrorSerializer>
```

**Parameters:**
- `newSecondaryEmails` - List of users and secondary emails to add.

**Returns:** `Team.AddSecondaryEmailsResult` on success, `Team.AddSecondaryEmailsError` on failure.

---

## membersSecondaryEmailsDelete

Delete secondary emails from users. Permission : Team member management. Users will be notified of deletions of verified secondary emails at both the secondary email and their primary email.

**Scope:** `members.write`

```swift
@discardableResult public func membersSecondaryEmailsDelete(
    emailsToDelete: [Team.UserSecondaryEmailsArg]
) -> RpcRequest<Team.DeleteSecondaryEmailsResultSerializer, VoidSerializer>
```

**Parameters:**
- `emailsToDelete` - List of users and their secondary emails to delete.

**Returns:** `Team.DeleteSecondaryEmailsResult` on success, `Void` on failure.

---

## membersSecondaryEmailsResendVerificationEmails

Resend secondary email verification emails. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSecondaryEmailsResendVerificationEmails(
    emailsToResend: [Team.UserSecondaryEmailsArg]
) -> RpcRequest<Team.ResendVerificationEmailResultSerializer, VoidSerializer>
```

**Parameters:**
- `emailsToResend` - List of users and secondary emails to resend verification emails to.

**Returns:** `Team.ResendVerificationEmailResult` on success, `Void` on failure.

---

## membersSendWelcomeEmail

Sends welcome email to pending team member. Permission : Team member management. Exactly one of team_member_id, email, or external_id must be provided to identify the user account. No-op if team member is not pending.

**Scope:** `members.write`

```swift
@discardableResult public func membersSendWelcomeEmail(
    userSelectorArg: Team.UserSelectorArg
) -> RpcRequest<VoidSerializer, Team.MembersSendWelcomeErrorSerializer>
```

**Parameters:**
- `userSelectorArg` - Argument for selecting a single user, either by team_member_id, external_id or email.

**Returns:** `Void` on success, `Team.MembersSendWelcomeError` on failure.

---

## membersSetAdminPermissions

Updates a team member's permissions. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetAdminPermissions(
    user: Team.UserSelectorArg,
    newRole: Team.AdminTier
) -> RpcRequest<Team.MembersSetPermissionsResultSerializer, Team.MembersSetPermissionsErrorSerializer>
```

**Parameters:**
- `user` - Identity of user whose role will be set.
- `newRole` - The new role of the member.

**Returns:** `Team.MembersSetPermissionsResult` on success, `Team.MembersSetPermissionsError` on failure.

---

## membersSetAdminPermissionsV2

Updates a team member's permissions. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetAdminPermissionsV2(
    user: Team.UserSelectorArg,
    newRoles: [String]? = nil
) -> RpcRequest<Team.MembersSetPermissions2ResultSerializer, Team.MembersSetPermissions2ErrorSerializer>
```

**Parameters:**
- `user` - Identity of user whose role will be set.
- `newRoles` - The new roles for the member. Send empty list to make user member only. For now, only up to one role is allowed.

**Returns:** `Team.MembersSetPermissions2Result` on success, `Team.MembersSetPermissions2Error` on failure.

---

## membersSetProfile

Updates a team member's profile. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetProfile(
    user: Team.UserSelectorArg,
    newEmail: String? = nil,
    newExternalId: String? = nil,
    newGivenName: String? = nil,
    newSurname: String? = nil,
    newPersistentId: String? = nil,
    newIsDirectoryRestricted: Bool? = nil
) -> RpcRequest<Team.TeamMemberInfoSerializer, Team.MembersSetProfileErrorSerializer>
```

**Parameters:**
- `user` - Identity of user whose profile will be set.
- `newEmail` - New email for member.
- `newExternalId` - New external ID for member.
- `newGivenName` - New given name for member.
- `newSurname` - New surname for member.
- `newPersistentId` - New persistent ID. This field only available to teams using persistent ID SAML configuration.
- `newIsDirectoryRestricted` - New value for whether the user is a directory restricted user.

**Returns:** `Team.TeamMemberInfo` on success, `Team.MembersSetProfileError` on failure.

---

## membersSetProfileV2

Updates a team member's profile. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetProfileV2(
    user: Team.UserSelectorArg,
    newEmail: String? = nil,
    newExternalId: String? = nil,
    newGivenName: String? = nil,
    newSurname: String? = nil,
    newPersistentId: String? = nil,
    newIsDirectoryRestricted: Bool? = nil
) -> RpcRequest<Team.TeamMemberInfoV2ResultSerializer, Team.MembersSetProfileErrorSerializer>
```

**Parameters:**
- `user` - Identity of user whose profile will be set.
- `newEmail` - New email for member.
- `newExternalId` - New external ID for member.
- `newGivenName` - New given name for member.
- `newSurname` - New surname for member.
- `newPersistentId` - New persistent ID. This field only available to teams using persistent ID SAML configuration.
- `newIsDirectoryRestricted` - New value for whether the user is a directory restricted user.

**Returns:** `Team.TeamMemberInfoV2Result` on success, `Team.MembersSetProfileError` on failure.

---

## membersSetProfilePhoto

Updates a team member's profile photo. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetProfilePhoto(
    user: Team.UserSelectorArg,
    photo: Account.PhotoSourceArg
) -> RpcRequest<Team.TeamMemberInfoSerializer, Team.MembersSetProfilePhotoErrorSerializer>
```

**Parameters:**
- `user` - Identity of the user whose profile photo will be set.
- `photo` - Image to set as the member's new profile photo.

**Returns:** `Team.TeamMemberInfo` on success, `Team.MembersSetProfilePhotoError` on failure.

---

## membersSetProfilePhotoV2

Updates a team member's profile photo. Permission : Team member management.

**Scope:** `members.write`

```swift
@discardableResult public func membersSetProfilePhotoV2(
    user: Team.UserSelectorArg,
    photo: Account.PhotoSourceArg
) -> RpcRequest<Team.TeamMemberInfoV2ResultSerializer, Team.MembersSetProfilePhotoErrorSerializer>
```

**Parameters:**
- `user` - Identity of the user whose profile photo will be set.
- `photo` - Image to set as the member's new profile photo.

**Returns:** `Team.TeamMemberInfoV2Result` on success, `Team.MembersSetProfilePhotoError` on failure.

---

## membersSuspend

Suspend a member from a team. Permission : Team member management. Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Scope:** `members.write`

```swift
@discardableResult public func membersSuspend(
    user: Team.UserSelectorArg,
    wipeData: Bool = true
) -> RpcRequest<VoidSerializer, Team.MembersSuspendErrorSerializer>
```

**Parameters:**
- `user` - The user to suspend.
- `wipeData` - If provided, controls if the user's data will be deleted on their linked devices.

**Returns:** `Void` on success, `Team.MembersSuspendError` on failure.

---

## membersUnsuspend

Unsuspend a member from a team. Permission : Team member management. Exactly one of team_member_id, email, or external_id must be provided to identify the user account.

**Scope:** `members.write`

```swift
@discardableResult public func membersUnsuspend(
    user: Team.UserSelectorArg
) -> RpcRequest<VoidSerializer, Team.MembersUnsuspendErrorSerializer>
```

**Parameters:**
- `user` - Identity of user to unsuspend.

**Returns:** `Void` on success, `Team.MembersUnsuspendError` on failure.

---

## namespacesList

Returns a list of all team-accessible namespaces. This list includes team folders, shared folders containing team members, team members' home namespaces, and team members' app folders. Home namespaces and app folders are always owned by this team or members of the team, but shared folders may be owned by other users or other teams. Duplicates may occur in the list.

**Scope:** `team_data.member`

```swift
@discardableResult public func namespacesList(
    limit: UInt32 = 1_000
) -> RpcRequest<Team.TeamNamespacesListResultSerializer, Team.TeamNamespacesListErrorSerializer>
```

**Parameters:**
- `limit` - Specifying a value here has no effect.

**Returns:** `Team.TeamNamespacesListResult` on success, `Team.TeamNamespacesListError` on failure.

---

## namespacesListContinue

Once a cursor has been retrieved from namespacesList, use this to paginate through all team-accessible namespaces. Duplicates may occur in the list.

**Scope:** `team_data.member`

```swift
@discardableResult public func namespacesListContinue(
    cursor: String
) -> RpcRequest<Team.TeamNamespacesListResultSerializer, Team.TeamNamespacesListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of team-accessible namespaces.

**Returns:** `Team.TeamNamespacesListResult` on success, `Team.TeamNamespacesListContinueError` on failure.

---

## propertiesTemplateAdd

Permission : Team member file access.

> **Deprecated**

**Scope:** `files.team_metadata.write`

```swift
@discardableResult public func propertiesTemplateAdd(
    name: String,
    description_: String,
    fields: [FileProperties.PropertyFieldTemplate]
) -> RpcRequest<FileProperties.AddTemplateResultSerializer, FileProperties.ModifyTemplateErrorSerializer>
```

**Parameters:**
- `name` - Display name for the template.
- `description_` - Description for the template.
- `fields` - Property field templates to be added to the group template.

**Returns:** `FileProperties.AddTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.

---

## propertiesTemplateGet

Permission : Team member file access. The scope for the route is files.team_metadata.write.

> **Deprecated**

**Scope:** `files.team_metadata.write`

```swift
@discardableResult public func propertiesTemplateGet(
    templateId: String
) -> RpcRequest<FileProperties.GetTemplateResultSerializer, FileProperties.TemplateErrorSerializer>
```

**Parameters:**
- `templateId` - An identifier for template added by route. See templatesAddForUser or templatesAddForTeam.

**Returns:** `FileProperties.GetTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## propertiesTemplateList

Permission : Team member file access. The scope for the route is files.team_metadata.write.

> **Deprecated**

**Scope:** `files.team_metadata.write`

```swift
@discardableResult public func propertiesTemplateList()
    -> RpcRequest<FileProperties.ListTemplateResultSerializer, FileProperties.TemplateErrorSerializer>
```

**Parameters:**

None.

**Returns:** `FileProperties.ListTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## propertiesTemplateUpdate

Permission : Team member file access.

> **Deprecated**

**Scope:** `files.team_metadata.write`

```swift
@discardableResult public func propertiesTemplateUpdate(
    templateId: String,
    name: String? = nil,
    description_: String? = nil,
    addFields: [FileProperties.PropertyFieldTemplate]? = nil
) -> RpcRequest<FileProperties.UpdateTemplateResultSerializer, FileProperties.ModifyTemplateErrorSerializer>
```

**Parameters:**
- `templateId` - An identifier for template added by. See templatesAddForUser or templatesAddForTeam.
- `name` - A display name for the template. Template names can be up to 256 bytes.
- `description_` - Description for the new template. Template descriptions can be up to 1024 bytes.
- `addFields` - Property field templates to be added to the group template. There can be up to 32 properties in a single template.

**Returns:** `FileProperties.UpdateTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.

---

## reportsGetActivity

Retrieves reporting data about a team's user activity. Deprecated: Will be removed on July 1st 2021.

> **Deprecated**

**Scope:** `team_info.read`

```swift
@discardableResult public func reportsGetActivity(
    startDate: Date? = nil,
    endDate: Date? = nil
) -> RpcRequest<Team.GetActivityReportSerializer, Team.DateRangeErrorSerializer>
```

**Parameters:**
- `startDate` - Optional starting date (inclusive). If start_date is None or too long ago, this field will be set to 6 months ago.
- `endDate` - Optional ending date (exclusive).

**Returns:** `Team.GetActivityReport` on success, `Team.DateRangeError` on failure.

---

## reportsGetDevices

Retrieves reporting data about a team's linked devices. Deprecated: Will be removed on July 1st 2021.

> **Deprecated**

**Scope:** `team_info.read`

```swift
@discardableResult public func reportsGetDevices(
    startDate: Date? = nil,
    endDate: Date? = nil
) -> RpcRequest<Team.GetDevicesReportSerializer, Team.DateRangeErrorSerializer>
```

**Parameters:**
- `startDate` - Optional starting date (inclusive). If start_date is None or too long ago, this field will be set to 6 months ago.
- `endDate` - Optional ending date (exclusive).

**Returns:** `Team.GetDevicesReport` on success, `Team.DateRangeError` on failure.

---

## reportsGetMembership

Retrieves reporting data about a team's membership. Deprecated: Will be removed on July 1st 2021.

> **Deprecated**

**Scope:** `team_info.read`

```swift
@discardableResult public func reportsGetMembership(
    startDate: Date? = nil,
    endDate: Date? = nil
) -> RpcRequest<Team.GetMembershipReportSerializer, Team.DateRangeErrorSerializer>
```

**Parameters:**
- `startDate` - Optional starting date (inclusive). If start_date is None or too long ago, this field will be set to 6 months ago.
- `endDate` - Optional ending date (exclusive).

**Returns:** `Team.GetMembershipReport` on success, `Team.DateRangeError` on failure.

---

## reportsGetStorage

Retrieves reporting data about a team's storage usage. Deprecated: Will be removed on July 1st 2021.

> **Deprecated**

**Scope:** `team_info.read`

```swift
@discardableResult public func reportsGetStorage(
    startDate: Date? = nil,
    endDate: Date? = nil
) -> RpcRequest<Team.GetStorageReportSerializer, Team.DateRangeErrorSerializer>
```

**Parameters:**
- `startDate` - Optional starting date (inclusive). If start_date is None or too long ago, this field will be set to 6 months ago.
- `endDate` - Optional ending date (exclusive).

**Returns:** `Team.GetStorageReport` on success, `Team.DateRangeError` on failure.

---

## sharingAllowlistAdd

Endpoint adds Approve List entries. Changes are effective immediately. Changes are committed in transaction. In case of single validation error - all entries are rejected. Valid domains (RFC-1034/5) and emails (RFC-5322/822) are accepted. Added entries cannot overflow limit of 10000 entries per team. Maximum 100 entries per call is allowed.

**Scope:** `team_info.write`

```swift
@discardableResult public func sharingAllowlistAdd(
    domains: [String]? = nil,
    emails: [String]? = nil
) -> RpcRequest<Team.SharingAllowlistAddResponseSerializer, Team.SharingAllowlistAddErrorSerializer>
```

**Parameters:**
- `domains` - List of domains represented by valid string representation (RFC-1034/5).
- `emails` - List of emails represented by valid string representation (RFC-5322/822).

**Returns:** `Team.SharingAllowlistAddResponse` on success, `Team.SharingAllowlistAddError` on failure.

---

## sharingAllowlistList

Lists Approve List entries for given team, from newest to oldest, returning up to `limit` entries at a time. If there are more than `limit` entries associated with the current team, more can be fetched by passing the returned `cursor` to sharingAllowlistListContinue.

**Scope:** `team_info.read`

```swift
@discardableResult public func sharingAllowlistList(
    limit: UInt32 = 1_000
) -> RpcRequest<Team.SharingAllowlistListResponseSerializer, Team.SharingAllowlistListErrorSerializer>
```

**Parameters:**
- `limit` - The number of entries to fetch at one time.

**Returns:** `Team.SharingAllowlistListResponse` on success, `Team.SharingAllowlistListError` on failure.

---

## sharingAllowlistListContinue

Lists entries associated with given team, starting from a the cursor. See sharingAllowlistList.

**Scope:** `team_info.read`

```swift
@discardableResult public func sharingAllowlistListContinue(
    cursor: String
) -> RpcRequest<Team.SharingAllowlistListResponseSerializer, Team.SharingAllowlistListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - The cursor returned from a previous call to sharingAllowlistList or sharingAllowlistListContinue.

**Returns:** `Team.SharingAllowlistListResponse` on success, `Team.SharingAllowlistListContinueError` on failure.

---

## sharingAllowlistRemove

Endpoint removes Approve List entries. Changes are effective immediately. Changes are committed in transaction. In case of single validation error - all entries are rejected. Valid domains (RFC-1034/5) and emails (RFC-5322/822) are accepted. Entries being removed have to be present on the list. Maximum 1000 entries per call is allowed.

**Scope:** `team_info.write`

```swift
@discardableResult public func sharingAllowlistRemove(
    domains: [String]? = nil,
    emails: [String]? = nil
) -> RpcRequest<Team.SharingAllowlistRemoveResponseSerializer, Team.SharingAllowlistRemoveErrorSerializer>
```

**Parameters:**
- `domains` - List of domains represented by valid string representation (RFC-1034/5).
- `emails` - List of emails represented by valid string representation (RFC-5322/822).

**Returns:** `Team.SharingAllowlistRemoveResponse` on success, `Team.SharingAllowlistRemoveError` on failure.

---

## teamFolderActivate

Sets an archived team folder's status to active. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderActivate(
    teamFolderId: String
) -> RpcRequest<Team.TeamFolderMetadataSerializer, Team.TeamFolderActivateErrorSerializer>
```

**Parameters:**
- `teamFolderId` - The ID of the team folder.

**Returns:** `Team.TeamFolderMetadata` on success, `Team.TeamFolderActivateError` on failure.

---

## teamFolderArchive

Sets an active team folder's status to archived and removes all folder and file members. This endpoint cannot be used for teams that have a shared team space. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderArchive(
    teamFolderId: String,
    forceAsyncOff: Bool = false
) -> RpcRequest<Team.TeamFolderArchiveLaunchSerializer, Team.TeamFolderArchiveErrorSerializer>
```

**Parameters:**
- `teamFolderId` - The ID of the team folder.
- `forceAsyncOff` - Whether to force the archive to happen synchronously.

**Returns:** `Team.TeamFolderArchiveLaunch` on success, `Team.TeamFolderArchiveError` on failure.

---

## teamFolderArchiveCheck

Returns the status of an asynchronous job for archiving a team folder. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderArchiveCheck(
    asyncJobId: String
) -> RpcRequest<Team.TeamFolderArchiveJobStatusSerializer, Async.PollErrorSerializer>
```

**Parameters:**
- `asyncJobId` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

**Returns:** `Team.TeamFolderArchiveJobStatus` on success, `Async.PollError` on failure.

---

## teamFolderCreate

Creates a new, active, team folder with no members. This endpoint can only be used for teams that do not already have a shared team space. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderCreate(
    name: String,
    syncSetting: Files.SyncSettingArg? = nil
) -> RpcRequest<Team.TeamFolderMetadataSerializer, Team.TeamFolderCreateErrorSerializer>
```

**Parameters:**
- `name` - Name for the new team folder.
- `syncSetting` - The sync setting to apply to this team folder. Only permitted if the team has team selective sync enabled.

**Returns:** `Team.TeamFolderMetadata` on success, `Team.TeamFolderCreateError` on failure.

---

## teamFolderGetInfo

Retrieves metadata for team folders. Permission : Team member file access.

**Scope:** `team_data.content.read`

```swift
@discardableResult public func teamFolderGetInfo(
    teamFolderIds: [String]
) -> RpcRequest<ArraySerializer<Team.TeamFolderGetInfoItemSerializer>, VoidSerializer>
```

**Parameters:**
- `teamFolderIds` - The list of team folder IDs.

**Returns:** `Array<Team.TeamFolderGetInfoItem>` on success, `Void` on failure.

---

## teamFolderList

Lists all team folders. Permission : Team member file access.

**Scope:** `team_data.content.read`

```swift
@discardableResult public func teamFolderList(
    limit: UInt32 = 1_000
) -> RpcRequest<Team.TeamFolderListResultSerializer, Team.TeamFolderListErrorSerializer>
```

**Parameters:**
- `limit` - The maximum number of results to return per request.

**Returns:** `Team.TeamFolderListResult` on success, `Team.TeamFolderListError` on failure.

---

## teamFolderListContinue

Once a cursor has been retrieved from teamFolderList, use this to paginate through all team folders. Permission : Team member file access.

**Scope:** `team_data.content.read`

```swift
@discardableResult public func teamFolderListContinue(
    cursor: String
) -> RpcRequest<Team.TeamFolderListResultSerializer, Team.TeamFolderListContinueErrorSerializer>
```

**Parameters:**
- `cursor` - Indicates from what point to get the next set of team folders.

**Returns:** `Team.TeamFolderListResult` on success, `Team.TeamFolderListContinueError` on failure.

---

## teamFolderPermanentlyDelete

Permanently deletes an archived team folder. This endpoint cannot be used for teams that have a shared team space. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderPermanentlyDelete(
    teamFolderId: String
) -> RpcRequest<VoidSerializer, Team.TeamFolderPermanentlyDeleteErrorSerializer>
```

**Parameters:**
- `teamFolderId` - The ID of the team folder.

**Returns:** `Void` on success, `Team.TeamFolderPermanentlyDeleteError` on failure.

---

## teamFolderRename

Changes an active team folder's name. Permission : Team member file access.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderRename(
    teamFolderId: String,
    name: String
) -> RpcRequest<Team.TeamFolderMetadataSerializer, Team.TeamFolderRenameErrorSerializer>
```

**Parameters:**
- `teamFolderId` - The ID of the team folder.
- `name` - New team folder name.

**Returns:** `Team.TeamFolderMetadata` on success, `Team.TeamFolderRenameError` on failure.

---

## teamFolderUpdateSyncSettings

Updates the sync settings on a team folder or its contents. Use of this endpoint requires that the team has team selective sync enabled.

**Scope:** `team_data.content.write`

```swift
@discardableResult public func teamFolderUpdateSyncSettings(
    teamFolderId: String,
    syncSetting: Files.SyncSettingArg? = nil,
    contentSyncSettings: [Files.ContentSyncSettingArg]? = nil
) -> RpcRequest<Team.TeamFolderMetadataSerializer, Team.TeamFolderUpdateSyncSettingsErrorSerializer>
```

**Parameters:**
- `teamFolderId` - The ID of the team folder.
- `syncSetting` - Sync setting to apply to the team folder itself. Only meaningful if the team folder is not a shared team root.
- `contentSyncSettings` - Sync settings to apply to contents of this team folder.

**Returns:** `Team.TeamFolderMetadata` on success, `Team.TeamFolderUpdateSyncSettingsError` on failure.

---

## tokenGetAuthenticatedAdmin

Returns the member profile of the admin who generated the team access token used to make the call.

**Scope:** `team_info.read`

```swift
@discardableResult public func tokenGetAuthenticatedAdmin()
    -> RpcRequest<Team.TokenGetAuthenticatedAdminResultSerializer, Team.TokenGetAuthenticatedAdminErrorSerializer>
```

**Parameters:**

None.

**Returns:** `Team.TokenGetAuthenticatedAdminResult` on success, `Team.TokenGetAuthenticatedAdminError` on failure.

---
