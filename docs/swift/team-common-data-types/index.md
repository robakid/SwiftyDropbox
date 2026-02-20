# TeamCommon Data Types

Data types for the TeamCommon namespace.

## GroupManagementType

The group type determines how a group is managed.

**Cases:**
- `userManaged` - A group which is managed by selected users.
- `companyManaged` - A group which is managed by team admins only.
- `systemManaged` - A group which is managed automatically by Dropbox.
- `other` - An unspecified error.

---

## GroupSummary

Information about a group.

**Properties:**
- `groupName: String` - The name of the group.
- `groupId: String` - The unique ID of the group.
- `groupExternalId: String?` - External ID of group. This is an arbitrary ID that an admin can attach to a group.
- `memberCount: UInt32?` - The number of members in the group.
- `groupManagementType: TeamCommon.GroupManagementType` - Who is allowed to manage the group.

---

## GroupType

The group type determines how a group is created and managed.

**Cases:**
- `team` - A group to which team members are automatically added. Applicable to team folders only.
- `userManaged` - A group is created and managed by a user.
- `other` - An unspecified error.

---

## MemberSpaceLimitType

The type of the space limit imposed on a team member.

**Cases:**
- `off` - The team member does not have imposed space limit.
- `alertOnly` - The team member has soft imposed space limit - the limit is used for display and for notifications.
- `stopSync` - The team member has hard imposed space limit - Dropbox file sync will stop after the limit is reached.
- `other` - An unspecified error.

---

## TimeRange

Time range.

**Properties:**
- `startTime: Date?` - Optional starting time (inclusive).
- `endTime: Date?` - Optional ending time (exclusive).
