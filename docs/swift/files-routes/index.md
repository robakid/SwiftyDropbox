# FilesRoutes

Routes for the `files` namespace. Access via `client.files` on a `DropboxClient` instance.

For Objective-C compatible routes see `DBFilesRoutes`.

---

## alphaGetMetadata

> **Deprecated.** Use `getMetadata` instead.

Returns the metadata for a file or folder. This is an alpha endpoint compatible with the properties API. Note: Metadata for the root folder is unsupported.

**Scope:** `files.metadata.read`

```swift
@available(*, unavailable, message: "alphaGetMetadata is deprecated. Use getMetadata.")
func alphaGetMetadata(
    path: String,
    includeMediaInfo: Bool = false,
    includeDeleted: Bool = false,
    includeHasExplicitSharedMembers: Bool = false,
    includePropertyGroups: FileProperties.TemplateFilterBase? = nil,
    includePropertyTemplates: [String]? = nil
) -> RpcRequest<Files.MetadataSerializer, Files.AlphaGetMetadataErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of a file or folder on Dropbox. |
| `includeMediaInfo` | `Bool` | If true, media info is set for photo and video. Default `false`. |
| `includeDeleted` | `Bool` | If true, deleted metadata will be returned. Default `false`. |
| `includeHasExplicitSharedMembers` | `Bool` | If true, includes explicit shared members flag. Default `false`. |
| `includePropertyGroups` | `FileProperties.TemplateFilterBase?` | Filter for property groups. Default `nil`. |
| `includePropertyTemplates` | `[String]?` | If set to a valid list of template IDs, propertyGroups is set for files with custom properties. Default `nil`. |

### Returns

`Files.Metadata` on success, `Files.AlphaGetMetadataError` on failure.

---

## alphaUpload

> **Deprecated.** Use `upload` instead.

Create a new file with the contents provided in the request. Do not use this to upload a file larger than 150 MB. Instead, create an upload session with `uploadSessionStart`.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "alphaUpload is deprecated. Use upload.")
func alphaUpload(
    path: String,
    mode: Files.WriteMode = .add,
    autorename: Bool = false,
    clientModified: Date? = nil,
    mute: Bool = false,
    propertyGroups: [FileProperties.PropertyGroup]? = nil,
    strictConflict: Bool = false,
    contentHash: String? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.FileMetadataSerializer, Files.UploadErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to save the file. |
| `mode` | `Files.WriteMode` | Selects what to do if the file already exists. Default `.add`. |
| `autorename` | `Bool` | If there's a conflict, autorename the file. Default `false`. |
| `clientModified` | `Date?` | The value to store as the client modified timestamp. Default `nil`. |
| `mute` | `Bool` | If true, this file will not generate notifications. Default `false`. |
| `propertyGroups` | `[FileProperties.PropertyGroup]?` | Property groups to associate with the file. Default `nil`. |
| `strictConflict` | `Bool` | Be more strict about how each WriteMode detects conflict. Default `false`. |
| `contentHash` | `String?` | A hash of the file content. If provided and mismatched, an error is returned. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.FileMetadata` on success, `Files.UploadError` on failure.

---

## copy

> **Deprecated.** Use `copyV2` instead.

