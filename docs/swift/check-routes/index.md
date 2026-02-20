# CheckRoutes

Routes for the check namespace. For Objective-C compatible routes see `DBCheckRoutes`.

---

## user

This endpoint performs User Authentication, validating the supplied access token, and returns the supplied string, to allow you to test your code and connection to the Dropbox API. It has no other effect. If you receive an HTTP 200 response with the supplied query, it indicates at least part of the Dropbox API infrastructure is working and that the access token is valid.

**Scope:** `account_info.read`

```swift
func user(query: String = "") -> RpcRequest<Check.EchoResult, Void>
```

**Parameters:**
- `query` - The string that you'd like to be echoed back to you.

**Returns:** `Check.EchoResult` on success, `Void` on failure.
