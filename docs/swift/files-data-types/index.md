# Files Data Types

Data types for the files namespace.

## AddTagArg

`class`

**Properties:**

- `path: String` - Path to the item to be tagged.
- `tagText: String` - The value of the tag to add. Will be automatically converted to lowercase letters.

---

## BaseTagError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `other`

---

## AddTagError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `other`
- `tooManyTags` - The item already has the maximum supported number of tags.

---

## GetMetadataArg

`class`

**Properties:**

- `path: String` - The path of a file or folder on Dropbox.
- `includeMediaInfo: Bool` - If true, mediaInfo in FileMetadata is set for photo and video.
- `includeDeleted: Bool` - If true, DeletedMetadata will be returned for deleted file or folder, otherwise notFound in LookupError will be returned.
- `includeHasExplicitSharedMembers: Bool` - If true, the results will include a flag for each file indicating whether or not  that file has any explicit members.
- `includePropertyGroups: FileProperties.TemplateFilterBase?` - If set to a valid list of template IDs, propertyGroups in FileMetadata is set if there exists property data associated with the file and each of the listed templates.

---

## AlphaGetMetadataArg

`class` (inherits from `Files.GetMetadataArg`)

**Properties:**

- `includePropertyTemplates: [String]?` - If set to a valid list of template IDs, propertyGroups in FileMetadata is set for files with custom properties.

---

## GetMetadataError

`enum`

**Cases:**

- `path` (`Files.LookupError`)

---

## AlphaGetMetadataError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `propertiesError` (`FileProperties.LookUpPropertiesError`)

---

## CommitInfo

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to save the file.
- `mode: Files.WriteMode` - Selects what to do if the file already exists.
- `autorename: Bool` - If there's a conflict, as determined by mode, have the Dropbox server try to autorename the file to avoid conflict.
- `clientModified: Date?` - The value to store as the clientModified timestamp. Dropbox automatically records the time at which the file was written to the Dropbox servers. It can also record an additional timestamp, provided by Dropbox desktop clients, mobile clients, and API apps of when the file was actually created or modified.
- `mute: Bool` - Normally, users are made aware of any file modifications in their Dropbox account via notifications in the client software. If true, this tells the clients that this modification shouldn't result in a user notification.
- `propertyGroups: [FileProperties.PropertyGroup]?` - List of custom properties to add to file.
- `strictConflict: Bool` - Be more strict about how each WriteMode detects conflict. For example, always return a conflict error when mode = update in WriteMode and the given "rev" doesn't match the existing file's "rev", even if the existing file has been deleted. This also forces a conflict even when the target path refers to a file with identical contents.

---

## ContentSyncSetting

`class`

**Properties:**

- `id: String` - Id of the item this setting is applied to.
- `syncSetting: Files.SyncSetting` - Setting for this item.

---

## ContentSyncSettingArg

`class`

**Properties:**

- `id: String` - Id of the item this setting is applied to.
- `syncSetting: Files.SyncSettingArg` - Setting for this item.

---

## CreateFolderArg

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to create.
- `autorename: Bool` - If there's a conflict, have the Dropbox server try to autorename the folder to avoid the conflict.

---

## CreateFolderBatchArg

`class`

**Properties:**

- `paths: [String]` - List of paths to be created in the user's Dropbox. Duplicate path arguments in the batch are considered only once.
- `autorename: Bool` - If there's a conflict, have the Dropbox server try to autorename the folder to avoid the conflict.
- `forceAsync: Bool` - Whether to force the create to happen asynchronously.

---

## CreateFolderBatchError

`enum`

**Cases:**

- `tooManyFiles` - The operation would involve too many files or folders.
- `other`

---

## CreateFolderBatchJobStatus

`enum`

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.CreateFolderBatchResult`) - The batch create folder has finished.
- `failed` (`Files.CreateFolderBatchError`) - The batch create folder has failed.
- `other`

---

## CreateFolderBatchLaunch

`enum`

Result returned by createFolderBatch that may either launch an asynchronous job or complete synchronously.

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.CreateFolderBatchResult`)
- `other`

---

## FileOpsResult

`class`

No public stored properties.

---

## CreateFolderBatchResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `entries: [Files.CreateFolderBatchResultEntry]` - Each entry in paths in CreateFolderBatchArg will appear at the same position inside entries in CreateFolderBatchResult.

---

## CreateFolderBatchResultEntry

`enum`

**Cases:**

- `success` (`Files.CreateFolderEntryResult`)
- `failure` (`Files.CreateFolderEntryError`)

---

## CreateFolderEntryError

`enum`

**Cases:**

- `path` (`Files.WriteError`)
- `other`

---

## CreateFolderEntryResult

`class`

**Properties:**

- `metadata: Files.FolderMetadata` - Metadata of the created folder.

---

## CreateFolderError

`enum`

**Cases:**

- `path` (`Files.WriteError`)

---

## CreateFolderResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `metadata: Files.FolderMetadata` - Metadata of the created folder.

---

## DeleteArg

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to delete.
- `parentRev: String?` - Perform delete if given "rev" matches the existing file's latest "rev". This field does not support deleting a folder.

---

## DeleteBatchArg

`class`

**Properties:**

- `entries: [Files.DeleteArg]`

---

## DeleteBatchError

`enum`

**Cases:**

- `tooManyWriteOperations` - Use tooManyWriteOperations in DeleteError. deleteBatch now provides smaller granularity about which entry has failed because of this.
- `other`

---

## DeleteBatchJobStatus

`enum`

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.DeleteBatchResult`) - The batch delete has finished.
- `failed` (`Files.DeleteBatchError`) - The batch delete has failed.
- `other`

---

## DeleteBatchLaunch

`enum`

Result returned by deleteBatch that may either launch an asynchronous job or complete synchronously.

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.DeleteBatchResult`)
- `other`

---

## DeleteBatchResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `entries: [Files.DeleteBatchResultEntry]` - Each entry in entries in DeleteBatchArg will appear at the same position inside entries in DeleteBatchResult.

---

## DeleteBatchResultData

`class`

**Properties:**

- `metadata: Files.Metadata` - Metadata of the deleted object.

---

## DeleteBatchResultEntry

`enum`

**Cases:**

- `success` (`Files.DeleteBatchResultData`)
- `failure` (`Files.DeleteError`)

---

## DeleteError

`enum`

**Cases:**

- `pathLookup` (`Files.LookupError`)
- `pathWrite` (`Files.WriteError`)
- `tooManyWriteOperations` - There are too many write operations in user's Dropbox. Please retry this request.
- `tooManyFiles` - There are too many files in one request. Please retry with fewer files.
- `other`

---

## DeleteResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `metadata: Files.Metadata` - Metadata of the deleted object.

---

## Metadata

`class`

Metadata for a file or folder.

**Properties:**

- `name: String` - The last component of the path (including extension). This never contains a slash.
- `pathLower: String?` - The lowercased full path in the user's Dropbox. This always starts with a slash. This field will be null if the file or folder is not mounted.
- `pathDisplay: String?` - The cased path to be used for display purposes only. In rare instances the casing will not correctly match the user's filesystem, but this behavior will match the path provided in the Core API v1, and at least the last path component will have the correct casing. Changes to only the casing of paths won't be returned by listFolderContinue. This field will be null if the file or folder is not mounted.
- `parentSharedFolderId: String?` - Please use parentSharedFolderId in FileSharingInfo or parentSharedFolderId in FolderSharingInfo instead.
- `previewUrl: String?` - The preview URL of the file.