Copy a file or folder to a different location in the user's Dropbox. If the source path is a folder all its contents will be copied.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "copy is deprecated. Use copyV2.")
func copy(
    fromPath: String,
    toPath: String,
    allowSharedFolder: Bool = false,
    autorename: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.MetadataSerializer, Files.RelocationErrorSerializer>
```

### Returns

`Files.Metadata` on success, `Files.RelocationError` on failure.

---

## copyV2

Copy a file or folder to a different location in the user's Dropbox. If the source path is a folder all its contents will be copied.

**Scope:** `files.content.write`

```swift
func copyV2(
    fromPath: String,
    toPath: String,
    allowSharedFolder: Bool = false,
    autorename: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.RelocationResultSerializer, Files.RelocationErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `fromPath` | `String` | Path of the file or folder to copy. |
| `toPath` | `String` | Destination path. |
| `allowSharedFolder` | `Bool` | This flag has no effect. Default `false`. |
| `autorename` | `Bool` | If there's a conflict, autorename. Default `false`. |
| `allowOwnershipTransfer` | `Bool` | Allow moves by owner even if it would result in an ownership transfer. Default `false`. |

### Returns

`Files.RelocationResult` on success, `Files.RelocationError` on failure.

---

## copyBatch

> **Deprecated.** Use `copyBatchV2` instead.

Copy multiple files or folders to different locations at once in the user's Dropbox. Returns a job ID immediately and does the async copy in background. Use `copyBatchCheck` to check the job status.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "copyBatch is deprecated. Use copyBatchV2.")
func copyBatch(
    entries: [Files.RelocationPath],
    autorename: Bool = false,
    allowSharedFolder: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.RelocationBatchLaunchSerializer, VoidSerializer>
```

### Returns

`Files.RelocationBatchLaunch` on success, `Void` on failure.

---

## copyBatchV2

Copy multiple files or folders to different locations at once. This route returns status for each entry. This route will either finish synchronously, or return a job ID. Use `copyBatchCheckV2` to check the job status.

**Scope:** `files.content.write`

```swift
func copyBatchV2(
    entries: [Files.RelocationPath],
    autorename: Bool = false
) -> RpcRequest<Files.RelocationBatchV2LaunchSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.RelocationPath]` | List of entries to be copied. Each entry is RelocationPath. |
| `autorename` | `Bool` | If there's a conflict, autorename that file. Default `false`. |

### Returns

`Files.RelocationBatchV2Launch` on success, `Void` on failure.

---

## copyBatchCheck

> **Deprecated.** Use `copyBatchCheckV2` instead.

Returns the status of an asynchronous job for `copyBatch`.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "copyBatchCheck is deprecated. Use copyBatchCheckV2.")
func copyBatchCheck(asyncJobId: String)
    -> RpcRequest<Files.RelocationBatchJobStatusSerializer, Async.PollErrorSerializer>
```

### Returns

`Files.RelocationBatchJobStatus` on success, `Async.PollError` on failure.

---

## copyBatchCheckV2

Returns the status of an asynchronous job for `copyBatchV2`. It returns list of results for each entry.

**Scope:** `files.content.write`

```swift
func copyBatchCheckV2(asyncJobId: String)
    -> RpcRequest<Files.RelocationBatchV2JobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. This is the value of a response returned from the method that launched the job. |

### Returns

`Files.RelocationBatchV2JobStatus` on success, `Async.PollError` on failure.

---

## copyReferenceGet

Get a copy reference to a file or folder. This reference string can be used to save that file or folder to another user's Dropbox by passing it to `copyReferenceSave`.

**Scope:** `files.content.write`

```swift
func copyReferenceGet(path: String)
    -> RpcRequest<Files.GetCopyReferenceResultSerializer, Files.GetCopyReferenceErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path to the file or folder you want to get a copy reference to. |

### Returns

`Files.GetCopyReferenceResult` on success, `Files.GetCopyReferenceError` on failure.

---

## copyReferenceSave

Save a copy reference returned by `copyReferenceGet` to the user's Dropbox.

**Scope:** `files.content.write`

```swift
func copyReferenceSave(
    copyReference: String,
    path: String
) -> RpcRequest<Files.SaveCopyReferenceResultSerializer, Files.SaveCopyReferenceErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `copyReference` | `String` | A copy reference returned by `copyReferenceGet`. |
| `path` | `String` | Path in the user's Dropbox that is the destination. |

### Returns

`Files.SaveCopyReferenceResult` on success, `Files.SaveCopyReferenceError` on failure.

---

## createFolder

> **Deprecated.** Use `createFolderV2` instead.

Create a folder at a given path.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "createFolder is deprecated. Use createFolderV2.")
func createFolder(
    path: String,
    autorename: Bool = false
) -> RpcRequest<Files.FolderMetadataSerializer, Files.CreateFolderErrorSerializer>
```

### Returns

`Files.FolderMetadata` on success, `Files.CreateFolderError` on failure.

---

## createFolderV2

Create a folder at a given path.

**Scope:** `files.content.write`

```swift
func createFolderV2(
    path: String,
    autorename: Bool = false
) -> RpcRequest<Files.CreateFolderResultSerializer, Files.CreateFolderErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to create. |
| `autorename` | `Bool` | If there's a conflict, autorename the folder. Default `false`. |

### Returns

`Files.CreateFolderResult` on success, `Files.CreateFolderError` on failure.

---

## createFolderBatch

Create multiple folders at once. This route is asynchronous for large batches. Use `createFolderBatchCheck` to check the job status.

**Scope:** `files.content.write`

```swift
func createFolderBatch(
    paths: [String],
    autorename: Bool = false,
    forceAsync: Bool = false
) -> RpcRequest<Files.CreateFolderBatchLaunchSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `paths` | `[String]` | List of paths to be created in the user's Dropbox. Duplicate path arguments are considered only once. |
| `autorename` | `Bool` | If there's a conflict, autorename. Default `false`. |
| `forceAsync` | `Bool` | Whether to force the create to happen asynchronously. Default `false`. |

### Returns

`Files.CreateFolderBatchLaunch` on success, `Void` on failure.

---

## createFolderBatchCheck

Returns the status of an asynchronous job for `createFolderBatch`.

**Scope:** `files.content.write`

```swift
func createFolderBatchCheck(asyncJobId: String)
    -> RpcRequest<Files.CreateFolderBatchJobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. |

### Returns

`Files.CreateFolderBatchJobStatus` on success, `Async.PollError` on failure.

---

## delete

> **Deprecated.** Use `deleteV2` instead.

Delete the file or folder at a given path. If the path is a folder, all its contents will be deleted too.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "delete is deprecated. Use deleteV2.")
func delete(path: String, parentRev: String? = nil)
    -> RpcRequest<Files.MetadataSerializer, Files.DeleteErrorSerializer>
```

### Returns

`Files.Metadata` on success, `Files.DeleteError` on failure.

---

## deleteV2

Delete the file or folder at a given path. If the path is a folder, all its contents will be deleted too. The returned metadata will be the corresponding `FileMetadata` or `FolderMetadata` for the item at time of deletion.

**Scope:** `files.content.write`

```swift
func deleteV2(path: String, parentRev: String? = nil)
    -> RpcRequest<Files.DeleteResultSerializer, Files.DeleteErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to delete. |
| `parentRev` | `String?` | Perform delete if given "rev" matches the existing file's latest "rev". Does not support deleting a folder. Default `nil`. |

### Returns

`Files.DeleteResult` on success, `Files.DeleteError` on failure.

---

## deleteBatch

Delete multiple files/folders at once. This route is asynchronous. Use `deleteBatchCheck` to check the job status.

**Scope:** `files.content.write`

```swift
func deleteBatch(entries: [Files.DeleteArg])
    -> RpcRequest<Files.DeleteBatchLaunchSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.DeleteArg]` | List of entries to delete. |

### Returns

`Files.DeleteBatchLaunch` on success, `Void` on failure.

---

## deleteBatchCheck

Returns the status of an asynchronous job for `deleteBatch`.

**Scope:** `files.content.write`

```swift
func deleteBatchCheck(asyncJobId: String)
    -> RpcRequest<Files.DeleteBatchJobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. |

### Returns

`Files.DeleteBatchJobStatus` on success, `Async.PollError` on failure.

---

## download

Download a file from a user's Dropbox.

**Scope:** `files.content.read`

### Download to file

```swift
func download(
    path: String,
    rev: String? = nil,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.FileMetadataSerializer, Files.DownloadErrorSerializer>
```

### Download to memory

```swift
func download(
    path: String,
    rev: String? = nil
) -> DownloadRequestMemory<Files.FileMetadataSerializer, Files.DownloadErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of the file to download. |
| `rev` | `String?` | Please specify revision in path instead. Default `nil`. |
| `overwrite` | `Bool` | (File variant only) If `true`, overwrite conflicting file at destination. Default `false`. |
| `destination` | `URL` | (File variant only) The location to write the download to. |

### Returns

`Files.FileMetadata` on success, `Files.DownloadError` on failure.

---

## downloadZip

Download a folder from the user's Dropbox, as a zip file. The folder must be less than 20 GB in size and any single file within must be less than 4 GB in size. The resulting zip must have fewer than 10,000 total file and folder entries. Note: this endpoint does not support HTTP range requests.

**Scope:** `files.content.read`

### Download to file

```swift
func downloadZip(
    path: String,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.DownloadZipResultSerializer, Files.DownloadZipErrorSerializer>
```

### Download to memory

```swift
func downloadZip(path: String)
    -> DownloadRequestMemory<Files.DownloadZipResultSerializer, Files.DownloadZipErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of the folder to download. |
| `overwrite` | `Bool` | (File variant only) If `true`, overwrite conflicting file. Default `false`. |
| `destination` | `URL` | (File variant only) The location to write the download to. |

### Returns

`Files.DownloadZipResult` on success, `Files.DownloadZipError` on failure.

---

## export

Export a file from a user's Dropbox. This route only supports exporting files that cannot be downloaded directly and whose `fileMetadata` in `ExportResult` has `exportAs` in `ExportInfo` populated.

**Scope:** `files.content.read`

### Export to file

```swift
func export(
    path: String,
    exportFormat: String? = nil,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.ExportResultSerializer, Files.ExportErrorSerializer>
```

### Export to memory

```swift
func export(
    path: String,
    exportFormat: String? = nil
) -> DownloadRequestMemory<Files.ExportResultSerializer, Files.ExportErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of the file to be exported. |
| `exportFormat` | `String?` | The file format to export to. Must be one of the formats listed in the file's export_options. Default `nil`. |
| `overwrite` | `Bool` | (File variant only) If `true`, overwrite conflicting file. Default `false`. |
| `destination` | `URL` | (File variant only) The location to write the download to. |

### Returns

`Files.ExportResult` on success, `Files.ExportError` on failure.

---

## getFileLockBatch

Return the lock metadata for the given list of paths.

**Scope:** `files.content.read`

```swift
func getFileLockBatch(entries: [Files.LockFileArg])
    -> RpcRequest<Files.LockFileBatchResultSerializer, Files.LockFileErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.LockFileArg]` | List of entries. Each entry contains a path of the file to query. Duplicate path arguments are considered only once. |

### Returns

`Files.LockFileBatchResult` on success, `Files.LockFileError` on failure.

---

## getMetadata

Returns the metadata for a file or folder. Note: Metadata for the root folder is unsupported.

**Scope:** `files.metadata.read`

```swift
func getMetadata(
    path: String,
    includeMediaInfo: Bool = false,
    includeDeleted: Bool = false,
    includeHasExplicitSharedMembers: Bool = false,
    includePropertyGroups: FileProperties.TemplateFilterBase? = nil
) -> RpcRequest<Files.MetadataSerializer, Files.GetMetadataErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of a file or folder on Dropbox. |
| `includeMediaInfo` | `Bool` | If true, media info is set for photo and video. Default `false`. |
| `includeDeleted` | `Bool` | If true, `DeletedMetadata` will be returned for deleted items. Default `false`. |
| `includeHasExplicitSharedMembers` | `Bool` | If true, includes explicit shared members flag. Default `false`. |
| `includePropertyGroups` | `FileProperties.TemplateFilterBase?` | Filter for property groups. Default `nil`. |

### Returns

`Files.Metadata` on success, `Files.GetMetadataError` on failure.

---

## getPreview

Get a preview for a file. PDF previews are generated for: .ai, .doc, .docm, .docx, .eps, .gdoc, .gslides, .odp, .odt, .pps, .ppsm, .ppsx, .ppt, .pptm, .pptx, .rtf. HTML previews are generated for: .csv, .ods, .xls, .xlsm, .gsheet, .xlsx.

**Scope:** `files.content.read`

### Download to file

```swift
func getPreview(
    path: String,
    rev: String? = nil,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.FileMetadataSerializer, Files.PreviewErrorSerializer>
```

### Download to memory

```swift
func getPreview(
    path: String,
    rev: String? = nil
) -> DownloadRequestMemory<Files.FileMetadataSerializer, Files.PreviewErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path of the file to preview. |
| `rev` | `String?` | Please specify revision in path instead. Default `nil`. |

### Returns

`Files.FileMetadata` on success, `Files.PreviewError` on failure.

---

## getTemporaryLink

Get a temporary link to stream content of a file. This link will expire in four hours and afterwards you will get 410 Gone. This URL should not be used to display content directly in the browser.

**Scope:** `files.content.read`

```swift
func getTemporaryLink(path: String)
    -> RpcRequest<Files.GetTemporaryLinkResultSerializer, Files.GetTemporaryLinkErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path to the file you want a temporary link to. |

### Returns

`Files.GetTemporaryLinkResult` on success, `Files.GetTemporaryLinkError` on failure.

---

## getTemporaryUploadLink

Get a one-time use temporary upload link to upload a file to a Dropbox location. The returned temporary upload link may be used to make a POST request with the data to be uploaded. The maximum temporary upload link duration is 4 hours.

**Scope:** `files.content.write`

```swift
func getTemporaryUploadLink(
    commitInfo: Files.CommitInfo,
    duration: Double = 14_400.0
) -> RpcRequest<Files.GetTemporaryUploadLinkResultSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `commitInfo` | `Files.CommitInfo` | Contains the path and other optional modifiers for the future upload commit. Equivalent to the parameters provided to `upload`. |
| `duration` | `Double` | How long before this link expires, in seconds. Default `14400.0` (4 hours). |

### Returns

`Files.GetTemporaryUploadLinkResult` on success, `Void` on failure.

---

## getThumbnail

Get a thumbnail for an image. Supports: jpg, jpeg, png, tiff, tif, gif, webp, ppm and bmp. Photos larger than 20MB won't be converted.

**Scope:** `files.content.read`

### Download to file

```swift
func getThumbnail(
    path: String,
    format: Files.ThumbnailFormat = .jpeg,
    size: Files.ThumbnailSize = .w64h64,
    mode: Files.ThumbnailMode = .strict,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.FileMetadataSerializer, Files.ThumbnailErrorSerializer>
```

### Download to memory

```swift
func getThumbnail(
    path: String,
    format: Files.ThumbnailFormat = .jpeg,
    size: Files.ThumbnailSize = .w64h64,
    mode: Files.ThumbnailMode = .strict
) -> DownloadRequestMemory<Files.FileMetadataSerializer, Files.ThumbnailErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path to the image file you want to thumbnail. |
| `format` | `Files.ThumbnailFormat` | The format for the thumbnail image (jpeg or png). Default `.jpeg`. |
| `size` | `Files.ThumbnailSize` | The size for the thumbnail image. Default `.w64h64`. |
| `mode` | `Files.ThumbnailMode` | How to resize and crop the image. Default `.strict`. |

### Returns

`Files.FileMetadata` on success, `Files.ThumbnailError` on failure.

---

## getThumbnailV2

Get a thumbnail for an image. Supports: jpg, jpeg, png, tiff, tif, gif, webp, ppm and bmp. Photos larger than 20MB won't be converted.

**Scope:** `files.content.read`

### Download to file

```swift
func getThumbnailV2(
    resource: Files.PathOrLink,
    format: Files.ThumbnailFormat = .jpeg,
    size: Files.ThumbnailSize = .w64h64,
    mode: Files.ThumbnailMode = .strict,
    overwrite: Bool = false,
    destination: URL
) -> DownloadRequestFile<Files.PreviewResultSerializer, Files.ThumbnailV2ErrorSerializer>
```

### Download to memory

```swift
func getThumbnailV2(
    resource: Files.PathOrLink,
    format: Files.ThumbnailFormat = .jpeg,
    size: Files.ThumbnailSize = .w64h64,
    mode: Files.ThumbnailMode = .strict
) -> DownloadRequestMemory<Files.PreviewResultSerializer, Files.ThumbnailV2ErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `resource` | `Files.PathOrLink` | Information specifying which file to preview. This could be a path to a file, a shared link pointing to a file, or a shared link pointing to a folder with a relative path. |
| `format` | `Files.ThumbnailFormat` | The format for the thumbnail. Default `.jpeg`. |
| `size` | `Files.ThumbnailSize` | The size for the thumbnail. Default `.w64h64`. |
| `mode` | `Files.ThumbnailMode` | How to resize and crop. Default `.strict`. |

### Returns

`Files.PreviewResult` on success, `Files.ThumbnailV2Error` on failure.

---

## getThumbnailBatch

Get thumbnails for a list of images. Up to 25 thumbnails in a single batch. Supports: jpg, jpeg, png, tiff, tif, gif, webp, ppm and bmp.

**Scope:** `files.content.read`

```swift
func getThumbnailBatch(entries: [Files.ThumbnailArg])
    -> RpcRequest<Files.GetThumbnailBatchResultSerializer, Files.GetThumbnailBatchErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.ThumbnailArg]` | List of files to get thumbnails. |

### Returns

`Files.GetThumbnailBatchResult` on success, `Files.GetThumbnailBatchError` on failure.

---

## listFolder

Starts returning the contents of a folder. If the result's `hasMore` field is true, call `listFolderContinue` with the returned cursor to retrieve more entries.

**Scope:** `files.metadata.read`

```swift
func listFolder(
    path: String,
    recursive: Bool = false,
    includeMediaInfo: Bool = false,
    includeDeleted: Bool = false,
    includeHasExplicitSharedMembers: Bool = false,
    includeMountedFolders: Bool = true,
    limit: UInt32? = nil,
    sharedLink: Files.SharedLink? = nil,
    includePropertyGroups: FileProperties.TemplateFilterBase? = nil,
    includeNonDownloadableFiles: Bool = true
) -> RpcRequest<Files.ListFolderResultSerializer, Files.ListFolderErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | A unique identifier for the file. |
| `recursive` | `Bool` | If true, the list folder operation will be applied recursively to all subfolders. Default `false`. |
| `includeMediaInfo` | `Bool` | If true, media info is set for photo and video. Default `false`. |
| `includeDeleted` | `Bool` | If true, includes entries for files and folders that used to exist but were deleted. Default `false`. |
| `includeHasExplicitSharedMembers` | `Bool` | If true, includes explicit shared members flag. Default `false`. |
| `includeMountedFolders` | `Bool` | If true, includes entries under mounted folders. Default `true`. |
| `limit` | `UInt32?` | The maximum number of results to return per request (approximate). Default `nil`. |
| `sharedLink` | `Files.SharedLink?` | A shared link to list the contents of. Default `nil`. |
| `includePropertyGroups` | `FileProperties.TemplateFilterBase?` | Filter for property groups. Default `nil`. |
| `includeNonDownloadableFiles` | `Bool` | If true, include non-downloadable files (e.g. Google Docs). Default `true`. |

### Returns

`Files.ListFolderResult` on success, `Files.ListFolderError` on failure.

---

## listFolderContinue

Once a cursor has been retrieved from `listFolder`, use this to paginate through all files and retrieve updates to the folder.

**Scope:** `files.metadata.read`

```swift
func listFolderContinue(cursor: String)
    -> RpcRequest<Files.ListFolderResultSerializer, Files.ListFolderContinueErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `cursor` | `String` | The cursor returned by your last call to `listFolder` or `listFolderContinue`. |

### Returns

`Files.ListFolderResult` on success, `Files.ListFolderContinueError` on failure.

---

## listFolderGetLatestCursor

A way to quickly get a cursor for the folder's state. Unlike `listFolder`, this doesn't return any entries. This endpoint is for apps which only need to know about new files and modifications.

**Scope:** `files.metadata.read`

```swift
func listFolderGetLatestCursor(
    path: String,
    recursive: Bool = false,
    includeMediaInfo: Bool = false,
    includeDeleted: Bool = false,
    includeHasExplicitSharedMembers: Bool = false,
    includeMountedFolders: Bool = true,
    limit: UInt32? = nil,
    sharedLink: Files.SharedLink? = nil,
    includePropertyGroups: FileProperties.TemplateFilterBase? = nil,
    includeNonDownloadableFiles: Bool = true
) -> RpcRequest<Files.ListFolderGetLatestCursorResultSerializer, Files.ListFolderErrorSerializer>
```

### Parameters

Same parameters as `listFolder`.

### Returns

`Files.ListFolderGetLatestCursorResult` on success, `Files.ListFolderError` on failure.

---

## listFolderLongpoll

A longpoll endpoint to wait for changes on an account. In conjunction with `listFolderContinue`, this call gives you a low-latency way to monitor an account for file changes.

**Scope:** `files.metadata.read`

```swift
func listFolderLongpoll(
    cursor: String,
    timeout: UInt64 = 30
) -> RpcRequest<Files.ListFolderLongpollResultSerializer, Files.ListFolderLongpollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `cursor` | `String` | A cursor as returned by `listFolder` or `listFolderContinue`. |
| `timeout` | `UInt64` | A timeout in seconds. The request will block for at most this length of time, plus up to 90 seconds of random jitter. Default `30`. |

### Returns

`Files.ListFolderLongpollResult` on success, `Files.ListFolderLongpollError` on failure.

---

## listRevisions

Returns revisions for files based on a file path or a file id. The file path or file id is identified from the latest file entry at the given file path or id.

**Scope:** `files.metadata.read`

```swift
func listRevisions(
    path: String,
    mode: Files.ListRevisionsMode = .path,
    limit: UInt64 = 10
) -> RpcRequest<Files.ListRevisionsResultSerializer, Files.ListRevisionsErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path to the file you want to see the revisions of. |
| `mode` | `Files.ListRevisionsMode` | Determines the behavior of the API in listing revisions. Default `.path`. |
| `limit` | `UInt64` | The maximum number of revision entries returned. Default `10`. |

### Returns

`Files.ListRevisionsResult` on success, `Files.ListRevisionsError` on failure.

---

## lockFileBatch

Lock the files at the given paths. A locked file will be writable only by the lock holder.

**Scope:** `files.content.write`

```swift
func lockFileBatch(entries: [Files.LockFileArg])
    -> RpcRequest<Files.LockFileBatchResultSerializer, Files.LockFileErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.LockFileArg]` | List of entries. Each entry contains a path of the file to lock. Duplicate paths are considered only once. |

### Returns

`Files.LockFileBatchResult` on success, `Files.LockFileError` on failure.

---

## move

> **Deprecated.** Use `moveV2` instead.

Move a file or folder to a different location in the user's Dropbox.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "move is deprecated. Use moveV2.")
func move(
    fromPath: String,
    toPath: String,
    allowSharedFolder: Bool = false,
    autorename: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.MetadataSerializer, Files.RelocationErrorSerializer>
```

