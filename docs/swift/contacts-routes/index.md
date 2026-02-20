# ContactsRoutes

Routes for the contacts namespace. For Objective-C compatible routes see `DBContactsRoutes`.

---

## deleteManualContacts

Removes all manually added contacts. You'll still keep contacts who are on your team or who you imported. New contacts will be added when you share.

**Scope:** `contacts.write`

```swift
func deleteManualContacts() -> RpcRequest<Void, Void>
```

**Returns:** `Void` on success, `Void` on failure.

---

## deleteManualContactsBatch

Removes manually added contacts from the given list.

**Scope:** `contacts.write`

```swift
func deleteManualContactsBatch(emailAddresses: [String]) -> RpcRequest<Void, Contacts.DeleteManualContactsError>
```

**Parameters:**
- `emailAddresses` - List of manually added contacts to be deleted.

**Returns:** `Void` on success, `Contacts.DeleteManualContactsError` on failure.