---

## DeletedMetadata

`class` (inherits from `Files.Metadata`)

Indicates that there used to be a file or folder at this path, but it no longer exists.

No public stored properties.

---

## Dimensions

`class`

Dimensions for a photo or video.

**Properties:**

- `height: UInt64` - Height of the photo/video.
- `width: UInt64` - Width of the photo/video.

---

## DownloadArg

`class`

**Properties:**

- `path: String` - The path of the file to download.
- `rev: String?` - Please specify revision in path instead.

---

## DownloadError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `unsupportedFile` - This file type cannot be downloaded directly; use export instead.
- `other`

---

## DownloadZipArg

`class`

**Properties:**

- `path: String` - The path of the folder to download.

---

## DownloadZipError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `tooLarge` - The folder or a file is too large to download.
- `tooManyFiles` - The folder has too many files to download.
- `other`

---

## DownloadZipResult

`class`

**Properties:**

- `metadata: Files.FolderMetadata`

---

## ExportArg

`class`

**Properties:**

- `path: String` - The path of the file to be exported.
- `exportFormat: String?` - The file format to which the file should be exported. This must be one of the formats listed in the file's export_options returned by getMetadata. If none is specified, the default format (specified in export_as in file metadata) will be used.

---

## ExportError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `nonExportable` - This file type cannot be exported. Use download instead.
- `invalidExportFormat` - The specified export format is not a valid option for this file type.
- `retryError` - The exportable content is not yet available. Please retry later.
- `other`

---

## ExportInfo

`class`

Export information for a file.

**Properties:**

- `exportAs: String?` - Format to which the file can be exported to.
- `exportOptions: [String]?` - Additional formats to which the file can be exported. These values can be specified as the export_format in /files/export.

---

## ExportMetadata

`class`

**Properties:**

- `name: String` - The last component of the path (including extension). This never contains a slash.
- `size: UInt64` - The file size in bytes.
- `exportHash: String?` - A hash based on the exported file content. This field can be used to verify data integrity. Similar to content hash. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.
- `paperRevision: Int64?` - If the file is a Paper doc, this gives the latest doc revision which can be used in paperUpdate.

---

## ExportResult

`class`

**Properties:**

- `exportMetadata: Files.ExportMetadata` - Metadata for the exported version of the file.
- `fileMetadata: Files.FileMetadata` - Metadata for the original file.

---

## FileCategory

`enum`

**Cases:**

- `image` - jpg, png, gif, and more.
- `document` - doc, docx, txt, and more.
- `pdf` - pdf.
- `spreadsheet` - xlsx, xls, csv, and more.
- `presentation` - ppt, pptx, key, and more.
- `audio` - mp3, wav, mid, and more.
- `video` - mov, wmv, mp4, and more.
- `folder` - dropbox folder.
- `paper` - dropbox paper doc.
- `others` - any file not in one of the categories above.
- `other`

---

## FileLock

`class`

**Properties:**

- `content: Files.FileLockContent` - The lock description.

---

## FileLockContent

`enum`

**Cases:**

- `unlocked` - Empty type to indicate no lock.
- `singleUser` (`Files.SingleUserLock`) - A lock held by a single user.
- `other`

---

## FileLockMetadata

`class`

**Properties:**

- `isLockholder: Bool?` - True if caller holds the file lock.
- `lockholderName: String?` - The display name of the lock holder.
- `lockholderAccountId: String?` - The account ID of the lock holder if known.
- `created: Date?` - The timestamp of the lock was created.

---

## FileMetadata

`class` (inherits from `Files.Metadata`)

**Properties:**

- `id: String` - A unique identifier for the file.
- `clientModified: Date` - For files, this is the modification time set by the desktop client when the file was added to Dropbox. Since this time is not verified (the Dropbox server stores whatever the desktop client sends up), this should only be used for display purposes (such as sorting) and not, for example, to determine if a file has changed or not.
- `serverModified: Date` - The last time the file was modified on Dropbox.
- `rev: String` - A unique identifier for the current revision of a file. This field is the same rev as elsewhere in the API and can be used to detect changes and avoid conflicts.
- `size: UInt64` - The file size in bytes.
- `mediaInfo: Files.MediaInfo?` - Additional information if the file is a photo or video. This field will not be set on entries returned by listFolder, listFolderContinue, or getThumbnailBatch, starting December 2, 2019.
- `symlinkInfo: Files.SymlinkInfo?` - Set if this file is a symlink.
- `sharingInfo: Files.FileSharingInfo?` - Set if this file is contained in a shared folder.
- `isDownloadable: Bool` - If true, file can be downloaded directly; else the file must be exported.
- `exportInfo: Files.ExportInfo?` - Information about format this file can be exported to. This filed must be set if isDownloadable is set to false.
- `propertyGroups: [FileProperties.PropertyGroup]?` - Additional information if the file has custom properties with the property template specified.
- `hasExplicitSharedMembers: Bool?` - This flag will only be present if include_has_explicit_shared_members  is true in listFolder or getMetadata. If this  flag is present, it will be true if this file has any explicit shared  members. This is different from sharing_info in that this could be true  in the case where a file has explicit members but is not contained within  a shared folder.
- `contentHash: String?` - A hash of the file content. This field can be used to verify data integrity. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.
- `fileLockInfo: Files.FileLockMetadata?` - If present, the metadata associated with the file's current lock.

---

## SharingInfo

`class`

Sharing info for a file or folder.

**Properties:**

- `readOnly: Bool` - True if the file or folder is inside a read-only shared folder.

---

## FileSharingInfo

`class` (inherits from `Files.SharingInfo`)

Sharing info for a file which is contained by a shared folder.

**Properties:**

- `parentSharedFolderId: String` - ID of shared folder that holds this file.
- `modifiedBy: String?` - The last user who modified the file. This field will be null if the user's account has been deleted.

---

## FileStatus

`enum`

**Cases:**

- `active`
- `deleted`
- `other`

---

## FolderMetadata

`class` (inherits from `Files.Metadata`)

**Properties:**

- `id: String` - A unique identifier for the folder.
- `sharedFolderId: String?` - Please use sharingInfo instead.
- `sharingInfo: Files.FolderSharingInfo?` - Set if the folder is contained in a shared folder or is a shared folder mount point.
- `propertyGroups: [FileProperties.PropertyGroup]?` - Additional information if the file has custom properties with the property template specified. Note that only properties associated with user-owned templates, not team-owned templates, can be attached to folders.

---

## FolderSharingInfo

`class` (inherits from `Files.SharingInfo`)

Sharing info for a folder which is contained in a shared folder or is a shared folder mount point.

**Properties:**

- `parentSharedFolderId: String?` - Set if the folder is contained by a shared folder.
- `sharedFolderId: String?` - If this folder is a shared folder mount point, the ID of the shared folder mounted at this location.
- `traverseOnly: Bool` - Specifies that the folder can only be traversed and the user can only see a limited subset of the contents of this folder because they don't have read access to this folder. They do, however, have access to some sub folder.
- `noAccess: Bool` - Specifies that the folder cannot be accessed by the user.

---

## GetCopyReferenceArg

`class`

**Properties:**

- `path: String` - The path to the file or folder you want to get a copy reference to.

---

## GetCopyReferenceError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `other`

---

## GetCopyReferenceResult

`class`

**Properties:**

- `metadata: Files.Metadata` - Metadata of the file or folder.
- `copyReference: String` - A copy reference to the file or folder.
- `expires: Date` - The expiration date of the copy reference. This value is currently set to be far enough in the future so that expiration is effectively not an issue.