### Returns

`Files.Metadata` on success, `Files.RelocationError` on failure.

---

## moveV2

Move a file or folder to a different location in the user's Dropbox. If the source path is a folder all its contents will be moved. Note that case-only renaming is not currently supported.

**Scope:** `files.content.write`

```swift
func moveV2(
    fromPath: String,
    toPath: String,
    allowSharedFolder: Bool = false,
    autorename: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.RelocationResultSerializer, Files.RelocationErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `fromPath` | `String` | Path of the file or folder to move. |
| `toPath` | `String` | Destination path. |
| `allowSharedFolder` | `Bool` | This flag has no effect. Default `false`. |
| `autorename` | `Bool` | If there's a conflict, autorename. Default `false`. |
| `allowOwnershipTransfer` | `Bool` | Allow moves by owner even if it would result in an ownership transfer. Default `false`. |

### Returns

`Files.RelocationResult` on success, `Files.RelocationError` on failure.

---

## moveBatch

> **Deprecated.** Use `moveBatchV2` instead.

Move multiple files or folders to different locations at once. Returns a job ID immediately. Use `moveBatchCheck` to check the job status.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "moveBatch is deprecated. Use moveBatchV2.")
func moveBatch(
    entries: [Files.RelocationPath],
    autorename: Bool = false,
    allowSharedFolder: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.RelocationBatchLaunchSerializer, VoidSerializer>
```

