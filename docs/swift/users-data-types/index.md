# Users Data Types

Data types for the Users namespace.

## Account

The amount of detail revealed about an account depends on the user being queried and the user making the query.

**Properties:**
- `accountId: String` - The user's unique Dropbox ID.
- `name: Users.Name` - Details of a user's name.
- `email: String` - The user's email address. Do not rely on this without checking the emailVerified field. Even then, it's possible that the user has since lost access to their email.
- `emailVerified: Bool` - Whether the user has verified their email address.
- `profilePhotoUrl: String?` - URL for the photo representing the user, if one is set.
- `disabled: Bool` - Whether the user has been disabled.

---

## BasicAccount

Basic information about any account. Inherits from `Users.Account`.

**Properties:**
- `accountId: String` - *(inherited)* The user's unique Dropbox ID.
- `name: Users.Name` - *(inherited)* Details of a user's name.
- `email: String` - *(inherited)* The user's email address.
- `emailVerified: Bool` - *(inherited)* Whether the user has verified their email address.
- `profilePhotoUrl: String?` - *(inherited)* URL for the photo representing the user, if one is set.
- `disabled: Bool` - *(inherited)* Whether the user has been disabled.
- `isTeammate: Bool` - Whether this user is a teammate of the current user. If this account is the current user's account, then this will be true.
- `teamMemberId: String?` - The user's unique team member id. This field will only be present if the user is part of a team and isTeammate is true.

---

## FileLockingValue

The value for fileLocking in UserFeature.

**Cases:**
- `enabled` - When this value is True, the user can lock files in shared directories. When the value is False the user can unlock the files they have locked or request to unlock files locked by others. Associated value: `Bool`
- `other` - An unspecified error.

---

## FullAccount

Detailed information about the current user's account. Inherits from `Users.Account`.

**Properties:**
- `accountId: String` - *(inherited)* The user's unique Dropbox ID.
- `name: Users.Name` - *(inherited)* Details of a user's name.
- `email: String` - *(inherited)* The user's email address.
- `emailVerified: Bool` - *(inherited)* Whether the user has verified their email address.
- `profilePhotoUrl: String?` - *(inherited)* URL for the photo representing the user, if one is set.
- `disabled: Bool` - *(inherited)* Whether the user has been disabled.
- `country: String?` - The user's two-letter country code, if available. Country codes are based on ISO 3166-1.
- `locale: String` - The language that the user specified. Locale tags will be IETF language tags.
- `referralLink: String` - The user's referral link.
- `team: Users.FullTeam?` - If this account is a member of a team, information about that team.
- `teamMemberId: String?` - This account's unique team member id. This field will only be present if team is present.
- `isPaired: Bool` - Whether the user has a personal and work account. If the current account is personal, then team will always be null, but isPaired will indicate if a work account is linked.
- `accountType: UsersCommon.AccountType` - What type of account this user has.
- `rootInfo: Common.RootInfo` - The root info for this account.

---

## Team

Information about a team.

**Properties:**
- `id: String` - The team's unique ID.
- `name: String` - The name of the team.

---

## FullTeam

Detailed information about a team. Inherits from `Users.Team`.

**Properties:**
- `id: String` - *(inherited)* The team's unique ID.
- `name: String` - *(inherited)* The name of the team.
- `sharingPolicies: TeamPolicies.TeamSharingPolicies` - Team policies governing sharing.
- `officeAddinPolicy: TeamPolicies.OfficeAddInPolicy` - Team policy governing the use of the Office Add-In.

---

## GetAccountArg

The GetAccountArg struct.

**Properties:**
- `accountId: String` - A user's account identifier.

---

## GetAccountBatchArg

The GetAccountBatchArg struct.

**Properties:**
- `accountIds: [String]` - List of user account identifiers. Should not contain any duplicate account IDs.

---

## GetAccountBatchError

The GetAccountBatchError union.