---

## GetTagsArg

`class`

**Properties:**

- `paths: [String]` - Path to the items.

---

## GetTagsResult

`class`

**Properties:**

- `pathsToTags: [Files.PathToTags]` - List of paths and their corresponding tags.

---

## GetTemporaryLinkArg

`class`

**Properties:**

- `path: String` - The path to the file you want a temporary link to.

---

## GetTemporaryLinkError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `emailNotVerified` - This user's email address is not verified. This functionality is only available on accounts with a verified email address. Users can verify their email address here https://www.dropbox.com/help/317.
- `unsupportedFile` - Cannot get temporary link to this file type; use export instead.
- `notAllowed` - The user is not allowed to request a temporary link to the specified file. For example, this can occur if the file is restricted or if the user's links are banned https://help.dropbox.com/files-folders/share/banned-links.
- `other`

---

## GetTemporaryLinkResult

`class`

**Properties:**

- `metadata: Files.FileMetadata` - Metadata of the file.
- `link: String` - The temporary link which can be used to stream content the file.

---

## GetTemporaryUploadLinkArg

`class`

**Properties:**

- `commitInfo: Files.CommitInfo` - Contains the path and other optional modifiers for the future upload commit. Equivalent to the parameters provided to upload.
- `duration: Double` - How long before this link expires, in seconds.  Attempting to start an upload with this link longer than this period  of time after link creation will result in an error.

---

## GetTemporaryUploadLinkResult

`class`

**Properties:**

- `link: String` - The temporary link which can be used to stream a file to a Dropbox location.

---

## GetThumbnailBatchArg

`class`

Arguments for getThumbnailBatch.

**Properties:**

- `entries: [Files.ThumbnailArg]` - List of files to get thumbnails.

---

## GetThumbnailBatchError

`enum`

**Cases:**

- `tooManyFiles` - The operation involves more than 25 files.
- `other`

---

## GetThumbnailBatchResult

`class`

**Properties:**

- `entries: [Files.GetThumbnailBatchResultEntry]` - List of files and their thumbnails.

---

## GetThumbnailBatchResultData

`class`

**Properties:**

- `metadata: Files.FileMetadata`
- `thumbnail: String` - A string containing the base64-encoded thumbnail data for this file.

---

## GetThumbnailBatchResultEntry

`enum`

**Cases:**

- `success` (`Files.GetThumbnailBatchResultData`)
- `failure` (`Files.ThumbnailError`) - The result for this file if it was an error.
- `other`

---

## GpsCoordinates

`class`

GPS coordinates for a photo or video.

**Properties:**

- `latitude: Double` - Latitude of the GPS coordinates.
- `longitude: Double` - Longitude of the GPS coordinates.

---

## HighlightSpan

`class`

**Properties:**

- `highlightStr: String` - String to be determined whether it should be highlighted or not.
- `isHighlighted: Bool` - The string should be highlighted or not.

---

## ImportFormat

`enum`

The import format of the incoming Paper doc content.

**Cases:**

- `html` - The provided data is interpreted as standard HTML.
- `markdown` - The provided data is interpreted as markdown.
- `plainText` - The provided data is interpreted as plain text.
- `other`

---

## ListFolderArg

`class`

**Properties:**

- `path: String` - A unique identifier for the file.
- `recursive: Bool` - If true, the list folder operation will be applied recursively to all subfolders and the response will contain contents of all subfolders.
- `includeMediaInfo: Bool` - If true, mediaInfo in FileMetadata is set for photo and video. This parameter will no longer have an effect starting December 2, 2019.
- `includeDeleted: Bool` - If true, the results will include entries for files and folders that used to exist but were deleted.
- `includeHasExplicitSharedMembers: Bool` - If true, the results will include a flag for each file indicating whether or not  that file has any explicit members.
- `includeMountedFolders: Bool` - If true, the results will include entries under mounted folders which includes app folder, shared folder and team folder.
- `limit: UInt32?` - The maximum number of results to return per request. Note: This is an approximate number and there can be slightly more entries returned in some cases.
- `sharedLink: Files.SharedLink?` - A shared link to list the contents of. If the link is password-protected, the password must be provided. If this field is present, path in ListFolderArg will be relative to root of the shared link. Only non-recursive mode is supported for shared link.
- `includePropertyGroups: FileProperties.TemplateFilterBase?` - If set to a valid list of template IDs, propertyGroups in FileMetadata is set if there exists property data associated with the file and each of the listed templates.
- `includeNonDownloadableFiles: Bool` - If true, include files that are not downloadable, i.e. Google Docs.

---

## ListFolderContinueArg

`class`

**Properties:**

- `cursor: String` - The cursor returned by your last call to listFolder or listFolderContinue.

---

## ListFolderContinueError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `reset` - Indicates that the cursor has been invalidated. Call listFolder to obtain a new cursor.
- `other`

---

## ListFolderError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `templateError` (`FileProperties.TemplateError`)
- `other`

---

## ListFolderGetLatestCursorResult

`class`

**Properties:**

- `cursor: String` - Pass the cursor into listFolderContinue to see what's changed in the folder since your previous query.

---

## ListFolderLongpollArg

`class`

**Properties:**

- `cursor: String` - A cursor as returned by listFolder or listFolderContinue. Cursors retrieved by setting includeMediaInfo in ListFolderArg to true are not supported.
- `timeout: UInt64` - A timeout in seconds. The request will block for at most this length of time, plus up to 90 seconds of random jitter added to avoid the thundering herd problem. Care should be taken when using this parameter, as some network infrastructure does not support long timeouts.

---

## ListFolderLongpollError

`enum`

**Cases:**

- `reset` - Indicates that the cursor has been invalidated. Call listFolder to obtain a new cursor.
- `other`

---

## ListFolderLongpollResult

`class`

**Properties:**

- `changes: Bool` - Indicates whether new changes are available. If true, call listFolderContinue to retrieve the changes.
- `backoff: UInt64?` - If present, backoff for at least this many seconds before calling listFolderLongpoll again.

---

## ListFolderResult

`class`

**Properties:**

- `entries: [Files.Metadata]` - The files and (direct) subfolders in the folder.
- `cursor: String` - Pass the cursor into listFolderContinue to see what's changed in the folder since your previous query.
- `hasMore: Bool` - If true, then there are more entries available. Pass the cursor to listFolderContinue to retrieve the rest.

---

## ListRevisionsArg

`class`

**Properties:**

- `path: String` - The path to the file you want to see the revisions of.
- `mode: Files.ListRevisionsMode` - Determines the behavior of the API in listing the revisions for a given file path or id.
- `limit: UInt64` - The maximum number of revision entries returned.

---

## ListRevisionsError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `other`

---

## ListRevisionsMode

`enum`

**Cases:**

- `path` - Returns revisions with the same file path as identified by the latest file entry at the given file path or id.
- `id` - Returns revisions with the same file id as identified by the latest file entry at the given file path or id.
- `other`

---

## ListRevisionsResult

`class`

**Properties:**

- `isDeleted: Bool` - If the file identified by the latest revision in the response is either deleted or moved.
- `serverDeleted: Date?` - The time of deletion if the file was deleted.
- `entries: [Files.FileMetadata]` - The revisions for the file. Only revisions that are not deleted will show up here.

---

## LockConflictError

`class`

**Properties:**

- `lock: Files.FileLock` - The lock that caused the conflict.

---

## LockFileArg

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to a file.