### Returns

`Files.RelocationBatchLaunch` on success, `Void` on failure.

---

## moveBatchV2

Move multiple files or folders to different locations at once. Returns status for each entry. Use `moveBatchCheckV2` to check the job status.

**Scope:** `files.content.write`

```swift
func moveBatchV2(
    entries: [Files.RelocationPath],
    autorename: Bool = false,
    allowOwnershipTransfer: Bool = false
) -> RpcRequest<Files.RelocationBatchV2LaunchSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.RelocationPath]` | List of entries to be moved. |
| `autorename` | `Bool` | Autorename on conflict. Default `false`. |
| `allowOwnershipTransfer` | `Bool` | Allow moves by owner even if it would result in an ownership transfer. Default `false`. |

### Returns

`Files.RelocationBatchV2Launch` on success, `Void` on failure.

---

## moveBatchCheck

> **Deprecated.** Use `moveBatchCheckV2` instead.

Returns the status of an asynchronous job for `moveBatch`.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "moveBatchCheck is deprecated. Use moveBatchCheckV2.")
func moveBatchCheck(asyncJobId: String)
    -> RpcRequest<Files.RelocationBatchJobStatusSerializer, Async.PollErrorSerializer>
```

### Returns

`Files.RelocationBatchJobStatus` on success, `Async.PollError` on failure.

---

## moveBatchCheckV2

Returns the status of an asynchronous job for `moveBatchV2`. It returns list of results for each entry.

**Scope:** `files.content.write`

```swift
func moveBatchCheckV2(asyncJobId: String)
    -> RpcRequest<Files.RelocationBatchV2JobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. |

