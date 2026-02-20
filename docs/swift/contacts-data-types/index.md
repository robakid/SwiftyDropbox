# Contacts Data Types

Data types for the Contacts namespace.

## DeleteManualContactsArg

The DeleteManualContactsArg struct.

**Properties:**
- `emailAddresses: [String]` - List of manually added contacts to be deleted.

---

## DeleteManualContactsError

The DeleteManualContactsError union.

**Cases:**
- `contactsNotFound` - Can't delete contacts from this list. Make sure the list only has manually added contacts. The deletion was cancelled. Associated value: `[String]`
- `other` - An unspecified error.