---

## LockFileBatchArg

`class`

**Properties:**

- `entries: [Files.LockFileArg]` - List of 'entries'. Each 'entry' contains a path of the file which will be locked or queried. Duplicate path arguments in the batch are considered only once.

---

## LockFileBatchResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `entries: [Files.LockFileResultEntry]` - Each Entry in the 'entries' will have '.tag' with the operation status (e.g. success), the metadata for the file and the lock state after the operation.

---

## LockFileError

`enum`

**Cases:**

- `pathLookup` (`Files.LookupError`) - Could not find the specified resource.
- `tooManyWriteOperations` - There are too many write operations in user's Dropbox. Please retry this request.
- `tooManyFiles` - There are too many files in one request. Please retry with fewer files.
- `noWritePermission` - The user does not have permissions to change the lock state or access the file.
- `cannotBeLocked` - Item is a type that cannot be locked.
- `fileNotShared` - Requested file is not currently shared.
- `lockConflict` (`Files.LockConflictError`) - The user action conflicts with an existing lock on the file.
- `internalError` - Something went wrong with the job on Dropbox's end. You'll need to verify that the action you were taking succeeded, and if not, try again. This should happen very rarely.
- `other`

---

## LockFileResult

`class`

**Properties:**

- `metadata: Files.Metadata` - Metadata of the file.
- `lock: Files.FileLock` - The file lock state after the operation.

---

## LockFileResultEntry

`enum`

**Cases:**

- `success` (`Files.LockFileResult`)
- `failure` (`Files.LockFileError`)

---

## LookupError

`enum`

**Cases:**

- `malformedPath` (`String?`) - The given path does not satisfy the required path format. Please refer to the Path formats documentation https://www.dropbox.com/developers/documentation/http/documentation#path-formats for more information.
- `notFound` - There is nothing at the given path.
- `notFile` - We were expecting a file, but the given path refers to something that isn't a file.
- `notFolder` - We were expecting a folder, but the given path refers to something that isn't a folder.
- `restrictedContent` - The file cannot be transferred because the content is restricted. For example, we might restrict a file due to legal requirements.
- `unsupportedContentType` - This operation is not supported for this content type.
- `locked` - The given path is locked.
- `other`

---

## MediaInfo

`enum`

**Cases:**

- `pending` - Indicate the photo/video is still under processing and metadata is not available yet.
- `metadata` (`Files.MediaMetadata`) - The metadata for the photo/video.

---

## MediaMetadata

`class`

Metadata for a photo or video.

**Properties:**

- `dimensions: Files.Dimensions?` - Dimension of the photo/video.
- `location: Files.GpsCoordinates?` - The GPS coordinate of the photo/video.
- `timeTaken: Date?` - The timestamp when the photo/video is taken.

---

## MetadataV2

`enum`

Metadata for a file, folder or other resource types.

**Cases:**

- `metadata` (`Files.Metadata`)
- `other`

---

## MinimalFileLinkMetadata

`class`

**Properties:**

- `url: String` - URL of the shared link.
- `id: String?` - Unique identifier for the linked file.
- `path: String?` - Full path in the user's Dropbox. This always starts with a slash. This field will only be present only if the linked file is in the authenticated user's Dropbox.
- `rev: String` - A unique identifier for the current revision of a file. This field is the same rev as elsewhere in the API and can be used to detect changes and avoid conflicts.

---

## RelocationBatchArgBase

`class`

**Properties:**

- `entries: [Files.RelocationPath]` - List of entries to be moved or copied. Each entry is RelocationPath.
- `autorename: Bool` - If there's a conflict with any file, have the Dropbox server try to autorename that file to avoid the conflict.

---

## MoveBatchArg

`class` (inherits from `Files.RelocationBatchArgBase`)

**Properties:**

- `allowOwnershipTransfer: Bool` - Allow moves by owner even if it would result in an ownership transfer for the content being moved. This does not apply to copies.

---

## MoveIntoFamilyError

`enum`

**Cases:**

- `isSharedFolder` - Moving shared folder into Family Room folder is not allowed.
- `other`

---

## MoveIntoVaultError

`enum`

**Cases:**

- `isSharedFolder` - Moving shared folder into Vault is not allowed.
- `other`

---

## PaperContentError

`enum`

**Cases:**

- `insufficientPermissions` - Your account does not have permissions to edit Paper docs.
- `contentMalformed` - The provided content was malformed and cannot be imported to Paper.
- `docLengthExceeded` - The Paper doc would be too large, split the content into multiple docs.
- `imageSizeExceeded` - The imported document contains an image that is too large. The current limit is 1MB. This only applies to HTML with data URI.
- `other`

---

## PaperCreateArg

`class`

**Properties:**

- `path: String` - The fully qualified path to the location in the user's Dropbox where the Paper Doc should be created. This should include the document's title and end with .paper.
- `importFormat: Files.ImportFormat` - The format of the provided data.

---

## PaperCreateError

`enum`

**Cases:**

- `insufficientPermissions` - Your account does not have permissions to edit Paper docs.
- `contentMalformed` - The provided content was malformed and cannot be imported to Paper.
- `docLengthExceeded` - The Paper doc would be too large, split the content into multiple docs.
- `imageSizeExceeded` - The imported document contains an image that is too large. The current limit is 1MB. This only applies to HTML with data URI.
- `other`
- `invalidPath` - The file could not be saved to the specified location.
- `emailUnverified` - The user's email must be verified to create Paper docs.
- `invalidFileExtension` - The file path must end in .paper.
- `paperDisabled` - Paper is disabled for your team.

---

## PaperCreateResult

`class`

**Properties:**

- `url: String` - URL to open the Paper Doc.
- `resultPath: String` - The fully qualified path the Paper Doc was actually created at.
- `fileId: String` - The id to use in Dropbox APIs when referencing the Paper Doc.
- `paperRevision: Int64` - The current doc revision.

---

## PaperDocUpdatePolicy

`enum`

**Cases:**

- `update` - Sets the doc content to the provided content if the provided paper_revision matches the latest doc revision. Otherwise, returns an error.
- `overwrite` - Sets the doc content to the provided content without checking paper_revision.
- `prepend` - Adds the provided content to the beginning of the doc without checking paper_revision.
- `append` - Adds the provided content to the end of the doc without checking paper_revision.
- `other`

---

## PaperUpdateArg

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to update. The path must correspond to a Paper doc or an error will be returned.
- `importFormat: Files.ImportFormat` - The format of the provided data.
- `docUpdatePolicy: Files.PaperDocUpdatePolicy` - How the provided content should be applied to the doc.
- `paperRevision: Int64?` - The latest doc revision. Required when doc_update_policy is update. This value must match the current revision of the doc or error revision_mismatch will be returned.

---

## PaperUpdateError

`enum`

**Cases:**

- `insufficientPermissions` - Your account does not have permissions to edit Paper docs.
- `contentMalformed` - The provided content was malformed and cannot be imported to Paper.
- `docLengthExceeded` - The Paper doc would be too large, split the content into multiple docs.
- `imageSizeExceeded` - The imported document contains an image that is too large. The current limit is 1MB. This only applies to HTML with data URI.
- `other`
- `path` (`Files.LookupError`)
- `revisionMismatch` - The provided revision does not match the document head.
- `docArchived` - This operation is not allowed on archived Paper docs.
- `docDeleted` - This operation is not allowed on deleted Paper docs.

---

## PaperUpdateResult

`class`

**Properties:**

- `paperRevision: Int64` - The current doc revision.