### Returns

`Files.RelocationBatchV2JobStatus` on success, `Async.PollError` on failure.

---

## paperCreate

Creates a new Paper doc with the provided content.

**Scope:** `files.content.write`

```swift
func paperCreate(
    path: String,
    importFormat: Files.ImportFormat,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.PaperCreateResultSerializer, Files.PaperCreateErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The fully qualified path to the location where the Paper Doc should be created. Should end with `.paper`. |
| `importFormat` | `Files.ImportFormat` | The format of the provided data. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.PaperCreateResult` on success, `Files.PaperCreateError` on failure.

---

## paperUpdate

Updates an existing Paper doc with the provided content.

**Scope:** `files.content.write`

```swift
func paperUpdate(
    path: String,
    importFormat: Files.ImportFormat,
    docUpdatePolicy: Files.PaperDocUpdatePolicy,
    paperRevision: Int64? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.PaperUpdateResultSerializer, Files.PaperUpdateErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to update. Must correspond to a Paper doc. |
| `importFormat` | `Files.ImportFormat` | The format of the provided data. |
| `docUpdatePolicy` | `Files.PaperDocUpdatePolicy` | How the provided content should be applied to the doc. |
| `paperRevision` | `Int64?` | The latest doc revision. Required when doc_update_policy is update. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.PaperUpdateResult` on success, `Files.PaperUpdateError` on failure.

