# UsersRoutes

Routes for the users namespace. For Objective-C compatible routes see `DBUsersRoutes`.

---

## featuresGetValues

Get a list of feature values that may be configured for the current account.

**Scope:** `account_info.read`

```swift
func featuresGetValues(features: [Users.UserFeature]) -> RpcRequest<Users.UserFeaturesGetValuesBatchResult, Users.UserFeaturesGetValuesBatchError>
```

**Parameters:**
- `features` - A list of features in `UserFeature`. If the list is empty, this route will return `UserFeaturesGetValuesBatchError`.

**Returns:** `Users.UserFeaturesGetValuesBatchResult` on success, `Users.UserFeaturesGetValuesBatchError` on failure.

---

## getAccount

Get information about a user's account.

**Scope:** `sharing.read`

```swift
func getAccount(accountId: String) -> RpcRequest<Users.BasicAccount, Users.GetAccountError>
```

**Parameters:**
- `accountId` - A user's account identifier.

**Returns:** `Users.BasicAccount` on success, `Users.GetAccountError` on failure.

---

## getAccountBatch

Get information about multiple user accounts. At most 300 accounts may be queried per request.

**Scope:** `sharing.read`

```swift
func getAccountBatch(accountIds: [String]) -> RpcRequest<Array<Users.BasicAccount>, Users.GetAccountBatchError>
```

**Parameters:**
- `accountIds` - List of user account identifiers. Should not contain any duplicate account IDs.

**Returns:** `Array<Users.BasicAccount>` on success, `Users.GetAccountBatchError` on failure.

---

## getCurrentAccount

Get information about the current user's account.

**Scope:** `account_info.read`

```swift
func getCurrentAccount() -> RpcRequest<Users.FullAccount, Void>
```

**Returns:** `Users.FullAccount` on success, `Void` on failure.

---

## getSpaceUsage

Get the space usage information for the current user's account.

**Scope:** `account_info.read`

```swift
func getSpaceUsage() -> RpcRequest<Users.SpaceUsage, Void>
```

**Returns:** `Users.SpaceUsage` on success, `Void` on failure.