---

## PathOrLink

`enum`

**Cases:**

- `path` (`String`)
- `link` (`Files.SharedLinkFileInfo`)
- `other`

---

## PathToTags

`class`

**Properties:**

- `path: String` - Path of the item.
- `tags: [Files.Tag]` - Tags assigned to this item.

---

## PhotoMetadata

`class` (inherits from `Files.MediaMetadata`)

Metadata for a photo.

No public stored properties.

---

## PreviewArg

`class`

**Properties:**

- `path: String` - The path of the file to preview.
- `rev: String?` - Please specify revision in path instead.

---

## PreviewError

`enum`

**Cases:**

- `path` (`Files.LookupError`) - An error occurs when downloading metadata for the file.
- `inProgress` - This preview generation is still in progress and the file is not ready  for preview yet.
- `unsupportedExtension` - The file extension is not supported preview generation.
- `unsupportedContent` - The file content is not supported for preview generation.

---

## PreviewResult

`class`

**Properties:**

- `fileMetadata: Files.FileMetadata?` - Metadata corresponding to the file received as an argument. Will be populated if the endpoint is called with a path (ReadPath).
- `linkMetadata: Files.MinimalFileLinkMetadata?` - Minimal metadata corresponding to the file received as an argument. Will be populated if the endpoint is called using a shared link (SharedLinkFileInfo).

---

## RelocationPath

`class`

**Properties:**

- `fromPath: String` - Path in the user's Dropbox to be copied or moved.
- `toPath: String` - Path in the user's Dropbox that is the destination.

---

## RelocationArg

`class` (inherits from `Files.RelocationPath`)

**Properties:**

- `allowSharedFolder: Bool` - This flag has no effect.
- `autorename: Bool` - If there's a conflict, have the Dropbox server try to autorename the file to avoid the conflict.
- `allowOwnershipTransfer: Bool` - Allow moves by owner even if it would result in an ownership transfer for the content being moved. This does not apply to copies.

---

## RelocationBatchArg

`class` (inherits from `Files.RelocationBatchArgBase`)

**Properties:**

- `allowSharedFolder: Bool` - This flag has no effect.
- `allowOwnershipTransfer: Bool` - Allow moves by owner even if it would result in an ownership transfer for the content being moved. This does not apply to copies.

---

## RelocationError

`enum`

**Cases:**

- `fromLookup` (`Files.LookupError`)
- `fromWrite` (`Files.WriteError`)
- `to` (`Files.WriteError`)
- `cantCopySharedFolder` - Shared folders can't be copied.
- `cantNestSharedFolder` - Your move operation would result in nested shared folders.  This is not allowed.
- `cantMoveFolderIntoItself` - You cannot move a folder into itself.
- `tooManyFiles` - The operation would involve more than 10,000 files and folders.
- `duplicatedOrNestedPaths` - There are duplicated/nested paths among fromPath in RelocationArg and toPath in RelocationArg.
- `cantTransferOwnership` - Your move operation would result in an ownership transfer. You may reissue the request with the field allowOwnershipTransfer in RelocationArg to true.
- `insufficientQuota` - The current user does not have enough space to move or copy the files.
- `internalError` - Something went wrong with the job on Dropbox's end. You'll need to verify that the action you were taking succeeded, and if not, try again. This should happen very rarely.
- `cantMoveSharedFolder` - Can't move the shared folder to the given destination.
- `cantMoveIntoVault` (`Files.MoveIntoVaultError`) - Some content cannot be moved into Vault under certain circumstances, see detailed error.
- `cantMoveIntoFamily` (`Files.MoveIntoFamilyError`) - Some content cannot be moved into the Family Room folder under certain circumstances, see detailed error.
- `other`

---

## RelocationBatchError

`enum`

**Cases:**

- `fromLookup` (`Files.LookupError`)
- `fromWrite` (`Files.WriteError`)
- `to` (`Files.WriteError`)
- `cantCopySharedFolder` - Shared folders can't be copied.
- `cantNestSharedFolder` - Your move operation would result in nested shared folders.  This is not allowed.
- `cantMoveFolderIntoItself` - You cannot move a folder into itself.
- `tooManyFiles` - The operation would involve more than 10,000 files and folders.
- `duplicatedOrNestedPaths` - There are duplicated/nested paths among fromPath in RelocationArg and toPath in RelocationArg.
- `cantTransferOwnership` - Your move operation would result in an ownership transfer. You may reissue the request with the field allowOwnershipTransfer in RelocationArg to true.
- `insufficientQuota` - The current user does not have enough space to move or copy the files.
- `internalError` - Something went wrong with the job on Dropbox's end. You'll need to verify that the action you were taking succeeded, and if not, try again. This should happen very rarely.
- `cantMoveSharedFolder` - Can't move the shared folder to the given destination.
- `cantMoveIntoVault` (`Files.MoveIntoVaultError`) - Some content cannot be moved into Vault under certain circumstances, see detailed error.
- `cantMoveIntoFamily` (`Files.MoveIntoFamilyError`) - Some content cannot be moved into the Family Room folder under certain circumstances, see detailed error.
- `other`
- `tooManyWriteOperations` - There are too many write operations in user's Dropbox. Please retry this request.

---

## RelocationBatchErrorEntry

`enum`

**Cases:**

- `relocationError` (`Files.RelocationError`) - User errors that retry won't help.
- `internalError` - Something went wrong with the job on Dropbox's end. You'll need to verify that the action you were taking succeeded, and if not, try again. This should happen very rarely.
- `tooManyWriteOperations` - There are too many write operations in user's Dropbox. Please retry this request.
- `other`

---

## RelocationBatchJobStatus

`enum`

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.RelocationBatchResult`) - The copy or move batch job has finished.
- `failed` (`Files.RelocationBatchError`) - The copy or move batch job has failed with exception.

---

## RelocationBatchLaunch

`enum`

Result returned by copyBatch or moveBatch that may either launch an asynchronous job or complete synchronously.

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.RelocationBatchResult`)
- `other`

---

## RelocationBatchResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `entries: [Files.RelocationBatchResultData]`

---

## RelocationBatchResultData

`class`

**Properties:**

- `metadata: Files.Metadata` - Metadata of the relocated object.

---

## RelocationBatchResultEntry

`enum`

**Cases:**

- `success` (`Files.Metadata`)
- `failure` (`Files.RelocationBatchErrorEntry`)
- `other`

---

## RelocationBatchV2JobStatus

`enum`

Result returned by copyBatchCheckV2 or moveBatchCheckV2 that may either be in progress or completed with result for each entry.

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.RelocationBatchV2Result`) - The copy or move batch job has finished.

---

## RelocationBatchV2Launch

`enum`

Result returned by copyBatchV2 or moveBatchV2 that may either launch an asynchronous job or complete synchronously.

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.RelocationBatchV2Result`)

---

## RelocationBatchV2Result

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `entries: [Files.RelocationBatchResultEntry]` - Each entry in CopyBatchArg.entries or entries in MoveBatchArg will appear at the same position inside entries in RelocationBatchV2Result.

---

## RelocationResult

`class` (inherits from `Files.FileOpsResult`)

**Properties:**

- `metadata: Files.Metadata` - Metadata of the relocated object.

---

## RemoveTagArg

`class`

**Properties:**

- `path: String` - Path to the item to tag.
- `tagText: String` - The tag to remove. Will be automatically converted to lowercase letters.

---

## RemoveTagError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `other`
- `tagNotPresent` - That tag doesn't exist at this path.

