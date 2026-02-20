# Account Data Types

Data types for the Account namespace.

## PhotoSourceArg

The PhotoSourceArg union.

**Cases:**
- `base64Data` - Image data in base64-encoded bytes. Associated value: `String`
- `other` - An unspecified error.

---

## SetProfilePhotoArg

The SetProfilePhotoArg struct.

**Properties:**
- `photo: Account.PhotoSourceArg` - Image to set as the user's new profile photo.

---

## SetProfilePhotoError

The SetProfilePhotoError union.

**Cases:**
- `fileTypeError` - File cannot be set as profile photo.
- `fileSizeError` - File cannot exceed 10 MB.
- `dimensionError` - Image must be larger than 128 x 128.
- `thumbnailError` - Image could not be thumbnailed.
- `transientError` - Temporary infrastructure failure, please retry.
- `other` - An unspecified error.

---

## SetProfilePhotoResult

The SetProfilePhotoResult struct.

**Properties:**
- `profilePhotoUrl: String` - URL for the photo representing the user, if one is set.
