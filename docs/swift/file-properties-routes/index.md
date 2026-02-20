# FilePropertiesRoutes

Routes for the file_properties namespace. For Objective-C compatible routes see `DBFilePropertiesRoutes`.

---

## propertiesAdd

Add property groups to a Dropbox file. See `templatesAddForUser` or `templatesAddForTeam` to create new templates.

**Scope:** `files.metadata.write`

```swift
func propertiesAdd(path: String, propertyGroups: [FileProperties.PropertyGroup]) -> RpcRequest<Void, FileProperties.AddPropertiesError>
```

**Parameters:**
- `path` - A unique identifier for the file or folder.
- `propertyGroups` - The property groups which are to be added to a Dropbox file. No two groups in the input should refer to the same template.

**Returns:** `Void` on success, `FileProperties.AddPropertiesError` on failure.

---

## propertiesOverwrite

Overwrite property groups associated with a file. This endpoint should be used instead of `propertiesUpdate` when property groups are being updated via a "snapshot" instead of via a "delta". In other words, this endpoint will delete all omitted fields from a property group, whereas `propertiesUpdate` will only delete fields that are explicitly marked for deletion.

**Scope:** `files.metadata.write`

```swift
func propertiesOverwrite(path: String, propertyGroups: [FileProperties.PropertyGroup]) -> RpcRequest<Void, FileProperties.InvalidPropertyGroupError>
```

**Parameters:**
- `path` - A unique identifier for the file or folder.
- `propertyGroups` - The property groups "snapshot" updates to force apply. No two groups in the input should refer to the same template.

**Returns:** `Void` on success, `FileProperties.InvalidPropertyGroupError` on failure.

---

## propertiesRemove

Permanently removes the specified property group from the file. To remove specific property field key value pairs, see `propertiesUpdate`. To update a template, see `templatesUpdateForUser` or `templatesUpdateForTeam`. To remove a template, see `templatesRemoveForUser` or `templatesRemoveForTeam`.

**Scope:** `files.metadata.write`

```swift
func propertiesRemove(path: String, propertyTemplateIds: [String]) -> RpcRequest<Void, FileProperties.RemovePropertiesError>
```

**Parameters:**
- `path` - A unique identifier for the file or folder.
- `propertyTemplateIds` - A list of identifiers for a template created by `templatesAddForUser` or `templatesAddForTeam`.

**Returns:** `Void` on success, `FileProperties.RemovePropertiesError` on failure.

---

## propertiesSearch

Search across property templates for particular property field values.

**Scope:** `files.metadata.read`

```swift
func propertiesSearch(queries: [FileProperties.PropertiesSearchQuery], templateFilter: FileProperties.TemplateFilter = .filterNone) -> RpcRequest<FileProperties.PropertiesSearchResult, FileProperties.PropertiesSearchError>
```

**Parameters:**
- `queries` - Queries to search.
- `templateFilter` - Filter results to contain only properties associated with these template IDs.

**Returns:** `FileProperties.PropertiesSearchResult` on success, `FileProperties.PropertiesSearchError` on failure.

---

## propertiesSearchContinue

Once a cursor has been retrieved from `propertiesSearch`, use this to paginate through all search results.

**Scope:** `files.metadata.read`

```swift
func propertiesSearchContinue(cursor: String) -> RpcRequest<FileProperties.PropertiesSearchResult, FileProperties.PropertiesSearchContinueError>
```

**Parameters:**
- `cursor` - The cursor returned by your last call to `propertiesSearch` or `propertiesSearchContinue`.

**Returns:** `FileProperties.PropertiesSearchResult` on success, `FileProperties.PropertiesSearchContinueError` on failure.

---

## propertiesUpdate

Add, update or remove properties associated with the supplied file and templates. This endpoint should be used instead of `propertiesOverwrite` when property groups are being updated via a "delta" instead of via a "snapshot". In other words, this endpoint will not delete any omitted fields from a property group, whereas `propertiesOverwrite` will delete any fields that are omitted from a property group.

**Scope:** `files.metadata.write`

```swift
func propertiesUpdate(path: String, updatePropertyGroups: [FileProperties.PropertyGroupUpdate]) -> RpcRequest<Void, FileProperties.UpdatePropertiesError>
```

**Parameters:**
- `path` - A unique identifier for the file or folder.
- `updatePropertyGroups` - The property groups "delta" updates to apply.

**Returns:** `Void` on success, `FileProperties.UpdatePropertiesError` on failure.

---

## templatesAddForTeam

Add a template associated with a team. See `propertiesAdd` to add properties to a file or folder. Note: this endpoint will create team-owned templates.

**Scope:** `files.team_metadata.write`

```swift
func templatesAddForTeam(name: String, description_: String, fields: [FileProperties.PropertyFieldTemplate]) -> RpcRequest<FileProperties.AddTemplateResult, FileProperties.ModifyTemplateError>
```

**Parameters:**
- `name` - A display name for the template.
- `description_` - Description for the new template.
- `fields` - Property field templates to be added to the group template.

