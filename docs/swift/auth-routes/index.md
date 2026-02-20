# AuthRoutes

Routes for the auth namespace. For Objective-C compatible routes see `DBAuthRoutes`.

---

## tokenRevoke

Disables the access token used to authenticate the call. If there is a corresponding refresh token for the access token, this disables that refresh token, as well as any other access tokens for that refresh token.

```swift
func tokenRevoke() -> RpcRequest<Void, Void>
```

**Returns:** `Void` on success, `Void` on failure.
