# Auth Data Types

Data types for the Auth namespace.

## AccessError

Error occurred because the account doesn't have permission to access the resource.

**Cases:**
- `invalidAccountType` - Current account type cannot access the resource. Associated value: `Auth.InvalidAccountTypeError`
- `paperAccessDenied` - Current account cannot access Paper. Associated value: `Auth.PaperAccessError`
- `other` - An unspecified error.

---

## AuthError

Errors occurred during authentication.

**Cases:**
- `invalidAccessToken` - The access token is invalid.
- `invalidSelectUser` - The user specified in 'Dropbox-API-Select-User' is no longer on the team.
- `invalidSelectAdmin` - The user specified in 'Dropbox-API-Select-Admin' is not a Dropbox Business team admin.
- `userSuspended` - The user has been suspended.
- `expiredAccessToken` - The access token has expired.
- `missingScope` - The access token does not have the required scope to access the route. Associated value: `Auth.TokenScopeError`
- `routeAccessDenied` - The route is not available to public.
- `other` - An unspecified error.

---

## InvalidAccountTypeError

The InvalidAccountTypeError union.

**Cases:**
- `endpoint` - Current account type doesn't have permission to access this route endpoint.
- `feature` - Current account type doesn't have permission to access this feature.
- `other` - An unspecified error.

---

## PaperAccessError

The PaperAccessError union.

**Cases:**
- `paperDisabled` - Paper is disabled.
- `notPaperUser` - The provided user has not used Paper yet.
- `other` - An unspecified error.

---

## RateLimitError

Error occurred because the app is being rate limited.

**Properties:**
- `reason: Auth.RateLimitReason` - The reason why the app is being rate limited.
- `retryAfter: UInt64` - The number of seconds that the app should wait before making another request.

---

## RateLimitReason

The RateLimitReason union.

**Cases:**
- `tooManyRequests` - You are making too many requests in the past few minutes.
- `tooManyWriteOperations` - There are currently too many write operations happening in the user's Dropbox.
- `other` - An unspecified error.

---

## TokenFromOAuth1Arg

The TokenFromOAuth1Arg struct.

**Properties:**
- `oauth1Token: String` - The supplied OAuth 1.0 access token.
- `oauth1TokenSecret: String` - The token secret associated with the supplied access token.

---

## TokenFromOAuth1Error

The TokenFromOAuth1Error union.

**Cases:**
- `invalidOauth1TokenInfo` - Part or all of the OAuth 1.0 access token info is invalid.
- `appIdMismatch` - The authorized app does not match the app associated with the supplied access token.
- `other` - An unspecified error.

---

## TokenFromOAuth1Result

The TokenFromOAuth1Result struct.

**Properties:**
- `oauth2Token: String` - The OAuth 2.0 token generated from the supplied OAuth 1.0 token.

---

## TokenScopeError

The TokenScopeError struct.

**Properties:**
- `requiredScope: String` - The required scope to access the route.