---

## RestoreArg

`class`

**Properties:**

- `path: String` - The path to save the restored file.
- `rev: String` - The revision to restore.

---

## RestoreError

`enum`

**Cases:**

- `pathLookup` (`Files.LookupError`) - An error occurs when downloading metadata for the file.
- `pathWrite` (`Files.WriteError`) - An error occurs when trying to restore the file to that path.
- `invalidRevision` - The revision is invalid. It may not exist or may point to a deleted file.
- `inProgress` - The restore is currently executing, but has not yet completed.
- `other`

---

## SaveCopyReferenceArg

`class`

**Properties:**

- `copyReference: String` - A copy reference returned by copyReferenceGet.
- `path: String` - Path in the user's Dropbox that is the destination.

---

## SaveCopyReferenceError

`enum`

**Cases:**

- `path` (`Files.WriteError`)
- `invalidCopyReference` - The copy reference is invalid.
- `noPermission` - You don't have permission to save the given copy reference. Please make sure this app is same app which created the copy reference and the source user is still linked to the app.
- `notFound` - The file referenced by the copy reference cannot be found.
- `tooManyFiles` - The operation would involve more than 10,000 files and folders.
- `other`

---

## SaveCopyReferenceResult

`class`

**Properties:**

- `metadata: Files.Metadata` - The metadata of the saved file or folder in the user's Dropbox.

---

## SaveUrlArg

`class`

**Properties:**

- `path: String` - The path in Dropbox where the URL will be saved to.
- `url: String` - The URL to be saved.

---

## SaveUrlError

`enum`

**Cases:**

- `path` (`Files.WriteError`)
- `downloadFailed` - Failed downloading the given URL. The URL may be  password-protected and the password provided was incorrect,  or the link may be disabled.
- `invalidUrl` - The given URL is invalid.
- `notFound` - The file where the URL is saved to no longer exists.
- `other`

---

## SaveUrlJobStatus

`enum`

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.FileMetadata`) - Metadata of the file where the URL is saved to.
- `failed` (`Files.SaveUrlError`)

---

## SaveUrlResult

`enum`

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.FileMetadata`) - Metadata of the file where the URL is saved to.

---

## SearchArg

`class`

**Properties:**

- `path: String` - The path in the user's Dropbox to search. Should probably be a folder.
- `query: String` - The string to search for. Query string may be rewritten to improve relevance of results. The string is split on spaces into multiple tokens. For file name searching, the last token is used for prefix matching (i.e. "bat c" matches "bat cave" but not "batman car").
- `start: UInt64` - The starting index within the search results (used for paging).
- `maxResults: UInt64` - The maximum number of search results to return.
- `mode: Files.SearchMode` - The search mode (filename, filename_and_content, or deleted_filename). Note that searching file content is only available for Dropbox Business accounts.

---

## SearchError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `invalidArgument` (`String?`)
- `internalError` - Something went wrong, please try again.
- `other`

---

## SearchMatch

`class`

**Properties:**

- `matchType: Files.SearchMatchType` - The type of the match.
- `metadata: Files.Metadata` - The metadata for the matched file or folder.

---

## SearchMatchFieldOptions

`class`

**Properties:**

- `includeHighlights: Bool` - Whether to include highlight span from file title.

---

## SearchMatchType

`enum`

Indicates what type of match was found for a given item.

**Cases:**

- `filename` - This item was matched on its file or folder name.
- `content` - This item was matched based on its file contents.
- `both` - This item was matched based on both its contents and its file name.

---

## SearchMatchTypeV2

`enum`

Indicates what type of match was found for a given item.

**Cases:**

- `filename` - This item was matched on its file or folder name.
- `fileContent` - This item was matched based on its file contents.
- `filenameAndContent` - This item was matched based on both its contents and its file name.
- `imageContent` - This item was matched on image content.
- `other`

---

## SearchMatchV2

`class`

**Properties:**

- `metadata: Files.MetadataV2` - The metadata for the matched file or folder.
- `matchType: Files.SearchMatchTypeV2?` - The type of the match.
- `highlightSpans: [Files.HighlightSpan]?` - The list of HighlightSpan determines which parts of the file title should be highlighted.

---

## SearchMode

`enum`

**Cases:**

- `filename` - Search file and folder names.
- `filenameAndContent` - Search file and folder names as well as file contents.
- `deletedFilename` - Search for deleted file and folder names.

---

## SearchOptions

`class`

**Properties:**

- `path: String?` - Scopes the search to a path in the user's Dropbox. Searches the entire Dropbox if not specified.
- `maxResults: UInt64` - The maximum number of search results to return.
- `orderBy: Files.SearchOrderBy?` - Specified property of the order of search results. By default, results are sorted by relevance.
- `fileStatus: Files.FileStatus` - Restricts search to the given file status.
- `filenameOnly: Bool` - Restricts search to only match on filenames.
- `fileExtensions: [String]?` - Restricts search to only the extensions specified. Only supported for active file search.
- `fileCategories: [Files.FileCategory]?` - Restricts search to only the file categories specified. Only supported for active file search.
- `accountId: String?` - Restricts results to the given account id.

---

## SearchOrderBy

`enum`

**Cases:**

- `relevance`
- `lastModifiedTime`
- `other`

---

## SearchResult

`class`

**Properties:**

- `matches: [Files.SearchMatch]` - A list (possibly empty) of matches for the query.
- `more: Bool` - Used for paging. If true, indicates there is another page of results available that can be fetched by calling search again.
- `start: UInt64` - Used for paging. Value to set the start argument to when calling search to fetch the next page of results.

---

## SearchV2Arg

`class`

**Properties:**

- `query: String` - The string to search for. May match across multiple fields based on the request arguments.
- `options: Files.SearchOptions?` - Options for more targeted search results.
- `matchFieldOptions: Files.SearchMatchFieldOptions?` - Options for search results match fields.
- `includeHighlights: Bool?` - Deprecated and moved this option to SearchMatchFieldOptions.

---

## SearchV2ContinueArg

`class`

**Properties:**

- `cursor: String` - The cursor returned by your last call to searchV2. Used to fetch the next page of results.

---

## SearchV2Result

`class`

**Properties:**

- `matches: [Files.SearchMatchV2]` - A list (possibly empty) of matches for the query.
- `hasMore: Bool` - Used for paging. If true, indicates there is another page of results available that can be fetched by calling searchContinueV2 with the cursor.
- `cursor: String?` - Pass the cursor into searchContinueV2 to fetch the next page of results.

---

## SharedLink

`class`

**Properties:**

- `url: String` - Shared link url.
- `password: String?` - Password for the shared link.

---

## SharedLinkFileInfo

`class`

**Properties:**

- `url: String` - The shared link corresponding to either a file or shared link to a folder. If it is for a folder shared link, we use the path param to determine for which file in the folder the view is for.
- `path: String?` - The path corresponding to a file in a shared link to a folder. Required for shared links to folders.
- `password: String?` - Password for the shared link. Required for password-protected shared links to files  unless it can be read from a cookie.

---

## SingleUserLock

`class`

**Properties:**

- `created: Date` - The time the lock was created.
- `lockHolderAccountId: String` - The account ID of the lock holder if known.
- `lockHolderTeamId: String?` - The id of the team of the account holder if it exists.

---

## SymlinkInfo

`class`

**Properties:**

- `target: String` - The target this symlink points to.

---

## SyncSetting

`enum`

**Cases:**

