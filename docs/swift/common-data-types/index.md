# Common Data Types

Data types for the Common namespace.

## PathRoot

The PathRoot union.

**Cases:**
- `home` - Paths are relative to the authenticating user's home namespace, whether or not that user belongs to a team.
- `root` - Paths are relative to the authenticating user's root namespace (This results in invalidRoot in PathRootError if the user's root namespace has changed.). Associated value: `String`
- `namespaceId` - Paths are relative to given namespace id (This results in noPermission in PathRootError if you don't have access to this namespace.). Associated value: `String`
- `other` - An unspecified error.

---

## PathRootError

The PathRootError union.

**Cases:**
- `invalidRoot` - The root namespace id in Dropbox-API-Path-Root header is not valid. The value of this error is the user's latest root info. Associated value: `Common.RootInfo`
- `noPermission` - You don't have permission to access the namespace id in Dropbox-API-Path-Root header.
- `other` - An unspecified error.

---

## RootInfo

Information about current user's root.

**Properties:**
- `rootNamespaceId: String` - The namespace ID for user's root namespace. It will be the namespace ID of the shared team root if the user is member of a team with a separate team root. Otherwise it will be same as homeNamespaceId in RootInfo.
- `homeNamespaceId: String` - The namespace ID for user's home namespace.

---

## TeamRootInfo

Root info when user is member of a team with a separate root namespace ID. Inherits from `Common.RootInfo`.

**Properties:**
- `rootNamespaceId: String` - *(inherited)* The namespace ID for user's root namespace.
- `homeNamespaceId: String` - *(inherited)* The namespace ID for user's home namespace.
- `homePath: String` - The path for user's home directory under the shared team root.

---

## UserRootInfo

Root info when user is not member of a team or the user is a member of a team and the team does not have a separate root namespace. Inherits from `Common.RootInfo`.

**Properties:**
- `rootNamespaceId: String` - *(inherited)* The namespace ID for user's root namespace.
- `homeNamespaceId: String` - *(inherited)* The namespace ID for user's home namespace.
