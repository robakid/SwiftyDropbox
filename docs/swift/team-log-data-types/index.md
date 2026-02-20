# TeamLog Data Types

Data types for the team_log namespace. This namespace contains an extensive set of types for team event logging and auditing.

The `TeamLog` namespace encompasses over 1,100 public data types (classes and enums) organized into categories covering every aspect of Dropbox team activity logging. These types are auto-generated from the Dropbox Stone API specification and are used to represent team audit log events, their details, the actors and contexts involved, and the various policy settings that can be changed.

---

## Table of Contents

- [Core Event & API Types](#core-event-api-types)
- [Actor, Context & Origin Log Info](#actor-context-origin-log-info)
- [Access & Session Log Info](#access-session-log-info)
- [Account & Account Capture](#account-account-capture)
- [Admin Alerting](#admin-alerting)
- [Admin Console & Roles](#admin-console-roles)
- [App Management](#app-management)
- [Asset & Path Log Info](#asset-path-log-info)
- [Backup & Computer Backup](#backup-computer-backup)
- [Binder Operations](#binder-operations)
- [Camera & Capture](#camera-capture)
- [Classification & Content](#classification-content)
- [Collection & Naming](#collection-naming)
- [Common Supporting Types](#common-supporting-types)
- [Data Governance & Retention](#data-governance-retention)
- [Device & Session Management](#device-session-management)
- [Domain & DNS](#domain-dns)
- [Domain & Feature Settings](#domain-feature-settings)
- [Dropbox Passwords](#dropbox-passwords)
- [Email Ingest](#email-ingest)
- [EMM & Mobile Device Management](#emm-mobile-device-management)
- [Enterprise & Federation](#enterprise-federation)
- [Export & Reporting](#export-reporting)
- [External Sharing & Users](#external-sharing-users)
- [Feature Settings](#feature-settings)
- [File & Folder Operations](#file-folder-operations)
- [Group Management](#group-management)
- [Integration & Third-Party](#integration-third-party)
- [Legal Holds](#legal-holds)
- [Login & Authentication](#login-authentication)
- [Member Management](#member-management)
- [Namespace](#namespace)
- [Network & Geo](#network-geo)
- [Paper & Notes](#paper-notes)
- [Password & Security](#password-security)
- [Policy Types](#policy-types)
- [Ransomware & Threat](#ransomware-threat)
- [Reseller & Support](#reseller-support)
- [Shared Folder Operations](#shared-folder-operations)
- [Shared Links](#shared-links)
- [Sharing & Permissions](#sharing-permissions)
- [Showcase](#showcase)
- [Smart Sync](#smart-sync)
- [SSO & Certificate](#sso-certificate)
- [Team Invite Links](#team-invite-links)
- [Team Settings & Operations](#team-settings-operations)
- [Trusted Teams](#trusted-teams)
- [User & Member Log Info](#user-member-log-info)
- [Web Sessions](#web-sessions)
- [Other Types](#other-types)

---

## Core Event & API Types

### EventCategory

`enum` 

Category of events in event audit log.

### EventDetails

`enum` 

Additional fields depending on the event type.

### EventType

`enum` 

The type of the event with description.

### EventTypeArg

`enum` 

The type of the event.

### GetTeamEventsArg

`class` 

Type for get team events arg.

### GetTeamEventsContinueArg

`class` 

Type for get team events continue arg.

### GetTeamEventsContinueError

`enum` 

Errors that can be raised when calling getEventsContinue.

### GetTeamEventsError

`enum` 

Errors that can be raised when calling getEvents.

### GetTeamEventsResult

`class` 

Type for get team events result.

---

## Actor, Context & Origin Log Info

### ActionDetails

`enum` 

Additional information indicating the action taken that caused status change.

### ActorLogInfo

`enum` 

The entity who performed the action.

### ContextLogInfo

`enum` 

The primary entity on which the action was done.

### OriginLogInfo

`class` 

The origin from which the actor performed the action.

---

## Access & Session Log Info

### AccessMethodLogInfo

`enum` 

Indicates the method in which the action was performed.

### ApiSessionLogInfo

`class` 

Api session.

### DeviceSessionLogInfo

`class` 

Device's session logged information.

### DesktopDeviceSessionLogInfo

`class` 

Information about linked Dropbox desktop client sessions

### SessionLogInfo

`class` 

Session's logged information.

### DesktopSessionLogInfo

`class` 

Desktop session.

### LegacyDeviceSessionLogInfo

`class` 

Information on sessions, in legacy format

### MobileDeviceSessionLogInfo

`class` 

Information about linked Dropbox mobile client sessions

### MobileSessionLogInfo

`class` 

Mobile session.

### WebDeviceSessionLogInfo

`class` 

Information on active web sessions

### WebSessionLogInfo

`class` 

Web session.

---

## Account & Account Capture

### AccountCaptureAvailability

`enum` 

Type for account capture availability.

### AccountCaptureChangeAvailabilityDetails

`class` 

Granted/revoked option to enable account capture on team domains.

### AccountCaptureChangeAvailabilityType

`class` 

Type for account capture change availability type.

### AccountCaptureChangePolicyDetails

`class` 

Changed account capture setting on team domain.

### AccountCaptureChangePolicyType

`class` 

Type for account capture change policy type.

### AccountCaptureMigrateAccountDetails

`class` 

Account-captured user migrated account to team.

### AccountCaptureMigrateAccountType

`class` 

Type for account capture migrate account type.

### AccountCaptureNotificationEmailsSentDetails

`class` 

Sent account capture email to all unmanaged members.

### AccountCaptureNotificationEmailsSentType

`class` 

Type for account capture notification emails sent type.

### AccountCaptureNotificationType

`enum` 

Type for account capture notification type.

### AccountCapturePolicy

`enum` 

Type for account capture policy.

### AccountCaptureRelinquishAccountDetails

`class` 

Account-captured user changed account email to personal email.

### AccountCaptureRelinquishAccountType

`class` 

Type for account capture relinquish account type.

### AccountLockOrUnlockedDetails

`class` 

Unlocked/locked account after failed sign in attempts.

### AccountLockOrUnlockedType

`class` 

Type for account lock or unlocked type.

### AccountState

`enum` 

Type for account state.

---

## Admin Alerting

### AdminAlertCategoryEnum

`enum` 

Alert category

### AdminAlertGeneralStateEnum

`enum` 

Alert state

### AdminAlertSeverityEnum

`enum` 

Alert severity

### AdminAlertingAlertConfiguration

`class` 

Alert configurations

### AdminAlertingAlertSensitivity

`enum` 

Alert sensitivity

### AdminAlertingAlertStateChangedDetails

`class` 

Changed an alert state.

### AdminAlertingAlertStateChangedType

`class` 

Type for admin alerting alert state changed type.

### AdminAlertingAlertStatePolicy

`enum` 

Policy for controlling whether an alert can be triggered or not

### AdminAlertingChangedAlertConfigDetails

`class` 

Changed an alert setting.

### AdminAlertingChangedAlertConfigType

`class` 

Type for admin alerting changed alert config type.

### AdminAlertingTriggeredAlertDetails

`class` 

Triggered security alert.

### AdminAlertingTriggeredAlertType

`class` 

Type for admin alerting triggered alert type.

### AlertRecipientsSettingType

`enum` 

Alert recipients setting type

### RecipientsConfiguration

`class` 

Recipients Configuration

---

## Admin Console & Roles

### AdminConsoleAppPermission

`enum` 

Type for admin console app permission.

### AdminConsoleAppPolicy

`enum` 

Type for admin console app policy.

### AdminEmailRemindersChangedDetails

`class` 

Changed admin reminder settings for requests to join the team.

### AdminEmailRemindersChangedType

`class` 

Type for admin email reminders changed type.

### AdminEmailRemindersPolicy

`enum` 

Policy for deciding whether team admins receive reminder emails for requests to join the team

### AdminRole

`enum` 

Type for admin role.

---

## App Management

### AppBlockedByPermissionsDetails

`class` 

Failed to connect app for member.

### AppBlockedByPermissionsType

`class` 

Type for app blocked by permissions type.

### AppLinkTeamDetails

`class` 

Linked app for team.

### AppLinkTeamType

`class` 

Type for app link team type.

### AppLinkUserDetails

`class` 

Linked app for member.

### AppLinkUserType

`class` 

Type for app link user type.

### AppLogInfo

`class` 

App's logged information.

### AppPermissionsChangedDetails

`class` 

Changed app permissions.

### AppPermissionsChangedType

`class` 

Type for app permissions changed type.

### AppUnlinkTeamDetails

`class` 

Unlinked app for team.

### AppUnlinkTeamType

`class` 

Type for app unlink team type.

### AppUnlinkUserDetails

`class` 

Unlinked app for member.

### AppUnlinkUserType

`class` 

Type for app unlink user type.

### ApplyNamingConventionDetails

`class` 

Applied naming convention.

### ApplyNamingConventionType

`class` 

Type for apply naming convention type.

---

## Asset & Path Log Info

### AssetLogInfo

`enum` 

Asset details.

### FileLogInfo

`class` 

File's logged information.

### FolderLogInfo

`class` 

Folder's logged information.

### PathLogInfo

`class` 

Path's details.

---

## Backup & Computer Backup

### BackupAdminInvitationSentDetails

`class` 

Invited members to activate Backup.

### BackupAdminInvitationSentType

`class` 

Type for backup admin invitation sent type.

### BackupInvitationOpenedDetails

`class` 

Opened Backup invite.

### BackupInvitationOpenedType

`class` 

Type for backup invitation opened type.

### BackupStatus

`enum` 

Backup status

### ComputerBackupPolicy

`enum` 

Policy for controlling team access to computer backup feature

### ComputerBackupPolicyChangedDetails

`class` 

Changed computer backup policy for team.

### ComputerBackupPolicyChangedType

`class` 

Type for computer backup policy changed type.

---

## Binder Operations

### BinderAddPageDetails

`class` 

Added Binder page.

### BinderAddPageType

`class` 

Type for binder add page type.

### BinderAddSectionDetails

`class` 

Added Binder section.

### BinderAddSectionType

`class` 

Type for binder add section type.

### BinderRemovePageDetails

`class` 

Removed Binder page.

### BinderRemovePageType

`class` 

Type for binder remove page type.

### BinderRemoveSectionDetails

`class` 

Removed Binder section.

### BinderRemoveSectionType

`class` 

Type for binder remove section type.

### BinderRenamePageDetails

`class` 

Renamed Binder page.

### BinderRenamePageType

`class` 

Type for binder rename page type.

### BinderRenameSectionDetails

`class` 

Renamed Binder section.

### BinderRenameSectionType

`class` 

Type for binder rename section type.

### BinderReorderPageDetails

`class` 

Reordered Binder page.

### BinderReorderPageType

`class` 

Type for binder reorder page type.

### BinderReorderSectionDetails

`class` 

Reordered Binder section.

### BinderReorderSectionType

`class` 

Type for binder reorder section type.

---

## Camera & Capture

### CameraUploadsPolicy

`enum` 

Policy for controlling if team members can activate camera uploads

### CameraUploadsPolicyChangedDetails

`class` 

Changed camera uploads setting for team.

### CameraUploadsPolicyChangedType

`class` 

Type for camera uploads policy changed type.

### CaptureTranscriptPolicy

`enum` 

Policy for deciding whether team users can transcription in Capture

### CaptureTranscriptPolicyChangedDetails

`class` 

Changed Capture transcription policy for team.

### CaptureTranscriptPolicyChangedType

`class` 

Type for capture transcript policy changed type.

---

## Classification & Content

### ClassificationChangePolicyDetails

`class` 

Changed classification policy for team.

### ClassificationChangePolicyType

`class` 

Type for classification change policy type.

### ClassificationCreateReportDetails

`class` 

Created Classification report.

### ClassificationCreateReportFailDetails

`class` 

Couldn't create Classification report.

### ClassificationCreateReportFailType

`class` 

Type for classification create report fail type.

### ClassificationCreateReportType

`class` 

Type for classification create report type.

### ClassificationPolicyEnumWrapper

`enum` 

Policy for controlling team access to the classification feature

### ClassificationType

`enum` 

The type of classification (currently only personal information)

### ContentAdministrationPolicyChangedDetails

`class` 

Changed content management setting.

### ContentAdministrationPolicyChangedType

`class` 

Type for content administration policy changed type.

### ContentPermanentDeletePolicy

`enum` 

Policy for pemanent content deletion

---

## Collection & Naming

### CollectionShareDetails

`class` 

Shared album.

### CollectionShareType

`class` 

Type for collection share type.

---

## Common Supporting Types

### DurationLogInfo

`class` 

Represents a time duration: unit and amount

### FailureDetailsLogInfo

`class` 

Provides details about a failure

### PlacementRestriction

`enum` 

Type for placement restriction.

---

## Data Governance & Retention

### DataResidencyMigrationRequestSuccessfulDetails

`class` 

Requested data residency migration for team data.

### DataResidencyMigrationRequestSuccessfulType

`class` 

Type for data residency migration request successful type.

### DataResidencyMigrationRequestUnsuccessfulDetails

`class` 

Request for data residency migration for team data has failed.

### DataResidencyMigrationRequestUnsuccessfulType

`class` 

Type for data residency migration request unsuccessful type.

### DispositionActionType

`enum` 

Type for disposition action type.

---

## Device & Session Management

### DeviceApprovalsAddExceptionDetails

`class` 

Added members to device approvals exception list.

### DeviceApprovalsAddExceptionType

`class` 

Type for device approvals add exception type.

### DeviceApprovalsChangeDesktopPolicyDetails

`class` 

Set/removed limit on number of computers member can link to team Dropbox account.

### DeviceApprovalsChangeDesktopPolicyType

`class` 

Type for device approvals change desktop policy type.

### DeviceApprovalsChangeMobilePolicyDetails

`class` 

Set/removed limit on number of mobile devices member can link to team Dropbox account.

### DeviceApprovalsChangeMobilePolicyType

`class` 

Type for device approvals change mobile policy type.

### DeviceApprovalsChangeOverageActionDetails

`class` 

Changed device approvals setting when member is over limit.

### DeviceApprovalsChangeOverageActionType

`class` 

Type for device approvals change overage action type.

### DeviceApprovalsChangeUnlinkActionDetails

`class` 

Changed device approvals setting when member unlinks approved device.

### DeviceApprovalsChangeUnlinkActionType

`class` 

Type for device approvals change unlink action type.

### DeviceApprovalsPolicy

`enum` 

Type for device approvals policy.

### DeviceApprovalsRemoveExceptionDetails

`class` 

Removed members from device approvals exception list.

### DeviceApprovalsRemoveExceptionType

`class` 

Type for device approvals remove exception type.

### DeviceChangeIpDesktopDetails

`class` 

Changed IP address associated with active desktop session.

### DeviceChangeIpDesktopType

`class` 

Type for device change ip desktop type.

### DeviceChangeIpMobileDetails

`class` 

Changed IP address associated with active mobile session.

### DeviceChangeIpMobileType

`class` 

Type for device change ip mobile type.

### DeviceChangeIpWebDetails

`class` 

Changed IP address associated with active web session.

### DeviceChangeIpWebType

`class` 

Type for device change ip web type.

### DeviceDeleteOnUnlinkFailDetails

`class` 

Failed to delete all files from unlinked device.

### DeviceDeleteOnUnlinkFailType

`class` 

Type for device delete on unlink fail type.

### DeviceDeleteOnUnlinkSuccessDetails

`class` 

Deleted all files from unlinked device.

### DeviceDeleteOnUnlinkSuccessType

`class` 

Type for device delete on unlink success type.

### DeviceLinkFailDetails

`class` 

Failed to link device.

### DeviceLinkFailType

`class` 

Type for device link fail type.

### DeviceLinkSuccessDetails

`class` 

Linked device.

### DeviceLinkSuccessType

`class` 

Type for device link success type.

### DeviceManagementDisabledDetails

`class` 

Disabled device management.

### DeviceManagementDisabledType

`class` 

Type for device management disabled type.

### DeviceManagementEnabledDetails

`class` 

Enabled device management.

### DeviceManagementEnabledType

`class` 

Type for device management enabled type.

### DeviceSyncBackupStatusChangedDetails

`class` 

Enabled/disabled backup for computer.

### DeviceSyncBackupStatusChangedType

`class` 

Type for device sync backup status changed type.

### DeviceType

`enum` 

Type for device type.

### DeviceUnlinkDetails

`class` 

Disconnected device.

### DeviceUnlinkPolicy

`enum` 

Type for device unlink policy.

### DeviceUnlinkType

`class` 

Type for device unlink type.

### LinkedDeviceLogInfo

`enum` 

The device sessions that user is linked to.

---

## Domain & DNS

### DomainInvitesApproveRequestToJoinTeamDetails

`class` 

Approved user's request to join team.

### DomainInvitesApproveRequestToJoinTeamType

`class` 

Type for domain invites approve request to join team type.

### DomainInvitesDeclineRequestToJoinTeamDetails

`class` 

Declined user's request to join team.

### DomainInvitesDeclineRequestToJoinTeamType

`class` 

Type for domain invites decline request to join team type.

### DomainInvitesEmailExistingUsersDetails

`class` 

Sent domain invites to existing domain accounts.

### DomainInvitesEmailExistingUsersType

`class` 

Type for domain invites email existing users type.

### DomainInvitesRequestToJoinTeamDetails

`class` 

Requested to join team.

### DomainInvitesRequestToJoinTeamType

`class` 

Type for domain invites request to join team type.

### DomainInvitesSetInviteNewUserPrefToNoDetails

`class` 

Disabled "Automatically invite new users".

### DomainInvitesSetInviteNewUserPrefToNoType

`class` 

Type for domain invites set invite new user pref to no type.

### DomainInvitesSetInviteNewUserPrefToYesDetails

`class` 

Enabled "Automatically invite new users".

### DomainInvitesSetInviteNewUserPrefToYesType

`class` 

Type for domain invites set invite new user pref to yes type.

### DomainVerificationAddDomainFailDetails

`class` 

Failed to verify team domain.

### DomainVerificationAddDomainFailType

`class` 

Type for domain verification add domain fail type.

### DomainVerificationAddDomainSuccessDetails

`class` 

Verified team domain.

### DomainVerificationAddDomainSuccessType

`class` 

Type for domain verification add domain success type.

### DomainVerificationRemoveDomainDetails

`class` 

Removed domain from list of verified team domains.

### DomainVerificationRemoveDomainType

`class` 

Type for domain verification remove domain type.

---

## Domain & Feature Settings

### DisabledDomainInvitesDetails

`class` 

Disabled domain invites.

### DisabledDomainInvitesType

`class` 

Type for disabled domain invites type.

### EnabledDomainInvitesDetails

`class` 

Enabled domain invites.

### EnabledDomainInvitesType

`class` 

Type for enabled domain invites type.

---

## Dropbox Passwords

### DropboxPasswordsExportedDetails

`class` 

Exported passwords.

### DropboxPasswordsExportedType

`class` 

Type for dropbox passwords exported type.

### DropboxPasswordsNewDeviceEnrolledDetails

`class` 

Enrolled new Dropbox Passwords device.

### DropboxPasswordsNewDeviceEnrolledType

`class` 

Type for dropbox passwords new device enrolled type.

### DropboxPasswordsPolicy

`enum` 

Policy for deciding whether team users can use Dropbox Passwords

### DropboxPasswordsPolicyChangedDetails

`class` 

Changed Dropbox Passwords policy for team.

### DropboxPasswordsPolicyChangedType

`class` 

Type for dropbox passwords policy changed type.

---

## Email Ingest

### EmailIngestPolicy

`enum` 

Policy for deciding whether a team can use Email to Dropbox feature

### EmailIngestPolicyChangedDetails

`class` 

Changed email to Dropbox policy for team.

### EmailIngestPolicyChangedType

`class` 

Type for email ingest policy changed type.

### EmailIngestReceiveFileDetails

`class` 

Received files via Email to Dropbox.

### EmailIngestReceiveFileType

`class` 

Type for email ingest receive file type.

---

## EMM & Mobile Device Management

### EmmAddExceptionDetails

`class` 

Added members to EMM exception list.

### EmmAddExceptionType

`class` 

Type for emm add exception type.

### EmmChangePolicyDetails

`class` 

Enabled/disabled enterprise mobility management for members.

### EmmChangePolicyType

`class` 

Type for emm change policy type.

### EmmCreateExceptionsReportDetails

`class` 

Created EMM-excluded users report.

### EmmCreateExceptionsReportType

`class` 

Type for emm create exceptions report type.

### EmmCreateUsageReportDetails

`class` 

Created EMM mobile app usage report.

### EmmCreateUsageReportType

`class` 

Type for emm create usage report type.

### EmmErrorDetails

`class` 

Failed to sign in via EMM.

### EmmErrorType

`class` 

Type for emm error type.

### EmmRefreshAuthTokenDetails

`class` 

Refreshed auth token used for setting up EMM.

### EmmRefreshAuthTokenType

`class` 

Type for emm refresh auth token type.

### EmmRemoveExceptionDetails

`class` 

Removed members from EMM exception list.

### EmmRemoveExceptionType

`class` 

Type for emm remove exception type.

---

## Enterprise & Federation

### ChangedEnterpriseAdminRoleDetails

`class` 

Changed enterprise admin role.

### ChangedEnterpriseAdminRoleType

`class` 

Type for changed enterprise admin role type.

### ChangedEnterpriseConnectedTeamStatusDetails

`class` 

Changed enterprise-connected team status.

### ChangedEnterpriseConnectedTeamStatusType

`class` 

Type for changed enterprise connected team status type.

### ConnectedTeamName

`class` 

The name of the team

### EndedEnterpriseAdminSessionDeprecatedDetails

`class` 

Ended enterprise admin session.

### EndedEnterpriseAdminSessionDeprecatedType

`class` 

Type for ended enterprise admin session deprecated type.

### EndedEnterpriseAdminSessionDetails

`class` 

Ended enterprise admin session.

### EndedEnterpriseAdminSessionType

`class` 

Type for ended enterprise admin session type.

### EnterpriseSettingsLockingDetails

`class` 

Changed who can update a setting.

### EnterpriseSettingsLockingType

`class` 

Type for enterprise settings locking type.

### FedAdminRole

`enum` 

Type for fed admin role.

### FedExtraDetails

`enum` 

More details about the organization or team.

### FedHandshakeAction

`enum` 

Type for fed handshake action.

### FederationStatusChangeAdditionalInfo

`enum` 

Additional information about the organization or connected team

### StartedEnterpriseAdminSessionDetails

`class` 

Started enterprise admin session.

### StartedEnterpriseAdminSessionType

`class` 

Type for started enterprise admin session type.

---

## Export & Reporting

### ExportMembersReportDetails

`class` 

Created member data report.

### ExportMembersReportFailDetails

`class` 

Failed to create members data report.

### ExportMembersReportFailType

`class` 

Type for export members report fail type.

### ExportMembersReportType

`class` 

Type for export members report type.

---

## External Sharing & Users

### ExternalDriveBackupEligibilityStatus

`enum` 

External Drive Backup eligibility status

### ExternalDriveBackupEligibilityStatusCheckedDetails

`class` 

Checked external drive backup eligibility status.

### ExternalDriveBackupEligibilityStatusCheckedType

`class` 

Type for external drive backup eligibility status checked type.

### ExternalDriveBackupPolicy

`enum` 

Policy for controlling team access to external drive backup feature

### ExternalDriveBackupPolicyChangedDetails

`class` 

Changed external drive backup policy for team.

### ExternalDriveBackupPolicyChangedType

`class` 

Type for external drive backup policy changed type.

### ExternalDriveBackupStatus

`enum` 

External Drive Backup status

### ExternalDriveBackupStatusChangedDetails

`class` 

Modified external drive backup.

### ExternalDriveBackupStatusChangedType

`class` 

Type for external drive backup status changed type.

### ExternalSharingCreateReportDetails

`class` 

Created External sharing report.

### ExternalSharingCreateReportType

`class` 

Type for external sharing create report type.

### ExternalSharingReportFailedDetails

`class` 

Couldn't create External sharing report.

### ExternalSharingReportFailedType

`class` 

Type for external sharing report failed type.

### ExternalUserLogInfo

`class` 

A user without a Dropbox account.

### GuestAdminChangeStatusDetails

`class` 

Changed guest team admin status.

### GuestAdminChangeStatusType

`class` 

Type for guest admin change status type.

### GuestAdminSignedInViaTrustedTeamsDetails

`class` 

Started trusted team admin session.

### GuestAdminSignedInViaTrustedTeamsType

`class` 

Type for guest admin signed in via trusted teams type.

### GuestAdminSignedOutViaTrustedTeamsDetails

`class` 

Ended trusted team admin session.

### GuestAdminSignedOutViaTrustedTeamsType

`class` 

Type for guest admin signed out via trusted teams type.

---

## Feature Settings

### AllowDownloadDisabledDetails

`class` 

Disabled downloads.

### AllowDownloadDisabledType

`class` 

Type for allow download disabled type.

### AllowDownloadEnabledDetails

`class` 

Enabled downloads.

### AllowDownloadEnabledType

`class` 

Type for allow download enabled type.

### NoPasswordLinkGenCreateReportDetails

`class` 

Report created: Links created without passwords.

### NoPasswordLinkGenCreateReportType

`class` 

Type for no password link gen create report type.

### NoPasswordLinkGenReportFailedDetails

`class` 

Couldn't create report: Links created without passwords.

### NoPasswordLinkGenReportFailedType

`class` 

Type for no password link gen report failed type.

### NoPasswordLinkViewCreateReportDetails

`class` 

Report created: Views of links without passwords.

### NoPasswordLinkViewCreateReportType

`class` 

Type for no password link view create report type.

### NoPasswordLinkViewReportFailedDetails

`class` 

Couldn't create report: Views of links without passwords.

### NoPasswordLinkViewReportFailedType

`class` 

Type for no password link view report failed type.

---

## File & Folder Operations

### CreateFolderDetails

`class` 

Created folders.

### CreateFolderType

`class` 

Type for create folder type.

### DirectoryRestrictionsAddMembersDetails

`class` 

Added members to directory restrictions list.

### DirectoryRestrictionsAddMembersType

`class` 

Type for directory restrictions add members type.

### DirectoryRestrictionsRemoveMembersDetails

`class` 

Removed members from directory restrictions list.

### DirectoryRestrictionsRemoveMembersType

`class` 

Type for directory restrictions remove members type.

### FileAddCommentDetails

`class` 

Added file comment.

### FileAddCommentType

`class` 

Type for file add comment type.

### FileAddDetails

`class` 

Added files and/or folders.

### FileAddFromAutomationDetails

`class` 

Added files and/or folders from automation.

### FileAddFromAutomationType

`class` 

Type for file add from automation type.

### FileAddType

`class` 

Type for file add type.

### FileChangeCommentSubscriptionDetails

`class` 

Subscribed to or unsubscribed from comment notifications for file.

### FileChangeCommentSubscriptionType

`class` 

Type for file change comment subscription type.

### FileCommentNotificationPolicy

`enum` 

Enable or disable file comments notifications

### FileCommentsChangePolicyDetails

`class` 

Enabled/disabled commenting on team files.

### FileCommentsChangePolicyType

`class` 

Type for file comments change policy type.

### FileCommentsPolicy

`enum` 

File comments policy

### FileCopyDetails

`class` 

Copied files and/or folders.

### FileCopyType

`class` 

Type for file copy type.

### FileDeleteCommentDetails

`class` 

Deleted file comment.

### FileDeleteCommentType

`class` 

Type for file delete comment type.

### FileDeleteDetails

`class` 

Deleted files and/or folders.

### FileDeleteType

`class` 

Type for file delete type.

### FileDownloadDetails

`class` 

Downloaded files and/or folders.

### FileDownloadType

`class` 

Type for file download type.

### FileEditCommentDetails

`class` 

Edited file comment.

### FileEditCommentType

`class` 

Type for file edit comment type.

### FileEditDetails

`class` 

Edited files.

### FileEditType

`class` 

Type for file edit type.

### FileGetCopyReferenceDetails

`class` 

Created copy reference to file/folder.

### FileGetCopyReferenceType

`class` 

Type for file get copy reference type.

### FileLikeCommentDetails

`class` 

Liked file comment.

### FileLikeCommentType

`class` 

Type for file like comment type.

### FileLockingLockStatusChangedDetails

`class` 

Locked/unlocked editing for a file.

### FileLockingLockStatusChangedType

`class` 

Type for file locking lock status changed type.

### FileLockingPolicyChangedDetails

`class` 

Changed file locking policy for team.

### FileLockingPolicyChangedType

`class` 

Type for file locking policy changed type.

### FileOrFolderLogInfo

`class` 

Generic information relevant both for files and folders

### FileMoveDetails

`class` 

Moved files and/or folders.

### FileMoveType

`class` 

Type for file move type.

### FilePermanentlyDeleteDetails

`class` 

Permanently deleted files and/or folders.

### FilePermanentlyDeleteType

`class` 

Type for file permanently delete type.

### FilePreviewDetails

`class` 

Previewed files and/or folders.

### FilePreviewType

`class` 

Type for file preview type.

### FileProviderMigrationPolicyChangedDetails

`class` 

Changed File Provider Migration policy for team.

### FileProviderMigrationPolicyChangedType

`class` 

Type for file provider migration policy changed type.

### FileRenameDetails

`class` 

Renamed files and/or folders.

### FileRenameType

`class` 

Type for file rename type.

### FileRequestChangeDetails

`class` 

Changed file request.

### FileRequestChangeType

`class` 

Type for file request change type.

### FileRequestCloseDetails

`class` 

Closed file request.

### FileRequestCloseType

`class` 

Type for file request close type.

### FileRequestCreateDetails

`class` 

Created file request.

### FileRequestCreateType

`class` 

Type for file request create type.

### FileRequestDeadline

`class` 

File request deadline

### FileRequestDeleteDetails

`class` 

Delete file request.

### FileRequestDeleteType

`class` 

Type for file request delete type.

### FileRequestDetails

`class` 

File request details

### FileRequestReceiveFileDetails

`class` 

Received files for file request.

### FileRequestReceiveFileType

`class` 

Type for file request receive file type.

### FileRequestsChangePolicyDetails

`class` 

Enabled/disabled file requests.

### FileRequestsChangePolicyType

`class` 

Type for file requests change policy type.

### FileRequestsEmailsEnabledDetails

`class` 

Enabled file request emails for everyone.

### FileRequestsEmailsEnabledType

`class` 

Type for file requests emails enabled type.

### FileRequestsEmailsRestrictedToTeamOnlyDetails

`class` 

Enabled file request emails for team.

### FileRequestsEmailsRestrictedToTeamOnlyType

`class` 

Type for file requests emails restricted to team only type.

### FileRequestsPolicy

`enum` 

File requests policy

### FileResolveCommentDetails

`class` 

Resolved file comment.

### FileResolveCommentType

`class` 

Type for file resolve comment type.

### FileRestoreDetails

`class` 

Restored deleted files and/or folders.

### FileRestoreType

`class` 

Type for file restore type.

### FileRevertDetails

`class` 

Reverted files to previous version.

### FileRevertType

`class` 

Type for file revert type.

### FileRollbackChangesDetails

`class` 

Rolled back file actions.

### FileRollbackChangesType

`class` 

Type for file rollback changes type.

### FileSaveCopyReferenceDetails

`class` 

Saved file/folder using copy reference.

### FileSaveCopyReferenceType

`class` 

Type for file save copy reference type.

### FileTransfersFileAddDetails

`class` 

Transfer files added.

### FileTransfersFileAddType

`class` 

Type for file transfers file add type.

### FileTransfersPolicy

`enum` 

File transfers policy

### FileTransfersPolicyChangedDetails

`class` 

Changed file transfers policy for team.

### FileTransfersPolicyChangedType

`class` 

Type for file transfers policy changed type.

### FileTransfersTransferDeleteDetails

`class` 

Deleted transfer.

### FileTransfersTransferDeleteType

`class` 

Type for file transfers transfer delete type.

### FileTransfersTransferDownloadDetails

`class` 

Transfer downloaded.

### FileTransfersTransferDownloadType

`class` 

Type for file transfers transfer download type.

### FileTransfersTransferSendDetails

`class` 

Sent transfer.

### FileTransfersTransferSendType

`class` 

Type for file transfers transfer send type.

### FileTransfersTransferViewDetails

`class` 

Viewed transfer.

### FileTransfersTransferViewType

`class` 

Type for file transfers transfer view type.

### FileUnlikeCommentDetails

`class` 

Unliked file comment.

### FileUnlikeCommentType

`class` 

Type for file unlike comment type.

### FileUnresolveCommentDetails

`class` 

Unresolved file comment.

### FileUnresolveCommentType

`class` 

Type for file unresolve comment type.

### FolderLinkRestrictionPolicy

`enum` 

Policy for deciding whether applying link restrictions on all team owned folders

### FolderLinkRestrictionPolicyChangedDetails

`class` 

Changed folder link restrictions policy for team.

### FolderLinkRestrictionPolicyChangedType

`class` 

Type for folder link restriction policy changed type.

### FolderOverviewDescriptionChangedDetails

`class` 

Updated folder overview.

### FolderOverviewDescriptionChangedType

`class` 

Type for folder overview description changed type.

### FolderOverviewItemPinnedDetails

`class` 

Pinned item to folder overview.

### FolderOverviewItemPinnedType

`class` 

Type for folder overview item pinned type.

### FolderOverviewItemUnpinnedDetails

`class` 

Unpinned item from folder overview.

### FolderOverviewItemUnpinnedType

`class` 

Type for folder overview item unpinned type.

### ObjectLabelAddedDetails

`class` 

Added a label.

### ObjectLabelAddedType

`class` 

Type for object label added type.

### ObjectLabelRemovedDetails

`class` 

Removed a label.

### ObjectLabelRemovedType

`class` 

Type for object label removed type.

### ObjectLabelUpdatedValueDetails

`class` 

Updated a label's value.

### ObjectLabelUpdatedValueType

`class` 

Type for object label updated value type.

### RewindFolderDetails

`class` 

Rewound a folder.

### RewindFolderType

`class` 

Type for rewind folder type.

### UndoNamingConventionDetails

`class` 

Reverted naming convention.

### UndoNamingConventionType

`class` 

Type for undo naming convention type.

### UndoOrganizeFolderWithTidyDetails

`class` 

Removed multi-file organize.

### UndoOrganizeFolderWithTidyType

`class` 

Type for undo organize folder with tidy type.

---

## Group Management

### GroupAddExternalIdDetails

`class` 

Added external ID for group.

### GroupAddExternalIdType

`class` 

Type for group add external id type.

### GroupAddMemberDetails

`class` 

Added team members to group.

### GroupAddMemberType

`class` 

Type for group add member type.

### GroupChangeExternalIdDetails

`class` 

Changed external ID for group.

### GroupChangeExternalIdType

`class` 

Type for group change external id type.

### GroupChangeManagementTypeDetails

`class` 

Changed group management type.

### GroupChangeManagementTypeType

`class` 

Type for group change management type type.

### GroupChangeMemberRoleDetails

`class` 

Changed manager permissions of group member.

### GroupChangeMemberRoleType

`class` 

Type for group change member role type.

### GroupCreateDetails

`class` 

Created group.

### GroupCreateType

`class` 

Type for group create type.

### GroupDeleteDetails

`class` 

Deleted group.

### GroupDeleteType

`class` 

Type for group delete type.

### GroupDescriptionUpdatedDetails

`class` 

Updated group.

### GroupDescriptionUpdatedType

`class` 

Type for group description updated type.

### GroupJoinPolicy

`enum` 

Type for group join policy.

### GroupJoinPolicyUpdatedDetails

`class` 

Updated group join policy.

### GroupJoinPolicyUpdatedType

`class` 

Type for group join policy updated type.

### GroupLogInfo

`class` 

Group's logged information.

### GroupMovedDetails

`class` 

Moved group.

### GroupMovedType

`class` 

Type for group moved type.

### GroupRemoveExternalIdDetails

`class` 

Removed external ID for group.

### GroupRemoveExternalIdType

`class` 

Type for group remove external id type.

### GroupRemoveMemberDetails

`class` 

Removed team members from group.

### GroupRemoveMemberType

`class` 

Type for group remove member type.

### GroupRenameDetails

`class` 

Renamed group.

### GroupRenameType

`class` 

Type for group rename type.

### GroupUserManagementChangePolicyDetails

`class` 

Changed who can create groups.

### GroupUserManagementChangePolicyType

`class` 

Type for group user management change policy type.

---

## Integration & Third-Party

### GoogleSsoChangePolicyDetails

`class` 

Enabled/disabled Google single sign-on for team.

### GoogleSsoChangePolicyType

`class` 

Type for google sso change policy type.

### GoogleSsoPolicy

`enum` 

Google SSO policy

### IntegrationConnectedDetails

`class` 

Connected integration for member.

### IntegrationConnectedType

`class` 

Type for integration connected type.

### IntegrationDisconnectedDetails

`class` 

Disconnected integration for member.

### IntegrationDisconnectedType

`class` 

Type for integration disconnected type.

### IntegrationPolicy

`enum` 

Policy for controlling whether a service integration is enabled for the team.

### IntegrationPolicyChangedDetails

`class` 

Changed integration policy for team.

### IntegrationPolicyChangedType

`class` 

Type for integration policy changed type.

---

## Legal Holds

### LegalHoldsActivateAHoldDetails

`class` 

Activated a hold.

### LegalHoldsActivateAHoldType

`class` 

Type for legal holds activate a hold type.

### LegalHoldsAddMembersDetails

`class` 

Added members to a hold.

### LegalHoldsAddMembersType

`class` 

Type for legal holds add members type.

### LegalHoldsChangeHoldDetailsDetails

`class` 

Edited details for a hold.

### LegalHoldsChangeHoldDetailsType

`class` 

Type for legal holds change hold details type.

### LegalHoldsChangeHoldNameDetails

`class` 

Renamed a hold.

### LegalHoldsChangeHoldNameType

`class` 

Type for legal holds change hold name type.

### LegalHoldsExportAHoldDetails

`class` 

Exported hold.

### LegalHoldsExportAHoldType

`class` 

Type for legal holds export a hold type.

### LegalHoldsExportCancelledDetails

`class` 

Canceled export for a hold.

### LegalHoldsExportCancelledType

`class` 

Type for legal holds export cancelled type.

### LegalHoldsExportDownloadedDetails

`class` 

Downloaded export for a hold.

### LegalHoldsExportDownloadedType

`class` 

Type for legal holds export downloaded type.

### LegalHoldsExportRemovedDetails

`class` 

Removed export for a hold.

### LegalHoldsExportRemovedType

`class` 

Type for legal holds export removed type.

### LegalHoldsReleaseAHoldDetails

`class` 

Released a hold.

### LegalHoldsReleaseAHoldType

`class` 

Type for legal holds release a hold type.

### LegalHoldsRemoveMembersDetails

`class` 

Removed members from a hold.

### LegalHoldsRemoveMembersType

`class` 

Type for legal holds remove members type.

### LegalHoldsReportAHoldDetails

`class` 

Created a summary report for a hold.

### LegalHoldsReportAHoldType

`class` 

Type for legal holds report a hold type.

---

## Login & Authentication

### LoginFailDetails

`class` 

Failed to sign in.

### LoginFailType

`class` 

Type for login fail type.

### LoginMethod

`enum` 

Type for login method.

### LoginSuccessDetails

`class` 

Signed in.

### LoginSuccessType

`class` 

Type for login success type.

### LogoutDetails

`class` 

Signed out.

### LogoutType

`class` 

Type for logout type.

### SignInAsSessionEndDetails

`class` 

Ended admin sign-in-as session.

### SignInAsSessionEndType

`class` 

Type for sign in as session end type.

### SignInAsSessionStartDetails

`class` 

Started admin sign-in-as session.

### SignInAsSessionStartType

`class` 

Type for sign in as session start type.

---

## Member Management

### InviteAcceptanceEmailPolicy

`enum` 

Policy for deciding whether team admins receive email when an invitation to join the team is accepted

### InviteAcceptanceEmailPolicyChangedDetails

`class` 

Changed invite accept email policy for team.

### InviteAcceptanceEmailPolicyChangedType

`class` 

Type for invite acceptance email policy changed type.

### InviteMethod

`enum` 

Type for invite method.

### JoinTeamDetails

`class` 

Additional information relevant when a new member joins the team.

### MemberAddExternalIdDetails

`class` 

Added an external ID for team member.

### MemberAddExternalIdType

`class` 

Type for member add external id type.

### MemberAddNameDetails

`class` 

Added team member name.

### MemberAddNameType

`class` 

Type for member add name type.

### MemberChangeAdminRoleDetails

`class` 

Changed team member admin role.

### MemberChangeAdminRoleType

`class` 

Type for member change admin role type.

### MemberChangeEmailDetails

`class` 

Changed team member email.

### MemberChangeEmailType

`class` 

Type for member change email type.

### MemberChangeExternalIdDetails

`class` 

Changed the external ID for team member.

### MemberChangeExternalIdType

`class` 

Type for member change external id type.

### MemberChangeMembershipTypeDetails

`class` 

Changed membership type (limited/full) of member.

### MemberChangeMembershipTypeType

`class` 

Type for member change membership type type.

### MemberChangeNameDetails

`class` 

Changed team member name.

### MemberChangeNameType

`class` 

Type for member change name type.

### MemberChangeResellerRoleDetails

`class` 

Changed team member reseller role.

### MemberChangeResellerRoleType

`class` 

Type for member change reseller role type.

### MemberChangeStatusDetails

`class` 

Changed member status (invited, joined, suspended, etc.).

### MemberChangeStatusType

`class` 

Type for member change status type.

### MemberDeleteManualContactsDetails

`class` 

Cleared manually added contacts.

### MemberDeleteManualContactsType

`class` 

Type for member delete manual contacts type.

### MemberDeleteProfilePhotoDetails

`class` 

Deleted team member profile photo.

### MemberDeleteProfilePhotoType

`class` 

Type for member delete profile photo type.

### MemberPermanentlyDeleteAccountContentsDetails

`class` 

Permanently deleted contents of deleted team member account.

### MemberPermanentlyDeleteAccountContentsType

`class` 

Type for member permanently delete account contents type.

### MemberRemoveActionType

`enum` 

Type for member remove action type.

### MemberRemoveExternalIdDetails

`class` 

Removed the external ID for team member.

### MemberRemoveExternalIdType

`class` 

Type for member remove external id type.

### MemberRequestsChangePolicyDetails

`class` 

Changed whether users can find team when not invited.

### MemberRequestsChangePolicyType

`class` 

Type for member requests change policy type.

### MemberRequestsPolicy

`enum` 

Type for member requests policy.

### MemberSendInvitePolicy

`enum` 

Policy for controlling whether team members can send team invites

### MemberSendInvitePolicyChangedDetails

`class` 

Changed member send invite policy for team.

### MemberSendInvitePolicyChangedType

`class` 

Type for member send invite policy changed type.

### MemberSetProfilePhotoDetails

`class` 

Set team member profile photo.

### MemberSetProfilePhotoType

`class` 

Type for member set profile photo type.

### MemberSpaceLimitsAddCustomQuotaDetails

`class` 

Set custom member space limit.

### MemberSpaceLimitsAddCustomQuotaType

`class` 

Type for member space limits add custom quota type.

### MemberSpaceLimitsAddExceptionDetails

`class` 

Added members to member space limit exception list.

### MemberSpaceLimitsAddExceptionType

`class` 

Type for member space limits add exception type.

### MemberSpaceLimitsChangeCapsTypePolicyDetails

`class` 

Changed member space limit type for team.

### MemberSpaceLimitsChangeCapsTypePolicyType

`class` 

Type for member space limits change caps type policy type.

### MemberSpaceLimitsChangeCustomQuotaDetails

`class` 

Changed custom member space limit.

### MemberSpaceLimitsChangeCustomQuotaType

`class` 

Type for member space limits change custom quota type.

### MemberSpaceLimitsChangePolicyDetails

`class` 

Changed team default member space limit.

### MemberSpaceLimitsChangePolicyType

`class` 

Type for member space limits change policy type.

### MemberSpaceLimitsChangeStatusDetails

`class` 

Changed space limit status.

### MemberSpaceLimitsChangeStatusType

`class` 

Type for member space limits change status type.

### MemberSpaceLimitsRemoveCustomQuotaDetails

`class` 

Removed custom member space limit.

### MemberSpaceLimitsRemoveCustomQuotaType

`class` 

Type for member space limits remove custom quota type.

### MemberSpaceLimitsRemoveExceptionDetails

`class` 

Removed members from member space limit exception list.

### MemberSpaceLimitsRemoveExceptionType

`class` 

Type for member space limits remove exception type.

### MemberStatus

`enum` 

Type for member status.

### MemberSuggestDetails

`class` 

Suggested person to add to team.

### MemberSuggestType

`class` 

Type for member suggest type.

### MemberSuggestionsChangePolicyDetails

`class` 

Enabled/disabled option for team members to suggest people to add to team.

### MemberSuggestionsChangePolicyType

`class` 

Type for member suggestions change policy type.

### MemberSuggestionsPolicy

`enum` 

Member suggestions policy

### MemberTransferAccountContentsDetails

`class` 

Transferred contents of deleted member account to another member.

### MemberTransferAccountContentsType

`class` 

Type for member transfer account contents type.

### MemberTransferredInternalFields

`class` 

Internal only - fields for target team computations

### SecondaryEmailDeletedDetails

`class` 

Deleted secondary email.

### SecondaryEmailDeletedType

`class` 

Type for secondary email deleted type.

### SecondaryEmailVerifiedDetails

`class` 

Verified secondary email.

### SecondaryEmailVerifiedType

`class` 

Type for secondary email verified type.

### TeamInviteDetails

`class` 

Details about team invites

### TeamMergeFromDetails

`class` 

Merged another team into this team.

### TeamMergeFromType

`class` 

Type for team merge from type.

### TeamMergeRequestAcceptedDetails

`class` 

Accepted a team merge request.

### TeamMergeRequestAcceptedExtraDetails

`enum` 

Team merge request acceptance details

### TeamMergeRequestAcceptedShownToPrimaryTeamDetails

`class` 

Accepted a team merge request.

### TeamMergeRequestAcceptedShownToPrimaryTeamType

`class` 

Type for team merge request accepted shown to primary team type.

### TeamMergeRequestAcceptedShownToSecondaryTeamDetails

`class` 

Accepted a team merge request.

### TeamMergeRequestAcceptedShownToSecondaryTeamType

`class` 

Type for team merge request accepted shown to secondary team type.

### TeamMergeRequestAcceptedType

`class` 

Type for team merge request accepted type.

### TeamMergeRequestAutoCanceledDetails

`class` 

Automatically canceled team merge request.

### TeamMergeRequestAutoCanceledType

`class` 

Type for team merge request auto canceled type.

### TeamMergeRequestCanceledDetails

`class` 

Canceled a team merge request.

### TeamMergeRequestCanceledExtraDetails

`enum` 

Team merge request cancellation details

### TeamMergeRequestCanceledShownToPrimaryTeamDetails

`class` 

Canceled a team merge request.

### TeamMergeRequestCanceledShownToPrimaryTeamType

`class` 

Type for team merge request canceled shown to primary team type.

### TeamMergeRequestCanceledShownToSecondaryTeamDetails

`class` 

Canceled a team merge request.

### TeamMergeRequestCanceledShownToSecondaryTeamType

`class` 

Type for team merge request canceled shown to secondary team type.

### TeamMergeRequestCanceledType

`class` 

Type for team merge request canceled type.

### TeamMergeRequestExpiredDetails

`class` 

Team merge request expired.

### TeamMergeRequestExpiredExtraDetails

`enum` 

Team merge request expiration details

### TeamMergeRequestExpiredShownToPrimaryTeamDetails

`class` 

Team merge request expired.

### TeamMergeRequestExpiredShownToPrimaryTeamType

`class` 

Type for team merge request expired shown to primary team type.

### TeamMergeRequestExpiredShownToSecondaryTeamDetails

`class` 

Team merge request expired.

### TeamMergeRequestExpiredShownToSecondaryTeamType

`class` 

Type for team merge request expired shown to secondary team type.

### TeamMergeRequestExpiredType

`class` 

Type for team merge request expired type.

### TeamMergeRequestRejectedShownToPrimaryTeamDetails

`class` 

Rejected a team merge request.

### TeamMergeRequestRejectedShownToPrimaryTeamType

`class` 

Type for team merge request rejected shown to primary team type.

### TeamMergeRequestRejectedShownToSecondaryTeamDetails

`class` 

Rejected a team merge request.

### TeamMergeRequestRejectedShownToSecondaryTeamType

`class` 

Type for team merge request rejected shown to secondary team type.

### TeamMergeRequestReminderDetails

`class` 

Sent a team merge request reminder.

### TeamMergeRequestReminderExtraDetails

`enum` 

Team merge request reminder details

### TeamMergeRequestReminderShownToPrimaryTeamDetails

`class` 

Sent a team merge request reminder.

### TeamMergeRequestReminderShownToPrimaryTeamType

`class` 

Type for team merge request reminder shown to primary team type.

### TeamMergeRequestReminderShownToSecondaryTeamDetails

`class` 

Sent a team merge request reminder.

### TeamMergeRequestReminderShownToSecondaryTeamType

`class` 

Type for team merge request reminder shown to secondary team type.

### TeamMergeRequestReminderType

`class` 

Type for team merge request reminder type.

### TeamMergeRequestRevokedDetails

`class` 

Canceled the team merge.

### TeamMergeRequestRevokedType

`class` 

Type for team merge request revoked type.

### TeamMergeRequestSentShownToPrimaryTeamDetails

`class` 

Requested to merge their Dropbox team into yours.

### TeamMergeRequestSentShownToPrimaryTeamType

`class` 

Type for team merge request sent shown to primary team type.

### TeamMergeRequestSentShownToSecondaryTeamDetails

`class` 

Requested to merge your team into another Dropbox team.

### TeamMergeRequestSentShownToSecondaryTeamType

`class` 

Type for team merge request sent shown to secondary team type.

### TeamMergeToDetails

`class` 

Merged this team into another team.

### TeamMergeToType

`class` 

Type for team merge to type.

---

## Namespace

### NamespaceRelativePathLogInfo

`class` 

Namespace relative path details.

---

## Network & Geo

### GeoLocationLogInfo

`class` 

Geographic location details.

### NetworkControlChangePolicyDetails

`class` 

Enabled/disabled network control.

### NetworkControlChangePolicyType

`class` 

Type for network control change policy type.

### NetworkControlPolicy

`enum` 

Network control policy

---

## Paper & Notes

### NoteAclInviteOnlyDetails

`class` 

Changed Paper doc to invite-only.

### NoteAclInviteOnlyType

`class` 

Type for note acl invite only type.

### NoteAclLinkDetails

`class` 

Changed Paper doc to link-accessible.

### NoteAclLinkType

`class` 

Type for note acl link type.

### NoteAclTeamLinkDetails

`class` 

Changed Paper doc to link-accessible for team.

### NoteAclTeamLinkType

`class` 

Type for note acl team link type.

### NoteShareReceiveDetails

`class` 

Shared received Paper doc.

### NoteShareReceiveType

`class` 

Type for note share receive type.

### NoteSharedDetails

`class` 

Shared Paper doc.

### NoteSharedType

`class` 

Type for note shared type.

### PaperAccessType

`enum` 

Type for paper access type.

### PaperAdminExportStartDetails

`class` 

Exported all team Paper docs.

### PaperAdminExportStartType

`class` 

Type for paper admin export start type.

### PaperChangeDeploymentPolicyDetails

`class` 

Changed whether Dropbox Paper, when enabled, is deployed to all members or to specific members.

### PaperChangeDeploymentPolicyType

`class` 

Type for paper change deployment policy type.

### PaperChangeMemberLinkPolicyDetails

`class` 

Changed whether non-members can view Paper docs with link.

### PaperChangeMemberLinkPolicyType

`class` 

Type for paper change member link policy type.

### PaperChangeMemberPolicyDetails

`class` 

anyone by default.

### PaperChangeMemberPolicyType

`class` 

Type for paper change member policy type.

### PaperChangePolicyDetails

`class` 

Enabled/disabled Dropbox Paper for team.

### PaperChangePolicyType

`class` 

Type for paper change policy type.

### PaperContentAddMemberDetails

`class` 

Added users and/or groups to Paper doc/folder.

### PaperContentAddMemberType

`class` 

Type for paper content add member type.

### PaperContentAddToFolderDetails

`class` 

Added Paper doc/folder to folder.

### PaperContentAddToFolderType

`class` 

Type for paper content add to folder type.

### PaperContentArchiveDetails

`class` 

Archived Paper doc/folder.

### PaperContentArchiveType

`class` 

Type for paper content archive type.

### PaperContentCreateDetails

`class` 

Created Paper doc/folder.

### PaperContentCreateType

`class` 

Type for paper content create type.

### PaperContentPermanentlyDeleteDetails

`class` 

Permanently deleted Paper doc/folder.

### PaperContentPermanentlyDeleteType

`class` 

Type for paper content permanently delete type.

### PaperContentRemoveFromFolderDetails

`class` 

Removed Paper doc/folder from folder.

### PaperContentRemoveFromFolderType

`class` 

Type for paper content remove from folder type.

### PaperContentRemoveMemberDetails

`class` 

Removed users and/or groups from Paper doc/folder.

### PaperContentRemoveMemberType

`class` 

Type for paper content remove member type.

### PaperContentRenameDetails

`class` 

Renamed Paper doc/folder.

### PaperContentRenameType

`class` 

Type for paper content rename type.

### PaperContentRestoreDetails

`class` 

Restored archived Paper doc/folder.

### PaperContentRestoreType

`class` 

Type for paper content restore type.

### PaperDefaultFolderPolicy

`enum` 

Policy to set default access for newly created Paper folders.

### PaperDefaultFolderPolicyChangedDetails

`class` 

Changed Paper Default Folder Policy setting for team.

### PaperDefaultFolderPolicyChangedType

`class` 

Type for paper default folder policy changed type.

### PaperDesktopPolicy

`enum` 

Policy for controlling if team members can use Paper Desktop

### PaperDesktopPolicyChangedDetails

`class` 

Enabled/disabled Paper Desktop for team.

### PaperDesktopPolicyChangedType

`class` 

Type for paper desktop policy changed type.

### PaperDocAddCommentDetails

`class` 

Added Paper doc comment.

### PaperDocAddCommentType

`class` 

Type for paper doc add comment type.

### PaperDocChangeMemberRoleDetails

`class` 

Changed member permissions for Paper doc.

### PaperDocChangeMemberRoleType

`class` 

Type for paper doc change member role type.

### PaperDocChangeSharingPolicyDetails

`class` 

Changed sharing setting for Paper doc.

### PaperDocChangeSharingPolicyType

`class` 

Type for paper doc change sharing policy type.

### PaperDocChangeSubscriptionDetails

`class` 

Followed/unfollowed Paper doc.

### PaperDocChangeSubscriptionType

`class` 

Type for paper doc change subscription type.

### PaperDocDeleteCommentDetails

`class` 

Deleted Paper doc comment.

### PaperDocDeleteCommentType

`class` 

Type for paper doc delete comment type.

### PaperDocDeletedDetails

`class` 

Archived Paper doc.

### PaperDocDeletedType

`class` 

Type for paper doc deleted type.

### PaperDocDownloadDetails

`class` 

Downloaded Paper doc in specific format.

### PaperDocDownloadType

`class` 

Type for paper doc download type.

### PaperDocEditCommentDetails

`class` 

Edited Paper doc comment.

### PaperDocEditCommentType

`class` 

Type for paper doc edit comment type.

### PaperDocEditDetails

`class` 

Edited Paper doc.

### PaperDocEditType

`class` 

Type for paper doc edit type.

### PaperDocFollowedDetails

`class` 

Followed Paper doc.

### PaperDocFollowedType

`class` 

Type for paper doc followed type.

### PaperDocMentionDetails

`class` 

Mentioned user in Paper doc.

### PaperDocMentionType

`class` 

Type for paper doc mention type.

### PaperDocOwnershipChangedDetails

`class` 

Transferred ownership of Paper doc.

### PaperDocOwnershipChangedType

`class` 

Type for paper doc ownership changed type.

### PaperDocRequestAccessDetails

`class` 

Requested access to Paper doc.

### PaperDocRequestAccessType

`class` 

Type for paper doc request access type.

### PaperDocResolveCommentDetails

`class` 

Resolved Paper doc comment.

### PaperDocResolveCommentType

`class` 

Type for paper doc resolve comment type.

### PaperDocRevertDetails

`class` 

Restored Paper doc to previous version.

### PaperDocRevertType

`class` 

Type for paper doc revert type.

### PaperDocSlackShareDetails

`class` 

Shared Paper doc via Slack.

### PaperDocSlackShareType

`class` 

Type for paper doc slack share type.

### PaperDocTeamInviteDetails

`class` 

Shared Paper doc with users and/or groups.

### PaperDocTeamInviteType

`class` 

Type for paper doc team invite type.

### PaperDocTrashedDetails

`class` 

Deleted Paper doc.

### PaperDocTrashedType

`class` 

Type for paper doc trashed type.

### PaperDocUnresolveCommentDetails

`class` 

Unresolved Paper doc comment.

### PaperDocUnresolveCommentType

`class` 

Type for paper doc unresolve comment type.

### PaperDocUntrashedDetails

`class` 

Restored Paper doc.

### PaperDocUntrashedType

`class` 

Type for paper doc untrashed type.

### PaperDocViewDetails

`class` 

Viewed Paper doc.

### PaperDocViewType

`class` 

Type for paper doc view type.

### PaperDocumentLogInfo

`class` 

Paper document's logged information.

### PaperDownloadFormat

`enum` 

Type for paper download format.

### PaperEnabledUsersGroupAdditionDetails

`class` 

Added users to Paper-enabled users list.

### PaperEnabledUsersGroupAdditionType

`class` 

Type for paper enabled users group addition type.

### PaperEnabledUsersGroupRemovalDetails

`class` 

Removed users from Paper-enabled users list.

### PaperEnabledUsersGroupRemovalType

`class` 

Type for paper enabled users group removal type.

### PaperExternalViewAllowDetails

`class` 

Changed Paper external sharing setting to anyone.

### PaperExternalViewAllowType

`class` 

Type for paper external view allow type.

### PaperExternalViewDefaultTeamDetails

`class` 

Changed Paper external sharing setting to default team.

### PaperExternalViewDefaultTeamType

`class` 

Type for paper external view default team type.

### PaperExternalViewForbidDetails

`class` 

Changed Paper external sharing setting to team-only.

### PaperExternalViewForbidType

`class` 

Type for paper external view forbid type.

### PaperFolderChangeSubscriptionDetails

`class` 

Followed/unfollowed Paper folder.

### PaperFolderChangeSubscriptionType

`class` 

Type for paper folder change subscription type.

### PaperFolderDeletedDetails

`class` 

Archived Paper folder.

### PaperFolderDeletedType

`class` 

Type for paper folder deleted type.

### PaperFolderFollowedDetails

`class` 

Followed Paper folder.

### PaperFolderFollowedType

`class` 

Type for paper folder followed type.

### PaperFolderLogInfo

`class` 

Paper folder's logged information.

### PaperFolderTeamInviteDetails

`class` 

Shared Paper folder with users and/or groups.

### PaperFolderTeamInviteType

`class` 

Type for paper folder team invite type.

### PaperMemberPolicy

`enum` 

Policy for controlling if team members can share Paper documents externally.

### PaperPublishedLinkChangePermissionDetails

`class` 

Changed permissions for published doc.

### PaperPublishedLinkChangePermissionType

`class` 

Type for paper published link change permission type.

### PaperPublishedLinkCreateDetails

`class` 

Published doc.

### PaperPublishedLinkCreateType

`class` 

Type for paper published link create type.

### PaperPublishedLinkDisabledDetails

`class` 

Unpublished doc.

### PaperPublishedLinkDisabledType

`class` 

Type for paper published link disabled type.

### PaperPublishedLinkViewDetails

`class` 

Viewed published doc.

### PaperPublishedLinkViewType

`class` 

Type for paper published link view type.

---

## Password & Security

### PasswordChangeDetails

`class` 

Changed password.

### PasswordChangeType

`class` 

Type for password change type.

### PasswordResetAllDetails

`class` 

Reset all team member passwords.

### PasswordResetAllType

`class` 

Type for password reset all type.

### PasswordResetDetails

`class` 

Reset password.

### PasswordResetType

`class` 

Type for password reset type.

### PasswordStrengthRequirementsChangePolicyDetails

`class` 

Changed team password strength requirements.

### PasswordStrengthRequirementsChangePolicyType

`class` 

Type for password strength requirements change policy type.

### TfaAddBackupPhoneDetails

`class` 

Added backup phone for two-step verification.

### TfaAddBackupPhoneType

`class` 

Type for tfa add backup phone type.

### TfaAddExceptionDetails

`class` 

Added members to two factor authentication exception list.

### TfaAddExceptionType

`class` 

Type for tfa add exception type.

### TfaAddSecurityKeyDetails

`class` 

Added security key for two-step verification.

### TfaAddSecurityKeyType

`class` 

Type for tfa add security key type.

### TfaChangeBackupPhoneDetails

`class` 

Changed backup phone for two-step verification.

### TfaChangeBackupPhoneType

`class` 

Type for tfa change backup phone type.

### TfaChangePolicyDetails

`class` 

Changed two-step verification setting for team.

### TfaChangePolicyType

`class` 

Type for tfa change policy type.

### TfaChangeStatusDetails

`class` 

Enabled/disabled/changed two-step verification setting.

### TfaChangeStatusType

`class` 

Type for tfa change status type.

### TfaConfiguration

`enum` 

Two factor authentication configuration. Note: the enabled option is deprecated.

### TfaRemoveBackupPhoneDetails

`class` 

Removed backup phone for two-step verification.

### TfaRemoveBackupPhoneType

`class` 

Type for tfa remove backup phone type.

### TfaRemoveExceptionDetails

`class` 

Removed members from two factor authentication exception list.

### TfaRemoveExceptionType

`class` 

Type for tfa remove exception type.

### TfaRemoveSecurityKeyDetails

`class` 

Removed security key for two-step verification.

### TfaRemoveSecurityKeyType

`class` 

Type for tfa remove security key type.

### TfaResetDetails

`class` 

Reset two-step verification for team member.

### TfaResetType

`class` 

Type for tfa reset type.

---

## Policy Types

### ChangeLinkExpirationPolicy

`enum` 

link is updated

### DataPlacementRestrictionChangePolicyDetails

`class` 

Set restrictions on data center locations where team data resides.

### DataPlacementRestrictionChangePolicyType

`class` 

Type for data placement restriction change policy type.

### DataPlacementRestrictionSatisfyPolicyDetails

`class` 

Completed restrictions on data center locations where team data resides.

### DataPlacementRestrictionSatisfyPolicyType

`class` 

Type for data placement restriction satisfy policy type.

### DefaultLinkExpirationDaysPolicy

`enum` 

Policy for the default number of days until an externally shared link expires

### DownloadPolicyType

`enum` 

Shared content downloads policy

### EnforceLinkPasswordPolicy

`enum` 

Policy for deciding whether password must be enforced when an externally shared link is updated

### ExtendedVersionHistoryChangePolicyDetails

`class` 

Accepted/opted out of extended version history.

### ExtendedVersionHistoryChangePolicyType

`class` 

Type for extended version history change policy type.

### ExtendedVersionHistoryPolicy

`enum` 

Type for extended version history policy.

### GovernancePolicyAddFolderFailedDetails

`class` 

Couldn't add a folder to a policy.

### GovernancePolicyAddFolderFailedType

`class` 

Type for governance policy add folder failed type.

### GovernancePolicyAddFoldersDetails

`class` 

Added folders to policy.

### GovernancePolicyAddFoldersType

`class` 

Type for governance policy add folders type.

### GovernancePolicyContentDisposedDetails

`class` 

Content disposed.

### GovernancePolicyContentDisposedType

`class` 

Type for governance policy content disposed type.

### GovernancePolicyCreateDetails

`class` 

Activated a new policy.

### GovernancePolicyCreateType

`class` 

Type for governance policy create type.

### GovernancePolicyDeleteDetails

`class` 

Deleted a policy.

### GovernancePolicyDeleteType

`class` 

Type for governance policy delete type.

### GovernancePolicyEditDetailsDetails

`class` 

Edited policy.

### GovernancePolicyEditDetailsType

`class` 

Type for governance policy edit details type.

### GovernancePolicyEditDurationDetails

`class` 

Changed policy duration.

### GovernancePolicyEditDurationType

`class` 

Type for governance policy edit duration type.

### GovernancePolicyExportCreatedDetails

`class` 

Created a policy download.

### GovernancePolicyExportCreatedType

`class` 

Type for governance policy export created type.

### GovernancePolicyExportRemovedDetails

`class` 

Removed a policy download.

### GovernancePolicyExportRemovedType

`class` 

Type for governance policy export removed type.

### GovernancePolicyRemoveFoldersDetails

`class` 

Removed folders from policy.

### GovernancePolicyRemoveFoldersType

`class` 

Type for governance policy remove folders type.

### GovernancePolicyReportCreatedDetails

`class` 

Created a summary report for a policy.

### GovernancePolicyReportCreatedType

`class` 

Type for governance policy report created type.

### GovernancePolicyZipPartDownloadedDetails

`class` 

Downloaded content from a policy.

### GovernancePolicyZipPartDownloadedType

`class` 

Type for governance policy zip part downloaded type.

### MicrosoftOfficeAddinChangePolicyDetails

`class` 

Enabled/disabled Microsoft Office add-in.

### MicrosoftOfficeAddinChangePolicyType

`class` 

Type for microsoft office addin change policy type.

### MicrosoftOfficeAddinPolicy

`enum` 

Microsoft Office addin policy

### PassPolicy

`enum` 

Type for pass policy.

### PermanentDeleteChangePolicyDetails

`class` 

Enabled/disabled ability of team members to permanently delete content.

### PermanentDeleteChangePolicyType

`class` 

Type for permanent delete change policy type.

### PolicyType

`enum` 

Type for policy type.

### ResellerSupportChangePolicyDetails

`class` 

Enabled/disabled reseller support.

### ResellerSupportChangePolicyType

`class` 

Type for reseller support change policy type.

### ResellerSupportPolicy

`enum` 

Policy for controlling if reseller can access the admin console as administrator

### RewindPolicy

`enum` 

Policy for controlling whether team members can rewind

### RewindPolicyChangedDetails

`class` 

Changed Rewind policy for team.

### RewindPolicyChangedType

`class` 

Type for rewind policy changed type.

### SecondaryMailsPolicy

`enum` 

Type for secondary mails policy.

### SecondaryMailsPolicyChangedDetails

`class` 

Secondary mails policy changed.

### SecondaryMailsPolicyChangedType

`class` 

Type for secondary mails policy changed type.

### SendForSignaturePolicy

`enum` 

Policy for controlling team access to send for signature feature

### SendForSignaturePolicyChangedDetails

`class` 

Changed send for signature policy for team.

### SendForSignaturePolicyChangedType

`class` 

Type for send for signature policy changed type.

### ShowcaseChangeDownloadPolicyDetails

`class` 

Enabled/disabled downloading files from Dropbox Showcase for team.

### ShowcaseChangeDownloadPolicyType

`class` 

Type for showcase change download policy type.

### ShowcaseChangeEnabledPolicyDetails

`class` 

Enabled/disabled Dropbox Showcase for team.

### ShowcaseChangeEnabledPolicyType

`class` 

Type for showcase change enabled policy type.

### ShowcaseChangeExternalSharingPolicyDetails

`class` 

Enabled/disabled sharing Dropbox Showcase externally for team.

### ShowcaseChangeExternalSharingPolicyType

`class` 

Type for showcase change external sharing policy type.

### ShowcaseDownloadPolicy

`enum` 

Policy for controlling if files can be downloaded from Showcases by team members

### ShowcaseEnabledPolicy

`enum` 

Policy for controlling whether Showcase is enabled.

### ShowcaseExternalSharingPolicy

`enum` 

Policy for controlling if team members can share Showcases externally.

### SmartSyncChangePolicyDetails

`class` 

Changed default Smart Sync setting for team members.

### SmartSyncChangePolicyType

`class` 

Type for smart sync change policy type.

### SmartSyncOptOutPolicy

`enum` 

Type for smart sync opt out policy.

### SmarterSmartSyncPolicyChangedDetails

`class` 

Changed automatic Smart Sync setting for team.

### SmarterSmartSyncPolicyChangedType

`class` 

Type for smarter smart sync policy changed type.

### SsoChangePolicyDetails

`class` 

Changed single sign-on setting for team.

### SsoChangePolicyType

`class` 

Type for sso change policy type.

### TeamBrandingPolicy

`enum` 

Policy for controlling team access to setting up branding feature

### TeamBrandingPolicyChangedDetails

`class` 

Changed team branding policy for team.

### TeamBrandingPolicyChangedType

`class` 

Type for team branding policy changed type.

### TeamExtensionsPolicy

`enum` 

Policy for controlling whether App Integrations are enabled for the team.

### TeamExtensionsPolicyChangedDetails

`class` 

Changed App Integrations setting for team.

### TeamExtensionsPolicyChangedType

`class` 

Type for team extensions policy changed type.

### TeamSelectiveSyncPolicy

`enum` 

Policy for controlling whether team selective sync is enabled for team.

### TeamSelectiveSyncPolicyChangedDetails

`class` 

Enabled/disabled Team Selective Sync for team.

### TeamSelectiveSyncPolicyChangedType

`class` 

Type for team selective sync policy changed type.

### TwoAccountChangePolicyDetails

`class` 

Enabled/disabled option for members to link personal Dropbox account and team account to same computer.

### TwoAccountChangePolicyType

`class` 

Type for two account change policy type.

### TwoAccountPolicy

`enum` 

Policy for pairing personal account to work account

### ViewerInfoPolicyChangedDetails

`class` 

Changed team policy for viewer info.

### ViewerInfoPolicyChangedType

`class` 

Type for viewer info policy changed type.

### WatermarkingPolicy

`enum` 

Policy for controlling team access to watermarking feature

### WatermarkingPolicyChangedDetails

`class` 

Changed watermarking policy for team.

### WatermarkingPolicyChangedType

`class` 

Type for watermarking policy changed type.

### WebSessionsChangeFixedLengthPolicyDetails

`class` 

Changed how long members can stay signed in to Dropbox.com.

### WebSessionsChangeFixedLengthPolicyType

`class` 

Type for web sessions change fixed length policy type.

### WebSessionsChangeIdleLengthPolicyDetails

`class` 

Changed how long team members can be idle while signed in to Dropbox.com.

### WebSessionsChangeIdleLengthPolicyType

`class` 

Type for web sessions change idle length policy type.

### WebSessionsFixedLengthPolicy

`enum` 

Web sessions fixed length policy.

### WebSessionsIdleLengthPolicy

`enum` 

Web sessions idle length policy.

---

## Ransomware & Threat

### RansomwareAlertCreateReportDetails

`class` 

Created ransomware report.

### RansomwareAlertCreateReportFailedDetails

`class` 

Couldn't generate ransomware report.

### RansomwareAlertCreateReportFailedType

`class` 

Type for ransomware alert create report failed type.

### RansomwareAlertCreateReportType

`class` 

Type for ransomware alert create report type.

### RansomwareRestoreProcessCompletedDetails

`class` 

Completed ransomware restore process.

### RansomwareRestoreProcessCompletedType

`class` 

Type for ransomware restore process completed type.

### RansomwareRestoreProcessStartedDetails

`class` 

Started ransomware restore process.

### RansomwareRestoreProcessStartedType

`class` 

Type for ransomware restore process started type.

---

## Reseller & Support

### ResellerLogInfo

`class` 

Reseller information.

### ResellerRole

`enum` 

Type for reseller role.

### ResellerSupportSessionEndDetails

`class` 

Ended reseller support session.

### ResellerSupportSessionEndType

`class` 

Type for reseller support session end type.

### ResellerSupportSessionStartDetails

`class` 

Started reseller support session.

### ResellerSupportSessionStartType

`class` 

Type for reseller support session start type.

---

## Shared Folder Operations

### SfAddGroupDetails

`class` 

Added team to shared folder.

### SfAddGroupType

`class` 

Type for sf add group type.

### SfAllowNonMembersToViewSharedLinksDetails

`class` 

Allowed non-collaborators to view links to files in shared folder.

### SfAllowNonMembersToViewSharedLinksType

`class` 

Type for sf allow non members to view shared links type.

### SfExternalInviteWarnDetails

`class` 

Set team members to see warning before sharing folders outside team.

### SfExternalInviteWarnType

`class` 

Type for sf external invite warn type.

### SfFbInviteChangeRoleDetails

`class` 

Changed Facebook user's role in shared folder.

### SfFbInviteChangeRoleType

`class` 

Type for sf fb invite change role type.

### SfFbInviteDetails

`class` 

Invited Facebook users to shared folder.

### SfFbInviteType

`class` 

Type for sf fb invite type.

### SfFbUninviteDetails

`class` 

Uninvited Facebook user from shared folder.

### SfFbUninviteType

`class` 

Type for sf fb uninvite type.

### SfInviteGroupDetails

`class` 

Invited group to shared folder.

### SfInviteGroupType

`class` 

Type for sf invite group type.

### SfTeamGrantAccessDetails

`class` 

Granted access to shared folder.

### SfTeamGrantAccessType

`class` 

Type for sf team grant access type.

### SfTeamInviteChangeRoleDetails

`class` 

Changed team member's role in shared folder.

### SfTeamInviteChangeRoleType

`class` 

Type for sf team invite change role type.

### SfTeamInviteDetails

`class` 

Invited team members to shared folder.

### SfTeamInviteType

`class` 

Type for sf team invite type.

### SfTeamJoinDetails

`class` 

Joined team member's shared folder.

### SfTeamJoinFromOobLinkDetails

`class` 

Joined team member's shared folder from link.

### SfTeamJoinFromOobLinkType

`class` 

Type for sf team join from oob link type.

### SfTeamJoinType

`class` 

Type for sf team join type.

### SfTeamUninviteDetails

`class` 

Unshared folder with team member.

### SfTeamUninviteType

`class` 

Type for sf team uninvite type.

---

## Shared Links

### SharedLinkAccessLevel

`enum` 

Shared link access level.

### SharedLinkAddExpiryDetails

`class` 

Added shared link expiration date.

### SharedLinkAddExpiryType

`class` 

Type for shared link add expiry type.

### SharedLinkChangeExpiryDetails

`class` 

Changed shared link expiration date.

### SharedLinkChangeExpiryType

`class` 

Type for shared link change expiry type.

### SharedLinkChangeVisibilityDetails

`class` 

Changed visibility of shared link.

### SharedLinkChangeVisibilityType

`class` 

Type for shared link change visibility type.

### SharedLinkCopyDetails

`class` 

Added file/folder to Dropbox from shared link.

### SharedLinkCopyType

`class` 

Type for shared link copy type.

### SharedLinkCreateDetails

`class` 

Created shared link.

### SharedLinkCreateType

`class` 

Type for shared link create type.

### SharedLinkDisableDetails

`class` 

Removed shared link.

### SharedLinkDisableType

`class` 

Type for shared link disable type.

### SharedLinkDownloadDetails

`class` 

Downloaded file/folder from shared link.

### SharedLinkDownloadType

`class` 

Type for shared link download type.

### SharedLinkRemoveExpiryDetails

`class` 

Removed shared link expiration date.

### SharedLinkRemoveExpiryType

`class` 

Type for shared link remove expiry type.

### SharedLinkSettingsAddExpirationDetails

`class` 

Added an expiration date to the shared link.

### SharedLinkSettingsAddExpirationType

`class` 

Type for shared link settings add expiration type.

### SharedLinkSettingsAddPasswordDetails

`class` 

Added a password to the shared link.

### SharedLinkSettingsAddPasswordType

`class` 

Type for shared link settings add password type.

### SharedLinkSettingsAllowDownloadDisabledDetails

`class` 

Disabled downloads.

### SharedLinkSettingsAllowDownloadDisabledType

`class` 

Type for shared link settings allow download disabled type.

### SharedLinkSettingsAllowDownloadEnabledDetails

`class` 

Enabled downloads.

### SharedLinkSettingsAllowDownloadEnabledType

`class` 

Type for shared link settings allow download enabled type.

### SharedLinkSettingsChangeAudienceDetails

`class` 

Changed the audience of the shared link.

### SharedLinkSettingsChangeAudienceType

`class` 

Type for shared link settings change audience type.

### SharedLinkSettingsChangeExpirationDetails

`class` 

Changed the expiration date of the shared link.

### SharedLinkSettingsChangeExpirationType

`class` 

Type for shared link settings change expiration type.

### SharedLinkSettingsChangePasswordDetails

`class` 

Changed the password of the shared link.

### SharedLinkSettingsChangePasswordType

`class` 

Type for shared link settings change password type.

### SharedLinkSettingsRemoveExpirationDetails

`class` 

Removed the expiration date from the shared link.

### SharedLinkSettingsRemoveExpirationType

`class` 

Type for shared link settings remove expiration type.

### SharedLinkSettingsRemovePasswordDetails

`class` 

Removed the password from the shared link.

### SharedLinkSettingsRemovePasswordType

`class` 

Type for shared link settings remove password type.

### SharedLinkShareDetails

`class` 

Added members as audience of shared link.

### SharedLinkShareType

`class` 

Type for shared link share type.

### SharedLinkViewDetails

`class` 

Opened shared link.

### SharedLinkViewType

`class` 

Type for shared link view type.

### SharedLinkVisibility

`enum` 

Defines who has access to a shared link.

---

## Sharing & Permissions

### SharedContentAddInviteesDetails

`class` 

Invited user to Dropbox and added them to shared file/folder.

### SharedContentAddInviteesType

`class` 

Type for shared content add invitees type.

### SharedContentAddLinkExpiryDetails

`class` 

Added expiration date to link for shared file/folder.

### SharedContentAddLinkExpiryType

`class` 

Type for shared content add link expiry type.

### SharedContentAddLinkPasswordDetails

`class` 

Added password to link for shared file/folder.

### SharedContentAddLinkPasswordType

`class` 

Type for shared content add link password type.

### SharedContentAddMemberDetails

`class` 

Added users and/or groups to shared file/folder.

### SharedContentAddMemberType

`class` 

Type for shared content add member type.

### SharedContentChangeDownloadsPolicyDetails

`class` 

Changed whether members can download shared file/folder.

### SharedContentChangeDownloadsPolicyType

`class` 

Type for shared content change downloads policy type.

### SharedContentChangeInviteeRoleDetails

`class` 

Changed access type of invitee to shared file/folder before invite was accepted.

### SharedContentChangeInviteeRoleType

`class` 

Type for shared content change invitee role type.

### SharedContentChangeLinkAudienceDetails

`class` 

Changed link audience of shared file/folder.

### SharedContentChangeLinkAudienceType

`class` 

Type for shared content change link audience type.

### SharedContentChangeLinkExpiryDetails

`class` 

Changed link expiration of shared file/folder.

### SharedContentChangeLinkExpiryType

`class` 

Type for shared content change link expiry type.

### SharedContentChangeLinkPasswordDetails

`class` 

Changed link password of shared file/folder.

### SharedContentChangeLinkPasswordType

`class` 

Type for shared content change link password type.

### SharedContentChangeMemberRoleDetails

`class` 

Changed access type of shared file/folder member.

### SharedContentChangeMemberRoleType

`class` 

Type for shared content change member role type.

### SharedContentChangeViewerInfoPolicyDetails

`class` 

Changed whether members can see who viewed shared file/folder.

### SharedContentChangeViewerInfoPolicyType

`class` 

Type for shared content change viewer info policy type.

### SharedContentClaimInvitationDetails

`class` 

Acquired membership of shared file/folder by accepting invite.

### SharedContentClaimInvitationType

`class` 

Type for shared content claim invitation type.

### SharedContentCopyDetails

`class` 

Copied shared file/folder to own Dropbox.

### SharedContentCopyType

`class` 

Type for shared content copy type.

### SharedContentDownloadDetails

`class` 

Downloaded shared file/folder.

### SharedContentDownloadType

`class` 

Type for shared content download type.

### SharedContentRelinquishMembershipDetails

`class` 

Left shared file/folder.

### SharedContentRelinquishMembershipType

`class` 

Type for shared content relinquish membership type.

### SharedContentRemoveInviteesDetails

`class` 

Removed invitee from shared file/folder before invite was accepted.

### SharedContentRemoveInviteesType

`class` 

Type for shared content remove invitees type.

### SharedContentRemoveLinkExpiryDetails

`class` 

Removed link expiration date of shared file/folder.

### SharedContentRemoveLinkExpiryType

`class` 

Type for shared content remove link expiry type.

### SharedContentRemoveLinkPasswordDetails

`class` 

Removed link password of shared file/folder.

### SharedContentRemoveLinkPasswordType

`class` 

Type for shared content remove link password type.

### SharedContentRemoveMemberDetails

`class` 

Removed user/group from shared file/folder.

### SharedContentRemoveMemberType

`class` 

Type for shared content remove member type.

### SharedContentRequestAccessDetails

`class` 

Requested access to shared file/folder.

### SharedContentRequestAccessType

`class` 

Type for shared content request access type.

### SharedContentRestoreInviteesDetails

`class` 

Restored shared file/folder invitees.

### SharedContentRestoreInviteesType

`class` 

Type for shared content restore invitees type.

### SharedContentRestoreMemberDetails

`class` 

Restored users and/or groups to membership of shared file/folder.

### SharedContentRestoreMemberType

`class` 

Type for shared content restore member type.

### SharedContentUnshareDetails

`class` 

Unshared file/folder by clearing membership.

### SharedContentUnshareType

`class` 

Type for shared content unshare type.

### SharedContentViewDetails

`class` 

Previewed shared file/folder.

### SharedContentViewType

`class` 

Type for shared content view type.

### SharedFolderChangeLinkPolicyDetails

`class` 

Changed who can access shared folder via link.

### SharedFolderChangeLinkPolicyType

`class` 

Type for shared folder change link policy type.

### SharedFolderChangeMembersInheritancePolicyDetails

`class` 

Changed whether shared folder inherits members from parent folder.

### SharedFolderChangeMembersInheritancePolicyType

`class` 

Type for shared folder change members inheritance policy type.

### SharedFolderChangeMembersManagementPolicyDetails

`class` 

Changed who can add/remove members of shared folder.

### SharedFolderChangeMembersManagementPolicyType

`class` 

Type for shared folder change members management policy type.

### SharedFolderChangeMembersPolicyDetails

`class` 

Changed who can become member of shared folder.

### SharedFolderChangeMembersPolicyType

`class` 

Type for shared folder change members policy type.

### SharedFolderCreateDetails

`class` 

Created shared folder.

### SharedFolderCreateType

`class` 

Type for shared folder create type.

### SharedFolderDeclineInvitationDetails

`class` 

Declined team member's invite to shared folder.

### SharedFolderDeclineInvitationType

`class` 

Type for shared folder decline invitation type.

### SharedFolderMembersInheritancePolicy

`enum` 

Specifies if a shared folder inherits its members from the parent folder.

### SharedFolderMountDetails

`class` 

Added shared folder to own Dropbox.

### SharedFolderMountType

`class` 

Type for shared folder mount type.

### SharedFolderNestDetails

`class` 

Changed parent of shared folder.

### SharedFolderNestType

`class` 

Type for shared folder nest type.

### SharedFolderTransferOwnershipDetails

`class` 

Transferred ownership of shared folder to another member.

### SharedFolderTransferOwnershipType

`class` 

Type for shared folder transfer ownership type.

### SharedFolderUnmountDetails

`class` 

Deleted shared folder from Dropbox.

### SharedFolderUnmountType

`class` 

Type for shared folder unmount type.

### SharingChangeFolderJoinPolicyDetails

`class` 

Changed whether team members can join shared folders owned outside team.

### SharingChangeFolderJoinPolicyType

`class` 

Type for sharing change folder join policy type.

### SharingChangeLinkAllowChangeExpirationPolicyDetails

`class` 

Changed the allow remove or change expiration policy for the links shared outside of the team.

### SharingChangeLinkAllowChangeExpirationPolicyType

`class` 

Type for sharing change link allow change expiration policy type.

### SharingChangeLinkDefaultExpirationPolicyDetails

`class` 

Changed the default expiration for the links shared outside of the team.

### SharingChangeLinkDefaultExpirationPolicyType

`class` 

Type for sharing change link default expiration policy type.

### SharingChangeLinkEnforcePasswordPolicyDetails

`class` 

Changed the password requirement for the links shared outside of the team.

### SharingChangeLinkEnforcePasswordPolicyType

`class` 

Type for sharing change link enforce password policy type.

### SharingChangeLinkPolicyDetails

`class` 

by default.

### SharingChangeLinkPolicyType

`class` 

Type for sharing change link policy type.

### SharingChangeMemberPolicyDetails

`class` 

Changed whether members can share files/folders outside team.

### SharingChangeMemberPolicyType

`class` 

Type for sharing change member policy type.

### SharingFolderJoinPolicy

`enum` 

Policy for controlling if team members can join shared folders owned by non team members.

### SharingLinkPolicy

`enum` 

Policy for controlling if team members can share links externally

### SharingMemberPolicy

`enum` 

External sharing policy

---

## Showcase

### ShowcaseAccessGrantedDetails

`class` 

Granted access to showcase.

### ShowcaseAccessGrantedType

`class` 

Type for showcase access granted type.

### ShowcaseAddMemberDetails

`class` 

Added member to showcase.

### ShowcaseAddMemberType

`class` 

Type for showcase add member type.

### ShowcaseArchivedDetails

`class` 

Archived showcase.

### ShowcaseArchivedType

`class` 

Type for showcase archived type.

### ShowcaseCreatedDetails

`class` 

Created showcase.

### ShowcaseCreatedType

`class` 

Type for showcase created type.

### ShowcaseDeleteCommentDetails

`class` 

Deleted showcase comment.

### ShowcaseDeleteCommentType

`class` 

Type for showcase delete comment type.

### ShowcaseDocumentLogInfo

`class` 

Showcase document's logged information.

### ShowcaseEditCommentDetails

`class` 

Edited showcase comment.

### ShowcaseEditCommentType

`class` 

Type for showcase edit comment type.

### ShowcaseEditedDetails

`class` 

Edited showcase.

### ShowcaseEditedType

`class` 

Type for showcase edited type.

### ShowcaseFileAddedDetails

`class` 

Added file to showcase.

### ShowcaseFileAddedType

`class` 

Type for showcase file added type.

### ShowcaseFileDownloadDetails

`class` 

Downloaded file from showcase.

### ShowcaseFileDownloadType

`class` 

Type for showcase file download type.

### ShowcaseFileRemovedDetails

`class` 

Removed file from showcase.

### ShowcaseFileRemovedType

`class` 

Type for showcase file removed type.

### ShowcaseFileViewDetails

`class` 

Viewed file in showcase.

### ShowcaseFileViewType

`class` 

Type for showcase file view type.

### ShowcasePermanentlyDeletedDetails

`class` 

Permanently deleted showcase.

### ShowcasePermanentlyDeletedType

`class` 

Type for showcase permanently deleted type.

### ShowcasePostCommentDetails

`class` 

Added showcase comment.

### ShowcasePostCommentType

`class` 

Type for showcase post comment type.

### ShowcaseRemoveMemberDetails

`class` 

Removed member from showcase.

### ShowcaseRemoveMemberType

`class` 

Type for showcase remove member type.

### ShowcaseRenamedDetails

`class` 

Renamed showcase.

### ShowcaseRenamedType

`class` 

Type for showcase renamed type.

### ShowcaseRequestAccessDetails

`class` 

Requested access to showcase.

### ShowcaseRequestAccessType

`class` 

Type for showcase request access type.

### ShowcaseResolveCommentDetails

`class` 

Resolved showcase comment.

### ShowcaseResolveCommentType

`class` 

Type for showcase resolve comment type.

### ShowcaseRestoredDetails

`class` 

Unarchived showcase.

### ShowcaseRestoredType

`class` 

Type for showcase restored type.

### ShowcaseTrashedDeprecatedDetails

`class` 

Deleted showcase (old version).

### ShowcaseTrashedDeprecatedType

`class` 

Type for showcase trashed deprecated type.

### ShowcaseTrashedDetails

`class` 

Deleted showcase.

### ShowcaseTrashedType

`class` 

Type for showcase trashed type.

### ShowcaseUnresolveCommentDetails

`class` 

Unresolved showcase comment.

### ShowcaseUnresolveCommentType

`class` 

Type for showcase unresolve comment type.

### ShowcaseUntrashedDeprecatedDetails

`class` 

Restored showcase (old version).

### ShowcaseUntrashedDeprecatedType

`class` 

Type for showcase untrashed deprecated type.

### ShowcaseUntrashedDetails

`class` 

Restored showcase.

### ShowcaseUntrashedType

`class` 

Type for showcase untrashed type.

### ShowcaseViewDetails

`class` 

Viewed showcase.

### ShowcaseViewType

`class` 

Type for showcase view type.

---

## Smart Sync

### SmartSyncCreateAdminPrivilegeReportDetails

`class` 

Created Smart Sync non-admin devices report.

### SmartSyncCreateAdminPrivilegeReportType

`class` 

Type for smart sync create admin privilege report type.

### SmartSyncNotOptOutDetails

`class` 

Opted team into Smart Sync.

### SmartSyncNotOptOutType

`class` 

Type for smart sync not opt out type.

### SmartSyncOptOutDetails

`class` 

Opted team out of Smart Sync.

### SmartSyncOptOutType

`class` 

Type for smart sync opt out type.

---

## SSO & Certificate

### Certificate

`class` 

Certificate details.

### SsoAddCertDetails

`class` 

Added X.509 certificate for SSO.

### SsoAddCertType

`class` 

Type for sso add cert type.

### SsoAddLoginUrlDetails

`class` 

Added sign-in URL for SSO.

### SsoAddLoginUrlType

`class` 

Type for sso add login url type.

### SsoAddLogoutUrlDetails

`class` 

Added sign-out URL for SSO.

### SsoAddLogoutUrlType

`class` 

Type for sso add logout url type.

### SsoChangeCertDetails

`class` 

Changed X.509 certificate for SSO.

### SsoChangeCertType

`class` 

Type for sso change cert type.

### SsoChangeLoginUrlDetails

`class` 

Changed sign-in URL for SSO.

### SsoChangeLoginUrlType

`class` 

Type for sso change login url type.

### SsoChangeLogoutUrlDetails

`class` 

Changed sign-out URL for SSO.

### SsoChangeLogoutUrlType

`class` 

Type for sso change logout url type.

### SsoChangeSamlIdentityModeDetails

`class` 

Changed SAML identity mode for SSO.

### SsoChangeSamlIdentityModeType

`class` 

Type for sso change saml identity mode type.

### SsoErrorDetails

`class` 

Failed to sign in via SSO.

### SsoErrorType

`class` 

Type for sso error type.

### SsoRemoveCertDetails

`class` 

Removed X.509 certificate for SSO.

### SsoRemoveCertType

`class` 

Type for sso remove cert type.

### SsoRemoveLoginUrlDetails

`class` 

Removed sign-in URL for SSO.

### SsoRemoveLoginUrlType

`class` 

Type for sso remove login url type.

### SsoRemoveLogoutUrlDetails

`class` 

Removed sign-out URL for SSO.

### SsoRemoveLogoutUrlType

`class` 

Type for sso remove logout url type.

---

## Team Invite Links

### CreateTeamInviteLinkDetails

`class` 

Created team invite link.

### CreateTeamInviteLinkType

`class` 

Type for create team invite link type.

### DeleteTeamInviteLinkDetails

`class` 

Deleted team invite link.

### DeleteTeamInviteLinkType

`class` 

Type for delete team invite link type.

---

## Team Settings & Operations

### TeamActivityCreateReportDetails

`class` 

Created team activity report.

### TeamActivityCreateReportFailDetails

`class` 

Couldn't generate team activity report.

### TeamActivityCreateReportFailType

`class` 

Type for team activity create report fail type.

### TeamActivityCreateReportType

`class` 

Type for team activity create report type.

### TeamDetails

`class` 

More details about the team.

### TeamEncryptionKeyCancelKeyDeletionDetails

`class` 

Canceled team encryption key deletion.

### TeamEncryptionKeyCancelKeyDeletionType

`class` 

Type for team encryption key cancel key deletion type.

### TeamEncryptionKeyCreateKeyDetails

`class` 

Created team encryption key.

### TeamEncryptionKeyCreateKeyType

`class` 

Type for team encryption key create key type.

### TeamEncryptionKeyDeleteKeyDetails

`class` 

Deleted team encryption key.

### TeamEncryptionKeyDeleteKeyType

`class` 

Type for team encryption key delete key type.

### TeamEncryptionKeyDisableKeyDetails

`class` 

Disabled team encryption key.

### TeamEncryptionKeyDisableKeyType

`class` 

Type for team encryption key disable key type.

### TeamEncryptionKeyEnableKeyDetails

`class` 

Enabled team encryption key.

### TeamEncryptionKeyEnableKeyType

`class` 

Type for team encryption key enable key type.

### TeamEncryptionKeyRotateKeyDetails

`class` 

Rotated team encryption key.

### TeamEncryptionKeyRotateKeyType

`class` 

Type for team encryption key rotate key type.

### TeamEncryptionKeyScheduleKeyDeletionDetails

`class` 

Scheduled encryption key deletion.

### TeamEncryptionKeyScheduleKeyDeletionType

`class` 

Type for team encryption key schedule key deletion type.

### TeamEvent

`class` 

An audit log event.

### TeamFolderChangeStatusDetails

`class` 

Changed archival status of team folder.

### TeamFolderChangeStatusType

`class` 

Type for team folder change status type.

### TeamFolderCreateDetails

`class` 

Created team folder in active status.

### TeamFolderCreateType

`class` 

Type for team folder create type.

### TeamFolderDowngradeDetails

`class` 

Downgraded team folder to regular shared folder.

### TeamFolderDowngradeType

`class` 

Type for team folder downgrade type.

### TeamFolderPermanentlyDeleteDetails

`class` 

Permanently deleted archived team folder.

### TeamFolderPermanentlyDeleteType

`class` 

Type for team folder permanently delete type.

### TeamFolderRenameDetails

`class` 

Renamed active/archived team folder.

### TeamFolderRenameType

`class` 

Type for team folder rename type.

### TeamLinkedAppLogInfo

`class` 

Team linked app

### TeamLogInfo

`class` 

Team's logged information.

### TeamMemberLogInfo

`class` 

Team member's logged information.

### TeamMembershipType

`enum` 

Type for team membership type.

### TeamName

`class` 

Team name details

### TeamProfileAddBackgroundDetails

`class` 

Added team background to display on shared link headers.

### TeamProfileAddBackgroundType

`class` 

Type for team profile add background type.

### TeamProfileAddLogoDetails

`class` 

Added team logo to display on shared link headers.

### TeamProfileAddLogoType

`class` 

Type for team profile add logo type.

### TeamProfileChangeBackgroundDetails

`class` 

Changed team background displayed on shared link headers.

### TeamProfileChangeBackgroundType

`class` 

Type for team profile change background type.

### TeamProfileChangeDefaultLanguageDetails

`class` 

Changed default language for team.

### TeamProfileChangeDefaultLanguageType

`class` 

Type for team profile change default language type.

### TeamProfileChangeLogoDetails

`class` 

Changed team logo displayed on shared link headers.

### TeamProfileChangeLogoType

`class` 

Type for team profile change logo type.

### TeamProfileChangeNameDetails

`class` 

Changed team name.

### TeamProfileChangeNameType

`class` 

Type for team profile change name type.

### TeamProfileRemoveBackgroundDetails

`class` 

Removed team background displayed on shared link headers.

### TeamProfileRemoveBackgroundType

`class` 

Type for team profile remove background type.

### TeamProfileRemoveLogoDetails

`class` 

Removed team logo displayed on shared link headers.

### TeamProfileRemoveLogoType

`class` 

Type for team profile remove logo type.

### TeamSelectiveSyncSettingsChangedDetails

`class` 

Changed sync default.

### TeamSelectiveSyncSettingsChangedType

`class` 

Type for team selective sync settings changed type.

### TeamSharingWhitelistSubjectsChangedDetails

`class` 

Edited the approved list for sharing externally.

### TeamSharingWhitelistSubjectsChangedType

`class` 

Type for team sharing whitelist subjects changed type.

---

## Trusted Teams

### TrustedNonTeamMemberLogInfo

`class` 

User that is not a member of the team but considered trusted.

### TrustedNonTeamMemberType

`enum` 

Type for trusted non team member type.

### TrustedTeamsRequestAction

`enum` 

Type for trusted teams request action.

### TrustedTeamsRequestState

`enum` 

Type for trusted teams request state.

---

## User & Member Log Info

### UserLogInfo

`class` 

User's logged information.

### NonTeamMemberLogInfo

`class` 

Non team member's logged information.

### UserNameLogInfo

`class` 

User's name logged information

---

## Web Sessions

### WebSessionsChangeActiveSessionLimitDetails

`class` 

Changed limit on active sessions per member.

### WebSessionsChangeActiveSessionLimitType

`class` 

Type for web sessions change active session limit type.

---

## Other Types

### IdentifierType

`enum` 

Type for identifier type.

### LabelType

`enum` 

Label type

### LockStatus

`enum` 

File lock status

### MissingDetails

`class` 

a result.

### NoExpirationLinkGenCreateReportDetails

`class` 

Report created: Links created with no expiration.

### NoExpirationLinkGenCreateReportType

`class` 

Type for no expiration link gen create report type.

### NoExpirationLinkGenReportFailedDetails

`class` 

Couldn't create report: Links created with no expiration.

### NoExpirationLinkGenReportFailedType

`class` 

Type for no expiration link gen report failed type.

### NonTrustedTeamDetails

`class` 

The email to which the request was sent

### OpenNoteSharedDetails

`class` 

Opened shared Paper doc.

### OpenNoteSharedType

`class` 

Type for open note shared type.

### OrganizationDetails

`class` 

More details about the organization.

### OrganizationName

`class` 

The name of the organization

### OrganizeFolderWithTidyDetails

`class` 

Organized a folder with multi-file organize.

### OrganizeFolderWithTidyType

`class` 

Type for organize folder with tidy type.

### OutdatedLinkViewCreateReportDetails

`class` 

Report created: Views of old links.

### OutdatedLinkViewCreateReportType

`class` 

Type for outdated link view create report type.

### OutdatedLinkViewReportFailedDetails

`class` 

Couldn't create report: Views of old links.

### OutdatedLinkViewReportFailedType

`class` 

Type for outdated link view report failed type.

### ParticipantLogInfo

`enum` 

A user or group

### PendingSecondaryEmailAddedDetails

`class` 

Added pending secondary email.

### PendingSecondaryEmailAddedType

`class` 

Type for pending secondary email added type.

### PrimaryTeamRequestAcceptedDetails

`class` 

Team merge request acceptance details shown to the primary team

### PrimaryTeamRequestCanceledDetails

`class` 

Team merge request cancellation details shown to the primary team

### PrimaryTeamRequestExpiredDetails

`class` 

Team merge request expiration details shown to the primary team

### PrimaryTeamRequestReminderDetails

`class` 

Team merge request reminder details shown to the primary team

### QuickActionType

`enum` 

Quick action type.

### RelocateAssetReferencesLogInfo

`class` 

Provides the indices of the source asset and the destination asset for a relocate action.

### ReplayFileDeleteDetails

`class` 

Deleted files in Replay.

### ReplayFileDeleteType

`class` 

Type for replay file delete type.

### ReplayFileSharedLinkCreatedDetails

`class` 

Created shared link in Replay.

### ReplayFileSharedLinkCreatedType

`class` 

Type for replay file shared link created type.

### ReplayFileSharedLinkModifiedDetails

`class` 

Modified shared link in Replay.

### ReplayFileSharedLinkModifiedType

`class` 

Type for replay file shared link modified type.

### ReplayProjectTeamAddDetails

`class` 

Added member to Replay Project.

### ReplayProjectTeamAddType

`class` 

Type for replay project team add type.

### ReplayProjectTeamDeleteDetails

`class` 

Removed member from Replay Project.

### ReplayProjectTeamDeleteType

`class` 

Type for replay project team delete type.

### SecondaryTeamRequestAcceptedDetails

`class` 

Team merge request acceptance details shown to the secondary team

### SecondaryTeamRequestCanceledDetails

`class` 

Team merge request cancellation details shown to the secondary team

### SecondaryTeamRequestExpiredDetails

`class` 

Team merge request expiration details shown to the secondary team

### SecondaryTeamRequestReminderDetails

`class` 

Team merge request reminder details shown to the secondary team

### SharedNoteOpenedDetails

`class` 

Opened shared Paper doc.

### SharedNoteOpenedType

`class` 

Type for shared note opened type.

### ShmodelDisableDownloadsDetails

`class` 

Disabled downloads for link.

### ShmodelDisableDownloadsType

`class` 

Type for shmodel disable downloads type.

### ShmodelEnableDownloadsDetails

`class` 

Enabled downloads for link.

### ShmodelEnableDownloadsType

`class` 

Type for shmodel enable downloads type.

### ShmodelGroupShareDetails

`class` 

Shared link with group.

### ShmodelGroupShareType

`class` 

Type for shmodel group share type.

### SpaceCapsType

`enum` 

Space limit alert policy

### SpaceLimitsStatus

`enum` 

Type for space limits status.

### TimeUnit

`enum` 

Type for time unit.

### UserLinkedAppLogInfo

`class` 

User linked app

### UserOrTeamLinkedAppLogInfo

`class` 

User or team linked app. Used when linked type is missing due to historical data gap.

### UserTagsAddedDetails

`class` 

Tagged a file.

### UserTagsAddedType

`class` 

Type for user tags added type.

### UserTagsRemovedDetails

`class` 

Removed tags.

### UserTagsRemovedType

`class` 

Type for user tags removed type.

---