**Returns:** `FileProperties.AddTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.

---

## templatesAddForUser

Add a template associated with a user. See `propertiesAdd` to add properties to a file. This endpoint can't be called on a team member or admin's behalf.

**Scope:** `files.metadata.write`

```swift
func templatesAddForUser(name: String, description_: String, fields: [FileProperties.PropertyFieldTemplate]) -> RpcRequest<FileProperties.AddTemplateResult, FileProperties.ModifyTemplateError>
```

**Parameters:**
- `name` - A display name for the template.
- `description_` - Description for the new template.
- `fields` - Property field templates to be added to the group template.

**Returns:** `FileProperties.AddTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.

---

## templatesGetForTeam

Get the schema for a specified template.

**Scope:** `files.team_metadata.write`

```swift
func templatesGetForTeam(templateId: String) -> RpcRequest<FileProperties.GetTemplateResult, FileProperties.TemplateError>
```

**Parameters:**
- `templateId` - An identifier for template added by route. See `templatesAddForUser` or `templatesAddForTeam`.

**Returns:** `FileProperties.GetTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## templatesGetForUser

Get the schema for a specified template. This endpoint can't be called on a team member or admin's behalf.

**Scope:** `files.metadata.read`

```swift
func templatesGetForUser(templateId: String) -> RpcRequest<FileProperties.GetTemplateResult, FileProperties.TemplateError>
```

**Parameters:**
- `templateId` - An identifier for template added by route. See `templatesAddForUser` or `templatesAddForTeam`.

**Returns:** `FileProperties.GetTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## templatesListForTeam

Get the template identifiers for a team. To get the schema of each template use `templatesGetForTeam`.

**Scope:** `files.team_metadata.write`

```swift
func templatesListForTeam() -> RpcRequest<FileProperties.ListTemplateResult, FileProperties.TemplateError>
```

**Returns:** `FileProperties.ListTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## templatesListForUser

Get the template identifiers for a team. To get the schema of each template use `templatesGetForUser`. This endpoint can't be called on a team member or admin's behalf.

**Scope:** `files.metadata.read`

```swift
func templatesListForUser() -> RpcRequest<FileProperties.ListTemplateResult, FileProperties.TemplateError>
```

**Returns:** `FileProperties.ListTemplateResult` on success, `FileProperties.TemplateError` on failure.

---

## templatesRemoveForTeam

Permanently removes the specified template created from `templatesAddForUser`. All properties associated with the template will also be removed. This action cannot be undone.

**Scope:** `files.team_metadata.write`

```swift
func templatesRemoveForTeam(templateId: String) -> RpcRequest<Void, FileProperties.TemplateError>
```

**Parameters:**
- `templateId` - An identifier for a template created by `templatesAddForUser` or `templatesAddForTeam`.

**Returns:** `Void` on success, `FileProperties.TemplateError` on failure.

---

## templatesRemoveForUser

Permanently removes the specified template created from `templatesAddForUser`. All properties associated with the template will also be removed. This action cannot be undone.

**Scope:** `files.metadata.write`

```swift
func templatesRemoveForUser(templateId: String) -> RpcRequest<Void, FileProperties.TemplateError>
```

**Parameters:**
- `templateId` - An identifier for a template created by `templatesAddForUser` or `templatesAddForTeam`.

**Returns:** `Void` on success, `FileProperties.TemplateError` on failure.

---

## templatesUpdateForTeam

Update a template associated with a team. This route can update the template name, the template description and add optional properties to templates.

**Scope:** `files.team_metadata.write`

```swift
func templatesUpdateForTeam(templateId: String, name: String? = nil, description_: String? = nil, addFields: [FileProperties.PropertyFieldTemplate]? = nil) -> RpcRequest<FileProperties.UpdateTemplateResult, FileProperties.ModifyTemplateError>
```

**Parameters:**
- `templateId` - An identifier for template added by `templatesAddForUser` or `templatesAddForTeam`.
- `name` - A display name for the template. Template names can be up to 256 bytes.
- `description_` - Description for the new template. Template descriptions can be up to 1024 bytes.
- `addFields` - Property field templates to be added to the group template. There can be up to 32 properties in a single template.

**Returns:** `FileProperties.UpdateTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.

---

## templatesUpdateForUser

Update a template associated with a user. This route can update the template name, the template description and add optional properties to templates. This endpoint can't be called on a team member or admin's behalf.

**Scope:** `files.metadata.write`

```swift
func templatesUpdateForUser(templateId: String, name: String? = nil, description_: String? = nil, addFields: [FileProperties.PropertyFieldTemplate]? = nil) -> RpcRequest<FileProperties.UpdateTemplateResult, FileProperties.ModifyTemplateError>
```

**Parameters:**
- `templateId` - An identifier for template added by `templatesAddForUser` or `templatesAddForTeam`.
- `name` - A display name for the template. Template names can be up to 256 bytes.
- `description_` - Description for the new template. Template descriptions can be up to 1024 bytes.
- `addFields` - Property field templates to be added to the group template. There can be up to 32 properties in a single template.

**Returns:** `FileProperties.UpdateTemplateResult` on success, `FileProperties.ModifyTemplateError` on failure.
