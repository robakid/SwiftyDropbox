# OpenidRoutes

Routes for the openid namespace. For Objective-C compatible routes see `DBOpenidRoutes`.

---

## userinfo

This route is used for refreshing the info that is found in the id_token during the OIDC flow. This route doesn't require any arguments and will use the scopes approved for the given access token.

**Scope:** `openid`

```swift
func userinfo() -> RpcRequest<Openid.UserInfoResult, Openid.UserInfoError>
```

**Returns:** `Openid.UserInfoResult` on success, `Openid.UserInfoError` on failure.
