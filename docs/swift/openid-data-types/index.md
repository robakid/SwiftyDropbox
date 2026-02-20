# Openid Data Types

Data types for the Openid namespace.

## OpenIdError

The OpenIdError union.

**Cases:**
- `incorrectOpenidScopes` - Missing openid claims for the associated access token.
- `other` - An unspecified error.

---

## UserInfoArgs

No parameters.

---

## UserInfoError

The UserInfoError union.

**Cases:**
- `openidError` - An unspecified error. Associated value: `Openid.OpenIdError`
- `other` - An unspecified error.

---

## UserInfoResult

The UserInfoResult struct.

**Properties:**
- `familyName: String?` - Last name of user.
- `givenName: String?` - First name of user.
- `email: String?` - Email address of user.
- `emailVerified: Bool?` - If user is email verified.
- `iss: String` - Issuer of token (in this case Dropbox).
- `sub: String` - An identifier for the user. This is the Dropbox account_id, a string value such as dbid:AAH4f99T0taONIb-OurWxbNQ6ywGRopQngc.
