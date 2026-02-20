# AccountRoutes

Routes for the account namespace. For Objective-C compatible routes see `DBAccountRoutes`.

---

## setProfilePhoto

Sets a user's profile photo.

**Scope:** `account_info.write`

```swift
func setProfilePhoto(photo: Account.PhotoSourceArg) -> RpcRequest<Account.SetProfilePhotoResult, Account.SetProfilePhotoError>
```

**Parameters:**
- `photo` - Image to set as the user's new profile photo.

**Returns:** `Account.SetProfilePhotoResult` on success, `Account.SetProfilePhotoError` on failure.