---

## permanentlyDelete

Permanently delete the file or folder at a given path. If the given file or folder is not yet deleted, this route will first delete it. Note: This endpoint is only available for Dropbox Business apps.

**Scope:** `files.permanent_delete`

```swift
func permanentlyDelete(path: String, parentRev: String? = nil)
    -> RpcRequest<VoidSerializer, Files.DeleteErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to delete. |
| `parentRev` | `String?` | Perform delete if given "rev" matches the existing file's latest "rev". Default `nil`. |

### Returns

`Void` on success, `Files.DeleteError` on failure.

---

## propertiesAdd

> **Deprecated.**

Add custom properties to a file.

**Scope:** `files.metadata.write`

```swift
@available(*, unavailable, message: "propertiesAdd is deprecated.")
func propertiesAdd(
    path: String,
    propertyGroups: [FileProperties.PropertyGroup]
) -> RpcRequest<VoidSerializer, FileProperties.AddPropertiesErrorSerializer>
```

### Returns

`Void` on success, `FileProperties.AddPropertiesError` on failure.

---

## propertiesOverwrite

> **Deprecated.**

Overwrite custom properties of a file.

**Scope:** `files.metadata.write`

```swift
@available(*, unavailable, message: "propertiesOverwrite is deprecated.")
func propertiesOverwrite(
    path: String,
    propertyGroups: [FileProperties.PropertyGroup]
) -> RpcRequest<VoidSerializer, FileProperties.InvalidPropertyGroupErrorSerializer>
```

### Returns

`Void` on success, `FileProperties.InvalidPropertyGroupError` on failure.

---

## propertiesRemove

> **Deprecated.**

Remove custom properties from a file.

**Scope:** `files.metadata.write`

```swift
@available(*, unavailable, message: "propertiesRemove is deprecated.")
func propertiesRemove(
    path: String,
    propertyTemplateIds: [String]
) -> RpcRequest<VoidSerializer, FileProperties.RemovePropertiesErrorSerializer>
```

### Returns

`Void` on success, `FileProperties.RemovePropertiesError` on failure.

---

## propertiesTemplateGet

> **Deprecated.**

Get a template for custom properties.

**Scope:** `files.metadata.read`

```swift
@available(*, unavailable, message: "propertiesTemplateGet is deprecated.")
func propertiesTemplateGet(templateId: String)
    -> RpcRequest<FileProperties.GetTemplateResultSerializer, FileProperties.TemplateErrorSerializer>
```

### Returns

`FileProperties.GetTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## propertiesTemplateList

> **Deprecated.**

List all templates for custom properties.

**Scope:** `files.metadata.read`

```swift
@available(*, unavailable, message: "propertiesTemplateList is deprecated.")
func propertiesTemplateList()
    -> RpcRequest<FileProperties.ListTemplateResultSerializer, FileProperties.TemplateErrorSerializer>
```

### Returns

`FileProperties.ListTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## propertiesUpdate

> **Deprecated.**

Update custom properties of a file.

**Scope:** `files.metadata.write`

```swift
@available(*, unavailable, message: "propertiesUpdate is deprecated.")
func propertiesUpdate(
    path: String,
    updatePropertyGroups: [FileProperties.PropertyGroupUpdate]
) -> RpcRequest<VoidSerializer, FileProperties.UpdatePropertiesErrorSerializer>
```

### Returns

`Void` on success, `FileProperties.UpdatePropertiesError` on failure.

---

## restore

Restore a specific revision of a file to the given path.

**Scope:** `files.content.write`

```swift
func restore(path: String, rev: String)
    -> RpcRequest<Files.FileMetadataSerializer, Files.RestoreErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path to save the restored file. |
| `rev` | `String` | The revision to restore. |

### Returns

`Files.FileMetadata` on success, `Files.RestoreError` on failure.

---

## saveUrl

Save the data from a specified URL into a file in user's Dropbox. Note that the transfer from the URL must complete within 15 minutes.

**Scope:** `files.content.write`