**Cases:**
- `noAccount` - The value is an account ID specified in accountIds in GetAccountBatchArg that does not exist. Associated value: `String`
- `other` - An unspecified error.

---

## GetAccountError

The GetAccountError union.

**Cases:**
- `noAccount` - The specified accountId in GetAccountArg does not exist.
- `other` - An unspecified error.

---

## IndividualSpaceAllocation

The IndividualSpaceAllocation struct.

**Properties:**
- `allocated: UInt64` - The total space allocated to the user's account (bytes).

---

## Name

Representations for a person's name to assist with internationalization.

**Properties:**
- `givenName: String` - Also known as a first name.
- `surname: String` - Also known as a last name or family name.
- `familiarName: String` - Locale-dependent name. In the US, a person's familiar name is their givenName, but elsewhere, it could be any combination of a person's givenName and surname.
- `displayName: String` - A name that can be used directly to represent the name of a user's Dropbox account.
- `abbreviatedName: String` - An abbreviated form of the person's name. Their initials in most locales.

---

## PaperAsFilesValue

The value for paperAsFiles in UserFeature.

**Cases:**
- `enabled` - When this value is true, the user's Paper docs are accessible in Dropbox with the .paper extension and must be accessed via the /files endpoints. When this value is false, the user's Paper docs are stored separate from Dropbox files and folders and should be accessed via the /paper endpoints. Associated value: `Bool`
- `other` - An unspecified error.

---

## SpaceAllocation

Space is allocated differently based on the type of account.

**Cases:**
- `individual` - The user's space allocation applies only to their individual account. Associated value: `Users.IndividualSpaceAllocation`
- `team` - The user shares space with other members of their team. Associated value: `Users.TeamSpaceAllocation`
- `other` - An unspecified error.

---

## SpaceUsage

Information about a user's space usage and quota.

**Properties:**
- `used: UInt64` - The user's total space usage (bytes).
- `allocation: Users.SpaceAllocation` - The user's space allocation.

---

## TeamSpaceAllocation

The TeamSpaceAllocation struct.

**Properties:**
- `used: UInt64` - The total space currently used by the user's team (bytes).
- `allocated: UInt64` - The total space allocated to the user's team (bytes).
- `userWithinTeamSpaceAllocated: UInt64` - The total space allocated to the user within its team allocated space (0 means that no restriction is imposed on the user's quota within its team).
- `userWithinTeamSpaceLimitType: TeamCommon.MemberSpaceLimitType` - The type of the space limit imposed on the team member (off, alert_only, stop_sync).
- `userWithinTeamSpaceUsedCached: UInt64` - An accurate cached calculation of a team member's total space usage (bytes).

---

## UserFeature

A set of features that a Dropbox User account may have configured.

**Cases:**
- `paperAsFiles` - This feature contains information about how the user's Paper files are stored.
- `fileLocking` - This feature allows users to lock files in order to restrict other users from editing them.
- `other` - An unspecified error.

---

## UserFeatureValue

Values that correspond to entries in UserFeature.

**Cases:**
- `paperAsFiles` - Associated value: `Users.PaperAsFilesValue`
- `fileLocking` - Associated value: `Users.FileLockingValue`
- `other` - An unspecified error.

---

## UserFeaturesGetValuesBatchArg

The UserFeaturesGetValuesBatchArg struct.

**Properties:**
- `features: [Users.UserFeature]` - A list of features in UserFeature. If the list is empty, this route will return UserFeaturesGetValuesBatchError.

---

## UserFeaturesGetValuesBatchError

The UserFeaturesGetValuesBatchError union.

**Cases:**
- `emptyFeaturesList` - At least one UserFeature must be included in the UserFeaturesGetValuesBatchArg.features list.
- `other` - An unspecified error.

---

## UserFeaturesGetValuesBatchResult

The UserFeaturesGetValuesBatchResult struct.

**Properties:**
- `values: [Users.UserFeatureValue]` - The list of feature values.