- `default_` - On first sync to members' computers, the specified folder will follow its parent folder's setting or otherwise follow default sync behavior.
- `notSynced` - On first sync to members' computers, the specified folder will be set to not sync with selective sync.
- `notSyncedInactive` - The specified folder's not_synced setting is inactive due to its location or other configuration changes. It will follow its parent folder's setting.
- `other`

---

## SyncSettingArg

`enum`

**Cases:**

- `default_` - On first sync to members' computers, the specified folder will follow its parent folder's setting or otherwise follow default sync behavior.
- `notSynced` - On first sync to members' computers, the specified folder will be set to not sync with selective sync.
- `other`

---

## SyncSettingsError

`enum`

**Cases:**

- `path` (`Files.LookupError`)
- `unsupportedCombination` - Setting this combination of sync settings simultaneously is not supported.
- `unsupportedConfiguration` - The specified configuration is not supported.
- `other`

---

## Tag

`enum`

Tag that can be added in multiple ways.

**Cases:**

- `userGeneratedTag` (`Files.UserGeneratedTag`) - Tag generated by the user.
- `other`

---

## ThumbnailArg

`class`

**Properties:**

- `path: String` - The path to the image file you want to thumbnail.
- `format: Files.ThumbnailFormat` - The format for the thumbnail image, jpeg (default) or png. For  images that are photos, jpeg should be preferred, while png is  better for screenshots and digital arts.
- `size: Files.ThumbnailSize` - The size for the thumbnail image.
- `mode: Files.ThumbnailMode` - How to resize and crop the image to achieve the desired size.

---

## ThumbnailError

`enum`

**Cases:**

- `path` (`Files.LookupError`) - An error occurs when downloading metadata for the image.
- `unsupportedExtension` - The file extension doesn't allow conversion to a thumbnail.
- `unsupportedImage` - The image cannot be converted to a thumbnail.
- `conversionError` - An error occurs during thumbnail conversion.

---

## ThumbnailFormat

`enum`

**Cases:**

- `jpeg`
- `png`

---

## ThumbnailMode

`enum`

**Cases:**

- `strict` - Scale down the image to fit within the given size.
- `bestfit` - Scale down the image to fit within the given size or its transpose.
- `fitoneBestfit` - Scale down the image to completely cover the given size or its transpose.

---

## ThumbnailSize

`enum`

**Cases:**

- `w32h32` - 32 by 32 px.
- `w64h64` - 64 by 64 px.
- `w128h128` - 128 by 128 px.
- `w256h256` - 256 by 256 px.
- `w480h320` - 480 by 320 px.
- `w640h480` - 640 by 480 px.
- `w960h640` - 960 by 640 px.
- `w1024h768` - 1024 by 768 px.
- `w2048h1536` - 2048 by 1536 px.

---

## ThumbnailV2Arg

`class`

**Properties:**

- `resource: Files.PathOrLink` - Information specifying which file to preview. This could be a path to a file, a shared link pointing to a file, or a shared link pointing to a folder, with a relative path.
- `format: Files.ThumbnailFormat` - The format for the thumbnail image, jpeg (default) or png. For  images that are photos, jpeg should be preferred, while png is  better for screenshots and digital arts.
- `size: Files.ThumbnailSize` - The size for the thumbnail image.
- `mode: Files.ThumbnailMode` - How to resize and crop the image to achieve the desired size.

---

## ThumbnailV2Error

`enum`

**Cases:**

- `path` (`Files.LookupError`) - An error occurred when downloading metadata for the image.
- `unsupportedExtension` - The file extension doesn't allow conversion to a thumbnail.
- `unsupportedImage` - The image cannot be converted to a thumbnail.
- `conversionError` - An error occurred during thumbnail conversion.
- `accessDenied` - Access to this shared link is forbidden.
- `notFound` - The shared link does not exist.
- `other`

---

## UnlockFileArg

`class`

**Properties:**

- `path: String` - Path in the user's Dropbox to a file.

---

## UnlockFileBatchArg

`class`

**Properties:**

- `entries: [Files.UnlockFileArg]` - List of 'entries'. Each 'entry' contains a path of the file which will be unlocked. Duplicate path arguments in the batch are considered only once.

---

## UploadArg

`class` (inherits from `Files.CommitInfo`)

**Properties:**

- `contentHash: String?` - A hash of the file content uploaded in this call. If provided and the uploaded content does not match this hash, an error will be returned. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.

---

## UploadError

`enum`

**Cases:**

- `path` (`Files.UploadWriteFailed`) - Unable to save the uploaded contents to a file.
- `propertiesError` (`FileProperties.InvalidPropertyGroupError`) - The supplied property group is invalid. The file has uploaded without property groups.
- `payloadTooLarge` - The request payload must be at most 150 MB.
- `contentHashMismatch` - The content received by the Dropbox server in this call does not match the provided content hash.
- `other`

---

## UploadSessionAppendArg

`class`

**Properties:**

- `cursor: Files.UploadSessionCursor` - Contains the upload session ID and the offset.
- `close: Bool` - If true, the current session will be closed, at which point you won't be able to call uploadSessionAppendV2 anymore with the current session.
- `contentHash: String?` - A hash of the file content uploaded in this call. If provided and the uploaded content does not match this hash, an error will be returned. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.

---

## UploadSessionLookupError

`enum`

**Cases:**

- `notFound` - The upload session ID was not found or has expired. Upload sessions are valid for 7 days.
- `incorrectOffset` (`Files.UploadSessionOffsetError`) - The specified offset was incorrect. See the value for the correct offset. This error may occur when a previous request was received and processed successfully but the client did not receive the response, e.g. due to a network error.
- `closed` - You are attempting to append data to an upload session that has already been closed (i.e. committed).
- `notClosed` - The session must be closed before calling upload_session/finish_batch.
- `tooLarge` - You can not append to the upload session because the size of a file should not reach the max file size limit (i.e. 350GB).
- `concurrentSessionInvalidOffset` - For concurrent upload sessions, offset needs to be multiple of 4194304 bytes.
- `concurrentSessionInvalidDataSize` - For concurrent upload sessions, only chunks with size multiple of 4194304 bytes can be uploaded.
- `payloadTooLarge` - The request payload must be at most 150 MB.
- `other`

---

## UploadSessionAppendError

`enum`

**Cases:**

- `notFound` - The upload session ID was not found or has expired. Upload sessions are valid for 7 days.
- `incorrectOffset` (`Files.UploadSessionOffsetError`) - The specified offset was incorrect. See the value for the correct offset. This error may occur when a previous request was received and processed successfully but the client did not receive the response, e.g. due to a network error.
- `closed` - You are attempting to append data to an upload session that has already been closed (i.e. committed).
- `notClosed` - The session must be closed before calling upload_session/finish_batch.
- `tooLarge` - You can not append to the upload session because the size of a file should not reach the max file size limit (i.e. 350GB).
- `concurrentSessionInvalidOffset` - For concurrent upload sessions, offset needs to be multiple of 4194304 bytes.
- `concurrentSessionInvalidDataSize` - For concurrent upload sessions, only chunks with size multiple of 4194304 bytes can be uploaded.
- `payloadTooLarge` - The request payload must be at most 150 MB.
- `other`
- `contentHashMismatch` - The content received by the Dropbox server in this call does not match the provided content hash.

---

## UploadSessionCursor

`class`

**Properties:**

- `sessionId: String` - The upload session ID (returned by uploadSessionStart).
- `offset: UInt64` - Offset in bytes at which data should be appended. We use this to make sure upload data isn't lost or duplicated in the event of a network error.