```swift
func saveUrl(path: String, url: String)
    -> RpcRequest<Files.SaveUrlResultSerializer, Files.SaveUrlErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | The path in Dropbox where the URL will be saved to. |
| `url` | `String` | The URL to be saved. |

### Returns

`Files.SaveUrlResult` on success, `Files.SaveUrlError` on failure.

---

## saveUrlCheckJobStatus

Check the status of a `saveUrl` job.

**Scope:** `files.content.write`

```swift
func saveUrlCheckJobStatus(asyncJobId: String)
    -> RpcRequest<Files.SaveUrlJobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. |

### Returns

`Files.SaveUrlJobStatus` on success, `Async.PollError` on failure.

---

## search

> **Deprecated.** Use `searchV2` instead.

Searches for files and folders.

**Scope:** `files.metadata.read`

```swift
@available(*, unavailable, message: "search is deprecated. Use searchV2.")
func search(
    path: String,
    query: String,
    start: UInt64 = 0,
    maxResults: UInt64 = 100,
    mode: Files.SearchMode = .filename
) -> RpcRequest<Files.SearchResultSerializer, Files.SearchErrorSerializer>
```

### Returns

`Files.SearchResult` on success, `Files.SearchError` on failure.

---

## searchV2

Searches for files and folders. Note: `searchV2` along with `searchContinueV2` can only retrieve a maximum of 10,000 matches.

**Scope:** `files.metadata.read`

```swift
func searchV2(
    query: String,
    options: Files.SearchOptions? = nil,
    matchFieldOptions: Files.SearchMatchFieldOptions? = nil,
    includeHighlights: Bool? = nil
) -> RpcRequest<Files.SearchV2ResultSerializer, Files.SearchErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `query` | `String` | The string to search for. May match across multiple fields. |
| `options` | `Files.SearchOptions?` | Options for more targeted search results. Default `nil`. |
| `matchFieldOptions` | `Files.SearchMatchFieldOptions?` | Options for search results match fields. Default `nil`. |
| `includeHighlights` | `Bool?` | Deprecated. Moved to `SearchMatchFieldOptions`. Default `nil`. |

### Returns

`Files.SearchV2Result` on success, `Files.SearchError` on failure.

---

## searchContinueV2

Fetches the next page of search results returned from `searchV2`.

**Scope:** `files.metadata.read`

```swift
func searchContinueV2(cursor: String)
    -> RpcRequest<Files.SearchV2ResultSerializer, Files.SearchErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `cursor` | `String` | The cursor returned by your last call to `searchV2`. Used to fetch the next page of results. |

### Returns

`Files.SearchV2Result` on success, `Files.SearchError` on failure.

---

## tagsAdd

Add a tag to an item. A tag is a string. The strings are automatically converted to lowercase letters. No more than 20 tags can be added to a given item.

**Scope:** `files.metadata.write`

```swift
func tagsAdd(path: String, tagText: String)
    -> RpcRequest<VoidSerializer, Files.AddTagErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path to the item to be tagged. |
| `tagText` | `String` | The value of the tag to add. Will be automatically converted to lowercase. |

### Returns

`Void` on success, `Files.AddTagError` on failure.

---

## tagsGet

Get list of tags assigned to items.

**Scope:** `files.metadata.read`

```swift
func tagsGet(paths: [String])
    -> RpcRequest<Files.GetTagsResultSerializer, Files.BaseTagErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `paths` | `[String]` | Path to the items. |

### Returns

`Files.GetTagsResult` on success, `Files.BaseTagError` on failure.

---

## tagsRemove

Remove a tag from an item.

**Scope:** `files.metadata.write`

