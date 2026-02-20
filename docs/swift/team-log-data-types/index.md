# TeamLog Data Types

Data types for the `team_log` namespace. This namespace contains an extensive set of types for team event logging and auditing.

The `TeamLog` namespace encompasses over 1,100 public data types (classes and enums) organized into categories covering every aspect of Dropbox team activity logging. These types are auto-generated from the Dropbox Stone API specification and are used to represent team audit log events, their details, the actors and contexts involved, and the various policy settings that can be changed.

---

## Table of Contents

- [Core Event & API Types (9)](#core-event-api-types)
- [Actor, Context & Origin Log Info (4)](#actor-context-origin-log-info)
- [Access & Session Log Info (11)](#access-session-log-info)
- [Account & Account Capture (16)](#account-account-capture)
- [Admin Alerting (14)](#admin-alerting)
- [Admin Console & Roles (6)](#admin-console-roles)
- [App Management (15)](#app-management)
- [Asset & Path Log Info (4)](#asset-path-log-info)
- [Backup & Computer Backup (8)](#backup-computer-backup)
- [Binder Operations (16)](#binder-operations)
- [Camera & Capture (6)](#camera-capture)
- [Classification & Content (11)](#classification-content)
- [Collections & Albums (2)](#collections-albums)
- [Common Supporting Types (6)](#common-supporting-types)
- [Data Governance & Retention (5)](#data-governance-retention)
- [Device & Session Management (38)](#device-session-management)
- [Domain & DNS (18)](#domain-dns)
- [Dropbox Passwords (7)](#dropbox-passwords)
- [Email Ingest (5)](#email-ingest)
- [EMM & Mobile Device Management (14)](#emm-mobile-device-management)
- [Enterprise & Federation (17)](#enterprise-federation)
- [Export & Reporting (4)](#export-reporting)
- [External Sharing & Users (20)](#external-sharing-users)
- [Feature Settings (20)](#feature-settings)
- [File & Folder Operations (112)](#file-folder-operations)
- [Group Management (30)](#group-management)
- [Integration & Third-Party (10)](#integration-third-party)
- [Legal Holds (22)](#legal-holds)
- [Login & Authentication (11)](#login-authentication)
- [Member Management (114)](#member-management)
- [Namespace (1)](#namespace)
- [Network & Geo (4)](#network-geo)
- [Paper & Notes (117)](#paper-notes)
- [Password & Security (29)](#password-security)
- [Policy Types (93)](#policy-types)
- [Ransomware & Threat (8)](#ransomware-threat)
- [Reseller & Support (6)](#reseller-support)
- [Shared Folder & Link Model Operations (32)](#shared-folder-link-model-operations)
- [Shared Links (40)](#shared-links)
- [Sharing & Permissions (84)](#sharing-permissions)
- [Showcase (49)](#showcase)
- [Smart Sync (6)](#smart-sync)
- [SSO & Certificate (23)](#sso-certificate)
- [Team Invite Links (4)](#team-invite-links)
- [Team Settings & Operations (55)](#team-settings-operations)
- [Trusted Teams (4)](#trusted-teams)
- [User & Member Log Info (9)](#user-member-log-info)
- [Web Sessions (2)](#web-sessions)
- [Other Types (44)](#other-types)

---

## Core Event & API Types

### EventCategory

`enum`

Category of events in event audit log.

**Cases:**

- `adminAlerting` - Events that involve team related alerts.
- `apps` - Events that apply to management of linked apps.
- `comments` - Events that have to do with comments on files and Paper documents.
- `dataGovernance` - Events that involve data governance actions
- `devices` - Events that apply to linked devices on mobile, desktop and Web platforms.
- `domains` - Events that involve domain management feature: domain verification, invite enforcement and account capture.
- `encryption` - Events that involve encryption.
- `fileOperations` - Events that have to do with filesystem operations on files and folders: copy, move, delete, etc.
- `fileRequests` - Events that apply to the file requests feature.
- `groups` - Events that involve group management.
- `logins` - Events that involve users signing in to or out of Dropbox.
- `members` - Events that involve team member management.
- `paper` - Events that apply to Dropbox Paper.
- `passwords` - Events that involve using, changing or resetting passwords.
- `reports` - Events that concern generation of admin reports, including team activity and device usage.
- `sharing` - Events that apply to all types of sharing and collaboration.
- `showcase` - Events that apply to Dropbox Showcase.
- `sso` - sign-on.
- `teamFolders` - Events that involve team folder management.
- `teamPolicies` - Events that involve a change in team-wide policies.
- `teamProfile` - Events that involve a change in the team profile.
- `tfa` - concerning two factor authentication.
- `trustedTeams` - Events that apply to cross-team trust establishment.
- `other`

### EventDetails

`enum`

Additional fields depending on the event type.

This enum has **505 cases** covering a wide range of event types. A representative sample:

- `adminAlertingAlertStateChangedDetails`
- `adminAlertingChangedAlertConfigDetails`
- `adminAlertingTriggeredAlertDetails`
- `ransomwareRestoreProcessCompletedDetails`
- `ransomwareRestoreProcessStartedDetails`
- `appBlockedByPermissionsDetails`
- `appLinkTeamDetails`
- `appLinkUserDetails`
- `appUnlinkTeamDetails`
- `appUnlinkUserDetails`
- `integrationConnectedDetails`
- `integrationDisconnectedDetails`
- `fileAddCommentDetails`
- `fileChangeCommentSubscriptionDetails`
- `fileDeleteCommentDetails`
- ... (485 more cases)
- `teamMergeRequestRevokedDetails`
- `teamMergeRequestSentShownToPrimaryTeamDetails`
- `teamMergeRequestSentShownToSecondaryTeamDetails`
- `missingDetails` - Hints that this event was returned with missing details due to an internal error.
- `other`

### EventType

`enum`

The type of the event with description.

This enum has **504 cases** covering a wide range of event types. A representative sample:

- `adminAlertingAlertStateChanged` - (admin_alerting) Changed an alert state
- `adminAlertingChangedAlertConfig` - (admin_alerting) Changed an alert setting
- `adminAlertingTriggeredAlert` - (admin_alerting) Triggered security alert
- `ransomwareRestoreProcessCompleted` - (admin_alerting) Completed ransomware restore process
- `ransomwareRestoreProcessStarted` - (admin_alerting) Started ransomware restore process
- `appBlockedByPermissions` - (apps) Failed to connect app for member
- `appLinkTeam` - (apps) Linked app for team
- `appLinkUser` - (apps) Linked app for member
- `appUnlinkTeam` - (apps) Unlinked app for team
- `appUnlinkUser` - (apps) Unlinked app for member
- `integrationConnected` - (apps) Connected integration for member
- `integrationDisconnected` - (apps) Disconnected integration for member
- `fileAddComment` - (comments) Added file comment
- `fileChangeCommentSubscription` - (comments) Subscribed to or unsubscribed from comment notifications for file
- `fileDeleteComment` - (comments) Deleted file comment
- ... (484 more cases)
- `teamMergeRequestReminderShownToSecondaryTeam` - reminder')
- `teamMergeRequestRevoked` - (trusted_teams) Canceled the team merge
- `teamMergeRequestSentShownToPrimaryTeam` - (trusted_teams) Requested to merge their Dropbox team into yours
- `teamMergeRequestSentShownToSecondaryTeam` - (trusted_teams) Requested to merge your team into another Dropbox team
- `other`

### EventTypeArg

`enum`

The type of the event.

This enum has **504 cases** covering a wide range of event types. A representative sample:

- `adminAlertingAlertStateChanged` - (admin_alerting) Changed an alert state
- `adminAlertingChangedAlertConfig` - (admin_alerting) Changed an alert setting
- `adminAlertingTriggeredAlert` - (admin_alerting) Triggered security alert
- `ransomwareRestoreProcessCompleted` - (admin_alerting) Completed ransomware restore process
- `ransomwareRestoreProcessStarted` - (admin_alerting) Started ransomware restore process
- `appBlockedByPermissions` - (apps) Failed to connect app for member
- `appLinkTeam` - (apps) Linked app for team
- `appLinkUser` - (apps) Linked app for member
- `appUnlinkTeam` - (apps) Unlinked app for team
- `appUnlinkUser` - (apps) Unlinked app for member
- `integrationConnected` - (apps) Connected integration for member
- `integrationDisconnected` - (apps) Disconnected integration for member
- `fileAddComment` - (comments) Added file comment
- `fileChangeCommentSubscription` - (comments) Subscribed to or unsubscribed from comment notifications for file
- `fileDeleteComment` - (comments) Deleted file comment
- ... (484 more cases)
- `teamMergeRequestReminderShownToSecondaryTeam` - reminder')
- `teamMergeRequestRevoked` - (trusted_teams) Canceled the team merge
- `teamMergeRequestSentShownToPrimaryTeam` - (trusted_teams) Requested to merge their Dropbox team into yours
- `teamMergeRequestSentShownToSecondaryTeam` - (trusted_teams) Requested to merge your team into another Dropbox team
- `other`

### GetTeamEventsArg

`class`

Type for get team events arg.

**Properties:**

- `limit`: `UInt32` - should fetch again using getEventsContinue.
- `accountId`: `String?` - Participants.
- `time`: `TeamCommon.TimeRange?` - Filter by time range.
- `category`: `TeamLog.EventCategory?` - event_type.
- `eventType`: `TeamLog.EventTypeArg?` - category.

### GetTeamEventsContinueArg

`class`

Type for get team events continue arg.

**Properties:**

- `cursor`: `String` - Indicates from what point to get the next set of events.

### GetTeamEventsContinueError

`enum`

Errors that can be raised when calling getEventsContinue.

**Cases:**

- `badCursor` - Bad cursor.
- `reset` - the cursor. This should be used as a resumption point when calling getEvents to obtain a new cursor.
- `other`

### GetTeamEventsError

`enum`

Errors that can be raised when calling getEvents.

**Cases:**

- `accountIdNotFound` - No user found matching the provided account_id.
- `invalidTimeRange` - Invalid time range.
- `invalidFilters` - Invalid filters. Do not specify both event_type and category parameters for the same call.
- `other`

### GetTeamEventsResult

`class`

Type for get team events result.

**Properties:**

- `events`: `[TeamLog.TeamEvent]` - List of events. Note that events are not guaranteed to be sorted by their timestamp value.
- `cursor`: `String` - handle reset exceptions for expired cursors.
- `hasMore`: `Bool` - getEventsContinue can retrieve them. Note that hasMore may be true, even if events is empty.

---

## Actor, Context & Origin Log Info

### ActionDetails

`enum`

Additional information indicating the action taken that caused status change.

**Cases:**

- `removeAction` - Define how the user was removed from the team.
- `teamInviteDetails` - Additional information relevant when someone is invited to the team.
- `teamJoinDetails` - Additional information relevant when a new member joins the team.
- `other`

### ActorLogInfo

`enum`

The entity who performed the action.

**Cases:**

- `admin` - The admin who did the action.
- `anonymous` - Anonymous actor.
- `app` - The application who did the action.
- `dropbox` - Action done by Dropbox.
- `reseller` - Action done by reseller.
- `user` - The user who did the action.
- `other`

### ContextLogInfo

`enum`

The primary entity on which the action was done.

**Cases:**

- `anonymous` - Anonymous context.
- `nonTeamMember` - Action was done on behalf of a non team member.
- `organizationTeam` - Action was done on behalf of a team that's part of an organization.
- `team` - Action was done on behalf of the team.
- `teamMember` - Action was done on behalf of a team member.
- `trustedNonTeamMember` - Action was done on behalf of a trusted non team member.
- `other`

### OriginLogInfo

`class`

The origin from which the actor performed the action.

**Properties:**

- `geoLocation`: `TeamLog.GeoLocationLogInfo?` - Geographic location details.
- `accessMethod`: `TeamLog.AccessMethodLogInfo` - The method that was used to perform the action.

---

## Access & Session Log Info

### AccessMethodLogInfo

`enum`

Indicates the method in which the action was performed.

**Cases:**

- `adminConsole` - Admin console session details.
- `api` - Api session details.
- `contentManager` - Content manager session details.
- `endUser` - End user session details.
- `enterpriseConsole` - Enterprise console session details.
- `signInAs` - Sign in as session details.
- `other`

### ApiSessionLogInfo

`class`

Api session.

**Properties:**

- `requestId`: `String` - Api request ID.

### DeviceSessionLogInfo

`class`

Device's session logged information.

**Properties:**

- `ipAddress`: `String?` - The IP address of the last activity from this session.
- `created`: `Date?` - The time this session was created.
- `updated`: `Date?` - The time of the last activity from this session.

### DesktopDeviceSessionLogInfo

`class`

Information about linked Dropbox desktop client sessions

**Properties:**

- `sessionInfo`: `TeamLog.DesktopSessionLogInfo?` - Desktop session unique id.
- `hostName`: `String` - Name of the hosting desktop.
- `clientType`: `Team.DesktopPlatform` - The Dropbox desktop client type.
- `clientVersion`: `String?` - The Dropbox client version.
- `platform`: `String` - Information on the hosting platform.
- `isDeleteOnUnlinkSupported`: `Bool` - Whether itu2019s possible to delete all of the account files upon unlinking.

### SessionLogInfo

`class`

Session's logged information.

**Properties:**

- `sessionId`: `String?` - Session ID.

### DesktopSessionLogInfo

`class`

Desktop session.

### LegacyDeviceSessionLogInfo

`class`

Information on sessions, in legacy format

**Properties:**

- `sessionInfo`: `TeamLog.SessionLogInfo?` - Session unique id.
- `displayName`: `String?` - The device name. Might be missing due to historical data gap.
- `isEmmManaged`: `Bool?` - Is device managed by emm. Might be missing due to historical data gap.
- `platform`: `String?` - Information on the hosting platform. Might be missing due to historical data gap.
- `macAddress`: `String?` - The mac address of the last activity from this session. Might be missing due to historical data gap.
- `osVersion`: `String?` - The hosting OS version. Might be missing due to historical data gap.
- `deviceType`: `String?` - Information on the hosting device type. Might be missing due to historical data gap.
- `clientVersion`: `String?` - The Dropbox client version. Might be missing due to historical data gap.
- `legacyUniqId`: `String?` - gap.

### MobileDeviceSessionLogInfo

`class`

Information about linked Dropbox mobile client sessions

**Properties:**

- `sessionInfo`: `TeamLog.MobileSessionLogInfo?` - Mobile session unique id.
- `deviceName`: `String` - The device name.
- `clientType`: `Team.MobileClientPlatform` - The mobile application type.
- `clientVersion`: `String?` - The Dropbox client version.
- `osVersion`: `String?` - The hosting OS version.
- `lastCarrier`: `String?` - last carrier used by the device.

### MobileSessionLogInfo

`class`

Mobile session.

### WebDeviceSessionLogInfo

`class`

Information on active web sessions

**Properties:**

- `sessionInfo`: `TeamLog.WebSessionLogInfo?` - Web session unique id.
- `userAgent`: `String` - Information on the hosting device.
- `os`: `String` - Information on the hosting operating system.
- `browser`: `String` - Information on the browser used for this web session.

### WebSessionLogInfo

`class`

Web session.

---

## Account & Account Capture

### AccountCaptureAvailability

`enum`

Type for account capture availability.

**Cases:**

- `available`
- `unavailable`
- `other`

### AccountCaptureChangeAvailabilityDetails

`class`

Granted/revoked option to enable account capture on team domains.

**Properties:**

- `newValue`: `TeamLog.AccountCaptureAvailability` - New account capture availabilty value.
- `previousValue`: `TeamLog.AccountCaptureAvailability?` - Previous account capture availabilty value. Might be missing due to historical data gap.

### AccountCaptureChangeAvailabilityType

`class`

Type for account capture change availability type.

**Properties:**

- `description_`: `String`

### AccountCaptureChangePolicyDetails

`class`

Changed account capture setting on team domain.

**Properties:**

- `newValue`: `TeamLog.AccountCapturePolicy` - New account capture policy.
- `previousValue`: `TeamLog.AccountCapturePolicy?` - Previous account capture policy. Might be missing due to historical data gap.

### AccountCaptureChangePolicyType

`class`

Type for account capture change policy type.

**Properties:**

- `description_`: `String`

### AccountCaptureMigrateAccountDetails

`class`

Account-captured user migrated account to team.

**Properties:**

- `domainName`: `String` - Domain name.

### AccountCaptureMigrateAccountType

`class`

Type for account capture migrate account type.

**Properties:**

- `description_`: `String`

### AccountCaptureNotificationEmailsSentDetails

`class`

Sent account capture email to all unmanaged members.

**Properties:**

- `domainName`: `String` - Domain name.
- `notificationType`: `TeamLog.AccountCaptureNotificationType?` - Account-capture email notification type.

### AccountCaptureNotificationEmailsSentType

`class`

Type for account capture notification emails sent type.

**Properties:**

- `description_`: `String`

### AccountCaptureNotificationType

`enum`

Type for account capture notification type.

**Cases:**

- `actionableNotification`
- `proactiveWarningNotification`
- `other`

### AccountCapturePolicy

`enum`

Type for account capture policy.

**Cases:**

- `allUsers`
- `disabled`
- `invitedUsers`
- `preventPersonalCreation`
- `other`

### AccountCaptureRelinquishAccountDetails

`class`

Account-captured user changed account email to personal email.

**Properties:**

- `domainName`: `String` - Domain name.

### AccountCaptureRelinquishAccountType

`class`

Type for account capture relinquish account type.

**Properties:**

- `description_`: `String`

### AccountLockOrUnlockedDetails

`class`

Unlocked/locked account after failed sign in attempts.

**Properties:**

- `previousValue`: `TeamLog.AccountState` - The previous account status.
- `newValue`: `TeamLog.AccountState` - The new account status.

### AccountLockOrUnlockedType

`class`

Type for account lock or unlocked type.

**Properties:**

- `description_`: `String`

### AccountState

`enum`

Type for account state.

**Cases:**

- `locked`
- `unlocked`
- `other`

---

## Admin Alerting

### AdminAlertCategoryEnum

`enum`

Alert category

**Cases:**

- `accountTakeover`
- `dataLossProtection`
- `informationGovernance`
- `malwareSharing`
- `massiveFileOperation`
- `na`
- `threatManagement`
- `other`

### AdminAlertGeneralStateEnum

`enum`

Alert state

**Cases:**

- `active`
- `dismissed`
- `inProgress`
- `na`
- `resolved`
- `other`

### AdminAlertSeverityEnum

`enum`

Alert severity

**Cases:**

- `high`
- `info`
- `low`
- `medium`
- `na`
- `other`

### AdminAlertingAlertConfiguration

`class`

Alert configurations

**Properties:**

- `alertState`: `TeamLog.AdminAlertingAlertStatePolicy?` - Alert state.
- `sensitivityLevel`: `TeamLog.AdminAlertingAlertSensitivity?` - Sensitivity level.
- `recipientsSettings`: `TeamLog.RecipientsConfiguration?` - Recipient settings.
- `text`: `String?` - Text.
- `excludedFileExtensions`: `String?` - Excluded file extensions.

### AdminAlertingAlertSensitivity

`enum`

Alert sensitivity

**Cases:**

- `high`
- `highest`
- `invalid`
- `low`
- `lowest`
- `medium`
- `other`

### AdminAlertingAlertStateChangedDetails

`class`

Changed an alert state.

**Properties:**

- `alertName`: `String` - Alert name.
- `alertSeverity`: `TeamLog.AdminAlertSeverityEnum` - Alert severity.
- `alertCategory`: `TeamLog.AdminAlertCategoryEnum` - Alert category.
- `alertInstanceId`: `String` - Alert ID.
- `previousValue`: `TeamLog.AdminAlertGeneralStateEnum` - Alert state before the change.
- `newValue`: `TeamLog.AdminAlertGeneralStateEnum` - Alert state after the change.

### AdminAlertingAlertStateChangedType

`class`

Type for admin alerting alert state changed type.

**Properties:**

- `description_`: `String`

### AdminAlertingAlertStatePolicy

`enum`

Policy for controlling whether an alert can be triggered or not

**Cases:**

- `off`
- `on`
- `other`

### AdminAlertingChangedAlertConfigDetails

`class`

Changed an alert setting.

**Properties:**

- `alertName`: `String` - Alert Name.
- `previousAlertConfig`: `TeamLog.AdminAlertingAlertConfiguration` - Previous alert configuration.
- `newAlertConfig`: `TeamLog.AdminAlertingAlertConfiguration` - New alert configuration.

### AdminAlertingChangedAlertConfigType

`class`

Type for admin alerting changed alert config type.

**Properties:**

- `description_`: `String`

### AdminAlertingTriggeredAlertDetails

`class`

Triggered security alert.

**Properties:**

- `alertName`: `String` - Alert name.
- `alertSeverity`: `TeamLog.AdminAlertSeverityEnum` - Alert severity.
- `alertCategory`: `TeamLog.AdminAlertCategoryEnum` - Alert category.
- `alertInstanceId`: `String` - Alert ID.

### AdminAlertingTriggeredAlertType

`class`

Type for admin alerting triggered alert type.

**Properties:**

- `description_`: `String`

### AlertRecipientsSettingType

`enum`

Alert recipients setting type

**Cases:**

- `customList`
- `invalid`
- `none`
- `teamAdmins`
- `other`

### RecipientsConfiguration

`class`

Recipients Configuration

**Properties:**

- `recipientSettingType`: `TeamLog.AlertRecipientsSettingType?` - Recipients setting type.
- `emails`: `[String]?` - A list of user emails to notify.
- `groups`: `[String]?` - A list of groups to notify.

---

## Admin Console & Roles

### AdminConsoleAppPermission

`enum`

Type for admin console app permission.

**Cases:**

- `defaultForListedApps`
- `defaultForUnlistedApps`
- `other`

### AdminConsoleAppPolicy

`enum`

Type for admin console app policy.

**Cases:**

- `allow`
- `block`
- `default_`
- `other`

### AdminEmailRemindersChangedDetails

`class`

Changed admin reminder settings for requests to join the team.

**Properties:**

- `newValue`: `TeamLog.AdminEmailRemindersPolicy` - To.
- `previousValue`: `TeamLog.AdminEmailRemindersPolicy` - From.

### AdminEmailRemindersChangedType

`class`

Type for admin email reminders changed type.

**Properties:**

- `description_`: `String`

### AdminEmailRemindersPolicy

`enum`

Policy for deciding whether team admins receive reminder emails for requests to join the team

**Cases:**

- `default_`
- `disabled`
- `enabled`
- `other`

### AdminRole

`enum`

Type for admin role.

**Cases:**

- `billingAdmin`
- `complianceAdmin`
- `contentAdmin`
- `limitedAdmin`
- `memberOnly`
- `reportingAdmin`
- `securityAdmin`
- `supportAdmin`
- `teamAdmin`
- `userManagementAdmin`
- `other`

---

## App Management

### AppBlockedByPermissionsDetails

`class`

Failed to connect app for member.

**Properties:**

- `appInfo`: `TeamLog.AppLogInfo` - Relevant application details.

### AppBlockedByPermissionsType

`class`

Type for app blocked by permissions type.

**Properties:**

- `description_`: `String`

### AppLinkTeamDetails

`class`

Linked app for team.

**Properties:**

- `appInfo`: `TeamLog.AppLogInfo` - Relevant application details.

### AppLinkTeamType

`class`

Type for app link team type.

**Properties:**

- `description_`: `String`

### AppLinkUserDetails

`class`

Linked app for member.

**Properties:**

- `appInfo`: `TeamLog.AppLogInfo` - Relevant application details.

### AppLinkUserType

`class`

Type for app link user type.

**Properties:**

- `description_`: `String`

### AppLogInfo

`class`

App's logged information.

**Properties:**

- `appId`: `String?` - App unique ID.
- `displayName`: `String?` - App display name.

### AppPermissionsChangedDetails

`class`

Changed app permissions.

**Properties:**

- `appName`: `String?` - Name of the app.
- `permission`: `TeamLog.AdminConsoleAppPermission?` - Permission that was changed.
- `previousValue`: `TeamLog.AdminConsoleAppPolicy` - Previous policy.
- `newValue`: `TeamLog.AdminConsoleAppPolicy` - New policy.

### AppPermissionsChangedType

`class`

Type for app permissions changed type.

**Properties:**

- `description_`: `String`

### AppUnlinkTeamDetails

`class`

Unlinked app for team.

**Properties:**

- `appInfo`: `TeamLog.AppLogInfo` - Relevant application details.

### AppUnlinkTeamType

`class`

Type for app unlink team type.

**Properties:**

- `description_`: `String`

### AppUnlinkUserDetails

`class`

Unlinked app for member.

**Properties:**

- `appInfo`: `TeamLog.AppLogInfo` - Relevant application details.

### AppUnlinkUserType

`class`

Type for app unlink user type.

**Properties:**

- `description_`: `String`

### ApplyNamingConventionDetails

`class`

Applied naming convention.

### ApplyNamingConventionType

`class`

Type for apply naming convention type.

**Properties:**

- `description_`: `String`

---

## Asset & Path Log Info

### AssetLogInfo

`enum`

Asset details.

**Cases:**

- `file` - File's details.
- `folder` - Folder's details.
- `paperDocument` - Paper document's details.
- `paperFolder` - Paper folder's details.
- `showcaseDocument` - Showcase document's details.
- `other`

### FileLogInfo

`class`

File's logged information.

### FolderLogInfo

`class`

Folder's logged information.

**Properties:**

- `fileCount`: `UInt64?` - Number of files within the folder.

### PathLogInfo

`class`

Path's details.

**Properties:**

- `contextual`: `String?` - Fully qualified path relative to event's context.
- `namespaceRelative`: `TeamLog.NamespaceRelativePathLogInfo` - Path relative to the namespace containing the content.

---

## Backup & Computer Backup

### BackupAdminInvitationSentDetails

`class`

Invited members to activate Backup.

### BackupAdminInvitationSentType

`class`

Type for backup admin invitation sent type.

**Properties:**

- `description_`: `String`

### BackupInvitationOpenedDetails

`class`

Opened Backup invite.

### BackupInvitationOpenedType

`class`

Type for backup invitation opened type.

**Properties:**

- `description_`: `String`

### BackupStatus

`enum`

Backup status

**Cases:**

- `disabled`
- `enabled`
- `other`

### ComputerBackupPolicy

`enum`

Policy for controlling team access to computer backup feature

**Cases:**

- `default_`
- `disabled`
- `enabled`
- `other`

### ComputerBackupPolicyChangedDetails

`class`

Changed computer backup policy for team.

**Properties:**

- `newValue`: `TeamLog.ComputerBackupPolicy` - New computer backup policy.
- `previousValue`: `TeamLog.ComputerBackupPolicy` - Previous computer backup policy.

### ComputerBackupPolicyChangedType

`class`

Type for computer backup policy changed type.

**Properties:**

- `description_`: `String`

---

## Binder Operations

### BinderAddPageDetails

`class`

Added Binder page.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderAddPageType

`class`

Type for binder add page type.

**Properties:**

- `description_`: `String`

### BinderAddSectionDetails

`class`

Added Binder section.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderAddSectionType

`class`

Type for binder add section type.

**Properties:**

- `description_`: `String`

### BinderRemovePageDetails

`class`

Removed Binder page.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderRemovePageType

`class`

Type for binder remove page type.

**Properties:**

- `description_`: `String`

### BinderRemoveSectionDetails

`class`

Removed Binder section.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderRemoveSectionType

`class`

Type for binder remove section type.

**Properties:**

- `description_`: `String`

### BinderRenamePageDetails

`class`

Renamed Binder page.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.
- `previousBinderItemName`: `String?` - Previous name of the Binder page/section.

### BinderRenamePageType

`class`

Type for binder rename page type.

**Properties:**

- `description_`: `String`

### BinderRenameSectionDetails

`class`

Renamed Binder section.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.
- `previousBinderItemName`: `String?` - Previous name of the Binder page/section.

### BinderRenameSectionType

`class`

Type for binder rename section type.

**Properties:**

- `description_`: `String`

### BinderReorderPageDetails

`class`

Reordered Binder page.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderReorderPageType

`class`

Type for binder reorder page type.

**Properties:**

- `description_`: `String`

### BinderReorderSectionDetails

`class`

Reordered Binder section.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `docTitle`: `String` - Title of the Binder doc.
- `binderItemName`: `String` - Name of the Binder page/section.

### BinderReorderSectionType

`class`

Type for binder reorder section type.

**Properties:**

- `description_`: `String`

---

## Camera & Capture

### CameraUploadsPolicy

`enum`

Policy for controlling if team members can activate camera uploads

**Cases:**

- `disabled`
- `enabled`
- `other`

### CameraUploadsPolicyChangedDetails

`class`

Changed camera uploads setting for team.

**Properties:**

- `newValue`: `TeamLog.CameraUploadsPolicy` - New camera uploads setting.
- `previousValue`: `TeamLog.CameraUploadsPolicy` - Previous camera uploads setting.

### CameraUploadsPolicyChangedType

`class`

Type for camera uploads policy changed type.

**Properties:**

- `description_`: `String`

### CaptureTranscriptPolicy

`enum`

Policy for deciding whether team users can transcription in Capture

**Cases:**

- `default_`
- `disabled`
- `enabled`
- `other`

### CaptureTranscriptPolicyChangedDetails

`class`

Changed Capture transcription policy for team.

**Properties:**

- `newValue`: `TeamLog.CaptureTranscriptPolicy` - To.
- `previousValue`: `TeamLog.CaptureTranscriptPolicy` - From.

### CaptureTranscriptPolicyChangedType

`class`

Type for capture transcript policy changed type.

**Properties:**

- `description_`: `String`

---

## Classification & Content

### ClassificationChangePolicyDetails

`class`

Changed classification policy for team.

**Properties:**

- `previousValue`: `TeamLog.ClassificationPolicyEnumWrapper` - Previous classification policy.
- `newValue`: `TeamLog.ClassificationPolicyEnumWrapper` - New classification policy.
- `classificationType`: `TeamLog.ClassificationType` - Policy type.

### ClassificationChangePolicyType

`class`

Type for classification change policy type.

**Properties:**

- `description_`: `String`

### ClassificationCreateReportDetails

`class`

Created Classification report.

### ClassificationCreateReportFailDetails

`class`

Couldn't create Classification report.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### ClassificationCreateReportFailType

`class`

Type for classification create report fail type.

**Properties:**

- `description_`: `String`

### ClassificationCreateReportType

`class`

Type for classification create report type.

**Properties:**

- `description_`: `String`

### ClassificationPolicyEnumWrapper

`enum`

Policy for controlling team access to the classification feature

**Cases:**

- `disabled`
- `enabled`
- `memberAndTeamFolders`
- `teamFolders`
- `other`

### ClassificationType

`enum`

The type of classification (currently only personal information)

**Cases:**

- `personalInformation`
- `pii`
- `other`

### ContentAdministrationPolicyChangedDetails

`class`

Changed content management setting.

**Properties:**

- `newValue`: `String` - New content administration policy.
- `previousValue`: `String` - Previous content administration policy.

### ContentAdministrationPolicyChangedType

`class`

Type for content administration policy changed type.

**Properties:**

- `description_`: `String`

### ContentPermanentDeletePolicy

`enum`

Policy for pemanent content deletion

**Cases:**

- `disabled`
- `enabled`
- `other`

---

## Collections & Albums

### CollectionShareDetails

`class`

Shared album.

**Properties:**

- `albumName`: `String` - Album name.

### CollectionShareType

`class`

Type for collection share type.

**Properties:**

- `description_`: `String`

---

## Common Supporting Types

### DurationLogInfo

`class`

Represents a time duration: unit and amount

**Properties:**

- `unit`: `TeamLog.TimeUnit` - Time unit.
- `amount`: `UInt64` - Amount of time.

### FailureDetailsLogInfo

`class`

Provides details about a failure

**Properties:**

- `userFriendlyMessage`: `String?` - A user friendly explanation of the error.
- `technicalErrorMessage`: `String?` - A technical explanation of the error. This is relevant for some errors.

### PlacementRestriction

`enum`

Type for placement restriction.

**Cases:**

- `australiaOnly`
- `europeOnly`
- `japanOnly`
- `none`
- `ukOnly`
- `usS3Only`
- `other`

### SpaceCapsType

`enum`

Space limit alert policy

**Cases:**

- `hard`
- `off`
- `soft`
- `other`

### SpaceLimitsStatus

`enum`

Type for space limits status.

**Cases:**

- `nearQuota`
- `overQuota`
- `withinQuota`
- `other`

### TimeUnit

`enum`

Type for time unit.

**Cases:**

- `days`
- `hours`
- `milliseconds`
- `minutes`
- `months`
- `seconds`
- `weeks`
- `years`
- `other`

---

## Data Governance & Retention

### DataResidencyMigrationRequestSuccessfulDetails

`class`

Requested data residency migration for team data.

### DataResidencyMigrationRequestSuccessfulType

`class`

Type for data residency migration request successful type.

**Properties:**

- `description_`: `String`

### DataResidencyMigrationRequestUnsuccessfulDetails

`class`

Request for data residency migration for team data has failed.

### DataResidencyMigrationRequestUnsuccessfulType

`class`

Type for data residency migration request unsuccessful type.

**Properties:**

- `description_`: `String`

### DispositionActionType

`enum`

Type for disposition action type.

**Cases:**

- `automaticDelete`
- `automaticPermanentlyDelete`
- `other`

---

## Device & Session Management

### DeviceApprovalsAddExceptionDetails

`class`

Added members to device approvals exception list.

### DeviceApprovalsAddExceptionType

`class`

Type for device approvals add exception type.

**Properties:**

- `description_`: `String`

### DeviceApprovalsChangeDesktopPolicyDetails

`class`

Set/removed limit on number of computers member can link to team Dropbox account.

**Properties:**

- `newValue`: `TeamLog.DeviceApprovalsPolicy?` - New desktop device approvals policy. Might be missing due to historical data gap.
- `previousValue`: `TeamLog.DeviceApprovalsPolicy?` - Previous desktop device approvals policy. Might be missing due to historical data gap.

### DeviceApprovalsChangeDesktopPolicyType

`class`

Type for device approvals change desktop policy type.

**Properties:**

- `description_`: `String`

### DeviceApprovalsChangeMobilePolicyDetails

`class`

Set/removed limit on number of mobile devices member can link to team Dropbox account.

**Properties:**

- `newValue`: `TeamLog.DeviceApprovalsPolicy?` - New mobile device approvals policy. Might be missing due to historical data gap.
- `previousValue`: `TeamLog.DeviceApprovalsPolicy?` - Previous mobile device approvals policy. Might be missing due to historical data gap.

### DeviceApprovalsChangeMobilePolicyType

`class`

Type for device approvals change mobile policy type.

**Properties:**

- `description_`: `String`

### DeviceApprovalsChangeOverageActionDetails

`class`

Changed device approvals setting when member is over limit.

**Properties:**

- `newValue`: `TeamPolicies.RolloutMethod?` - New over the limits policy. Might be missing due to historical data gap.
- `previousValue`: `TeamPolicies.RolloutMethod?` - Previous over the limit policy. Might be missing due to historical data gap.

### DeviceApprovalsChangeOverageActionType

`class`

Type for device approvals change overage action type.

**Properties:**

- `description_`: `String`

### DeviceApprovalsChangeUnlinkActionDetails

`class`

Changed device approvals setting when member unlinks approved device.

**Properties:**

- `newValue`: `TeamLog.DeviceUnlinkPolicy?` - New device unlink policy. Might be missing due to historical data gap.
- `previousValue`: `TeamLog.DeviceUnlinkPolicy?` - Previous device unlink policy. Might be missing due to historical data gap.

### DeviceApprovalsChangeUnlinkActionType

`class`

Type for device approvals change unlink action type.

**Properties:**

- `description_`: `String`

### DeviceApprovalsPolicy

`enum`

Type for device approvals policy.

**Cases:**

- `limited`
- `unlimited`
- `other`

### DeviceApprovalsRemoveExceptionDetails

`class`

Removed members from device approvals exception list.

### DeviceApprovalsRemoveExceptionType

`class`

Type for device approvals remove exception type.

**Properties:**

- `description_`: `String`

### DeviceChangeIpDesktopDetails

`class`

Changed IP address associated with active desktop session.

**Properties:**

- `deviceSessionInfo`: `TeamLog.DeviceSessionLogInfo` - Device's session logged information.

### DeviceChangeIpDesktopType

`class`

Type for device change ip desktop type.

**Properties:**

- `description_`: `String`

### DeviceChangeIpMobileDetails

`class`

Changed IP address associated with active mobile session.

**Properties:**

- `deviceSessionInfo`: `TeamLog.DeviceSessionLogInfo?` - Device's session logged information.

### DeviceChangeIpMobileType

`class`

Type for device change ip mobile type.

**Properties:**

- `description_`: `String`

### DeviceChangeIpWebDetails

`class`

Changed IP address associated with active web session.

**Properties:**

- `userAgent`: `String` - Web browser name.

### DeviceChangeIpWebType

`class`

Type for device change ip web type.

**Properties:**

- `description_`: `String`

### DeviceDeleteOnUnlinkFailDetails

`class`

Failed to delete all files from unlinked device.

**Properties:**

- `sessionInfo`: `TeamLog.SessionLogInfo?` - Session unique id.
- `displayName`: `String?` - The device name. Might be missing due to historical data gap.
- `numFailures`: `Int64` - The number of times that remote file deletion failed.

### DeviceDeleteOnUnlinkFailType

`class`

Type for device delete on unlink fail type.

**Properties:**

- `description_`: `String`

### DeviceDeleteOnUnlinkSuccessDetails

`class`

Deleted all files from unlinked device.

**Properties:**

- `sessionInfo`: `TeamLog.SessionLogInfo?` - Session unique id.
- `displayName`: `String?` - The device name. Might be missing due to historical data gap.

### DeviceDeleteOnUnlinkSuccessType

`class`

Type for device delete on unlink success type.

**Properties:**

- `description_`: `String`

### DeviceLinkFailDetails

`class`

Failed to link device.

**Properties:**

- `ipAddress`: `String?` - IP address. Might be missing due to historical data gap.
- `deviceType`: `TeamLog.DeviceType` - A description of the device used while user approval blocked.

### DeviceLinkFailType

`class`

Type for device link fail type.

**Properties:**

- `description_`: `String`

### DeviceLinkSuccessDetails

`class`

Linked device.

**Properties:**

- `deviceSessionInfo`: `TeamLog.DeviceSessionLogInfo?` - Device's session logged information.

### DeviceLinkSuccessType

`class`

Type for device link success type.

**Properties:**

- `description_`: `String`

### DeviceManagementDisabledDetails

`class`

Disabled device management.

### DeviceManagementDisabledType

`class`

Type for device management disabled type.

**Properties:**

- `description_`: `String`

### DeviceManagementEnabledDetails

`class`

Enabled device management.

### DeviceManagementEnabledType

`class`

Type for device management enabled type.

**Properties:**

- `description_`: `String`

### DeviceSyncBackupStatusChangedDetails

`class`

Enabled/disabled backup for computer.

**Properties:**

- `desktopDeviceSessionInfo`: `TeamLog.DesktopDeviceSessionLogInfo` - Device's session logged information.
- `previousValue`: `TeamLog.BackupStatus` - Previous status of computer backup on the device.
- `newValue`: `TeamLog.BackupStatus` - Next status of computer backup on the device.

### DeviceSyncBackupStatusChangedType

`class`

Type for device sync backup status changed type.

**Properties:**

- `description_`: `String`

### DeviceType

`enum`

Type for device type.

**Cases:**

- `desktop`
- `mobile`
- `other`

### DeviceUnlinkDetails

`class`

Disconnected device.

**Properties:**

- `sessionInfo`: `TeamLog.SessionLogInfo?` - Session unique id.
- `displayName`: `String?` - The device name. Might be missing due to historical data gap.
- `deleteData`: `Bool` - True if the user requested to delete data after device unlink, false otherwise.

### DeviceUnlinkPolicy

`enum`

Type for device unlink policy.

**Cases:**

- `keep`
- `remove`
- `other`

### DeviceUnlinkType

`class`

Type for device unlink type.

**Properties:**

- `description_`: `String`

### LinkedDeviceLogInfo

`enum`

The device sessions that user is linked to.

**Cases:**

- `desktopDeviceSession` - desktop device session's details.
- `legacyDeviceSession` - legacy device session's details.
- `mobileDeviceSession` - mobile device session's details.
- `webDeviceSession` - web device session's details.
- `other`

---

## Domain & DNS

### DomainInvitesApproveRequestToJoinTeamDetails

`class`

Approved user's request to join team.

### DomainInvitesApproveRequestToJoinTeamType

`class`

Type for domain invites approve request to join team type.

**Properties:**

- `description_`: `String`

### DomainInvitesDeclineRequestToJoinTeamDetails

`class`

Declined user's request to join team.

### DomainInvitesDeclineRequestToJoinTeamType

`class`

Type for domain invites decline request to join team type.

**Properties:**

- `description_`: `String`

### DomainInvitesEmailExistingUsersDetails

`class`

Sent domain invites to existing domain accounts.

**Properties:**

- `domainName`: `String` - Domain names.
- `numRecipients`: `UInt64` - Number of recipients.

### DomainInvitesEmailExistingUsersType

`class`

Type for domain invites email existing users type.

**Properties:**

- `description_`: `String`

### DomainInvitesRequestToJoinTeamDetails

`class`

Requested to join team.

### DomainInvitesRequestToJoinTeamType

`class`

Type for domain invites request to join team type.

**Properties:**

- `description_`: `String`

### DomainInvitesSetInviteNewUserPrefToNoDetails

`class`

Disabled "Automatically invite new users".

### DomainInvitesSetInviteNewUserPrefToNoType

`class`

Type for domain invites set invite new user pref to no type.

**Properties:**

- `description_`: `String`

### DomainInvitesSetInviteNewUserPrefToYesDetails

`class`

Enabled "Automatically invite new users".

### DomainInvitesSetInviteNewUserPrefToYesType

`class`

Type for domain invites set invite new user pref to yes type.

**Properties:**

- `description_`: `String`

### DomainVerificationAddDomainFailDetails

`class`

Failed to verify team domain.

**Properties:**

- `domainName`: `String` - Domain name.
- `verificationMethod`: `String?` - Domain name verification method. Might be missing due to historical data gap.

### DomainVerificationAddDomainFailType

`class`

Type for domain verification add domain fail type.

**Properties:**

- `description_`: `String`

### DomainVerificationAddDomainSuccessDetails

`class`

Verified team domain.

**Properties:**

- `domainNames`: `[String]` - Domain names.
- `verificationMethod`: `String?` - Domain name verification method. Might be missing due to historical data gap.

### DomainVerificationAddDomainSuccessType

`class`

Type for domain verification add domain success type.

**Properties:**

- `description_`: `String`

### DomainVerificationRemoveDomainDetails

`class`

Removed domain from list of verified team domains.

**Properties:**

- `domainNames`: `[String]` - Domain names.

### DomainVerificationRemoveDomainType

`class`

Type for domain verification remove domain type.

**Properties:**

- `description_`: `String`

---

## Dropbox Passwords

### DropboxPasswordsExportedDetails

`class`

Exported passwords.

**Properties:**

- `platform`: `String` - The platform the device runs export.

### DropboxPasswordsExportedType

`class`

Type for dropbox passwords exported type.

**Properties:**

- `description_`: `String`

### DropboxPasswordsNewDeviceEnrolledDetails

`class`

Enrolled new Dropbox Passwords device.

**Properties:**

- `isFirstDevice`: `Bool` - Whether it's a first device enrolled.
- `platform`: `String` - The platform the device is enrolled.

### DropboxPasswordsNewDeviceEnrolledType

`class`

Type for dropbox passwords new device enrolled type.

**Properties:**

- `description_`: `String`

### DropboxPasswordsPolicy

`enum`

Policy for deciding whether team users can use Dropbox Passwords

**Cases:**

- `default_`
- `disabled`
- `enabled`
- `other`

### DropboxPasswordsPolicyChangedDetails

`class`

Changed Dropbox Passwords policy for team.

**Properties:**

- `newValue`: `TeamLog.DropboxPasswordsPolicy` - To.
- `previousValue`: `TeamLog.DropboxPasswordsPolicy` - From.

### DropboxPasswordsPolicyChangedType

`class`

Type for dropbox passwords policy changed type.

**Properties:**

- `description_`: `String`

---

## Email Ingest

### EmailIngestPolicy

`enum`

Policy for deciding whether a team can use Email to Dropbox feature

**Cases:**

- `disabled`
- `enabled`
- `other`

### EmailIngestPolicyChangedDetails

`class`

Changed email to Dropbox policy for team.

**Properties:**

- `newValue`: `TeamLog.EmailIngestPolicy` - To.
- `previousValue`: `TeamLog.EmailIngestPolicy` - From.

### EmailIngestPolicyChangedType

`class`

Type for email ingest policy changed type.

**Properties:**

- `description_`: `String`

### EmailIngestReceiveFileDetails

`class`

Received files via Email to Dropbox.

**Properties:**

- `inboxName`: `String` - Inbox name.
- `attachmentNames`: `[String]` - Submitted file names.
- `subject`: `String?` - Subject of the email.
- `fromName`: `String?` - The name as provided by the submitter.
- `fromEmail`: `String?` - The email as provided by the submitter.

### EmailIngestReceiveFileType

`class`

Type for email ingest receive file type.

**Properties:**

- `description_`: `String`

---

## EMM & Mobile Device Management

### EmmAddExceptionDetails

`class`

Added members to EMM exception list.

### EmmAddExceptionType

`class`

Type for emm add exception type.

**Properties:**

- `description_`: `String`

### EmmChangePolicyDetails

`class`

Enabled/disabled enterprise mobility management for members.

**Properties:**

- `newValue`: `TeamPolicies.EmmState` - New enterprise mobility management policy.
- `previousValue`: `TeamPolicies.EmmState?` - Previous enterprise mobility management policy. Might be missing due to historical data gap.

### EmmChangePolicyType

`class`

Type for emm change policy type.

**Properties:**

- `description_`: `String`

### EmmCreateExceptionsReportDetails

`class`

Created EMM-excluded users report.

### EmmCreateExceptionsReportType

`class`

Type for emm create exceptions report type.

**Properties:**

- `description_`: `String`

### EmmCreateUsageReportDetails

`class`

Created EMM mobile app usage report.

### EmmCreateUsageReportType

`class`

Type for emm create usage report type.

**Properties:**

- `description_`: `String`

### EmmErrorDetails

`class`

Failed to sign in via EMM.

**Properties:**

- `errorDetails`: `TeamLog.FailureDetailsLogInfo` - Error details.

### EmmErrorType

`class`

Type for emm error type.

**Properties:**

- `description_`: `String`

### EmmRefreshAuthTokenDetails

`class`

Refreshed auth token used for setting up EMM.

### EmmRefreshAuthTokenType

`class`

Type for emm refresh auth token type.

**Properties:**

- `description_`: `String`

### EmmRemoveExceptionDetails

`class`

Removed members from EMM exception list.

### EmmRemoveExceptionType

`class`

Type for emm remove exception type.

**Properties:**

- `description_`: `String`

---

## Enterprise & Federation

### ChangedEnterpriseAdminRoleDetails

`class`

Changed enterprise admin role.

**Properties:**

- `previousValue`: `TeamLog.FedAdminRole` - The member&#x2019s previous enterprise admin role.
- `newValue`: `TeamLog.FedAdminRole` - The member&#x2019s new enterprise admin role.
- `teamName`: `String` - The name of the member&#x2019s team.

### ChangedEnterpriseAdminRoleType

`class`

Type for changed enterprise admin role type.

**Properties:**

- `description_`: `String`

### ChangedEnterpriseConnectedTeamStatusDetails

`class`

Changed enterprise-connected team status.

**Properties:**

- `action`: `TeamLog.FedHandshakeAction` - The preformed change in the team&#x2019s connection status.
- `additionalInfo`: `TeamLog.FederationStatusChangeAdditionalInfo` - Additional information about the organization or team.
- `previousValue`: `TeamLog.TrustedTeamsRequestState` - Previous request state.
- `newValue`: `TeamLog.TrustedTeamsRequestState` - New request state.

### ChangedEnterpriseConnectedTeamStatusType

`class`

Type for changed enterprise connected team status type.

**Properties:**

- `description_`: `String`

### ConnectedTeamName

`class`

The name of the team

**Properties:**

- `team`: `String` - The name of the team.

### EndedEnterpriseAdminSessionDeprecatedDetails

`class`

Ended enterprise admin session.

**Properties:**

- `federationExtraDetails`: `TeamLog.FedExtraDetails` - More information about the organization or team.

### EndedEnterpriseAdminSessionDeprecatedType

`class`

Type for ended enterprise admin session deprecated type.

**Properties:**

- `description_`: `String`

### EndedEnterpriseAdminSessionDetails

`class`

Ended enterprise admin session.

### EndedEnterpriseAdminSessionType

`class`

Type for ended enterprise admin session type.

**Properties:**

- `description_`: `String`

### EnterpriseSettingsLockingDetails

`class`

Changed who can update a setting.

**Properties:**

- `teamName`: `String` - The secondary team name.
- `settingsPageName`: `String` - Settings page name.
- `previousSettingsPageLockingState`: `String` - Previous locked settings page state.
- `newSettingsPageLockingState`: `String` - New locked settings page state.

### EnterpriseSettingsLockingType

`class`

Type for enterprise settings locking type.

**Properties:**

- `description_`: `String`

### FedAdminRole

`enum`

Type for fed admin role.

**Cases:**

- `enterpriseAdmin`
- `notEnterpriseAdmin`
- `other`

### FedExtraDetails

`enum`

More details about the organization or team.

**Cases:**

- `organization` - More details about the organization.
- `team` - More details about the team.
- `other`

### FedHandshakeAction

`enum`

Type for fed handshake action.

**Cases:**

- `acceptedInvite`
- `canceledInvite`
- `inviteExpired`
- `invited`
- `rejectedInvite`
- `removedTeam`
- `other`

### FederationStatusChangeAdditionalInfo

`enum`

Additional information about the organization or connected team

**Cases:**

- `connectedTeamName` - The name of the team.
- `nonTrustedTeamDetails` - The email to which the request was sent.
- `organizationName` - The name of the organization.
- `other`

### StartedEnterpriseAdminSessionDetails

`class`

Started enterprise admin session.

**Properties:**

- `federationExtraDetails`: `TeamLog.FedExtraDetails` - More information about the organization or team.

### StartedEnterpriseAdminSessionType

`class`

Type for started enterprise admin session type.

**Properties:**

- `description_`: `String`

---

## Export & Reporting

### ExportMembersReportDetails

`class`

Created member data report.

### ExportMembersReportFailDetails

`class`

Failed to create members data report.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### ExportMembersReportFailType

`class`

Type for export members report fail type.

**Properties:**

- `description_`: `String`

### ExportMembersReportType

`class`

Type for export members report type.

**Properties:**

- `description_`: `String`

---

## External Sharing & Users

### ExternalDriveBackupEligibilityStatus

`enum`

External Drive Backup eligibility status

**Cases:**

- `exceedLicenseCap`
- `success`
- `other`

### ExternalDriveBackupEligibilityStatusCheckedDetails

`class`

Checked external drive backup eligibility status.

**Properties:**

- `desktopDeviceSessionInfo`: `TeamLog.DesktopDeviceSessionLogInfo` - Device's session logged information.
- `status`: `TeamLog.ExternalDriveBackupEligibilityStatus` - Current eligibility status of external drive backup.
- `numberOfExternalDriveBackup`: `UInt64` - Total number of valid external drive backup for all the team members.

### ExternalDriveBackupEligibilityStatusCheckedType

`class`

Type for external drive backup eligibility status checked type.

**Properties:**

- `description_`: `String`

### ExternalDriveBackupPolicy

`enum`

Policy for controlling team access to external drive backup feature

**Cases:**

- `default_`
- `disabled`
- `enabled`
- `other`

### ExternalDriveBackupPolicyChangedDetails

`class`

Changed external drive backup policy for team.

**Properties:**

- `newValue`: `TeamLog.ExternalDriveBackupPolicy` - New external drive backup policy.
- `previousValue`: `TeamLog.ExternalDriveBackupPolicy` - Previous external drive backup policy.

### ExternalDriveBackupPolicyChangedType

`class`

Type for external drive backup policy changed type.

**Properties:**

- `description_`: `String`

### ExternalDriveBackupStatus

`enum`

External Drive Backup status

**Cases:**

- `broken`
- `created`
- `createdOrBroken`
- `deleted`
- `empty`
- `unknown`
- `other`

### ExternalDriveBackupStatusChangedDetails

`class`

Modified external drive backup.

**Properties:**

- `desktopDeviceSessionInfo`: `TeamLog.DesktopDeviceSessionLogInfo` - Device's session logged information.
- `previousValue`: `TeamLog.ExternalDriveBackupStatus` - Previous status of this external drive backup.
- `newValue`: `TeamLog.ExternalDriveBackupStatus` - Next status of this external drive backup.

### ExternalDriveBackupStatusChangedType

`class`

Type for external drive backup status changed type.

**Properties:**

- `description_`: `String`

### ExternalSharingCreateReportDetails

`class`

Created External sharing report.

### ExternalSharingCreateReportType

`class`

Type for external sharing create report type.

**Properties:**

- `description_`: `String`

### ExternalSharingReportFailedDetails

`class`

Couldn't create External sharing report.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### ExternalSharingReportFailedType

`class`

Type for external sharing report failed type.

**Properties:**

- `description_`: `String`

### ExternalUserLogInfo

`class`

A user without a Dropbox account.

**Properties:**

- `userIdentifier`: `String` - An external user identifier.
- `identifierType`: `TeamLog.IdentifierType` - Identifier type.

### GuestAdminChangeStatusDetails

`class`

Changed guest team admin status.

**Properties:**

- `isGuest`: `Bool` - True for guest, false for host.
- `guestTeamName`: `String?` - The name of the guest team.
- `hostTeamName`: `String?` - The name of the host team.
- `previousValue`: `TeamLog.TrustedTeamsRequestState` - Previous request state.
- `newValue`: `TeamLog.TrustedTeamsRequestState` - New request state.
- `actionDetails`: `TeamLog.TrustedTeamsRequestAction` - Action details.

### GuestAdminChangeStatusType

`class`

Type for guest admin change status type.

**Properties:**

- `description_`: `String`

### GuestAdminSignedInViaTrustedTeamsDetails

`class`

Started trusted team admin session.

**Properties:**

- `teamName`: `String?` - Host team name.
- `trustedTeamName`: `String?` - Trusted team name.

### GuestAdminSignedInViaTrustedTeamsType

`class`

Type for guest admin signed in via trusted teams type.

**Properties:**

- `description_`: `String`

### GuestAdminSignedOutViaTrustedTeamsDetails

`class`

Ended trusted team admin session.

**Properties:**

- `teamName`: `String?` - Host team name.
- `trustedTeamName`: `String?` - Trusted team name.

### GuestAdminSignedOutViaTrustedTeamsType

`class`

Type for guest admin signed out via trusted teams type.

**Properties:**

- `description_`: `String`

---

## Feature Settings

### AllowDownloadDisabledDetails

`class`

Disabled downloads.

### AllowDownloadDisabledType

`class`

Type for allow download disabled type.

**Properties:**

- `description_`: `String`

### AllowDownloadEnabledDetails

`class`

Enabled downloads.

### AllowDownloadEnabledType

`class`

Type for allow download enabled type.

**Properties:**

- `description_`: `String`

### DirectoryRestrictionsAddMembersDetails

`class`

Added members to directory restrictions list.

### DirectoryRestrictionsAddMembersType

`class`

Type for directory restrictions add members type.

**Properties:**

- `description_`: `String`

### DirectoryRestrictionsRemoveMembersDetails

`class`

Removed members from directory restrictions list.

### DirectoryRestrictionsRemoveMembersType

`class`

Type for directory restrictions remove members type.

**Properties:**

- `description_`: `String`

### DisabledDomainInvitesDetails

`class`

Disabled domain invites.

### DisabledDomainInvitesType

`class`

Type for disabled domain invites type.

**Properties:**

- `description_`: `String`

### EnabledDomainInvitesDetails

`class`

Enabled domain invites.

### EnabledDomainInvitesType

`class`

Type for enabled domain invites type.

**Properties:**

- `description_`: `String`

### NoPasswordLinkGenCreateReportDetails

`class`

Report created: Links created without passwords.

**Properties:**

- `startDate`: `Date` - Report start date.
- `endDate`: `Date` - Report end date.

### NoPasswordLinkGenCreateReportType

`class`

Type for no password link gen create report type.

**Properties:**

- `description_`: `String`

### NoPasswordLinkGenReportFailedDetails

`class`

Couldn't create report: Links created without passwords.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### NoPasswordLinkGenReportFailedType

`class`

Type for no password link gen report failed type.

**Properties:**

- `description_`: `String`

### NoPasswordLinkViewCreateReportDetails

`class`

Report created: Views of links without passwords.

**Properties:**

- `startDate`: `Date` - Report start date.
- `endDate`: `Date` - Report end date.

### NoPasswordLinkViewCreateReportType

`class`

Type for no password link view create report type.

**Properties:**

- `description_`: `String`

### NoPasswordLinkViewReportFailedDetails

`class`

Couldn't create report: Views of links without passwords.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### NoPasswordLinkViewReportFailedType

`class`

Type for no password link view report failed type.

**Properties:**

- `description_`: `String`

---

## File & Folder Operations

### CreateFolderDetails

`class`

Created folders.

### CreateFolderType

`class`

Type for create folder type.

**Properties:**

- `description_`: `String`

### FileAddCommentDetails

`class`

Added file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileAddCommentType

`class`

Type for file add comment type.

**Properties:**

- `description_`: `String`

### FileAddDetails

`class`

Added files and/or folders.

### FileAddFromAutomationDetails

`class`

Added files and/or folders from automation.

### FileAddFromAutomationType

`class`

Type for file add from automation type.

**Properties:**

- `description_`: `String`

### FileAddType

`class`

Type for file add type.

**Properties:**

- `description_`: `String`

### FileChangeCommentSubscriptionDetails

`class`

Subscribed to or unsubscribed from comment notifications for file.

**Properties:**

- `newValue`: `TeamLog.FileCommentNotificationPolicy` - New file comment subscription.
- `previousValue`: `TeamLog.FileCommentNotificationPolicy?` - Previous file comment subscription. Might be missing due to historical data gap.

### FileChangeCommentSubscriptionType

`class`

Type for file change comment subscription type.

**Properties:**

- `description_`: `String`

### FileCommentNotificationPolicy

`enum`

Enable or disable file comments notifications

**Cases:**

- `disabled`
- `enabled`
- `other`

### FileCommentsChangePolicyDetails

`class`

Enabled/disabled commenting on team files.

**Properties:**

- `newValue`: `TeamLog.FileCommentsPolicy` - New commenting on team files policy.
- `previousValue`: `TeamLog.FileCommentsPolicy?` - Previous commenting on team files policy. Might be missing due to historical data gap.

### FileCommentsChangePolicyType

`class`

Type for file comments change policy type.

**Properties:**

- `description_`: `String`

### FileCommentsPolicy

`enum`

File comments policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### FileCopyDetails

`class`

Copied files and/or folders.

**Properties:**

- `relocateActionDetails`: `[TeamLog.RelocateAssetReferencesLogInfo]` - Relocate action details.

### FileCopyType

`class`

Type for file copy type.

**Properties:**

- `description_`: `String`

### FileDeleteCommentDetails

`class`

Deleted file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileDeleteCommentType

`class`

Type for file delete comment type.

**Properties:**

- `description_`: `String`

### FileDeleteDetails

`class`

Deleted files and/or folders.

### FileDeleteType

`class`

Type for file delete type.

**Properties:**

- `description_`: `String`

### FileDownloadDetails

`class`

Downloaded files and/or folders.

### FileDownloadType

`class`

Type for file download type.

**Properties:**

- `description_`: `String`

### FileEditCommentDetails

`class`

Edited file comment.

**Properties:**

- `commentText`: `String?` - Comment text.
- `previousCommentText`: `String` - Previous comment text.

### FileEditCommentType

`class`

Type for file edit comment type.

**Properties:**

- `description_`: `String`

### FileEditDetails

`class`

Edited files.

### FileEditType

`class`

Type for file edit type.

**Properties:**

- `description_`: `String`

### FileGetCopyReferenceDetails

`class`

Created copy reference to file/folder.

### FileGetCopyReferenceType

`class`

Type for file get copy reference type.

**Properties:**

- `description_`: `String`

### FileLikeCommentDetails

`class`

Liked file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileLikeCommentType

`class`

Type for file like comment type.

**Properties:**

- `description_`: `String`

### FileLockingLockStatusChangedDetails

`class`

Locked/unlocked editing for a file.

**Properties:**

- `previousValue`: `TeamLog.LockStatus` - Previous lock status of the file.
- `newValue`: `TeamLog.LockStatus` - New lock status of the file.

### FileLockingLockStatusChangedType

`class`

Type for file locking lock status changed type.

**Properties:**

- `description_`: `String`

### FileLockingPolicyChangedDetails

`class`

Changed file locking policy for team.

**Properties:**

- `newValue`: `TeamPolicies.FileLockingPolicyState` - New file locking policy.
- `previousValue`: `TeamPolicies.FileLockingPolicyState` - Previous file locking policy.

### FileLockingPolicyChangedType

`class`

Type for file locking policy changed type.

**Properties:**

- `description_`: `String`

### FileOrFolderLogInfo

`class`

Generic information relevant both for files and folders

**Properties:**

- `path`: `TeamLog.PathLogInfo` - Path relative to event context.
- `displayName`: `String?` - Display name.
- `fileId`: `String?` - Unique ID.
- `fileSize`: `UInt64?` - File or folder size in bytes.

### FileMoveDetails

`class`

Moved files and/or folders.

**Properties:**

- `relocateActionDetails`: `[TeamLog.RelocateAssetReferencesLogInfo]` - Relocate action details.

### FileMoveType

`class`

Type for file move type.

**Properties:**

- `description_`: `String`

### FilePermanentlyDeleteDetails

`class`

Permanently deleted files and/or folders.

### FilePermanentlyDeleteType

`class`

Type for file permanently delete type.

**Properties:**

- `description_`: `String`

### FilePreviewDetails

`class`

Previewed files and/or folders.

### FilePreviewType

`class`

Type for file preview type.

**Properties:**

- `description_`: `String`

### FileProviderMigrationPolicyChangedDetails

`class`

Changed File Provider Migration policy for team.

**Properties:**

- `newValue`: `TeamPolicies.FileProviderMigrationPolicyState` - To.
- `previousValue`: `TeamPolicies.FileProviderMigrationPolicyState` - From.

### FileProviderMigrationPolicyChangedType

`class`

Type for file provider migration policy changed type.

**Properties:**

- `description_`: `String`

### FileRenameDetails

`class`

Renamed files and/or folders.

**Properties:**

- `relocateActionDetails`: `[TeamLog.RelocateAssetReferencesLogInfo]` - Relocate action details.

### FileRenameType

`class`

Type for file rename type.

**Properties:**

- `description_`: `String`

### FileRequestChangeDetails

`class`

Changed file request.

**Properties:**

- `fileRequestId`: `String?` - File request id. Might be missing due to historical data gap.
- `previousDetails`: `TeamLog.FileRequestDetails?` - Previous file request details. Might be missing due to historical data gap.
- `newDetails`: `TeamLog.FileRequestDetails` - New file request details.

### FileRequestChangeType

`class`

Type for file request change type.

**Properties:**

- `description_`: `String`

### FileRequestCloseDetails

`class`

Closed file request.

**Properties:**

- `fileRequestId`: `String?` - File request id. Might be missing due to historical data gap.
- `previousDetails`: `TeamLog.FileRequestDetails?` - Previous file request details. Might be missing due to historical data gap.

### FileRequestCloseType

`class`

Type for file request close type.

**Properties:**

- `description_`: `String`

### FileRequestCreateDetails

`class`

Created file request.

**Properties:**

- `fileRequestId`: `String?` - File request id. Might be missing due to historical data gap.
- `requestDetails`: `TeamLog.FileRequestDetails?` - File request details. Might be missing due to historical data gap.

### FileRequestCreateType

`class`

Type for file request create type.

**Properties:**

- `description_`: `String`

### FileRequestDeadline

`class`

File request deadline

**Properties:**

- `deadline`: `Date?` - The deadline for this file request. Might be missing due to historical data gap.
- `allowLateUploads`: `String?` - If set, allow uploads after the deadline has passed.

### FileRequestDeleteDetails

`class`

Delete file request.

**Properties:**

- `fileRequestId`: `String?` - File request id. Might be missing due to historical data gap.
- `previousDetails`: `TeamLog.FileRequestDetails?` - Previous file request details. Might be missing due to historical data gap.

### FileRequestDeleteType

`class`

Type for file request delete type.

**Properties:**

- `description_`: `String`

### FileRequestDetails

`class`

File request details

**Properties:**

- `assetIndex`: `UInt64` - Asset position in the Assets list.
- `deadline`: `TeamLog.FileRequestDeadline?` - File request deadline.

### FileRequestReceiveFileDetails

`class`

Received files for file request.

**Properties:**

- `fileRequestId`: `String?` - File request id. Might be missing due to historical data gap.
- `fileRequestDetails`: `TeamLog.FileRequestDetails?` - File request details. Might be missing due to historical data gap.
- `submittedFileNames`: `[String]` - Submitted file names.
- `submitterName`: `String?` - The name as provided by the submitter.
- `submitterEmail`: `String?` - The email as provided by the submitter.

### FileRequestReceiveFileType

`class`

Type for file request receive file type.

**Properties:**

- `description_`: `String`

### FileRequestsChangePolicyDetails

`class`

Enabled/disabled file requests.

**Properties:**

- `newValue`: `TeamLog.FileRequestsPolicy` - New file requests policy.
- `previousValue`: `TeamLog.FileRequestsPolicy?` - Previous file requests policy. Might be missing due to historical data gap.

### FileRequestsChangePolicyType

`class`

Type for file requests change policy type.

**Properties:**

- `description_`: `String`

### FileRequestsEmailsEnabledDetails

`class`

Enabled file request emails for everyone.

### FileRequestsEmailsEnabledType

`class`

Type for file requests emails enabled type.

**Properties:**

- `description_`: `String`

### FileRequestsEmailsRestrictedToTeamOnlyDetails

`class`

Enabled file request emails for team.

### FileRequestsEmailsRestrictedToTeamOnlyType

`class`

Type for file requests emails restricted to team only type.

**Properties:**

- `description_`: `String`

### FileRequestsPolicy

`enum`

File requests policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### FileResolveCommentDetails

`class`

Resolved file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileResolveCommentType

`class`

Type for file resolve comment type.

**Properties:**

- `description_`: `String`

### FileRestoreDetails

`class`

Restored deleted files and/or folders.

### FileRestoreType

`class`

Type for file restore type.

**Properties:**

- `description_`: `String`

### FileRevertDetails

`class`

Reverted files to previous version.

### FileRevertType

`class`

Type for file revert type.

**Properties:**

- `description_`: `String`

### FileRollbackChangesDetails

`class`

Rolled back file actions.

### FileRollbackChangesType

`class`

Type for file rollback changes type.

**Properties:**

- `description_`: `String`

### FileSaveCopyReferenceDetails

`class`

Saved file/folder using copy reference.

**Properties:**

- `relocateActionDetails`: `[TeamLog.RelocateAssetReferencesLogInfo]` - Relocate action details.

### FileSaveCopyReferenceType

`class`

Type for file save copy reference type.

**Properties:**

- `description_`: `String`

### FileTransfersFileAddDetails

`class`

Transfer files added.

**Properties:**

- `fileTransferId`: `String` - Transfer id.

### FileTransfersFileAddType

`class`

Type for file transfers file add type.

**Properties:**

- `description_`: `String`

### FileTransfersPolicy

`enum`

File transfers policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### FileTransfersPolicyChangedDetails

`class`

Changed file transfers policy for team.

**Properties:**

- `newValue`: `TeamLog.FileTransfersPolicy` - New file transfers policy.
- `previousValue`: `TeamLog.FileTransfersPolicy` - Previous file transfers policy.

### FileTransfersPolicyChangedType

`class`

Type for file transfers policy changed type.

**Properties:**

- `description_`: `String`

### FileTransfersTransferDeleteDetails

`class`

Deleted transfer.

**Properties:**

- `fileTransferId`: `String` - Transfer id.

### FileTransfersTransferDeleteType

`class`

Type for file transfers transfer delete type.

**Properties:**

- `description_`: `String`

### FileTransfersTransferDownloadDetails

`class`

Transfer downloaded.

**Properties:**

- `fileTransferId`: `String` - Transfer id.

### FileTransfersTransferDownloadType

`class`

Type for file transfers transfer download type.

**Properties:**

- `description_`: `String`

### FileTransfersTransferSendDetails

`class`

Sent transfer.

**Properties:**

- `fileTransferId`: `String` - Transfer id.

### FileTransfersTransferSendType

`class`

Type for file transfers transfer send type.

**Properties:**

- `description_`: `String`

### FileTransfersTransferViewDetails

`class`

Viewed transfer.

**Properties:**

- `fileTransferId`: `String` - Transfer id.

### FileTransfersTransferViewType

`class`

Type for file transfers transfer view type.

**Properties:**

- `description_`: `String`

### FileUnlikeCommentDetails

`class`

Unliked file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileUnlikeCommentType

`class`

Type for file unlike comment type.

**Properties:**

- `description_`: `String`

### FileUnresolveCommentDetails

`class`

Unresolved file comment.

**Properties:**

- `commentText`: `String?` - Comment text.

### FileUnresolveCommentType

`class`

Type for file unresolve comment type.

**Properties:**

- `description_`: `String`

### FolderLinkRestrictionPolicy

`enum`

Policy for deciding whether applying link restrictions on all team owned folders

**Cases:**

- `disabled`
- `enabled`
- `other`

### FolderLinkRestrictionPolicyChangedDetails

`class`

Changed folder link restrictions policy for team.

**Properties:**

- `newValue`: `TeamLog.FolderLinkRestrictionPolicy` - To.
- `previousValue`: `TeamLog.FolderLinkRestrictionPolicy` - From.

### FolderLinkRestrictionPolicyChangedType

`class`

Type for folder link restriction policy changed type.

**Properties:**

- `description_`: `String`

### FolderOverviewDescriptionChangedDetails

`class`

Updated folder overview.

**Properties:**

- `folderOverviewLocationAsset`: `UInt64` - Folder Overview location position in the Assets list.

### FolderOverviewDescriptionChangedType

`class`

Type for folder overview description changed type.

**Properties:**

- `description_`: `String`

### FolderOverviewItemPinnedDetails

`class`

Pinned item to folder overview.

**Properties:**

- `folderOverviewLocationAsset`: `UInt64` - Folder Overview location position in the Assets list.
- `pinnedItemsAssetIndices`: `[UInt64]` - Pinned items positions in the Assets list.

### FolderOverviewItemPinnedType

`class`

Type for folder overview item pinned type.

**Properties:**

- `description_`: `String`

### FolderOverviewItemUnpinnedDetails

`class`

Unpinned item from folder overview.

**Properties:**

- `folderOverviewLocationAsset`: `UInt64` - Folder Overview location position in the Assets list.
- `pinnedItemsAssetIndices`: `[UInt64]` - Pinned items positions in the Assets list.

### FolderOverviewItemUnpinnedType

`class`

Type for folder overview item unpinned type.

**Properties:**

- `description_`: `String`

### ObjectLabelAddedDetails

`class`

Added a label.

**Properties:**

- `labelType`: `TeamLog.LabelType` - Labels mark a file or folder.

### ObjectLabelAddedType

`class`

Type for object label added type.

**Properties:**

- `description_`: `String`

### ObjectLabelRemovedDetails

`class`

Removed a label.

**Properties:**

- `labelType`: `TeamLog.LabelType` - Labels mark a file or folder.

### ObjectLabelRemovedType

`class`

Type for object label removed type.

**Properties:**

- `description_`: `String`

### ObjectLabelUpdatedValueDetails

`class`

Updated a label's value.

**Properties:**

- `labelType`: `TeamLog.LabelType` - Labels mark a file or folder.

### ObjectLabelUpdatedValueType

`class`

Type for object label updated value type.

**Properties:**

- `description_`: `String`

### RewindFolderDetails

`class`

Rewound a folder.

**Properties:**

- `rewindFolderTargetTsMs`: `Date` - Folder was Rewound to this date.

### RewindFolderType

`class`

Type for rewind folder type.

**Properties:**

- `description_`: `String`

### UndoNamingConventionDetails

`class`

Reverted naming convention.

### UndoNamingConventionType

`class`

Type for undo naming convention type.

**Properties:**

- `description_`: `String`

### UndoOrganizeFolderWithTidyDetails

`class`

Removed multi-file organize.

### UndoOrganizeFolderWithTidyType

`class`

Type for undo organize folder with tidy type.

**Properties:**

- `description_`: `String`

---

## Group Management

### GroupAddExternalIdDetails

`class`

Added external ID for group.

**Properties:**

- `newValue`: `String` - Current external id.

### GroupAddExternalIdType

`class`

Type for group add external id type.

**Properties:**

- `description_`: `String`

### GroupAddMemberDetails

`class`

Added team members to group.

**Properties:**

- `isGroupOwner`: `Bool` - Is group owner.

### GroupAddMemberType

`class`

Type for group add member type.

**Properties:**

- `description_`: `String`

### GroupChangeExternalIdDetails

`class`

Changed external ID for group.

**Properties:**

- `newValue`: `String` - Current external id.
- `previousValue`: `String` - Old external id.

### GroupChangeExternalIdType

`class`

Type for group change external id type.

**Properties:**

- `description_`: `String`

### GroupChangeManagementTypeDetails

`class`

Changed group management type.

**Properties:**

- `newValue`: `TeamCommon.GroupManagementType` - New group management type.
- `previousValue`: `TeamCommon.GroupManagementType?` - Previous group management type. Might be missing due to historical data gap.

### GroupChangeManagementTypeType

`class`

Type for group change management type type.

**Properties:**

- `description_`: `String`

### GroupChangeMemberRoleDetails

`class`

Changed manager permissions of group member.

**Properties:**

- `isGroupOwner`: `Bool` - Is group owner.

### GroupChangeMemberRoleType

`class`

Type for group change member role type.

**Properties:**

- `description_`: `String`

### GroupCreateDetails

`class`

Created group.

**Properties:**

- `isCompanyManaged`: `Bool?` - Is company managed group.
- `joinPolicy`: `TeamLog.GroupJoinPolicy?` - Group join policy.

### GroupCreateType

`class`

Type for group create type.

**Properties:**

- `description_`: `String`

### GroupDeleteDetails

`class`

Deleted group.

**Properties:**

- `isCompanyManaged`: `Bool?` - Is company managed group.

### GroupDeleteType

`class`

Type for group delete type.

**Properties:**

- `description_`: `String`

### GroupDescriptionUpdatedDetails

`class`

Updated group.

### GroupDescriptionUpdatedType

`class`

Type for group description updated type.

**Properties:**

- `description_`: `String`

### GroupJoinPolicy

`enum`

Type for group join policy.

**Cases:**

- `open`
- `requestToJoin`
- `other`

### GroupJoinPolicyUpdatedDetails

`class`

Updated group join policy.

**Properties:**

- `isCompanyManaged`: `Bool?` - Is company managed group.
- `joinPolicy`: `TeamLog.GroupJoinPolicy?` - Group join policy.

### GroupJoinPolicyUpdatedType

`class`

Type for group join policy updated type.

**Properties:**

- `description_`: `String`

### GroupLogInfo

`class`

Group's logged information.

**Properties:**

- `groupId`: `String?` - The unique id of this group.
- `displayName`: `String` - The name of this group.
- `externalId`: `String?` - External group ID.

### GroupMovedDetails

`class`

Moved group.

### GroupMovedType

`class`

Type for group moved type.

**Properties:**

- `description_`: `String`

### GroupRemoveExternalIdDetails

`class`

Removed external ID for group.

**Properties:**

- `previousValue`: `String` - Old external id.

### GroupRemoveExternalIdType

`class`

Type for group remove external id type.

**Properties:**

- `description_`: `String`

### GroupRemoveMemberDetails

`class`

Removed team members from group.

### GroupRemoveMemberType

`class`

Type for group remove member type.

**Properties:**

- `description_`: `String`

### GroupRenameDetails

`class`

Renamed group.

**Properties:**

- `previousValue`: `String` - Previous display name.
- `newValue`: `String` - New display name.

### GroupRenameType

`class`

Type for group rename type.

**Properties:**

- `description_`: `String`

### GroupUserManagementChangePolicyDetails

`class`

Changed who can create groups.

**Properties:**

- `newValue`: `TeamPolicies.GroupCreation` - New group users management policy.
- `previousValue`: `TeamPolicies.GroupCreation?` - Previous group users management policy. Might be missing due to historical data gap.

### GroupUserManagementChangePolicyType

`class`

Type for group user management change policy type.

**Properties:**

- `description_`: `String`

---

## Integration & Third-Party

### GoogleSsoChangePolicyDetails

`class`

Enabled/disabled Google single sign-on for team.

**Properties:**

- `newValue`: `TeamLog.GoogleSsoPolicy` - New Google single sign-on policy.
- `previousValue`: `TeamLog.GoogleSsoPolicy?` - Previous Google single sign-on policy. Might be missing due to historical data gap.

### GoogleSsoChangePolicyType

`class`

Type for google sso change policy type.

**Properties:**

- `description_`: `String`

### GoogleSsoPolicy

`enum`

Google SSO policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### IntegrationConnectedDetails

`class`

Connected integration for member.

**Properties:**

- `integrationName`: `String` - Name of the third-party integration.

### IntegrationConnectedType

`class`

Type for integration connected type.

**Properties:**

- `description_`: `String`

### IntegrationDisconnectedDetails

`class`

Disconnected integration for member.

**Properties:**

- `integrationName`: `String` - Name of the third-party integration.

### IntegrationDisconnectedType

`class`

Type for integration disconnected type.

**Properties:**

- `description_`: `String`

### IntegrationPolicy

`enum`

Policy for controlling whether a service integration is enabled for the team.

**Cases:**

- `disabled`
- `enabled`
- `other`

### IntegrationPolicyChangedDetails

`class`

Changed integration policy for team.

**Properties:**

- `integrationName`: `String` - Name of the third-party integration.
- `newValue`: `TeamLog.IntegrationPolicy` - New integration policy.
- `previousValue`: `TeamLog.IntegrationPolicy` - Previous integration policy.

### IntegrationPolicyChangedType

`class`

Type for integration policy changed type.

**Properties:**

- `description_`: `String`

---

## Legal Holds

### LegalHoldsActivateAHoldDetails

`class`

Activated a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `startDate`: `Date` - Hold start date.
- `endDate`: `Date?` - Hold end date.

### LegalHoldsActivateAHoldType

`class`

Type for legal holds activate a hold type.

**Properties:**

- `description_`: `String`

### LegalHoldsAddMembersDetails

`class`

Added members to a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.

### LegalHoldsAddMembersType

`class`

Type for legal holds add members type.

**Properties:**

- `description_`: `String`

### LegalHoldsChangeHoldDetailsDetails

`class`

Edited details for a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `previousValue`: `String` - Previous details.
- `newValue`: `String` - New details.

### LegalHoldsChangeHoldDetailsType

`class`

Type for legal holds change hold details type.

**Properties:**

- `description_`: `String`

### LegalHoldsChangeHoldNameDetails

`class`

Renamed a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `previousValue`: `String` - Previous Name.
- `newValue`: `String` - New Name.

### LegalHoldsChangeHoldNameType

`class`

Type for legal holds change hold name type.

**Properties:**

- `description_`: `String`

### LegalHoldsExportAHoldDetails

`class`

Exported hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `exportName`: `String?` - Export name.

### LegalHoldsExportAHoldType

`class`

Type for legal holds export a hold type.

**Properties:**

- `description_`: `String`

### LegalHoldsExportCancelledDetails

`class`

Canceled export for a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `exportName`: `String` - Export name.

### LegalHoldsExportCancelledType

`class`

Type for legal holds export cancelled type.

**Properties:**

- `description_`: `String`

### LegalHoldsExportDownloadedDetails

`class`

Downloaded export for a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `exportName`: `String` - Export name.
- `part`: `String?` - Part.
- `fileName`: `String?` - Filename.

### LegalHoldsExportDownloadedType

`class`

Type for legal holds export downloaded type.

**Properties:**

- `description_`: `String`

### LegalHoldsExportRemovedDetails

`class`

Removed export for a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.
- `exportName`: `String` - Export name.

### LegalHoldsExportRemovedType

`class`

Type for legal holds export removed type.

**Properties:**

- `description_`: `String`

### LegalHoldsReleaseAHoldDetails

`class`

Released a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.

### LegalHoldsReleaseAHoldType

`class`

Type for legal holds release a hold type.

**Properties:**

- `description_`: `String`

### LegalHoldsRemoveMembersDetails

`class`

Removed members from a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.

### LegalHoldsRemoveMembersType

`class`

Type for legal holds remove members type.

**Properties:**

- `description_`: `String`

### LegalHoldsReportAHoldDetails

`class`

Created a summary report for a hold.

**Properties:**

- `legalHoldId`: `String` - Hold ID.
- `name`: `String` - Hold name.

### LegalHoldsReportAHoldType

`class`

Type for legal holds report a hold type.

**Properties:**

- `description_`: `String`

---

## Login & Authentication

### LoginFailDetails

`class`

Failed to sign in.

**Properties:**

- `isEmmManaged`: `Bool?` - Tells if the login device is EMM managed. Might be missing due to historical data gap.
- `loginMethod`: `TeamLog.LoginMethod` - Login method.
- `errorDetails`: `TeamLog.FailureDetailsLogInfo` - Error details.

### LoginFailType

`class`

Type for login fail type.

**Properties:**

- `description_`: `String`

### LoginMethod

`enum`

Type for login method.

**Cases:**

- `appleOauth`
- `firstPartyTokenExchange`
- `googleOauth`
- `lenovoOauth`
- `password`
- `qrCode`
- `saml`
- `twoFactorAuthentication`
- `webSession`
- `other`

### LoginSuccessDetails

`class`

Signed in.

**Properties:**

- `isEmmManaged`: `Bool?` - Tells if the login device is EMM managed. Might be missing due to historical data gap.
- `loginMethod`: `TeamLog.LoginMethod` - Login method.

### LoginSuccessType

`class`

Type for login success type.

**Properties:**

- `description_`: `String`

### LogoutDetails

`class`

Signed out.

**Properties:**

- `loginId`: `String?` - Login session id.

### LogoutType

`class`

Type for logout type.

**Properties:**

- `description_`: `String`

### SignInAsSessionEndDetails

`class`

Ended admin sign-in-as session.

### SignInAsSessionEndType

`class`

Type for sign in as session end type.

**Properties:**

- `description_`: `String`

### SignInAsSessionStartDetails

`class`

Started admin sign-in-as session.

### SignInAsSessionStartType

`class`

Type for sign in as session start type.

**Properties:**

- `description_`: `String`

---

## Member Management

### InviteAcceptanceEmailPolicy

`enum`

Policy for deciding whether team admins receive email when an invitation to join the team is accepted

**Cases:**

- `disabled`
- `enabled`
- `other`

### InviteAcceptanceEmailPolicyChangedDetails

`class`

Changed invite accept email policy for team.

**Properties:**

- `newValue`: `TeamLog.InviteAcceptanceEmailPolicy` - To.
- `previousValue`: `TeamLog.InviteAcceptanceEmailPolicy` - From.

### InviteAcceptanceEmailPolicyChangedType

`class`

Type for invite acceptance email policy changed type.

**Properties:**

- `description_`: `String`

### InviteMethod

`enum`

Type for invite method.

**Cases:**

- `autoApprove`
- `inviteLink`
- `memberInvite`
- `movedFromAnotherTeam`
- `other`

### JoinTeamDetails

`class`

Additional information relevant when a new member joins the team.

**Properties:**

- `linkedApps`: `[TeamLog.UserLinkedAppLogInfo]` - Linked applications. (Deprecated) Please use has_linked_apps boolean field instead.
- `linkedDevices`: `[TeamLog.LinkedDeviceLogInfo]` - Linked devices. (Deprecated) Please use has_linked_devices boolean field instead.
- `linkedSharedFolders`: `[TeamLog.FolderLogInfo]` - Linked shared folders. (Deprecated) Please use has_linked_shared_folders boolean field instead.
- `wasLinkedAppsTruncated`: `Bool?` - (Deprecated) True if the linked_apps list was truncated to the maximum supported length (50).
- `wasLinkedDevicesTruncated`: `Bool?` - (Deprecated) True if the linked_devices list was truncated to the maximum supported length (50).
- `wasLinkedSharedFoldersTruncated`: `Bool?` - (Deprecated) True if the linked_shared_folders list was truncated to the maximum supported length (50).
- `hasLinkedApps`: `Bool?` - True if the user had linked apps at event time.
- `hasLinkedDevices`: `Bool?` - True if the user had linked apps at event time.
- `hasLinkedSharedFolders`: `Bool?` - True if the user had linked shared folders at event time.

### MemberAddExternalIdDetails

`class`

Added an external ID for team member.

**Properties:**

- `newValue`: `String` - Current external id.

### MemberAddExternalIdType

`class`

Type for member add external id type.

**Properties:**

- `description_`: `String`

### MemberAddNameDetails

`class`

Added team member name.

**Properties:**

- `newValue`: `TeamLog.UserNameLogInfo` - New user's name.

### MemberAddNameType

`class`

Type for member add name type.

**Properties:**

- `description_`: `String`

### MemberChangeAdminRoleDetails

`class`

Changed team member admin role.

**Properties:**

- `newValue`: `TeamLog.AdminRole?` - admin rights to with admin rights.
- `previousValue`: `TeamLog.AdminRole?` - removed.

### MemberChangeAdminRoleType

`class`

Type for member change admin role type.

**Properties:**

- `description_`: `String`

### MemberChangeEmailDetails

`class`

Changed team member email.

**Properties:**

- `newValue`: `String` - New email.
- `previousValue`: `String?` - Previous email. Might be missing due to historical data gap.

### MemberChangeEmailType

`class`

Type for member change email type.

**Properties:**

- `description_`: `String`

### MemberChangeExternalIdDetails

`class`

Changed the external ID for team member.

**Properties:**

- `newValue`: `String` - Current external id.
- `previousValue`: `String` - Old external id.

### MemberChangeExternalIdType

`class`

Type for member change external id type.

**Properties:**

- `description_`: `String`

### MemberChangeMembershipTypeDetails

`class`

Changed membership type (limited/full) of member.

**Properties:**

- `prevValue`: `TeamLog.TeamMembershipType` - Previous membership type.
- `newValue`: `TeamLog.TeamMembershipType` - New membership type.

### MemberChangeMembershipTypeType

`class`

Type for member change membership type type.

**Properties:**

- `description_`: `String`

### MemberChangeNameDetails

`class`

Changed team member name.

**Properties:**

- `newValue`: `TeamLog.UserNameLogInfo` - New user's name.
- `previousValue`: `TeamLog.UserNameLogInfo?` - Previous user's name. Might be missing due to historical data gap.

### MemberChangeNameType

`class`

Type for member change name type.

**Properties:**

- `description_`: `String`

### MemberChangeResellerRoleDetails

`class`

Changed team member reseller role.

**Properties:**

- `newValue`: `TeamLog.ResellerRole` - New reseller role. This field is relevant when the reseller role is changed.
- `previousValue`: `TeamLog.ResellerRole` - is removed.

### MemberChangeResellerRoleType

`class`

Type for member change reseller role type.

**Properties:**

- `description_`: `String`

### MemberChangeStatusDetails

`class`

Changed member status (invited, joined, suspended, etc.).

**Properties:**

- `previousValue`: `TeamLog.MemberStatus?` - Previous member status. Might be missing due to historical data gap.
- `newValue`: `TeamLog.MemberStatus` - New member status.
- `action`: `TeamLog.ActionDetails?` - Additional information indicating the action taken that caused status change.
- `newTeam`: `String?` - The user's new team name. This field is relevant when the user is transferred off the team.
- `previousTeam`: `String?` - The user's previous team name. This field is relevant when the user is transferred onto the team.

### MemberChangeStatusType

`class`

Type for member change status type.

**Properties:**

- `description_`: `String`

### MemberDeleteManualContactsDetails

`class`

Cleared manually added contacts.

### MemberDeleteManualContactsType

`class`

Type for member delete manual contacts type.

**Properties:**

- `description_`: `String`

### MemberDeleteProfilePhotoDetails

`class`

Deleted team member profile photo.

### MemberDeleteProfilePhotoType

`class`

Type for member delete profile photo type.

**Properties:**

- `description_`: `String`

### MemberPermanentlyDeleteAccountContentsDetails

`class`

Permanently deleted contents of deleted team member account.

### MemberPermanentlyDeleteAccountContentsType

`class`

Type for member permanently delete account contents type.

**Properties:**

- `description_`: `String`

### MemberRemoveActionType

`enum`

Type for member remove action type.

**Cases:**

- `delete`
- `leave`
- `offboard`
- `offboardAndRetainTeamFolders`
- `other`

### MemberRemoveExternalIdDetails

`class`

Removed the external ID for team member.

**Properties:**

- `previousValue`: `String` - Old external id.

### MemberRemoveExternalIdType

`class`

Type for member remove external id type.

**Properties:**

- `description_`: `String`

### MemberRequestsChangePolicyDetails

`class`

Changed whether users can find team when not invited.

**Properties:**

- `newValue`: `TeamLog.MemberRequestsPolicy` - New member change requests policy.
- `previousValue`: `TeamLog.MemberRequestsPolicy?` - Previous member change requests policy. Might be missing due to historical data gap.

### MemberRequestsChangePolicyType

`class`

Type for member requests change policy type.

**Properties:**

- `description_`: `String`

### MemberRequestsPolicy

`enum`

Type for member requests policy.

**Cases:**

- `autoAccept`
- `disabled`
- `requireApproval`
- `other`

### MemberSendInvitePolicy

`enum`

Policy for controlling whether team members can send team invites

**Cases:**

- `disabled`
- `everyone`
- `specificMembers`
- `other`

### MemberSendInvitePolicyChangedDetails

`class`

Changed member send invite policy for team.

**Properties:**

- `newValue`: `TeamLog.MemberSendInvitePolicy` - New team member send invite policy.
- `previousValue`: `TeamLog.MemberSendInvitePolicy` - Previous team member send invite policy.

### MemberSendInvitePolicyChangedType

`class`

Type for member send invite policy changed type.

**Properties:**

- `description_`: `String`

### MemberSetProfilePhotoDetails

`class`

Set team member profile photo.

### MemberSetProfilePhotoType

`class`

Type for member set profile photo type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsAddCustomQuotaDetails

`class`

Set custom member space limit.

**Properties:**

- `newValue`: `UInt64` - New custom quota value in bytes.

### MemberSpaceLimitsAddCustomQuotaType

`class`

Type for member space limits add custom quota type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsAddExceptionDetails

`class`

Added members to member space limit exception list.

### MemberSpaceLimitsAddExceptionType

`class`

Type for member space limits add exception type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsChangeCapsTypePolicyDetails

`class`

Changed member space limit type for team.

**Properties:**

- `previousValue`: `TeamLog.SpaceCapsType` - Previous space limit type.
- `newValue`: `TeamLog.SpaceCapsType` - New space limit type.

### MemberSpaceLimitsChangeCapsTypePolicyType

`class`

Type for member space limits change caps type policy type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsChangeCustomQuotaDetails

`class`

Changed custom member space limit.

**Properties:**

- `previousValue`: `UInt64` - Previous custom quota value in bytes.
- `newValue`: `UInt64` - New custom quota value in bytes.

### MemberSpaceLimitsChangeCustomQuotaType

`class`

Type for member space limits change custom quota type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsChangePolicyDetails

`class`

Changed team default member space limit.

**Properties:**

- `previousValue`: `UInt64?` - Previous team default limit value in bytes. Might be missing due to historical data gap.
- `newValue`: `UInt64?` - New team default limit value in bytes. Might be missing due to historical data gap.

### MemberSpaceLimitsChangePolicyType

`class`

Type for member space limits change policy type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsChangeStatusDetails

`class`

Changed space limit status.

**Properties:**

- `previousValue`: `TeamLog.SpaceLimitsStatus` - Previous storage quota status.
- `newValue`: `TeamLog.SpaceLimitsStatus` - New storage quota status.

### MemberSpaceLimitsChangeStatusType

`class`

Type for member space limits change status type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsRemoveCustomQuotaDetails

`class`

Removed custom member space limit.

### MemberSpaceLimitsRemoveCustomQuotaType

`class`

Type for member space limits remove custom quota type.

**Properties:**

- `description_`: `String`

### MemberSpaceLimitsRemoveExceptionDetails

`class`

Removed members from member space limit exception list.

### MemberSpaceLimitsRemoveExceptionType

`class`

Type for member space limits remove exception type.

**Properties:**

- `description_`: `String`

### MemberStatus

`enum`

Type for member status.

**Cases:**

- `active`
- `invited`
- `movedToAnotherTeam`
- `notJoined`
- `removed`
- `suspended`
- `other`

### MemberSuggestDetails

`class`

Suggested person to add to team.

**Properties:**

- `suggestedMembers`: `[String]` - suggested users emails.

### MemberSuggestType

`class`

Type for member suggest type.

**Properties:**

- `description_`: `String`

### MemberSuggestionsChangePolicyDetails

`class`

Enabled/disabled option for team members to suggest people to add to team.

**Properties:**

- `newValue`: `TeamLog.MemberSuggestionsPolicy` - New team member suggestions policy.
- `previousValue`: `TeamLog.MemberSuggestionsPolicy?` - Previous team member suggestions policy. Might be missing due to historical data gap.

### MemberSuggestionsChangePolicyType

`class`

Type for member suggestions change policy type.

**Properties:**

- `description_`: `String`

### MemberSuggestionsPolicy

`enum`

Member suggestions policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### MemberTransferAccountContentsDetails

`class`

Transferred contents of deleted member account to another member.

### MemberTransferAccountContentsType

`class`

Type for member transfer account contents type.

**Properties:**

- `description_`: `String`

### MemberTransferredInternalFields

`class`

Internal only - fields for target team computations

**Properties:**

- `sourceTeamId`: `String` - Internal only - team user was moved from.
- `targetTeamId`: `String` - Internal only - team user was moved to.

### SecondaryEmailDeletedDetails

`class`

Deleted secondary email.

**Properties:**

- `secondaryEmail`: `String` - Deleted secondary email.

### SecondaryEmailDeletedType

`class`

Type for secondary email deleted type.

**Properties:**

- `description_`: `String`

### SecondaryEmailVerifiedDetails

`class`

Verified secondary email.

**Properties:**

- `secondaryEmail`: `String` - Verified secondary email.

### SecondaryEmailVerifiedType

`class`

Type for secondary email verified type.

**Properties:**

- `description_`: `String`

### TeamInviteDetails

`class`

Details about team invites

**Properties:**

- `inviteMethod`: `TeamLog.InviteMethod` - How the user was invited to the team.
- `additionalLicensePurchase`: `Bool?` - True if the invitation incurred an additional license purchase.

### TeamMergeFromDetails

`class`

Merged another team into this team.

**Properties:**

- `teamName`: `String` - The name of the team that was merged into this team.

### TeamMergeFromType

`class`

Type for team merge from type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestAcceptedDetails

`class`

Accepted a team merge request.

**Properties:**

- `requestAcceptedDetails`: `TeamLog.TeamMergeRequestAcceptedExtraDetails` - Team merge request acceptance details.

### TeamMergeRequestAcceptedExtraDetails

`enum`

Team merge request acceptance details

**Cases:**

- `primaryTeam` - Team merge request accepted details shown to the primary team.
- `secondaryTeam` - Team merge request accepted details shown to the secondary team.
- `other`

### TeamMergeRequestAcceptedShownToPrimaryTeamDetails

`class`

Accepted a team merge request.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestAcceptedShownToPrimaryTeamType

`class`

Type for team merge request accepted shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestAcceptedShownToSecondaryTeamDetails

`class`

Accepted a team merge request.

**Properties:**

- `primaryTeam`: `String` - The primary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestAcceptedShownToSecondaryTeamType

`class`

Type for team merge request accepted shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestAcceptedType

`class`

Type for team merge request accepted type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestAutoCanceledDetails

`class`

Automatically canceled team merge request.

**Properties:**

- `details`: `String?` - The cancellation reason.

### TeamMergeRequestAutoCanceledType

`class`

Type for team merge request auto canceled type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestCanceledDetails

`class`

Canceled a team merge request.

**Properties:**

- `requestCanceledDetails`: `TeamLog.TeamMergeRequestCanceledExtraDetails` - Team merge request cancellation details.

### TeamMergeRequestCanceledExtraDetails

`enum`

Team merge request cancellation details

**Cases:**

- `primaryTeam` - Team merge request cancellation details shown to the primary team.
- `secondaryTeam` - Team merge request cancellation details shown to the secondary team.
- `other`

### TeamMergeRequestCanceledShownToPrimaryTeamDetails

`class`

Canceled a team merge request.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestCanceledShownToPrimaryTeamType

`class`

Type for team merge request canceled shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestCanceledShownToSecondaryTeamDetails

`class`

Canceled a team merge request.

**Properties:**

- `sentTo`: `String` - The email of the primary team admin that the request was sent to.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestCanceledShownToSecondaryTeamType

`class`

Type for team merge request canceled shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestCanceledType

`class`

Type for team merge request canceled type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestExpiredDetails

`class`

Team merge request expired.

**Properties:**

- `requestExpiredDetails`: `TeamLog.TeamMergeRequestExpiredExtraDetails` - Team merge request expiration details.

### TeamMergeRequestExpiredExtraDetails

`enum`

Team merge request expiration details

**Cases:**

- `primaryTeam` - Team merge request canceled details shown to the primary team.
- `secondaryTeam` - Team merge request canceled details shown to the secondary team.
- `other`

### TeamMergeRequestExpiredShownToPrimaryTeamDetails

`class`

Team merge request expired.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestExpiredShownToPrimaryTeamType

`class`

Type for team merge request expired shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestExpiredShownToSecondaryTeamDetails

`class`

Team merge request expired.

**Properties:**

- `sentTo`: `String` - The email of the primary team admin the request was sent to.

### TeamMergeRequestExpiredShownToSecondaryTeamType

`class`

Type for team merge request expired shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestExpiredType

`class`

Type for team merge request expired type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestRejectedShownToPrimaryTeamDetails

`class`

Rejected a team merge request.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestRejectedShownToPrimaryTeamType

`class`

Type for team merge request rejected shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestRejectedShownToSecondaryTeamDetails

`class`

Rejected a team merge request.

**Properties:**

- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### TeamMergeRequestRejectedShownToSecondaryTeamType

`class`

Type for team merge request rejected shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestReminderDetails

`class`

Sent a team merge request reminder.

**Properties:**

- `requestReminderDetails`: `TeamLog.TeamMergeRequestReminderExtraDetails` - Team merge request reminder details.

### TeamMergeRequestReminderExtraDetails

`enum`

Team merge request reminder details

**Cases:**

- `primaryTeam` - Team merge request reminder details shown to the primary team.
- `secondaryTeam` - Team merge request reminder details shown to the secondary team.
- `other`

### TeamMergeRequestReminderShownToPrimaryTeamDetails

`class`

Sent a team merge request reminder.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentTo`: `String` - The name of the primary team admin the request was sent to.

### TeamMergeRequestReminderShownToPrimaryTeamType

`class`

Type for team merge request reminder shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestReminderShownToSecondaryTeamDetails

`class`

Sent a team merge request reminder.

**Properties:**

- `sentTo`: `String` - The email of the primary team admin the request was sent to.

### TeamMergeRequestReminderShownToSecondaryTeamType

`class`

Type for team merge request reminder shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestReminderType

`class`

Type for team merge request reminder type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestRevokedDetails

`class`

Canceled the team merge.

**Properties:**

- `team`: `String` - The name of the other team.

### TeamMergeRequestRevokedType

`class`

Type for team merge request revoked type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestSentShownToPrimaryTeamDetails

`class`

Requested to merge their Dropbox team into yours.

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentTo`: `String` - The name of the primary team admin the request was sent to.

### TeamMergeRequestSentShownToPrimaryTeamType

`class`

Type for team merge request sent shown to primary team type.

**Properties:**

- `description_`: `String`

### TeamMergeRequestSentShownToSecondaryTeamDetails

`class`

Requested to merge your team into another Dropbox team.

**Properties:**

- `sentTo`: `String` - The email of the primary team admin the request was sent to.

### TeamMergeRequestSentShownToSecondaryTeamType

`class`

Type for team merge request sent shown to secondary team type.

**Properties:**

- `description_`: `String`

### TeamMergeToDetails

`class`

Merged this team into another team.

**Properties:**

- `teamName`: `String` - The name of the team that this team was merged into.

### TeamMergeToType

`class`

Type for team merge to type.

**Properties:**

- `description_`: `String`

---

## Namespace

### NamespaceRelativePathLogInfo

`class`

Namespace relative path details.

**Properties:**

- `nsId`: `String?` - Namespace ID.
- `relativePath`: `String?` - A path relative to the specified namespace ID.
- `isSharedNamespace`: `Bool?` - True if the namespace is shared.

---

## Network & Geo

### GeoLocationLogInfo

`class`

Geographic location details.

**Properties:**

- `city`: `String?` - City name.
- `region`: `String?` - Region name.
- `country`: `String?` - Country code.
- `ipAddress`: `String` - IP address.

### NetworkControlChangePolicyDetails

`class`

Enabled/disabled network control.

**Properties:**

- `newValue`: `TeamLog.NetworkControlPolicy` - New network control policy.
- `previousValue`: `TeamLog.NetworkControlPolicy?` - Previous network control policy. Might be missing due to historical data gap.

### NetworkControlChangePolicyType

`class`

Type for network control change policy type.

**Properties:**

- `description_`: `String`

### NetworkControlPolicy

`enum`

Network control policy

**Cases:**

- `disabled`
- `enabled`
- `other`

---

## Paper & Notes

### NoteAclInviteOnlyDetails

`class`

Changed Paper doc to invite-only.

### NoteAclInviteOnlyType

`class`

Type for note acl invite only type.

**Properties:**

- `description_`: `String`

### NoteAclLinkDetails

`class`

Changed Paper doc to link-accessible.

### NoteAclLinkType

`class`

Type for note acl link type.

**Properties:**

- `description_`: `String`

### NoteAclTeamLinkDetails

`class`

Changed Paper doc to link-accessible for team.

### NoteAclTeamLinkType

`class`

Type for note acl team link type.

**Properties:**

- `description_`: `String`

### NoteShareReceiveDetails

`class`

Shared received Paper doc.

### NoteShareReceiveType

`class`

Type for note share receive type.

**Properties:**

- `description_`: `String`

### NoteSharedDetails

`class`

Shared Paper doc.

### NoteSharedType

`class`

Type for note shared type.

**Properties:**

- `description_`: `String`

### PaperAccessType

`enum`

Type for paper access type.

**Cases:**

- `commenter`
- `editor`
- `viewer`
- `other`

### PaperAdminExportStartDetails

`class`

Exported all team Paper docs.

### PaperAdminExportStartType

`class`

Type for paper admin export start type.

**Properties:**

- `description_`: `String`

### PaperChangeDeploymentPolicyDetails

`class`

Changed whether Dropbox Paper, when enabled, is deployed to all members or to specific members.

**Properties:**

- `newValue`: `TeamPolicies.PaperDeploymentPolicy` - New Dropbox Paper deployment policy.
- `previousValue`: `TeamPolicies.PaperDeploymentPolicy?` - Previous Dropbox Paper deployment policy. Might be missing due to historical data gap.

### PaperChangeDeploymentPolicyType

`class`

Type for paper change deployment policy type.

**Properties:**

- `description_`: `String`

### PaperChangeMemberLinkPolicyDetails

`class`

Changed whether non-members can view Paper docs with link.

**Properties:**

- `newValue`: `TeamLog.PaperMemberPolicy` - New paper external link accessibility policy.

### PaperChangeMemberLinkPolicyType

`class`

Type for paper change member link policy type.

**Properties:**

- `description_`: `String`

### PaperChangeMemberPolicyDetails

`class`

anyone by default.

**Properties:**

- `newValue`: `TeamLog.PaperMemberPolicy` - New paper external accessibility policy.
- `previousValue`: `TeamLog.PaperMemberPolicy?` - Previous paper external accessibility policy. Might be missing due to historical data gap.

### PaperChangeMemberPolicyType

`class`

Type for paper change member policy type.

**Properties:**

- `description_`: `String`

### PaperChangePolicyDetails

`class`

Enabled/disabled Dropbox Paper for team.

**Properties:**

- `newValue`: `TeamPolicies.PaperEnabledPolicy` - New Dropbox Paper policy.
- `previousValue`: `TeamPolicies.PaperEnabledPolicy?` - Previous Dropbox Paper policy. Might be missing due to historical data gap.

### PaperChangePolicyType

`class`

Type for paper change policy type.

**Properties:**

- `description_`: `String`

### PaperContentAddMemberDetails

`class`

Added users and/or groups to Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentAddMemberType

`class`

Type for paper content add member type.

**Properties:**

- `description_`: `String`

### PaperContentAddToFolderDetails

`class`

Added Paper doc/folder to folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `parentAssetIndex`: `UInt64` - Parent asset position in the Assets list.

### PaperContentAddToFolderType

`class`

Type for paper content add to folder type.

**Properties:**

- `description_`: `String`

### PaperContentArchiveDetails

`class`

Archived Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentArchiveType

`class`

Type for paper content archive type.

**Properties:**

- `description_`: `String`

### PaperContentCreateDetails

`class`

Created Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentCreateType

`class`

Type for paper content create type.

**Properties:**

- `description_`: `String`

### PaperContentPermanentlyDeleteDetails

`class`

Permanently deleted Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentPermanentlyDeleteType

`class`

Type for paper content permanently delete type.

**Properties:**

- `description_`: `String`

### PaperContentRemoveFromFolderDetails

`class`

Removed Paper doc/folder from folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `targetAssetIndex`: `UInt64?` - Target asset position in the Assets list.
- `parentAssetIndex`: `UInt64?` - Parent asset position in the Assets list.

### PaperContentRemoveFromFolderType

`class`

Type for paper content remove from folder type.

**Properties:**

- `description_`: `String`

### PaperContentRemoveMemberDetails

`class`

Removed users and/or groups from Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentRemoveMemberType

`class`

Type for paper content remove member type.

**Properties:**

- `description_`: `String`

### PaperContentRenameDetails

`class`

Renamed Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentRenameType

`class`

Type for paper content rename type.

**Properties:**

- `description_`: `String`

### PaperContentRestoreDetails

`class`

Restored archived Paper doc/folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperContentRestoreType

`class`

Type for paper content restore type.

**Properties:**

- `description_`: `String`

### PaperDefaultFolderPolicy

`enum`

Policy to set default access for newly created Paper folders.

**Cases:**

- `everyoneInTeam`
- `inviteOnly`
- `other`

### PaperDefaultFolderPolicyChangedDetails

`class`

Changed Paper Default Folder Policy setting for team.

**Properties:**

- `newValue`: `TeamLog.PaperDefaultFolderPolicy` - New Paper Default Folder Policy.
- `previousValue`: `TeamLog.PaperDefaultFolderPolicy` - Previous Paper Default Folder Policy.

### PaperDefaultFolderPolicyChangedType

`class`

Type for paper default folder policy changed type.

**Properties:**

- `description_`: `String`

### PaperDesktopPolicy

`enum`

Policy for controlling if team members can use Paper Desktop

**Cases:**

- `disabled`
- `enabled`
- `other`

### PaperDesktopPolicyChangedDetails

`class`

Enabled/disabled Paper Desktop for team.

**Properties:**

- `newValue`: `TeamLog.PaperDesktopPolicy` - New Paper Desktop policy.
- `previousValue`: `TeamLog.PaperDesktopPolicy` - Previous Paper Desktop policy.

### PaperDesktopPolicyChangedType

`class`

Type for paper desktop policy changed type.

**Properties:**

- `description_`: `String`

### PaperDocAddCommentDetails

`class`

Added Paper doc comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### PaperDocAddCommentType

`class`

Type for paper doc add comment type.

**Properties:**

- `description_`: `String`

### PaperDocChangeMemberRoleDetails

`class`

Changed member permissions for Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `accessType`: `TeamLog.PaperAccessType` - Paper doc access type.

### PaperDocChangeMemberRoleType

`class`

Type for paper doc change member role type.

**Properties:**

- `description_`: `String`

### PaperDocChangeSharingPolicyDetails

`class`

Changed sharing setting for Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `publicSharingPolicy`: `String?` - Sharing policy with external users.
- `teamSharingPolicy`: `String?` - Sharing policy with team.

### PaperDocChangeSharingPolicyType

`class`

Type for paper doc change sharing policy type.

**Properties:**

- `description_`: `String`

### PaperDocChangeSubscriptionDetails

`class`

Followed/unfollowed Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `newSubscriptionLevel`: `String` - New doc subscription level.
- `previousSubscriptionLevel`: `String?` - Previous doc subscription level. Might be missing due to historical data gap.

### PaperDocChangeSubscriptionType

`class`

Type for paper doc change subscription type.

**Properties:**

- `description_`: `String`

### PaperDocDeleteCommentDetails

`class`

Deleted Paper doc comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### PaperDocDeleteCommentType

`class`

Type for paper doc delete comment type.

**Properties:**

- `description_`: `String`

### PaperDocDeletedDetails

`class`

Archived Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocDeletedType

`class`

Type for paper doc deleted type.

**Properties:**

- `description_`: `String`

### PaperDocDownloadDetails

`class`

Downloaded Paper doc in specific format.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `exportFileFormat`: `TeamLog.PaperDownloadFormat` - Export file format.

### PaperDocDownloadType

`class`

Type for paper doc download type.

**Properties:**

- `description_`: `String`

### PaperDocEditCommentDetails

`class`

Edited Paper doc comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### PaperDocEditCommentType

`class`

Type for paper doc edit comment type.

**Properties:**

- `description_`: `String`

### PaperDocEditDetails

`class`

Edited Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocEditType

`class`

Type for paper doc edit type.

**Properties:**

- `description_`: `String`

### PaperDocFollowedDetails

`class`

Followed Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocFollowedType

`class`

Type for paper doc followed type.

**Properties:**

- `description_`: `String`

### PaperDocMentionDetails

`class`

Mentioned user in Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocMentionType

`class`

Type for paper doc mention type.

**Properties:**

- `description_`: `String`

### PaperDocOwnershipChangedDetails

`class`

Transferred ownership of Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `oldOwnerUserId`: `String?` - Previous owner.
- `newOwnerUserId`: `String` - New owner.

### PaperDocOwnershipChangedType

`class`

Type for paper doc ownership changed type.

**Properties:**

- `description_`: `String`

### PaperDocRequestAccessDetails

`class`

Requested access to Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocRequestAccessType

`class`

Type for paper doc request access type.

**Properties:**

- `description_`: `String`

### PaperDocResolveCommentDetails

`class`

Resolved Paper doc comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### PaperDocResolveCommentType

`class`

Type for paper doc resolve comment type.

**Properties:**

- `description_`: `String`

### PaperDocRevertDetails

`class`

Restored Paper doc to previous version.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocRevertType

`class`

Type for paper doc revert type.

**Properties:**

- `description_`: `String`

### PaperDocSlackShareDetails

`class`

Shared Paper doc via Slack.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocSlackShareType

`class`

Type for paper doc slack share type.

**Properties:**

- `description_`: `String`

### PaperDocTeamInviteDetails

`class`

Shared Paper doc with users and/or groups.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocTeamInviteType

`class`

Type for paper doc team invite type.

**Properties:**

- `description_`: `String`

### PaperDocTrashedDetails

`class`

Deleted Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocTrashedType

`class`

Type for paper doc trashed type.

**Properties:**

- `description_`: `String`

### PaperDocUnresolveCommentDetails

`class`

Unresolved Paper doc comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### PaperDocUnresolveCommentType

`class`

Type for paper doc unresolve comment type.

**Properties:**

- `description_`: `String`

### PaperDocUntrashedDetails

`class`

Restored Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocUntrashedType

`class`

Type for paper doc untrashed type.

**Properties:**

- `description_`: `String`

### PaperDocViewDetails

`class`

Viewed Paper doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperDocViewType

`class`

Type for paper doc view type.

**Properties:**

- `description_`: `String`

### PaperDocumentLogInfo

`class`

Paper document's logged information.

**Properties:**

- `docId`: `String` - Papers document Id.
- `docTitle`: `String` - Paper document title.

### PaperDownloadFormat

`enum`

Type for paper download format.

**Cases:**

- `docx`
- `html`
- `markdown`
- `pdf`
- `other`

### PaperEnabledUsersGroupAdditionDetails

`class`

Added users to Paper-enabled users list.

### PaperEnabledUsersGroupAdditionType

`class`

Type for paper enabled users group addition type.

**Properties:**

- `description_`: `String`

### PaperEnabledUsersGroupRemovalDetails

`class`

Removed users from Paper-enabled users list.

### PaperEnabledUsersGroupRemovalType

`class`

Type for paper enabled users group removal type.

**Properties:**

- `description_`: `String`

### PaperExternalViewAllowDetails

`class`

Changed Paper external sharing setting to anyone.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperExternalViewAllowType

`class`

Type for paper external view allow type.

**Properties:**

- `description_`: `String`

### PaperExternalViewDefaultTeamDetails

`class`

Changed Paper external sharing setting to default team.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperExternalViewDefaultTeamType

`class`

Type for paper external view default team type.

**Properties:**

- `description_`: `String`

### PaperExternalViewForbidDetails

`class`

Changed Paper external sharing setting to team-only.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperExternalViewForbidType

`class`

Type for paper external view forbid type.

**Properties:**

- `description_`: `String`

### PaperFolderChangeSubscriptionDetails

`class`

Followed/unfollowed Paper folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `newSubscriptionLevel`: `String` - New folder subscription level.
- `previousSubscriptionLevel`: `String?` - Previous folder subscription level. Might be missing due to historical data gap.

### PaperFolderChangeSubscriptionType

`class`

Type for paper folder change subscription type.

**Properties:**

- `description_`: `String`

### PaperFolderDeletedDetails

`class`

Archived Paper folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperFolderDeletedType

`class`

Type for paper folder deleted type.

**Properties:**

- `description_`: `String`

### PaperFolderFollowedDetails

`class`

Followed Paper folder.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperFolderFollowedType

`class`

Type for paper folder followed type.

**Properties:**

- `description_`: `String`

### PaperFolderLogInfo

`class`

Paper folder's logged information.

**Properties:**

- `folderId`: `String` - Papers folder Id.
- `folderName`: `String` - Paper folder name.

### PaperFolderTeamInviteDetails

`class`

Shared Paper folder with users and/or groups.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperFolderTeamInviteType

`class`

Type for paper folder team invite type.

**Properties:**

- `description_`: `String`

### PaperMemberPolicy

`enum`

Policy for controlling if team members can share Paper documents externally.

**Cases:**

- `anyoneWithLink`
- `onlyTeam`
- `teamAndExplicitlyShared`
- `other`

### PaperPublishedLinkChangePermissionDetails

`class`

Changed permissions for published doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `newPermissionLevel`: `String` - New permission level.
- `previousPermissionLevel`: `String` - Previous permission level.

### PaperPublishedLinkChangePermissionType

`class`

Type for paper published link change permission type.

**Properties:**

- `description_`: `String`

### PaperPublishedLinkCreateDetails

`class`

Published doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperPublishedLinkCreateType

`class`

Type for paper published link create type.

**Properties:**

- `description_`: `String`

### PaperPublishedLinkDisabledDetails

`class`

Unpublished doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperPublishedLinkDisabledType

`class`

Type for paper published link disabled type.

**Properties:**

- `description_`: `String`

### PaperPublishedLinkViewDetails

`class`

Viewed published doc.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### PaperPublishedLinkViewType

`class`

Type for paper published link view type.

**Properties:**

- `description_`: `String`

---

## Password & Security

### PasswordChangeDetails

`class`

Changed password.

### PasswordChangeType

`class`

Type for password change type.

**Properties:**

- `description_`: `String`

### PasswordResetAllDetails

`class`

Reset all team member passwords.

### PasswordResetAllType

`class`

Type for password reset all type.

**Properties:**

- `description_`: `String`

### PasswordResetDetails

`class`

Reset password.

### PasswordResetType

`class`

Type for password reset type.

**Properties:**

- `description_`: `String`

### PasswordStrengthRequirementsChangePolicyDetails

`class`

Changed team password strength requirements.

**Properties:**

- `previousValue`: `TeamPolicies.PasswordStrengthPolicy` - Old password strength policy.
- `newValue`: `TeamPolicies.PasswordStrengthPolicy` - New password strength policy.

### PasswordStrengthRequirementsChangePolicyType

`class`

Type for password strength requirements change policy type.

**Properties:**

- `description_`: `String`

### TfaAddBackupPhoneDetails

`class`

Added backup phone for two-step verification.

### TfaAddBackupPhoneType

`class`

Type for tfa add backup phone type.

**Properties:**

- `description_`: `String`

### TfaAddExceptionDetails

`class`

Added members to two factor authentication exception list.

### TfaAddExceptionType

`class`

Type for tfa add exception type.

**Properties:**

- `description_`: `String`

### TfaAddSecurityKeyDetails

`class`

Added security key for two-step verification.

### TfaAddSecurityKeyType

`class`

Type for tfa add security key type.

**Properties:**

- `description_`: `String`

### TfaChangeBackupPhoneDetails

`class`

Changed backup phone for two-step verification.

### TfaChangeBackupPhoneType

`class`

Type for tfa change backup phone type.

**Properties:**

- `description_`: `String`

### TfaChangePolicyDetails

`class`

Changed two-step verification setting for team.

**Properties:**

- `newValue`: `TeamPolicies.TwoStepVerificationPolicy` - New change policy.
- `previousValue`: `TeamPolicies.TwoStepVerificationPolicy?` - Previous change policy. Might be missing due to historical data gap.

### TfaChangePolicyType

`class`

Type for tfa change policy type.

**Properties:**

- `description_`: `String`

### TfaChangeStatusDetails

`class`

Enabled/disabled/changed two-step verification setting.

**Properties:**

- `newValue`: `TeamLog.TfaConfiguration` - The new two factor authentication configuration.
- `previousValue`: `TeamLog.TfaConfiguration?` - The previous two factor authentication configuration. Might be missing due to historical data gap.
- `usedRescueCode`: `Bool?` - configuration is disabled.

### TfaChangeStatusType

`class`

Type for tfa change status type.

**Properties:**

- `description_`: `String`

### TfaConfiguration

`enum`

Two factor authentication configuration. Note: the enabled option is deprecated.

**Cases:**

- `authenticator`
- `disabled`
- `enabled`
- `sms`
- `other`

### TfaRemoveBackupPhoneDetails

`class`

Removed backup phone for two-step verification.

### TfaRemoveBackupPhoneType

`class`

Type for tfa remove backup phone type.

**Properties:**

- `description_`: `String`

### TfaRemoveExceptionDetails

`class`

Removed members from two factor authentication exception list.

### TfaRemoveExceptionType

`class`

Type for tfa remove exception type.

**Properties:**

- `description_`: `String`

### TfaRemoveSecurityKeyDetails

`class`

Removed security key for two-step verification.

### TfaRemoveSecurityKeyType

`class`

Type for tfa remove security key type.

**Properties:**

- `description_`: `String`

### TfaResetDetails

`class`

Reset two-step verification for team member.

### TfaResetType

`class`

Type for tfa reset type.

**Properties:**

- `description_`: `String`

---

## Policy Types

### ChangeLinkExpirationPolicy

`enum`

link is updated

**Cases:**

- `allowed`
- `notAllowed`
- `other`

### DataPlacementRestrictionChangePolicyDetails

`class`

Set restrictions on data center locations where team data resides.

**Properties:**

- `previousValue`: `TeamLog.PlacementRestriction` - Previous placement restriction.
- `newValue`: `TeamLog.PlacementRestriction` - New placement restriction.

### DataPlacementRestrictionChangePolicyType

`class`

Type for data placement restriction change policy type.

**Properties:**

- `description_`: `String`

### DataPlacementRestrictionSatisfyPolicyDetails

`class`

Completed restrictions on data center locations where team data resides.

**Properties:**

- `placementRestriction`: `TeamLog.PlacementRestriction` - Placement restriction.

### DataPlacementRestrictionSatisfyPolicyType

`class`

Type for data placement restriction satisfy policy type.

**Properties:**

- `description_`: `String`

### DefaultLinkExpirationDaysPolicy

`enum`

Policy for the default number of days until an externally shared link expires

**Cases:**

- `day1`
- `day180`
- `day3`
- `day30`
- `day7`
- `day90`
- `none`
- `year1`
- `other`

### DownloadPolicyType

`enum`

Shared content downloads policy

**Cases:**

- `allow`
- `disallow`
- `other`

### EnforceLinkPasswordPolicy

`enum`

Policy for deciding whether password must be enforced when an externally shared link is updated

**Cases:**

- `optional`
- `required`
- `other`

### ExtendedVersionHistoryChangePolicyDetails

`class`

Accepted/opted out of extended version history.

**Properties:**

- `newValue`: `TeamLog.ExtendedVersionHistoryPolicy` - New extended version history policy.
- `previousValue`: `TeamLog.ExtendedVersionHistoryPolicy?` - Previous extended version history policy. Might be missing due to historical data gap.

### ExtendedVersionHistoryChangePolicyType

`class`

Type for extended version history change policy type.

**Properties:**

- `description_`: `String`

### ExtendedVersionHistoryPolicy

`enum`

Type for extended version history policy.

**Cases:**

- `explicitlyLimited`
- `explicitlyUnlimited`
- `implicitlyLimited`
- `implicitlyUnlimited`
- `other`

### GovernancePolicyAddFolderFailedDetails

`class`

Couldn't add a folder to a policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `folder`: `String` - Folder.
- `reason`: `String?` - Reason.

### GovernancePolicyAddFolderFailedType

`class`

Type for governance policy add folder failed type.

**Properties:**

- `description_`: `String`

### GovernancePolicyAddFoldersDetails

`class`

Added folders to policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `folders`: `[String]?` - Folders.

### GovernancePolicyAddFoldersType

`class`

Type for governance policy add folders type.

**Properties:**

- `description_`: `String`

### GovernancePolicyContentDisposedDetails

`class`

Content disposed.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `dispositionType`: `TeamLog.DispositionActionType` - Disposition type.

### GovernancePolicyContentDisposedType

`class`

Type for governance policy content disposed type.

**Properties:**

- `description_`: `String`

### GovernancePolicyCreateDetails

`class`

Activated a new policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `duration`: `TeamLog.DurationLogInfo` - Duration in days.
- `folders`: `[String]?` - Folders.

### GovernancePolicyCreateType

`class`

Type for governance policy create type.

**Properties:**

- `description_`: `String`

### GovernancePolicyDeleteDetails

`class`

Deleted a policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.

### GovernancePolicyDeleteType

`class`

Type for governance policy delete type.

**Properties:**

- `description_`: `String`

### GovernancePolicyEditDetailsDetails

`class`

Edited policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `attribute`: `String` - Attribute.
- `previousValue`: `String` - From.
- `newValue`: `String` - To.

### GovernancePolicyEditDetailsType

`class`

Type for governance policy edit details type.

**Properties:**

- `description_`: `String`

### GovernancePolicyEditDurationDetails

`class`

Changed policy duration.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `previousValue`: `TeamLog.DurationLogInfo` - From.
- `newValue`: `TeamLog.DurationLogInfo` - To.

### GovernancePolicyEditDurationType

`class`

Type for governance policy edit duration type.

**Properties:**

- `description_`: `String`

### GovernancePolicyExportCreatedDetails

`class`

Created a policy download.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `exportName`: `String` - Export name.

### GovernancePolicyExportCreatedType

`class`

Type for governance policy export created type.

**Properties:**

- `description_`: `String`

### GovernancePolicyExportRemovedDetails

`class`

Removed a policy download.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `exportName`: `String` - Export name.

### GovernancePolicyExportRemovedType

`class`

Type for governance policy export removed type.

**Properties:**

- `description_`: `String`

### GovernancePolicyRemoveFoldersDetails

`class`

Removed folders from policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `folders`: `[String]?` - Folders.
- `reason`: `String?` - Reason.

### GovernancePolicyRemoveFoldersType

`class`

Type for governance policy remove folders type.

**Properties:**

- `description_`: `String`

### GovernancePolicyReportCreatedDetails

`class`

Created a summary report for a policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.

### GovernancePolicyReportCreatedType

`class`

Type for governance policy report created type.

**Properties:**

- `description_`: `String`

### GovernancePolicyZipPartDownloadedDetails

`class`

Downloaded content from a policy.

**Properties:**

- `governancePolicyId`: `String` - Policy ID.
- `name`: `String` - Policy name.
- `policyType`: `TeamLog.PolicyType?` - Policy type.
- `exportName`: `String` - Export name.
- `part`: `String?` - Part.

### GovernancePolicyZipPartDownloadedType

`class`

Type for governance policy zip part downloaded type.

**Properties:**

- `description_`: `String`

### MicrosoftOfficeAddinChangePolicyDetails

`class`

Enabled/disabled Microsoft Office add-in.

**Properties:**

- `newValue`: `TeamLog.MicrosoftOfficeAddinPolicy` - New Microsoft Office addin policy.
- `previousValue`: `TeamLog.MicrosoftOfficeAddinPolicy?` - Previous Microsoft Office addin policy. Might be missing due to historical data gap.

### MicrosoftOfficeAddinChangePolicyType

`class`

Type for microsoft office addin change policy type.

**Properties:**

- `description_`: `String`

### MicrosoftOfficeAddinPolicy

`enum`

Microsoft Office addin policy

**Cases:**

- `disabled`
- `enabled`
- `other`

### PassPolicy

`enum`

Type for pass policy.

**Cases:**

- `allow`
- `disabled`
- `enabled`
- `other`

### PermanentDeleteChangePolicyDetails

`class`

Enabled/disabled ability of team members to permanently delete content.

**Properties:**

- `newValue`: `TeamLog.ContentPermanentDeletePolicy` - New permanent delete content policy.
- `previousValue`: `TeamLog.ContentPermanentDeletePolicy?` - Previous permanent delete content policy. Might be missing due to historical data gap.

### PermanentDeleteChangePolicyType

`class`

Type for permanent delete change policy type.

**Properties:**

- `description_`: `String`

### PolicyType

`enum`

Type for policy type.

**Cases:**

- `disposition`
- `retention`
- `other`

### ResellerSupportChangePolicyDetails

`class`

Enabled/disabled reseller support.

**Properties:**

- `newValue`: `TeamLog.ResellerSupportPolicy` - New Reseller support policy.
- `previousValue`: `TeamLog.ResellerSupportPolicy` - Previous Reseller support policy.

### ResellerSupportChangePolicyType

`class`

Type for reseller support change policy type.

**Properties:**

- `description_`: `String`

### ResellerSupportPolicy

`enum`

Policy for controlling if reseller can access the admin console as administrator

**Cases:**

- `disabled`
- `enabled`
- `other`

### RewindPolicy

`enum`

Policy for controlling whether team members can rewind

**Cases:**

- `adminsOnly`
- `everyone`
- `other`

### RewindPolicyChangedDetails

`class`

Changed Rewind policy for team.

**Properties:**

- `newValue`: `TeamLog.RewindPolicy` - New Dropbox Rewind policy.
- `previousValue`: `TeamLog.RewindPolicy` - Previous Dropbox Rewind policy.

### RewindPolicyChangedType

`class`

Type for rewind policy changed type.

**Properties:**

- `description_`: `String`

### SecondaryMailsPolicy

`enum`

Type for secondary mails policy.

**Cases:**

- `disabled`
- `enabled`
- `other`

### SecondaryMailsPolicyChangedDetails

`class`

Secondary mails policy changed.

**Properties:**

- `previousValue`: `TeamLog.SecondaryMailsPolicy` - Previous secondary mails policy.
- `newValue`: `TeamLog.SecondaryMailsPolicy` - New secondary mails policy.

### SecondaryMailsPolicyChangedType

`class`

Type for secondary mails policy changed type.

**Properties:**

- `description_`: `String`

### SendForSignaturePolicy

`enum`

Policy for controlling team access to send for signature feature

**Cases:**

- `disabled`
- `enabled`
- `other`

### SendForSignaturePolicyChangedDetails

`class`

Changed send for signature policy for team.

**Properties:**

- `newValue`: `TeamLog.SendForSignaturePolicy` - New send for signature policy.
- `previousValue`: `TeamLog.SendForSignaturePolicy` - Previous send for signature policy.

### SendForSignaturePolicyChangedType

`class`

Type for send for signature policy changed type.

**Properties:**

- `description_`: `String`

### ShowcaseChangeDownloadPolicyDetails

`class`

Enabled/disabled downloading files from Dropbox Showcase for team.

**Properties:**

- `newValue`: `TeamLog.ShowcaseDownloadPolicy` - New Dropbox Showcase download policy.
- `previousValue`: `TeamLog.ShowcaseDownloadPolicy` - Previous Dropbox Showcase download policy.

### ShowcaseChangeDownloadPolicyType

`class`

Type for showcase change download policy type.

**Properties:**

- `description_`: `String`

### ShowcaseChangeEnabledPolicyDetails

`class`

Enabled/disabled Dropbox Showcase for team.

**Properties:**

- `newValue`: `TeamLog.ShowcaseEnabledPolicy` - New Dropbox Showcase policy.
- `previousValue`: `TeamLog.ShowcaseEnabledPolicy` - Previous Dropbox Showcase policy.

### ShowcaseChangeEnabledPolicyType

`class`

Type for showcase change enabled policy type.

**Properties:**

- `description_`: `String`

### ShowcaseChangeExternalSharingPolicyDetails

`class`

Enabled/disabled sharing Dropbox Showcase externally for team.

**Properties:**

- `newValue`: `TeamLog.ShowcaseExternalSharingPolicy` - New Dropbox Showcase external sharing policy.
- `previousValue`: `TeamLog.ShowcaseExternalSharingPolicy` - Previous Dropbox Showcase external sharing policy.

### ShowcaseChangeExternalSharingPolicyType

`class`

Type for showcase change external sharing policy type.

**Properties:**

- `description_`: `String`

### ShowcaseDownloadPolicy

`enum`

Policy for controlling if files can be downloaded from Showcases by team members

**Cases:**

- `disabled`
- `enabled`
- `other`

### ShowcaseEnabledPolicy

`enum`

Policy for controlling whether Showcase is enabled.

**Cases:**

- `disabled`
- `enabled`
- `other`

### ShowcaseExternalSharingPolicy

`enum`

Policy for controlling if team members can share Showcases externally.

**Cases:**

- `disabled`
- `enabled`
- `other`

### SmartSyncChangePolicyDetails

`class`

Changed default Smart Sync setting for team members.

**Properties:**

- `newValue`: `TeamPolicies.SmartSyncPolicy?` - New smart sync policy.
- `previousValue`: `TeamPolicies.SmartSyncPolicy?` - Previous smart sync policy.

### SmartSyncChangePolicyType

`class`

Type for smart sync change policy type.

**Properties:**

- `description_`: `String`

### SmartSyncOptOutPolicy

`enum`

Type for smart sync opt out policy.

**Cases:**

- `default_`
- `optedOut`
- `other`

### SmarterSmartSyncPolicyChangedDetails

`class`

Changed automatic Smart Sync setting for team.

**Properties:**

- `previousValue`: `TeamPolicies.SmarterSmartSyncPolicyState` - Previous automatic Smart Sync setting.
- `newValue`: `TeamPolicies.SmarterSmartSyncPolicyState` - New automatic Smart Sync setting.

### SmarterSmartSyncPolicyChangedType

`class`

Type for smarter smart sync policy changed type.

**Properties:**

- `description_`: `String`

### SsoChangePolicyDetails

`class`

Changed single sign-on setting for team.

**Properties:**

- `newValue`: `TeamPolicies.SsoPolicy` - New single sign-on policy.
- `previousValue`: `TeamPolicies.SsoPolicy?` - Previous single sign-on policy. Might be missing due to historical data gap.

### SsoChangePolicyType

`class`

Type for sso change policy type.

**Properties:**

- `description_`: `String`

### TeamBrandingPolicy

`enum`

Policy for controlling team access to setting up branding feature

**Cases:**

- `disabled`
- `enabled`
- `other`

### TeamBrandingPolicyChangedDetails

`class`

Changed team branding policy for team.

**Properties:**

- `newValue`: `TeamLog.TeamBrandingPolicy` - New team branding policy.
- `previousValue`: `TeamLog.TeamBrandingPolicy` - Previous team branding policy.

### TeamBrandingPolicyChangedType

`class`

Type for team branding policy changed type.

**Properties:**

- `description_`: `String`

### TeamExtensionsPolicy

`enum`

Policy for controlling whether App Integrations are enabled for the team.

**Cases:**

- `disabled`
- `enabled`
- `other`

### TeamExtensionsPolicyChangedDetails

`class`

Changed App Integrations setting for team.

**Properties:**

- `newValue`: `TeamLog.TeamExtensionsPolicy` - New Extensions policy.
- `previousValue`: `TeamLog.TeamExtensionsPolicy` - Previous Extensions policy.

### TeamExtensionsPolicyChangedType

`class`

Type for team extensions policy changed type.

**Properties:**

- `description_`: `String`

### TeamSelectiveSyncPolicy

`enum`

Policy for controlling whether team selective sync is enabled for team.

**Cases:**

- `disabled`
- `enabled`
- `other`

### TeamSelectiveSyncPolicyChangedDetails

`class`

Enabled/disabled Team Selective Sync for team.

**Properties:**

- `newValue`: `TeamLog.TeamSelectiveSyncPolicy` - New Team Selective Sync policy.
- `previousValue`: `TeamLog.TeamSelectiveSyncPolicy` - Previous Team Selective Sync policy.

### TeamSelectiveSyncPolicyChangedType

`class`

Type for team selective sync policy changed type.

**Properties:**

- `description_`: `String`

### TwoAccountChangePolicyDetails

`class`

Enabled/disabled option for members to link personal Dropbox account and team account to same computer.

**Properties:**

- `newValue`: `TeamLog.TwoAccountPolicy` - New two account policy.
- `previousValue`: `TeamLog.TwoAccountPolicy?` - Previous two account policy. Might be missing due to historical data gap.

### TwoAccountChangePolicyType

`class`

Type for two account change policy type.

**Properties:**

- `description_`: `String`

### TwoAccountPolicy

`enum`

Policy for pairing personal account to work account

**Cases:**

- `disabled`
- `enabled`
- `other`

### ViewerInfoPolicyChangedDetails

`class`

Changed team policy for viewer info.

**Properties:**

- `previousValue`: `TeamLog.PassPolicy` - Previous Viewer Info policy.
- `newValue`: `TeamLog.PassPolicy` - New Viewer Info policy.

### ViewerInfoPolicyChangedType

`class`

Type for viewer info policy changed type.

**Properties:**

- `description_`: `String`

### WatermarkingPolicy

`enum`

Policy for controlling team access to watermarking feature

**Cases:**

- `disabled`
- `enabled`
- `other`

### WatermarkingPolicyChangedDetails

`class`

Changed watermarking policy for team.

**Properties:**

- `newValue`: `TeamLog.WatermarkingPolicy` - New watermarking policy.
- `previousValue`: `TeamLog.WatermarkingPolicy` - Previous watermarking policy.

### WatermarkingPolicyChangedType

`class`

Type for watermarking policy changed type.

**Properties:**

- `description_`: `String`

### WebSessionsChangeFixedLengthPolicyDetails

`class`

Changed how long members can stay signed in to Dropbox.com.

**Properties:**

- `newValue`: `TeamLog.WebSessionsFixedLengthPolicy?` - New session length policy. Might be missing due to historical data gap.
- `previousValue`: `TeamLog.WebSessionsFixedLengthPolicy?` - Previous session length policy. Might be missing due to historical data gap.

### WebSessionsChangeFixedLengthPolicyType

`class`

Type for web sessions change fixed length policy type.

**Properties:**

- `description_`: `String`

### WebSessionsChangeIdleLengthPolicyDetails

`class`

Changed how long team members can be idle while signed in to Dropbox.com.

**Properties:**

- `newValue`: `TeamLog.WebSessionsIdleLengthPolicy?` - New idle length policy. Might be missing due to historical data gap.
- `previousValue`: `TeamLog.WebSessionsIdleLengthPolicy?` - Previous idle length policy. Might be missing due to historical data gap.

### WebSessionsChangeIdleLengthPolicyType

`class`

Type for web sessions change idle length policy type.

**Properties:**

- `description_`: `String`

### WebSessionsFixedLengthPolicy

`enum`

Web sessions fixed length policy.

**Cases:**

- `defined` - Defined fixed session length.
- `undefined` - Undefined fixed session length.
- `other`

### WebSessionsIdleLengthPolicy

`enum`

Web sessions idle length policy.

**Cases:**

- `defined` - Defined idle session length.
- `undefined` - Undefined idle session length.
- `other`

---

## Ransomware & Threat

### RansomwareAlertCreateReportDetails

`class`

Created ransomware report.

### RansomwareAlertCreateReportFailedDetails

`class`

Couldn't generate ransomware report.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### RansomwareAlertCreateReportFailedType

`class`

Type for ransomware alert create report failed type.

**Properties:**

- `description_`: `String`

### RansomwareAlertCreateReportType

`class`

Type for ransomware alert create report type.

**Properties:**

- `description_`: `String`

### RansomwareRestoreProcessCompletedDetails

`class`

Completed ransomware restore process.

**Properties:**

- `status`: `String` - The status of the restore process.
- `restoredFilesCount`: `Int64` - Restored files count.
- `restoredFilesFailedCount`: `Int64` - Restored files failed count.

### RansomwareRestoreProcessCompletedType

`class`

Type for ransomware restore process completed type.

**Properties:**

- `description_`: `String`

### RansomwareRestoreProcessStartedDetails

`class`

Started ransomware restore process.

**Properties:**

- `extension_`: `String` - Ransomware filename extension.

### RansomwareRestoreProcessStartedType

`class`

Type for ransomware restore process started type.

**Properties:**

- `description_`: `String`

---

## Reseller & Support

### ResellerLogInfo

`class`

Reseller information.

**Properties:**

- `resellerName`: `String` - Reseller name.
- `resellerEmail`: `String` - Reseller email.

### ResellerRole

`enum`

Type for reseller role.

**Cases:**

- `notReseller`
- `resellerAdmin`
- `other`

### ResellerSupportSessionEndDetails

`class`

Ended reseller support session.

### ResellerSupportSessionEndType

`class`

Type for reseller support session end type.

**Properties:**

- `description_`: `String`

### ResellerSupportSessionStartDetails

`class`

Started reseller support session.

### ResellerSupportSessionStartType

`class`

Type for reseller support session start type.

**Properties:**

- `description_`: `String`

---

## Shared Folder & Link Model Operations

### SfAddGroupDetails

`class`

Added team to shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `sharingPermission`: `String?` - Sharing permission.
- `teamName`: `String` - Team name.

### SfAddGroupType

`class`

Type for sf add group type.

**Properties:**

- `description_`: `String`

### SfAllowNonMembersToViewSharedLinksDetails

`class`

Allowed non-collaborators to view links to files in shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `sharedFolderType`: `String?` - Shared folder type.

### SfAllowNonMembersToViewSharedLinksType

`class`

Type for sf allow non members to view shared links type.

**Properties:**

- `description_`: `String`

### SfExternalInviteWarnDetails

`class`

Set team members to see warning before sharing folders outside team.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `newSharingPermission`: `String?` - New sharing permission.
- `previousSharingPermission`: `String?` - Previous sharing permission.

### SfExternalInviteWarnType

`class`

Type for sf external invite warn type.

**Properties:**

- `description_`: `String`

### SfFbInviteChangeRoleDetails

`class`

Changed Facebook user's role in shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `previousSharingPermission`: `String?` - Previous sharing permission.
- `newSharingPermission`: `String?` - New sharing permission.

### SfFbInviteChangeRoleType

`class`

Type for sf fb invite change role type.

**Properties:**

- `description_`: `String`

### SfFbInviteDetails

`class`

Invited Facebook users to shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `sharingPermission`: `String?` - Sharing permission.

### SfFbInviteType

`class`

Type for sf fb invite type.

**Properties:**

- `description_`: `String`

### SfFbUninviteDetails

`class`

Uninvited Facebook user from shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.

### SfFbUninviteType

`class`

Type for sf fb uninvite type.

**Properties:**

- `description_`: `String`

### SfInviteGroupDetails

`class`

Invited group to shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.

### SfInviteGroupType

`class`

Type for sf invite group type.

**Properties:**

- `description_`: `String`

### SfTeamGrantAccessDetails

`class`

Granted access to shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.

### SfTeamGrantAccessType

`class`

Type for sf team grant access type.

**Properties:**

- `description_`: `String`

### SfTeamInviteChangeRoleDetails

`class`

Changed team member's role in shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `newSharingPermission`: `String?` - New sharing permission.
- `previousSharingPermission`: `String?` - Previous sharing permission.

### SfTeamInviteChangeRoleType

`class`

Type for sf team invite change role type.

**Properties:**

- `description_`: `String`

### SfTeamInviteDetails

`class`

Invited team members to shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `sharingPermission`: `String?` - Sharing permission.

### SfTeamInviteType

`class`

Type for sf team invite type.

**Properties:**

- `description_`: `String`

### SfTeamJoinDetails

`class`

Joined team member's shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.

### SfTeamJoinFromOobLinkDetails

`class`

Joined team member's shared folder from link.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.
- `tokenKey`: `String?` - Shared link token key.
- `sharingPermission`: `String?` - Sharing permission.

### SfTeamJoinFromOobLinkType

`class`

Type for sf team join from oob link type.

**Properties:**

- `description_`: `String`

### SfTeamJoinType

`class`

Type for sf team join type.

**Properties:**

- `description_`: `String`

### SfTeamUninviteDetails

`class`

Unshared folder with team member.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.
- `originalFolderName`: `String` - Original shared folder name.

### SfTeamUninviteType

`class`

Type for sf team uninvite type.

**Properties:**

- `description_`: `String`

### ShmodelDisableDownloadsDetails

`class`

Disabled downloads for link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### ShmodelDisableDownloadsType

`class`

Type for shmodel disable downloads type.

**Properties:**

- `description_`: `String`

### ShmodelEnableDownloadsDetails

`class`

Enabled downloads for link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### ShmodelEnableDownloadsType

`class`

Type for shmodel enable downloads type.

**Properties:**

- `description_`: `String`

### ShmodelGroupShareDetails

`class`

Shared link with group.

### ShmodelGroupShareType

`class`

Type for shmodel group share type.

**Properties:**

- `description_`: `String`

---

## Shared Links

### SharedLinkAccessLevel

`enum`

Shared link access level.

**Cases:**

- `none`
- `reader`
- `writer`
- `other`

### SharedLinkAddExpiryDetails

`class`

Added shared link expiration date.

**Properties:**

- `newValue`: `Date` - New shared link expiration date.

### SharedLinkAddExpiryType

`class`

Type for shared link add expiry type.

**Properties:**

- `description_`: `String`

### SharedLinkChangeExpiryDetails

`class`

Changed shared link expiration date.

**Properties:**

- `newValue`: `Date?` - New shared link expiration date. Might be missing due to historical data gap.
- `previousValue`: `Date?` - Previous shared link expiration date. Might be missing due to historical data gap.

### SharedLinkChangeExpiryType

`class`

Type for shared link change expiry type.

**Properties:**

- `description_`: `String`

### SharedLinkChangeVisibilityDetails

`class`

Changed visibility of shared link.

**Properties:**

- `newValue`: `TeamLog.SharedLinkVisibility` - New shared link visibility.
- `previousValue`: `TeamLog.SharedLinkVisibility?` - Previous shared link visibility. Might be missing due to historical data gap.

### SharedLinkChangeVisibilityType

`class`

Type for shared link change visibility type.

**Properties:**

- `description_`: `String`

### SharedLinkCopyDetails

`class`

Added file/folder to Dropbox from shared link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### SharedLinkCopyType

`class`

Type for shared link copy type.

**Properties:**

- `description_`: `String`

### SharedLinkCreateDetails

`class`

Created shared link.

**Properties:**

- `sharedLinkAccessLevel`: `TeamLog.SharedLinkAccessLevel?` - Defines who can access the shared link. Might be missing due to historical data gap.

### SharedLinkCreateType

`class`

Type for shared link create type.

**Properties:**

- `description_`: `String`

### SharedLinkDisableDetails

`class`

Removed shared link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### SharedLinkDisableType

`class`

Type for shared link disable type.

**Properties:**

- `description_`: `String`

### SharedLinkDownloadDetails

`class`

Downloaded file/folder from shared link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### SharedLinkDownloadType

`class`

Type for shared link download type.

**Properties:**

- `description_`: `String`

### SharedLinkRemoveExpiryDetails

`class`

Removed shared link expiration date.

**Properties:**

- `previousValue`: `Date?` - Previous shared link expiration date. Might be missing due to historical data gap.

### SharedLinkRemoveExpiryType

`class`

Type for shared link remove expiry type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsAddExpirationDetails

`class`

Added an expiration date to the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.
- `newValue`: `Date?` - New shared content link expiration date. Might be missing due to historical data gap.

### SharedLinkSettingsAddExpirationType

`class`

Type for shared link settings add expiration type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsAddPasswordDetails

`class`

Added a password to the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.

### SharedLinkSettingsAddPasswordType

`class`

Type for shared link settings add password type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsAllowDownloadDisabledDetails

`class`

Disabled downloads.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.

### SharedLinkSettingsAllowDownloadDisabledType

`class`

Type for shared link settings allow download disabled type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsAllowDownloadEnabledDetails

`class`

Enabled downloads.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.

### SharedLinkSettingsAllowDownloadEnabledType

`class`

Type for shared link settings allow download enabled type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsChangeAudienceDetails

`class`

Changed the audience of the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.
- `newValue`: `Sharing.LinkAudience` - New link audience value.
- `previousValue`: `Sharing.LinkAudience?` - Previous link audience value.

### SharedLinkSettingsChangeAudienceType

`class`

Type for shared link settings change audience type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsChangeExpirationDetails

`class`

Changed the expiration date of the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.
- `newValue`: `Date?` - New shared content link expiration date. Might be missing due to historical data gap.
- `previousValue`: `Date?` - Previous shared content link expiration date. Might be missing due to historical data gap.

### SharedLinkSettingsChangeExpirationType

`class`

Type for shared link settings change expiration type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsChangePasswordDetails

`class`

Changed the password of the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.

### SharedLinkSettingsChangePasswordType

`class`

Type for shared link settings change password type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsRemoveExpirationDetails

`class`

Removed the expiration date from the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.
- `previousValue`: `Date?` - Previous shared link expiration date. Might be missing due to historical data gap.

### SharedLinkSettingsRemoveExpirationType

`class`

Type for shared link settings remove expiration type.

**Properties:**

- `description_`: `String`

### SharedLinkSettingsRemovePasswordDetails

`class`

Removed the password from the shared link.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `sharedContentLink`: `String?` - Shared content link.

### SharedLinkSettingsRemovePasswordType

`class`

Type for shared link settings remove password type.

**Properties:**

- `description_`: `String`

### SharedLinkShareDetails

`class`

Added members as audience of shared link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.
- `externalUsers`: `[TeamLog.ExternalUserLogInfo]?` - Users without a Dropbox account that were added as shared link audience.

### SharedLinkShareType

`class`

Type for shared link share type.

**Properties:**

- `description_`: `String`

### SharedLinkViewDetails

`class`

Opened shared link.

**Properties:**

- `sharedLinkOwner`: `TeamLog.UserLogInfo?` - Shared link owner details. Might be missing due to historical data gap.

### SharedLinkViewType

`class`

Type for shared link view type.

**Properties:**

- `description_`: `String`

### SharedLinkVisibility

`enum`

Defines who has access to a shared link.

**Cases:**

- `noOne`
- `password`
- `public_`
- `teamOnly`
- `other`

---

## Sharing & Permissions

### SharedContentAddInviteesDetails

`class`

Invited user to Dropbox and added them to shared file/folder.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `invitees`: `[String]` - A list of invitees.

### SharedContentAddInviteesType

`class`

Type for shared content add invitees type.

**Properties:**

- `description_`: `String`

### SharedContentAddLinkExpiryDetails

`class`

Added expiration date to link for shared file/folder.

**Properties:**

- `newValue`: `Date?` - New shared content link expiration date. Might be missing due to historical data gap.

### SharedContentAddLinkExpiryType

`class`

Type for shared content add link expiry type.

**Properties:**

- `description_`: `String`

### SharedContentAddLinkPasswordDetails

`class`

Added password to link for shared file/folder.

### SharedContentAddLinkPasswordType

`class`

Type for shared content add link password type.

**Properties:**

- `description_`: `String`

### SharedContentAddMemberDetails

`class`

Added users and/or groups to shared file/folder.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.

### SharedContentAddMemberType

`class`

Type for shared content add member type.

**Properties:**

- `description_`: `String`

### SharedContentChangeDownloadsPolicyDetails

`class`

Changed whether members can download shared file/folder.

**Properties:**

- `newValue`: `TeamLog.DownloadPolicyType` - New downloads policy.
- `previousValue`: `TeamLog.DownloadPolicyType?` - Previous downloads policy. Might be missing due to historical data gap.

### SharedContentChangeDownloadsPolicyType

`class`

Type for shared content change downloads policy type.

**Properties:**

- `description_`: `String`

### SharedContentChangeInviteeRoleDetails

`class`

Changed access type of invitee to shared file/folder before invite was accepted.

**Properties:**

- `previousAccessLevel`: `Sharing.AccessLevel?` - Previous access level. Might be missing due to historical data gap.
- `newAccessLevel`: `Sharing.AccessLevel` - New access level.
- `invitee`: `String` - The invitee whose role was changed.

### SharedContentChangeInviteeRoleType

`class`

Type for shared content change invitee role type.

**Properties:**

- `description_`: `String`

### SharedContentChangeLinkAudienceDetails

`class`

Changed link audience of shared file/folder.

**Properties:**

- `newValue`: `Sharing.LinkAudience` - New link audience value.
- `previousValue`: `Sharing.LinkAudience?` - Previous link audience value.

### SharedContentChangeLinkAudienceType

`class`

Type for shared content change link audience type.

**Properties:**

- `description_`: `String`

### SharedContentChangeLinkExpiryDetails

`class`

Changed link expiration of shared file/folder.

**Properties:**

- `newValue`: `Date?` - New shared content link expiration date. Might be missing due to historical data gap.
- `previousValue`: `Date?` - Previous shared content link expiration date. Might be missing due to historical data gap.

### SharedContentChangeLinkExpiryType

`class`

Type for shared content change link expiry type.

**Properties:**

- `description_`: `String`

### SharedContentChangeLinkPasswordDetails

`class`

Changed link password of shared file/folder.

### SharedContentChangeLinkPasswordType

`class`

Type for shared content change link password type.

**Properties:**

- `description_`: `String`

### SharedContentChangeMemberRoleDetails

`class`

Changed access type of shared file/folder member.

**Properties:**

- `previousAccessLevel`: `Sharing.AccessLevel?` - Previous access level. Might be missing due to historical data gap.
- `newAccessLevel`: `Sharing.AccessLevel` - New access level.

### SharedContentChangeMemberRoleType

`class`

Type for shared content change member role type.

**Properties:**

- `description_`: `String`

### SharedContentChangeViewerInfoPolicyDetails

`class`

Changed whether members can see who viewed shared file/folder.

**Properties:**

- `newValue`: `Sharing.ViewerInfoPolicy` - New viewer info policy.
- `previousValue`: `Sharing.ViewerInfoPolicy?` - Previous view info policy.

### SharedContentChangeViewerInfoPolicyType

`class`

Type for shared content change viewer info policy type.

**Properties:**

- `description_`: `String`

### SharedContentClaimInvitationDetails

`class`

Acquired membership of shared file/folder by accepting invite.

**Properties:**

- `sharedContentLink`: `String?` - Shared content link.

### SharedContentClaimInvitationType

`class`

Type for shared content claim invitation type.

**Properties:**

- `description_`: `String`

### SharedContentCopyDetails

`class`

Copied shared file/folder to own Dropbox.

**Properties:**

- `sharedContentLink`: `String` - Shared content link.
- `sharedContentOwner`: `TeamLog.UserLogInfo?` - The shared content owner.
- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `destinationPath`: `String` - The path where the member saved the content.

### SharedContentCopyType

`class`

Type for shared content copy type.

**Properties:**

- `description_`: `String`

### SharedContentDownloadDetails

`class`

Downloaded shared file/folder.

**Properties:**

- `sharedContentLink`: `String` - Shared content link.
- `sharedContentOwner`: `TeamLog.UserLogInfo?` - The shared content owner.
- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.

### SharedContentDownloadType

`class`

Type for shared content download type.

**Properties:**

- `description_`: `String`

### SharedContentRelinquishMembershipDetails

`class`

Left shared file/folder.

### SharedContentRelinquishMembershipType

`class`

Type for shared content relinquish membership type.

**Properties:**

- `description_`: `String`

### SharedContentRemoveInviteesDetails

`class`

Removed invitee from shared file/folder before invite was accepted.

**Properties:**

- `invitees`: `[String]` - A list of invitees.

### SharedContentRemoveInviteesType

`class`

Type for shared content remove invitees type.

**Properties:**

- `description_`: `String`

### SharedContentRemoveLinkExpiryDetails

`class`

Removed link expiration date of shared file/folder.

**Properties:**

- `previousValue`: `Date?` - Previous shared content link expiration date. Might be missing due to historical data gap.

### SharedContentRemoveLinkExpiryType

`class`

Type for shared content remove link expiry type.

**Properties:**

- `description_`: `String`

### SharedContentRemoveLinkPasswordDetails

`class`

Removed link password of shared file/folder.

### SharedContentRemoveLinkPasswordType

`class`

Type for shared content remove link password type.

**Properties:**

- `description_`: `String`

### SharedContentRemoveMemberDetails

`class`

Removed user/group from shared file/folder.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel?` - Shared content access level.

### SharedContentRemoveMemberType

`class`

Type for shared content remove member type.

**Properties:**

- `description_`: `String`

### SharedContentRequestAccessDetails

`class`

Requested access to shared file/folder.

**Properties:**

- `sharedContentLink`: `String?` - Shared content link.

### SharedContentRequestAccessType

`class`

Type for shared content request access type.

**Properties:**

- `description_`: `String`

### SharedContentRestoreInviteesDetails

`class`

Restored shared file/folder invitees.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.
- `invitees`: `[String]` - A list of invitees.

### SharedContentRestoreInviteesType

`class`

Type for shared content restore invitees type.

**Properties:**

- `description_`: `String`

### SharedContentRestoreMemberDetails

`class`

Restored users and/or groups to membership of shared file/folder.

**Properties:**

- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.

### SharedContentRestoreMemberType

`class`

Type for shared content restore member type.

**Properties:**

- `description_`: `String`

### SharedContentUnshareDetails

`class`

Unshared file/folder by clearing membership.

### SharedContentUnshareType

`class`

Type for shared content unshare type.

**Properties:**

- `description_`: `String`

### SharedContentViewDetails

`class`

Previewed shared file/folder.

**Properties:**

- `sharedContentLink`: `String` - Shared content link.
- `sharedContentOwner`: `TeamLog.UserLogInfo?` - The shared content owner.
- `sharedContentAccessLevel`: `Sharing.AccessLevel` - Shared content access level.

### SharedContentViewType

`class`

Type for shared content view type.

**Properties:**

- `description_`: `String`

### SharedFolderChangeLinkPolicyDetails

`class`

Changed who can access shared folder via link.

**Properties:**

- `newValue`: `Sharing.SharedLinkPolicy` - New shared folder link policy.
- `previousValue`: `Sharing.SharedLinkPolicy?` - Previous shared folder link policy. Might be missing due to historical data gap.

### SharedFolderChangeLinkPolicyType

`class`

Type for shared folder change link policy type.

**Properties:**

- `description_`: `String`

### SharedFolderChangeMembersInheritancePolicyDetails

`class`

Changed whether shared folder inherits members from parent folder.

**Properties:**

- `newValue`: `TeamLog.SharedFolderMembersInheritancePolicy` - New member inheritance policy.
- `previousValue`: `TeamLog.SharedFolderMembersInheritancePolicy?` - Previous member inheritance policy. Might be missing due to historical data gap.

### SharedFolderChangeMembersInheritancePolicyType

`class`

Type for shared folder change members inheritance policy type.

**Properties:**

- `description_`: `String`

### SharedFolderChangeMembersManagementPolicyDetails

`class`

Changed who can add/remove members of shared folder.

**Properties:**

- `newValue`: `Sharing.AclUpdatePolicy` - New members management policy.
- `previousValue`: `Sharing.AclUpdatePolicy?` - Previous members management policy. Might be missing due to historical data gap.

### SharedFolderChangeMembersManagementPolicyType

`class`

Type for shared folder change members management policy type.

**Properties:**

- `description_`: `String`

### SharedFolderChangeMembersPolicyDetails

`class`

Changed who can become member of shared folder.

**Properties:**

- `newValue`: `Sharing.MemberPolicy` - New external invite policy.
- `previousValue`: `Sharing.MemberPolicy?` - Previous external invite policy. Might be missing due to historical data gap.

### SharedFolderChangeMembersPolicyType

`class`

Type for shared folder change members policy type.

**Properties:**

- `description_`: `String`

### SharedFolderCreateDetails

`class`

Created shared folder.

**Properties:**

- `targetNsId`: `String?` - Target namespace ID.

### SharedFolderCreateType

`class`

Type for shared folder create type.

**Properties:**

- `description_`: `String`

### SharedFolderDeclineInvitationDetails

`class`

Declined team member's invite to shared folder.

### SharedFolderDeclineInvitationType

`class`

Type for shared folder decline invitation type.

**Properties:**

- `description_`: `String`

### SharedFolderMembersInheritancePolicy

`enum`

Specifies if a shared folder inherits its members from the parent folder.

**Cases:**

- `dontInheritMembers`
- `inheritMembers`
- `other`

### SharedFolderMountDetails

`class`

Added shared folder to own Dropbox.

### SharedFolderMountType

`class`

Type for shared folder mount type.

**Properties:**

- `description_`: `String`

### SharedFolderNestDetails

`class`

Changed parent of shared folder.

**Properties:**

- `previousParentNsId`: `String?` - Previous parent namespace ID.
- `newParentNsId`: `String?` - New parent namespace ID.
- `previousNsPath`: `String?` - Previous namespace path.
- `newNsPath`: `String?` - New namespace path.

### SharedFolderNestType

`class`

Type for shared folder nest type.

**Properties:**

- `description_`: `String`

### SharedFolderTransferOwnershipDetails

`class`

Transferred ownership of shared folder to another member.

**Properties:**

- `previousOwnerEmail`: `String?` - The email address of the previous shared folder owner.
- `newOwnerEmail`: `String` - The email address of the new shared folder owner.

### SharedFolderTransferOwnershipType

`class`

Type for shared folder transfer ownership type.

**Properties:**

- `description_`: `String`

### SharedFolderUnmountDetails

`class`

Deleted shared folder from Dropbox.

### SharedFolderUnmountType

`class`

Type for shared folder unmount type.

**Properties:**

- `description_`: `String`

### SharingChangeFolderJoinPolicyDetails

`class`

Changed whether team members can join shared folders owned outside team.

**Properties:**

- `newValue`: `TeamLog.SharingFolderJoinPolicy` - New external join policy.
- `previousValue`: `TeamLog.SharingFolderJoinPolicy?` - Previous external join policy. Might be missing due to historical data gap.

### SharingChangeFolderJoinPolicyType

`class`

Type for sharing change folder join policy type.

**Properties:**

- `description_`: `String`

### SharingChangeLinkAllowChangeExpirationPolicyDetails

`class`

Changed the allow remove or change expiration policy for the links shared outside of the team.

**Properties:**

- `newValue`: `TeamLog.EnforceLinkPasswordPolicy` - To.
- `previousValue`: `TeamLog.EnforceLinkPasswordPolicy?` - From.

### SharingChangeLinkAllowChangeExpirationPolicyType

`class`

Type for sharing change link allow change expiration policy type.

**Properties:**

- `description_`: `String`

### SharingChangeLinkDefaultExpirationPolicyDetails

`class`

Changed the default expiration for the links shared outside of the team.

**Properties:**

- `newValue`: `TeamLog.DefaultLinkExpirationDaysPolicy` - To.
- `previousValue`: `TeamLog.DefaultLinkExpirationDaysPolicy?` - From.

### SharingChangeLinkDefaultExpirationPolicyType

`class`

Type for sharing change link default expiration policy type.

**Properties:**

- `description_`: `String`

### SharingChangeLinkEnforcePasswordPolicyDetails

`class`

Changed the password requirement for the links shared outside of the team.

**Properties:**

- `newValue`: `TeamLog.ChangeLinkExpirationPolicy` - To.
- `previousValue`: `TeamLog.ChangeLinkExpirationPolicy?` - From.

### SharingChangeLinkEnforcePasswordPolicyType

`class`

Type for sharing change link enforce password policy type.

**Properties:**

- `description_`: `String`

### SharingChangeLinkPolicyDetails

`class`

by default.

**Properties:**

- `newValue`: `TeamLog.SharingLinkPolicy` - New external link accessibility policy.
- `previousValue`: `TeamLog.SharingLinkPolicy?` - Previous external link accessibility policy. Might be missing due to historical data gap.

### SharingChangeLinkPolicyType

`class`

Type for sharing change link policy type.

**Properties:**

- `description_`: `String`

### SharingChangeMemberPolicyDetails

`class`

Changed whether members can share files/folders outside team.

**Properties:**

- `newValue`: `TeamLog.SharingMemberPolicy` - New external invite policy.
- `previousValue`: `TeamLog.SharingMemberPolicy?` - Previous external invite policy. Might be missing due to historical data gap.

### SharingChangeMemberPolicyType

`class`

Type for sharing change member policy type.

**Properties:**

- `description_`: `String`

### SharingFolderJoinPolicy

`enum`

Policy for controlling if team members can join shared folders owned by non team members.

**Cases:**

- `fromAnyone`
- `fromTeamOnly`
- `other`

### SharingLinkPolicy

`enum`

Policy for controlling if team members can share links externally

**Cases:**

- `defaultNoOne`
- `defaultPrivate`
- `defaultPublic`
- `onlyPrivate`
- `other`

### SharingMemberPolicy

`enum`

External sharing policy

**Cases:**

- `allow`
- `forbid`
- `forbidWithExclusions`
- `other`

---

## Showcase

### ShowcaseAccessGrantedDetails

`class`

Granted access to showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseAccessGrantedType

`class`

Type for showcase access granted type.

**Properties:**

- `description_`: `String`

### ShowcaseAddMemberDetails

`class`

Added member to showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseAddMemberType

`class`

Type for showcase add member type.

**Properties:**

- `description_`: `String`

### ShowcaseArchivedDetails

`class`

Archived showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseArchivedType

`class`

Type for showcase archived type.

**Properties:**

- `description_`: `String`

### ShowcaseCreatedDetails

`class`

Created showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseCreatedType

`class`

Type for showcase created type.

**Properties:**

- `description_`: `String`

### ShowcaseDeleteCommentDetails

`class`

Deleted showcase comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### ShowcaseDeleteCommentType

`class`

Type for showcase delete comment type.

**Properties:**

- `description_`: `String`

### ShowcaseDocumentLogInfo

`class`

Showcase document's logged information.

**Properties:**

- `showcaseId`: `String` - Showcase document Id.
- `showcaseTitle`: `String` - Showcase document title.

### ShowcaseEditCommentDetails

`class`

Edited showcase comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### ShowcaseEditCommentType

`class`

Type for showcase edit comment type.

**Properties:**

- `description_`: `String`

### ShowcaseEditedDetails

`class`

Edited showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseEditedType

`class`

Type for showcase edited type.

**Properties:**

- `description_`: `String`

### ShowcaseFileAddedDetails

`class`

Added file to showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseFileAddedType

`class`

Type for showcase file added type.

**Properties:**

- `description_`: `String`

### ShowcaseFileDownloadDetails

`class`

Downloaded file from showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `downloadType`: `String` - Showcase download type.

### ShowcaseFileDownloadType

`class`

Type for showcase file download type.

**Properties:**

- `description_`: `String`

### ShowcaseFileRemovedDetails

`class`

Removed file from showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseFileRemovedType

`class`

Type for showcase file removed type.

**Properties:**

- `description_`: `String`

### ShowcaseFileViewDetails

`class`

Viewed file in showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseFileViewType

`class`

Type for showcase file view type.

**Properties:**

- `description_`: `String`

### ShowcasePermanentlyDeletedDetails

`class`

Permanently deleted showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcasePermanentlyDeletedType

`class`

Type for showcase permanently deleted type.

**Properties:**

- `description_`: `String`

### ShowcasePostCommentDetails

`class`

Added showcase comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### ShowcasePostCommentType

`class`

Type for showcase post comment type.

**Properties:**

- `description_`: `String`

### ShowcaseRemoveMemberDetails

`class`

Removed member from showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseRemoveMemberType

`class`

Type for showcase remove member type.

**Properties:**

- `description_`: `String`

### ShowcaseRenamedDetails

`class`

Renamed showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseRenamedType

`class`

Type for showcase renamed type.

**Properties:**

- `description_`: `String`

### ShowcaseRequestAccessDetails

`class`

Requested access to showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseRequestAccessType

`class`

Type for showcase request access type.

**Properties:**

- `description_`: `String`

### ShowcaseResolveCommentDetails

`class`

Resolved showcase comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### ShowcaseResolveCommentType

`class`

Type for showcase resolve comment type.

**Properties:**

- `description_`: `String`

### ShowcaseRestoredDetails

`class`

Unarchived showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseRestoredType

`class`

Type for showcase restored type.

**Properties:**

- `description_`: `String`

### ShowcaseTrashedDeprecatedDetails

`class`

Deleted showcase (old version).

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseTrashedDeprecatedType

`class`

Type for showcase trashed deprecated type.

**Properties:**

- `description_`: `String`

### ShowcaseTrashedDetails

`class`

Deleted showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseTrashedType

`class`

Type for showcase trashed type.

**Properties:**

- `description_`: `String`

### ShowcaseUnresolveCommentDetails

`class`

Unresolved showcase comment.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.
- `commentText`: `String?` - Comment text.

### ShowcaseUnresolveCommentType

`class`

Type for showcase unresolve comment type.

**Properties:**

- `description_`: `String`

### ShowcaseUntrashedDeprecatedDetails

`class`

Restored showcase (old version).

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseUntrashedDeprecatedType

`class`

Type for showcase untrashed deprecated type.

**Properties:**

- `description_`: `String`

### ShowcaseUntrashedDetails

`class`

Restored showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseUntrashedType

`class`

Type for showcase untrashed type.

**Properties:**

- `description_`: `String`

### ShowcaseViewDetails

`class`

Viewed showcase.

**Properties:**

- `eventUuid`: `String` - Event unique identifier.

### ShowcaseViewType

`class`

Type for showcase view type.

**Properties:**

- `description_`: `String`

---

## Smart Sync

### SmartSyncCreateAdminPrivilegeReportDetails

`class`

Created Smart Sync non-admin devices report.

### SmartSyncCreateAdminPrivilegeReportType

`class`

Type for smart sync create admin privilege report type.

**Properties:**

- `description_`: `String`

### SmartSyncNotOptOutDetails

`class`

Opted team into Smart Sync.

**Properties:**

- `previousValue`: `TeamLog.SmartSyncOptOutPolicy` - Previous Smart Sync opt out policy.
- `newValue`: `TeamLog.SmartSyncOptOutPolicy` - New Smart Sync opt out policy.

### SmartSyncNotOptOutType

`class`

Type for smart sync not opt out type.

**Properties:**

- `description_`: `String`

### SmartSyncOptOutDetails

`class`

Opted team out of Smart Sync.

**Properties:**

- `previousValue`: `TeamLog.SmartSyncOptOutPolicy` - Previous Smart Sync opt out policy.
- `newValue`: `TeamLog.SmartSyncOptOutPolicy` - New Smart Sync opt out policy.

### SmartSyncOptOutType

`class`

Type for smart sync opt out type.

**Properties:**

- `description_`: `String`

---

## SSO & Certificate

### Certificate

`class`

Certificate details.

**Properties:**

- `subject`: `String` - Certificate subject.
- `issuer`: `String` - Certificate issuer.
- `issueDate`: `String` - Certificate issue date.
- `expirationDate`: `String` - Certificate expiration date.
- `serialNumber`: `String` - Certificate serial number.
- `sha1Fingerprint`: `String` - Certificate sha1 fingerprint.
- `commonName`: `String?` - Certificate common name.

### SsoAddCertDetails

`class`

Added X.509 certificate for SSO.

**Properties:**

- `certificateDetails`: `TeamLog.Certificate` - SSO certificate details.

### SsoAddCertType

`class`

Type for sso add cert type.

**Properties:**

- `description_`: `String`

### SsoAddLoginUrlDetails

`class`

Added sign-in URL for SSO.

**Properties:**

- `newValue`: `String` - New single sign-on login URL.

### SsoAddLoginUrlType

`class`

Type for sso add login url type.

**Properties:**

- `description_`: `String`

### SsoAddLogoutUrlDetails

`class`

Added sign-out URL for SSO.

**Properties:**

- `newValue`: `String?` - New single sign-on logout URL.

### SsoAddLogoutUrlType

`class`

Type for sso add logout url type.

**Properties:**

- `description_`: `String`

### SsoChangeCertDetails

`class`

Changed X.509 certificate for SSO.

**Properties:**

- `previousCertificateDetails`: `TeamLog.Certificate?` - Previous SSO certificate details. Might be missing due to historical data gap.
- `newCertificateDetails`: `TeamLog.Certificate` - New SSO certificate details.

### SsoChangeCertType

`class`

Type for sso change cert type.

**Properties:**

- `description_`: `String`

### SsoChangeLoginUrlDetails

`class`

Changed sign-in URL for SSO.

**Properties:**

- `previousValue`: `String` - Previous single sign-on login URL.
- `newValue`: `String` - New single sign-on login URL.

### SsoChangeLoginUrlType

`class`

Type for sso change login url type.

**Properties:**

- `description_`: `String`

### SsoChangeLogoutUrlDetails

`class`

Changed sign-out URL for SSO.

**Properties:**

- `previousValue`: `String?` - Previous single sign-on logout URL. Might be missing due to historical data gap.
- `newValue`: `String?` - New single sign-on logout URL.

### SsoChangeLogoutUrlType

`class`

Type for sso change logout url type.

**Properties:**

- `description_`: `String`

### SsoChangeSamlIdentityModeDetails

`class`

Changed SAML identity mode for SSO.

**Properties:**

- `previousValue`: `Int64` - Previous single sign-on identity mode.
- `newValue`: `Int64` - New single sign-on identity mode.

### SsoChangeSamlIdentityModeType

`class`

Type for sso change saml identity mode type.

**Properties:**

- `description_`: `String`

### SsoErrorDetails

`class`

Failed to sign in via SSO.

**Properties:**

- `errorDetails`: `TeamLog.FailureDetailsLogInfo` - Error details.

### SsoErrorType

`class`

Type for sso error type.

**Properties:**

- `description_`: `String`

### SsoRemoveCertDetails

`class`

Removed X.509 certificate for SSO.

### SsoRemoveCertType

`class`

Type for sso remove cert type.

**Properties:**

- `description_`: `String`

### SsoRemoveLoginUrlDetails

`class`

Removed sign-in URL for SSO.

**Properties:**

- `previousValue`: `String` - Previous single sign-on login URL.

### SsoRemoveLoginUrlType

`class`

Type for sso remove login url type.

**Properties:**

- `description_`: `String`

### SsoRemoveLogoutUrlDetails

`class`

Removed sign-out URL for SSO.

**Properties:**

- `previousValue`: `String` - Previous single sign-on logout URL.

### SsoRemoveLogoutUrlType

`class`

Type for sso remove logout url type.

**Properties:**

- `description_`: `String`

---

## Team Invite Links

### CreateTeamInviteLinkDetails

`class`

Created team invite link.

**Properties:**

- `linkUrl`: `String` - The invite link url that was created.
- `expiryDate`: `String` - The expiration date of the invite link.

### CreateTeamInviteLinkType

`class`

Type for create team invite link type.

**Properties:**

- `description_`: `String`

### DeleteTeamInviteLinkDetails

`class`

Deleted team invite link.

**Properties:**

- `linkUrl`: `String` - The invite link url that was deleted.

### DeleteTeamInviteLinkType

`class`

Type for delete team invite link type.

**Properties:**

- `description_`: `String`

---

## Team Settings & Operations

### TeamActivityCreateReportDetails

`class`

Created team activity report.

**Properties:**

- `startDate`: `Date` - Report start date.
- `endDate`: `Date` - Report end date.

### TeamActivityCreateReportFailDetails

`class`

Couldn't generate team activity report.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### TeamActivityCreateReportFailType

`class`

Type for team activity create report fail type.

**Properties:**

- `description_`: `String`

### TeamActivityCreateReportType

`class`

Type for team activity create report type.

**Properties:**

- `description_`: `String`

### TeamDetails

`class`

More details about the team.

**Properties:**

- `team`: `String` - The name of the team.

### TeamEncryptionKeyCancelKeyDeletionDetails

`class`

Canceled team encryption key deletion.

### TeamEncryptionKeyCancelKeyDeletionType

`class`

Type for team encryption key cancel key deletion type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyCreateKeyDetails

`class`

Created team encryption key.

### TeamEncryptionKeyCreateKeyType

`class`

Type for team encryption key create key type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyDeleteKeyDetails

`class`

Deleted team encryption key.

### TeamEncryptionKeyDeleteKeyType

`class`

Type for team encryption key delete key type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyDisableKeyDetails

`class`

Disabled team encryption key.

### TeamEncryptionKeyDisableKeyType

`class`

Type for team encryption key disable key type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyEnableKeyDetails

`class`

Enabled team encryption key.

### TeamEncryptionKeyEnableKeyType

`class`

Type for team encryption key enable key type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyRotateKeyDetails

`class`

Rotated team encryption key.

### TeamEncryptionKeyRotateKeyType

`class`

Type for team encryption key rotate key type.

**Properties:**

- `description_`: `String`

### TeamEncryptionKeyScheduleKeyDeletionDetails

`class`

Scheduled encryption key deletion.

### TeamEncryptionKeyScheduleKeyDeletionType

`class`

Type for team encryption key schedule key deletion type.

**Properties:**

- `description_`: `String`

### TeamEvent

`class`

An audit log event.

**Properties:**

- `timestamp_`: `Date` - The Dropbox timestamp representing when the action was taken.
- `eventCategory`: `TeamLog.EventCategory` - The category that this type of action belongs to.
- `actor`: `TeamLog.ActorLogInfo?` - The entity who actually performed the action. Might be missing due to historical data gap.
- `origin`: `TeamLog.OriginLogInfo?` - client.
- `involveNonTeamMember`: `Bool?` - missing due to historical data gap.
- `context`: `TeamLog.ContextLogInfo?` - gap.
- `participants`: `[TeamLog.ParticipantLogInfo]?` - actors or users in context.
- `assets`: `[TeamLog.AssetLogInfo]?` - the future we might add other asset types such as Paper documents, folders, projects, etc.
- `eventType`: `TeamLog.EventType` - The particular type of action taken.
- `details`: `TeamLog.EventDetails` - action.

### TeamFolderChangeStatusDetails

`class`

Changed archival status of team folder.

**Properties:**

- `newValue`: `Team.TeamFolderStatus` - New team folder status.
- `previousValue`: `Team.TeamFolderStatus?` - Previous team folder status. Might be missing due to historical data gap.

### TeamFolderChangeStatusType

`class`

Type for team folder change status type.

**Properties:**

- `description_`: `String`

### TeamFolderCreateDetails

`class`

Created team folder in active status.

### TeamFolderCreateType

`class`

Type for team folder create type.

**Properties:**

- `description_`: `String`

### TeamFolderDowngradeDetails

`class`

Downgraded team folder to regular shared folder.

**Properties:**

- `targetAssetIndex`: `UInt64` - Target asset position in the Assets list.

### TeamFolderDowngradeType

`class`

Type for team folder downgrade type.

**Properties:**

- `description_`: `String`

### TeamFolderPermanentlyDeleteDetails

`class`

Permanently deleted archived team folder.

### TeamFolderPermanentlyDeleteType

`class`

Type for team folder permanently delete type.

**Properties:**

- `description_`: `String`

### TeamFolderRenameDetails

`class`

Renamed active/archived team folder.

**Properties:**

- `previousFolderName`: `String` - Previous folder name.
- `newFolderName`: `String` - New folder name.

### TeamFolderRenameType

`class`

Type for team folder rename type.

**Properties:**

- `description_`: `String`

### TeamLinkedAppLogInfo

`class`

Team linked app

### TeamLogInfo

`class`

Team's logged information.

**Properties:**

- `displayName`: `String` - Team display name.

### TeamMemberLogInfo

`class`

Team member's logged information.

**Properties:**

- `teamMemberId`: `String?` - Team member ID.
- `memberExternalId`: `String?` - Team member external ID.
- `team`: `TeamLog.TeamLogInfo?` - Details about this user&#x2019s team for enterprise event.

### TeamMembershipType

`enum`

Type for team membership type.

**Cases:**

- `free`
- `full`
- `guest`
- `other`

### TeamName

`class`

Team name details

**Properties:**

- `teamDisplayName`: `String` - Team's display name.
- `teamLegalName`: `String` - Team's legal name.

### TeamProfileAddBackgroundDetails

`class`

Added team background to display on shared link headers.

### TeamProfileAddBackgroundType

`class`

Type for team profile add background type.

**Properties:**

- `description_`: `String`

### TeamProfileAddLogoDetails

`class`

Added team logo to display on shared link headers.

### TeamProfileAddLogoType

`class`

Type for team profile add logo type.

**Properties:**

- `description_`: `String`

### TeamProfileChangeBackgroundDetails

`class`

Changed team background displayed on shared link headers.

### TeamProfileChangeBackgroundType

`class`

Type for team profile change background type.

**Properties:**

- `description_`: `String`

### TeamProfileChangeDefaultLanguageDetails

`class`

Changed default language for team.

**Properties:**

- `newValue`: `String` - New team's default language.
- `previousValue`: `String` - Previous team's default language.

### TeamProfileChangeDefaultLanguageType

`class`

Type for team profile change default language type.

**Properties:**

- `description_`: `String`

### TeamProfileChangeLogoDetails

`class`

Changed team logo displayed on shared link headers.

### TeamProfileChangeLogoType

`class`

Type for team profile change logo type.

**Properties:**

- `description_`: `String`

### TeamProfileChangeNameDetails

`class`

Changed team name.

**Properties:**

- `previousValue`: `TeamLog.TeamName?` - Previous teams name. Might be missing due to historical data gap.
- `newValue`: `TeamLog.TeamName` - New team name.

### TeamProfileChangeNameType

`class`

Type for team profile change name type.

**Properties:**

- `description_`: `String`

### TeamProfileRemoveBackgroundDetails

`class`

Removed team background displayed on shared link headers.

### TeamProfileRemoveBackgroundType

`class`

Type for team profile remove background type.

**Properties:**

- `description_`: `String`

### TeamProfileRemoveLogoDetails

`class`

Removed team logo displayed on shared link headers.

### TeamProfileRemoveLogoType

`class`

Type for team profile remove logo type.

**Properties:**

- `description_`: `String`

### TeamSelectiveSyncSettingsChangedDetails

`class`

Changed sync default.

**Properties:**

- `previousValue`: `Files.SyncSetting` - Previous value.
- `newValue`: `Files.SyncSetting` - New value.

### TeamSelectiveSyncSettingsChangedType

`class`

Type for team selective sync settings changed type.

**Properties:**

- `description_`: `String`

### TeamSharingWhitelistSubjectsChangedDetails

`class`

Edited the approved list for sharing externally.

**Properties:**

- `addedWhitelistSubjects`: `[String]` - Domains or emails added to the approved list for sharing externally.
- `removedWhitelistSubjects`: `[String]` - Domains or emails removed from the approved list for sharing externally.

### TeamSharingWhitelistSubjectsChangedType

`class`

Type for team sharing whitelist subjects changed type.

**Properties:**

- `description_`: `String`

---

## Trusted Teams

### TrustedNonTeamMemberLogInfo

`class`

User that is not a member of the team but considered trusted.

**Properties:**

- `trustedNonTeamMemberType`: `TeamLog.TrustedNonTeamMemberType` - Indicates the type of the member of a trusted team.
- `team`: `TeamLog.TeamLogInfo?` - Details about this user's trusted team.

### TrustedNonTeamMemberType

`enum`

Type for trusted non team member type.

**Cases:**

- `enterpriseAdmin`
- `multiInstanceAdmin`
- `other`

### TrustedTeamsRequestAction

`enum`

Type for trusted teams request action.

**Cases:**

- `accepted`
- `declined`
- `expired`
- `invited`
- `revoked`
- `other`

### TrustedTeamsRequestState

`enum`

Type for trusted teams request state.

**Cases:**

- `invited`
- `linked`
- `unlinked`
- `other`

---

## User & Member Log Info

### UserLogInfo

`class`

User's logged information.

**Properties:**

- `accountId`: `String?` - User unique ID.
- `displayName`: `String?` - User display name.
- `email`: `String?` - User email address.

### NonTeamMemberLogInfo

`class`

Non team member's logged information.

### UserLinkedAppLogInfo

`class`

User linked app

### UserNameLogInfo

`class`

User's name logged information

**Properties:**

- `givenName`: `String` - Given name.
- `surname`: `String` - Surname.
- `locale`: `String?` - Locale. Might be missing due to historical data gap.

### UserOrTeamLinkedAppLogInfo

`class`

User or team linked app. Used when linked type is missing due to historical data gap.

### UserTagsAddedDetails

`class`

Tagged a file.

**Properties:**

- `values`: `[String]` - values.

### UserTagsAddedType

`class`

Type for user tags added type.

**Properties:**

- `description_`: `String`

### UserTagsRemovedDetails

`class`

Removed tags.

**Properties:**

- `values`: `[String]` - values.

### UserTagsRemovedType

`class`

Type for user tags removed type.

**Properties:**

- `description_`: `String`

---

## Web Sessions

### WebSessionsChangeActiveSessionLimitDetails

`class`

Changed limit on active sessions per member.

**Properties:**

- `previousValue`: `String` - Previous max number of concurrent active sessions policy.
- `newValue`: `String` - New max number of concurrent active sessions policy.

### WebSessionsChangeActiveSessionLimitType

`class`

Type for web sessions change active session limit type.

**Properties:**

- `description_`: `String`

---

## Other Types

### IdentifierType

`enum`

Type for identifier type.

**Cases:**

- `email`
- `facebookProfileName`
- `other`

### LabelType

`enum`

Label type

**Cases:**

- `personalInformation`
- `testOnly`
- `userDefinedTag`
- `other`

### LockStatus

`enum`

File lock status

**Cases:**

- `locked`
- `unlocked`
- `other`

### MissingDetails

`class`

a result.

**Properties:**

- `sourceEventFields`: `String?` - All the data that could be retrieved and converted from the source event.

### NoExpirationLinkGenCreateReportDetails

`class`

Report created: Links created with no expiration.

**Properties:**

- `startDate`: `Date` - Report start date.
- `endDate`: `Date` - Report end date.

### NoExpirationLinkGenCreateReportType

`class`

Type for no expiration link gen create report type.

**Properties:**

- `description_`: `String`

### NoExpirationLinkGenReportFailedDetails

`class`

Couldn't create report: Links created with no expiration.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### NoExpirationLinkGenReportFailedType

`class`

Type for no expiration link gen report failed type.

**Properties:**

- `description_`: `String`

### NonTrustedTeamDetails

`class`

The email to which the request was sent

**Properties:**

- `team`: `String` - The email to which the request was sent.

### OpenNoteSharedDetails

`class`

Opened shared Paper doc.

### OpenNoteSharedType

`class`

Type for open note shared type.

**Properties:**

- `description_`: `String`

### OrganizationDetails

`class`

More details about the organization.

**Properties:**

- `organization`: `String` - The name of the organization.

### OrganizationName

`class`

The name of the organization

**Properties:**

- `organization`: `String` - The name of the organization.

### OrganizeFolderWithTidyDetails

`class`

Organized a folder with multi-file organize.

### OrganizeFolderWithTidyType

`class`

Type for organize folder with tidy type.

**Properties:**

- `description_`: `String`

### OutdatedLinkViewCreateReportDetails

`class`

Report created: Views of old links.

**Properties:**

- `startDate`: `Date` - Report start date.
- `endDate`: `Date` - Report end date.

### OutdatedLinkViewCreateReportType

`class`

Type for outdated link view create report type.

**Properties:**

- `description_`: `String`

### OutdatedLinkViewReportFailedDetails

`class`

Couldn't create report: Views of old links.

**Properties:**

- `failureReason`: `Team.TeamReportFailureReason` - Failure reason.

### OutdatedLinkViewReportFailedType

`class`

Type for outdated link view report failed type.

**Properties:**

- `description_`: `String`

### ParticipantLogInfo

`enum`

A user or group

**Cases:**

- `group` - Group details.
- `user` - A user with a Dropbox account.
- `other`

### PendingSecondaryEmailAddedDetails

`class`

Added pending secondary email.

**Properties:**

- `secondaryEmail`: `String` - New pending secondary email.

### PendingSecondaryEmailAddedType

`class`

Type for pending secondary email added type.

**Properties:**

- `description_`: `String`

### PrimaryTeamRequestAcceptedDetails

`class`

Team merge request acceptance details shown to the primary team

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### PrimaryTeamRequestCanceledDetails

`class`

Team merge request cancellation details shown to the primary team

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### PrimaryTeamRequestExpiredDetails

`class`

Team merge request expiration details shown to the primary team

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### PrimaryTeamRequestReminderDetails

`class`

Team merge request reminder details shown to the primary team

**Properties:**

- `secondaryTeam`: `String` - The secondary team name.
- `sentTo`: `String` - The name of the primary team admin the request was sent to.

### QuickActionType

`enum`

Quick action type.

**Cases:**

- `deleteSharedLink`
- `resetPassword`
- `restoreFileOrFolder`
- `unlinkApp`
- `unlinkDevice`
- `unlinkSession`
- `other`

### RelocateAssetReferencesLogInfo

`class`

Provides the indices of the source asset and the destination asset for a relocate action.

**Properties:**

- `srcAssetIndex`: `UInt64` - Source asset position in the Assets list.
- `destAssetIndex`: `UInt64` - Destination asset position in the Assets list.

### ReplayFileDeleteDetails

`class`

Deleted files in Replay.

### ReplayFileDeleteType

`class`

Type for replay file delete type.

**Properties:**

- `description_`: `String`

### ReplayFileSharedLinkCreatedDetails

`class`

Created shared link in Replay.

### ReplayFileSharedLinkCreatedType

`class`

Type for replay file shared link created type.

**Properties:**

- `description_`: `String`

### ReplayFileSharedLinkModifiedDetails

`class`

Modified shared link in Replay.

### ReplayFileSharedLinkModifiedType

`class`

Type for replay file shared link modified type.

**Properties:**

- `description_`: `String`

### ReplayProjectTeamAddDetails

`class`

Added member to Replay Project.

### ReplayProjectTeamAddType

`class`

Type for replay project team add type.

**Properties:**

- `description_`: `String`

### ReplayProjectTeamDeleteDetails

`class`

Removed member from Replay Project.

### ReplayProjectTeamDeleteType

`class`

Type for replay project team delete type.

**Properties:**

- `description_`: `String`

### SecondaryTeamRequestAcceptedDetails

`class`

Team merge request acceptance details shown to the secondary team

**Properties:**

- `primaryTeam`: `String` - The primary team name.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### SecondaryTeamRequestCanceledDetails

`class`

Team merge request cancellation details shown to the secondary team

**Properties:**

- `sentTo`: `String` - The email of the primary team admin that the request was sent to.
- `sentBy`: `String` - The name of the secondary team admin who sent the request originally.

### SecondaryTeamRequestExpiredDetails

`class`

Team merge request expiration details shown to the secondary team

**Properties:**

- `sentTo`: `String` - The email of the primary team admin the request was sent to.

### SecondaryTeamRequestReminderDetails

`class`

Team merge request reminder details shown to the secondary team

**Properties:**

- `sentTo`: `String` - The email of the primary team admin the request was sent to.

### SharedNoteOpenedDetails

`class`

Opened shared Paper doc.

### SharedNoteOpenedType

`class`

Type for shared note opened type.

**Properties:**

- `description_`: `String`

---