---

## UploadSessionFinishArg

`class`

**Properties:**

- `cursor: Files.UploadSessionCursor` - Contains the upload session ID and the offset.
- `commit: Files.CommitInfo` - Contains the path and other optional modifiers for the commit.
- `contentHash: String?` - A hash of the file content uploaded in this call. If provided and the uploaded content does not match this hash, an error will be returned. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.

---

## UploadSessionFinishBatchArg

`class`

**Properties:**

- `entries: [Files.UploadSessionFinishArg]` - Commit information for each file in the batch.

---

## UploadSessionFinishBatchJobStatus

`enum`

**Cases:**

- `inProgress` - The asynchronous job is still in progress.
- `complete` (`Files.UploadSessionFinishBatchResult`) - The uploadSessionFinishBatch has finished.

---

## UploadSessionFinishBatchLaunch

`enum`

Result returned by uploadSessionFinishBatch that may either launch an asynchronous job or complete synchronously.

**Cases:**

- `asyncJobId` (`String`) - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` (`Files.UploadSessionFinishBatchResult`)
- `other`

---

## UploadSessionFinishBatchResult

`class`

**Properties:**

- `entries: [Files.UploadSessionFinishBatchResultEntry]` - Each entry in entries in UploadSessionFinishBatchArg will appear at the same position inside entries in UploadSessionFinishBatchResult.

---

## UploadSessionFinishBatchResultEntry

`enum`

**Cases:**

- `success` (`Files.FileMetadata`)
- `failure` (`Files.UploadSessionFinishError`)

---

## UploadSessionFinishError

`enum`

**Cases:**

- `lookupFailed` (`Files.UploadSessionLookupError`) - The session arguments are incorrect; the value explains the reason.
- `path` (`Files.WriteError`) - Unable to save the uploaded contents to a file. Data has already been appended to the upload session. Please retry with empty data body and updated offset.
- `propertiesError` (`FileProperties.InvalidPropertyGroupError`) - The supplied property group is invalid. The file has uploaded without property groups.
- `tooManySharedFolderTargets` - The batch request commits files into too many different shared folders. Please limit your batch request to files contained in a single shared folder.
- `tooManyWriteOperations` - There are too many write operations happening in the user's Dropbox. You should retry uploading this file.
- `concurrentSessionDataNotAllowed` - Uploading data not allowed when finishing concurrent upload session.
- `concurrentSessionNotClosed` - Concurrent upload sessions need to be closed before finishing.
- `concurrentSessionMissingData` - Not all pieces of data were uploaded before trying to finish the session.
- `payloadTooLarge` - The request payload must be at most 150 MB.
- `contentHashMismatch` - The content received by the Dropbox server in this call does not match the provided content hash.
- `other`

---

## UploadSessionOffsetError

`class`

**Properties:**

- `correctOffset: UInt64` - The offset up to which data has been collected.

---

## UploadSessionStartArg

`class`

**Properties:**

- `close: Bool` - If true, the current session will be closed, at which point you won't be able to call uploadSessionAppendV2 anymore with the current session.
- `sessionType: Files.UploadSessionType?` - Type of upload session you want to start. If not specified, default is sequential in UploadSessionType.
- `contentHash: String?` - A hash of the file content uploaded in this call. If provided and the uploaded content does not match this hash, an error will be returned. For more information see our Content hash https://www.dropbox.com/developers/reference/content-hash page.

---

## UploadSessionStartBatchArg

`class`

**Properties:**

- `sessionType: Files.UploadSessionType?` - Type of upload session you want to start. If not specified, default is sequential in UploadSessionType.
- `numSessions: UInt64` - The number of upload sessions to start.

---

## UploadSessionStartBatchResult

`class`

**Properties:**

- `sessionIds: [String]` - A List of unique identifiers for the upload session. Pass each session_id to uploadSessionAppendV2 and uploadSessionFinish.

---

## UploadSessionStartError

`enum`

**Cases:**

- `concurrentSessionDataNotAllowed` - Uploading data not allowed when starting concurrent upload session.
- `concurrentSessionCloseNotAllowed` - Can not start a closed concurrent upload session.
- `payloadTooLarge` - The request payload must be at most 150 MB.
- `contentHashMismatch` - The content received by the Dropbox server in this call does not match the provided content hash.
- `other`

---

## UploadSessionStartResult

`class`

**Properties:**

- `sessionId: String` - A unique identifier for the upload session. Pass this to uploadSessionAppendV2 and uploadSessionFinish.

---

## UploadSessionType

`enum`

**Cases:**

- `sequential` - Pieces of data are uploaded sequentially one after another. This is the default behavior.
- `concurrent` - Pieces of data can be uploaded in concurrent RPCs in any order.
- `other`

---

## UploadWriteFailed

`class`

**Properties:**

- `reason: Files.WriteError` - The reason why the file couldn't be saved.
- `uploadSessionId: String` - The upload session ID; data has already been uploaded to the corresponding upload session and this ID may be used to retry the commit with uploadSessionFinish.

---

## UserGeneratedTag

`class`

**Properties:**

- `tagText: String`

---

## VideoMetadata

`class` (inherits from `Files.MediaMetadata`)

Metadata for a video.

**Properties:**

- `duration: UInt64?` - The duration of the video in milliseconds.

---

## WriteConflictError

`enum`

**Cases:**

- `file` - There's a file in the way.
- `folder` - There's a folder in the way.
- `fileAncestor` - There's a file at an ancestor path, so we couldn't create the required parent folders.
- `other`

---

## WriteError

`enum`

**Cases:**

- `malformedPath` (`String?`) - The given path does not satisfy the required path format. Please refer to the Path formats documentation https://www.dropbox.com/developers/documentation/http/documentation#path-formats for more information.
- `conflict` (`Files.WriteConflictError`) - Couldn't write to the target path because there was something in the way.
- `noWritePermission` - The user doesn't have permissions to write to the target location.
- `insufficientSpace` - The user doesn't have enough available space (bytes) to write more data.
- `disallowedName` - Dropbox will not save the file or folder because of its name.
- `teamFolder` - This endpoint cannot move or delete team folders.
- `operationSuppressed` - This file operation is not allowed at this path.
- `tooManyWriteOperations` - There are too many write operations in user's Dropbox. Please retry this request.
- `other`

---

## WriteMode

`enum`

Your intent when writing a file to some path. This is used to determine what constitutes a conflict and what the autorename strategy is. In some situations, the conflict behavior is identical: (a) If the target path doesn't refer to anything, the file is always written; no conflict. (b) If the target path refers to a folder, it's always a conflict. (c) If the target path refers to a file with identical contents, nothing gets written; no conflict. The conflict checking differs in the case where there's a file at the target path with contents different from the contents you're trying to write.

**Cases:**

- `add` - Do not overwrite an existing file if there is a conflict. The autorename strategy is to append a number to the file name. For example, "document.txt" might become "document (2).txt".
- `overwrite` - Always overwrite the existing file. The autorename strategy is the same as it is for add.
- `update` (`String`) - Overwrite if the given "rev" matches the existing file's "rev". The supplied value should be the latest known "rev" of the file, for example, from FileMetadata, from when the file was last downloaded by the app. This will cause the file on the Dropbox servers to be overwritten if the given "rev" matches the existing file's current "rev" on the Dropbox servers. The autorename strategy is to append the string "conflicted copy" to the file name. For example, "document.txt" might become "document (conflicted copy).txt" or "document (Panda's conflicted copy).txt".

---