```swift
func tagsRemove(path: String, tagText: String)
    -> RpcRequest<VoidSerializer, Files.RemoveTagErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path to the item to untag. |
| `tagText` | `String` | The tag to remove. Will be automatically converted to lowercase. |

### Returns

`Void` on success, `Files.RemoveTagError` on failure.

---

## unlockFileBatch

Unlock the files at the given paths. A locked file can only be unlocked by the lock holder or, if a business account, a team admin.

**Scope:** `files.content.write`

```swift
func unlockFileBatch(entries: [Files.UnlockFileArg])
    -> RpcRequest<Files.LockFileBatchResultSerializer, Files.LockFileErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.UnlockFileArg]` | List of entries. Each entry contains a path of the file to unlock. Duplicate paths are considered only once. |

### Returns

`Files.LockFileBatchResult` on success, `Files.LockFileError` on failure.

---

## upload

Create a new file with the contents provided in the request. Do not use this to upload a file larger than 150 MB. Instead, create an upload session with `uploadSessionStart`.

**Scope:** `files.content.write`

```swift
func upload(
    path: String,
    mode: Files.WriteMode = .add,
    autorename: Bool = false,
    clientModified: Date? = nil,
    mute: Bool = false,
    propertyGroups: [FileProperties.PropertyGroup]? = nil,
    strictConflict: Bool = false,
    contentHash: String? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.FileMetadataSerializer, Files.UploadErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `path` | `String` | Path in the user's Dropbox to save the file. |
| `mode` | `Files.WriteMode` | Selects what to do if the file already exists. Default `.add`. |
| `autorename` | `Bool` | If there's a conflict, autorename the file. Default `false`. |
| `clientModified` | `Date?` | The value to store as the client modified timestamp. Default `nil`. |
| `mute` | `Bool` | If true, this file will not generate notifications. Default `false`. |
| `propertyGroups` | `[FileProperties.PropertyGroup]?` | Property groups to associate with the file. Default `nil`. |
| `strictConflict` | `Bool` | Be more strict about how each WriteMode detects conflict. Default `false`. |
| `contentHash` | `String?` | A hash of the file content. If provided and mismatched, an error is returned. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.FileMetadata` on success, `Files.UploadError` on failure.

---

## uploadSessionAppend

> **Deprecated.** Use `uploadSessionAppendV2` instead.

Append more data to an upload session. A single request should not upload more than 150 MB. The maximum size of a file one can upload to an upload session is 350 GB.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "uploadSessionAppend is deprecated. Use uploadSessionAppendV2.")
func uploadSessionAppend(
    sessionId: String,
    offset: UInt64,
    input: Data  // or URL or InputStream
) -> UploadRequest<VoidSerializer, Files.UploadSessionAppendErrorSerializer>
```

### Returns

`Void` on success, `Files.UploadSessionAppendError` on failure.

---

## uploadSessionAppendV2

Append more data to an upload session. When the parameter `close` is set, this call will close the session. A single request should not upload more than 150 MB. The maximum size of a file one can upload to an upload session is 350 GB.

**Scope:** `files.content.write`

```swift
func uploadSessionAppendV2(
    cursor: Files.UploadSessionCursor,
    close: Bool = false,
    contentHash: String? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<VoidSerializer, Files.UploadSessionAppendErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `cursor` | `Files.UploadSessionCursor` | Contains the upload session ID and the offset. |
| `close` | `Bool` | If true, the current session will be closed. Default `false`. |
| `contentHash` | `String?` | A hash of the file content. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Void` on success, `Files.UploadSessionAppendError` on failure.

---

## uploadSessionFinish

Finish an upload session and save the uploaded data to the given file path. A single request should not upload more than 150 MB. The maximum size of a file one can upload to an upload session is 350 GB.

**Scope:** `files.content.write`

```swift
func uploadSessionFinish(
    cursor: Files.UploadSessionCursor,
    commit: Files.CommitInfo,
    contentHash: String? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.FileMetadataSerializer, Files.UploadSessionFinishErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `cursor` | `Files.UploadSessionCursor` | Contains the upload session ID and the offset. |
| `commit` | `Files.CommitInfo` | Contains the path and other optional modifiers for the commit. |
| `contentHash` | `String?` | A hash of the file content. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.FileMetadata` on success, `Files.UploadSessionFinishError` on failure.

---

## uploadSessionFinishBatch

> **Deprecated.** Use `uploadSessionFinishBatchV2` instead.

Commit many files at once into a user's Dropbox. Use `uploadSessionStart` and `uploadSessionAppendV2` to upload file contents first. Up to 1000 entries in a single request.

**Scope:** `files.content.write`

```swift
@available(*, unavailable, message: "uploadSessionFinishBatch is deprecated. Use uploadSessionFinishBatchV2.")
func uploadSessionFinishBatch(entries: [Files.UploadSessionFinishArg])
    -> RpcRequest<Files.UploadSessionFinishBatchLaunchSerializer, VoidSerializer>
```

### Returns

`Files.UploadSessionFinishBatchLaunch` on success, `Void` on failure.

---

## uploadSessionFinishBatchV2

Commit many files at once into a user's Dropbox. Use `uploadSessionStart` and `uploadSessionAppendV2` to upload file contents first. Up to 1000 entries in a single request.

**Scope:** `files.content.write`

```swift
func uploadSessionFinishBatchV2(entries: [Files.UploadSessionFinishArg])
    -> RpcRequest<Files.UploadSessionFinishBatchResultSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `entries` | `[Files.UploadSessionFinishArg]` | Commit information for each file in the batch. |

### Returns

`Files.UploadSessionFinishBatchResult` on success, `Void` on failure.

---

## uploadSessionFinishBatchCheck

Returns the status of an asynchronous job for `uploadSessionFinishBatch`.

**Scope:** `files.content.write`

```swift
func uploadSessionFinishBatchCheck(asyncJobId: String)
    -> RpcRequest<Files.UploadSessionFinishBatchJobStatusSerializer, Async.PollErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `asyncJobId` | `String` | Id of the asynchronous job. |

### Returns

`Files.UploadSessionFinishBatchJobStatus` on success, `Async.PollError` on failure.

---

## uploadSessionStart

Upload sessions allow you to upload a single file in one or more requests, for example where the size of the file is greater than 150 MB. This call starts a new upload session with the given data. You can then use `uploadSessionAppendV2` to add more data and `uploadSessionFinish` to save all the data to a file in Dropbox.

A single request should not upload more than 150 MB. The maximum size of a file one can upload to an upload session is 350 GB. An upload session can be used for a maximum of 7 days.

For better performance, you can optionally use a concurrent upload session by setting `sessionType` to `.concurrent`.

**Scope:** `files.content.write`

```swift
func uploadSessionStart(
    close: Bool = false,
    sessionType: Files.UploadSessionType? = nil,
    contentHash: String? = nil,
    input: Data  // or URL or InputStream
) -> UploadRequest<Files.UploadSessionStartResultSerializer, Files.UploadSessionStartErrorSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `close` | `Bool` | If true, the current session will be closed. Default `false`. |
| `sessionType` | `Files.UploadSessionType?` | Type of upload session you want to start. Default is sequential. Default `nil`. |
| `contentHash` | `String?` | A hash of the file content. Default `nil`. |
| `input` | `Data`, `URL`, or `InputStream` | The file content to upload. |

### Returns

`Files.UploadSessionStartResult` on success, `Files.UploadSessionStartError` on failure.

---

## uploadSessionStartBatch

This route starts batch of upload sessions. Refer to `uploadSessionStart` usage.

**Scope:** `files.content.write`

```swift
func uploadSessionStartBatch(
    numSessions: UInt64,
    sessionType: Files.UploadSessionType? = nil
) -> RpcRequest<Files.UploadSessionStartBatchResultSerializer, VoidSerializer>
```

### Parameters

| Name | Type | Description |
|------|------|-------------|
| `numSessions` | `UInt64` | The number of upload sessions to start. |
| `sessionType` | `Files.UploadSessionType?` | Type of upload session. Default is sequential. Default `nil`. |

### Returns

`Files.UploadSessionStartBatchResult` on success, `Void` on failure.
