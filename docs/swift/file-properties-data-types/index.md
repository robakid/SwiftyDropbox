# FileProperties Data Types

Data types for the file_properties namespace.

## AddPropertiesArg

The AddPropertiesArg struct.

**Properties:**
- `path: String` - A unique identifier for the file or folder.
- `propertyGroups: [FileProperties.PropertyGroup]` - The property groups which are to be added to a Dropbox file. No two groups in the input should refer to the same template.

---

## TemplateError

The TemplateError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.

---

## PropertiesError

The PropertiesError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `path` - FileProperties.LookupError
- `unsupportedFolder` - This folder cannot be tagged. Tagging folders is not supported for team-owned templates.

---

## InvalidPropertyGroupError

The InvalidPropertyGroupError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `path` - FileProperties.LookupError
- `unsupportedFolder` - This folder cannot be tagged. Tagging folders is not supported for team-owned templates.
- `propertyFieldTooLarge` - One or more of the supplied property field values is too large.
- `doesNotFitTemplate` - One or more of the supplied property fields does not conform to the template specifications.
- `duplicatePropertyGroups` - There are 2 or more property groups referring to the same templates in the input.

---

## AddPropertiesError

The AddPropertiesError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `path` - FileProperties.LookupError
- `unsupportedFolder` - This folder cannot be tagged. Tagging folders is not supported for team-owned templates.
- `propertyFieldTooLarge` - One or more of the supplied property field values is too large.
- `doesNotFitTemplate` - One or more of the supplied property fields does not conform to the template specifications.
- `duplicatePropertyGroups` - There are 2 or more property groups referring to the same templates in the input.
- `propertyGroupAlreadyExists` - A property group associated with this template and file already exists.

---

## PropertyGroupTemplate

Defines how a property group may be structured.

**Properties:**
- `name: String` - Display name for the template. Template names can be up to 256 bytes.
- `description_: String` - Description for the template. Template descriptions can be up to 1024 bytes.
- `fields: [FileProperties.PropertyFieldTemplate]` - Definitions of the property fields associated with this template. There can be up to 32 properties in a single template.

---

## AddTemplateArg

The AddTemplateArg struct. Inherits from PropertyGroupTemplate.

**Properties:**
- Inherits all properties from `PropertyGroupTemplate`.

---

## AddTemplateResult

The AddTemplateResult struct.

**Properties:**
- `templateId: String` - An identifier for template added by templatesAddForUser or templatesAddForTeam.

---

## GetTemplateArg

The GetTemplateArg struct.

**Properties:**
- `templateId: String` - An identifier for template added by route templatesAddForUser or templatesAddForTeam.

---

## GetTemplateResult

The GetTemplateResult struct. Inherits from PropertyGroupTemplate.

**Properties:**
- Inherits all properties from `PropertyGroupTemplate`.

---

## ListTemplateResult

The ListTemplateResult struct.

**Properties:**
- `templateIds: [String]` - List of identifiers for templates added by templatesAddForUser or templatesAddForTeam.

---

## LogicalOperator

Logical operator to join search queries together.

**Cases:**
- `orOperator` - Append a query with an "or" operator.
- `other` - An unspecified error.

---

## LookUpPropertiesError

The LookUpPropertiesError union.

**Cases:**
- `propertyGroupNotFound` - No property group was found.
- `other` - An unspecified error.

---

## LookupError

The LookupError union.

**Cases:**
- `malformedPath` - String
- `notFound` - There is nothing at the given path.
- `notFile` - We were expecting a file, but the given path refers to something that isn't a file.
- `notFolder` - We were expecting a folder, but the given path refers to something that isn't a folder.
- `restrictedContent` - The file cannot be transferred because the content is restricted. For example, we might restrict a file due to legal requirements.
- `other` - An unspecified error.

---

## ModifyTemplateError

The ModifyTemplateError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `conflictingPropertyNames` - A property field key with that name already exists in the template.
- `tooManyProperties` - There are too many properties in the changed template. The maximum number of properties per template is 32.
- `tooManyTemplates` - There are too many templates for the team.
- `templateAttributeTooLarge` - The template name, description or one or more of the property field keys is too large.

---

## OverwritePropertyGroupArg

The OverwritePropertyGroupArg struct.

**Properties:**
- `path: String` - A unique identifier for the file or folder.
- `propertyGroups: [FileProperties.PropertyGroup]` - The property groups "snapshot" updates to force apply. No two groups in the input should refer to the same template.

---

## PropertiesSearchArg

The PropertiesSearchArg struct.

**Properties:**
- `queries: [FileProperties.PropertiesSearchQuery]` - Queries to search.
- `templateFilter: FileProperties.TemplateFilter` - Filter results to contain only properties associated with these template IDs.

---

## PropertiesSearchContinueArg

The PropertiesSearchContinueArg struct.

**Properties:**
- `cursor: String` - The cursor returned by your last call to propertiesSearch or propertiesSearchContinue.

---

## PropertiesSearchContinueError

The PropertiesSearchContinueError union.

**Cases:**
- `reset` - Indicates that the cursor has been invalidated. Call propertiesSearch to obtain a new cursor.
- `other` - An unspecified error.

---

## PropertiesSearchError

The PropertiesSearchError union.

**Cases:**
- `propertyGroupLookup` - FileProperties.LookUpPropertiesError
- `other` - An unspecified error.

---

## PropertiesSearchMatch

The PropertiesSearchMatch struct.

**Properties:**
- `id: String` - The ID for the matched file or folder.
- `path: String` - The path for the matched file or folder.
- `isDeleted: Bool` - Whether the file or folder is deleted.
- `propertyGroups: [FileProperties.PropertyGroup]` - List of custom property groups associated with the file.

---

## PropertiesSearchMode

The PropertiesSearchMode union.

**Cases:**
- `fieldName` - String - Search for a value associated with this field name.
- `other` - An unspecified error.

---

## PropertiesSearchQuery

The PropertiesSearchQuery struct.

**Properties:**
- `query: String` - The property field value for which to search across templates.
- `mode: FileProperties.PropertiesSearchMode` - The mode with which to perform the search.
- `logicalOperator: FileProperties.LogicalOperator` - The logical operator with which to append the query.

---

## PropertiesSearchResult

The PropertiesSearchResult struct.

**Properties:**
- `matches: [FileProperties.PropertiesSearchMatch]` - A list (possibly empty) of matches for the query.
- `cursor: String?` - Pass the cursor into propertiesSearchContinue to continue to receive search results. Cursor will be null when there are no more results.

---

## PropertyField

Raw key/value data to be associated with a Dropbox file. Property fields are added to Dropbox files as a PropertyGroup.

**Properties:**
- `name: String` - Key of the property field associated with a file and template. Keys can be up to 256 bytes.
- `value: String` - Value of the property field associated with a file and template. Values can be up to 1024 bytes.

---

## PropertyFieldTemplate

Defines how a single property field may be structured. Used exclusively by PropertyGroupTemplate.

**Properties:**
- `name: String` - Key of the property field being described. Property field keys can be up to 256 bytes.
- `description_: String` - Description of the property field. Property field descriptions can be up to 1024 bytes.
- `type: FileProperties.PropertyType` - Data type of the value of this property field. This type will be enforced upon property creation and modifications.

---

## PropertyGroup

A subset of the property fields described by the corresponding PropertyGroupTemplate. Properties are always added to a Dropbox file as a PropertyGroup. The possible key names and value types in this group are defined by the corresponding PropertyGroupTemplate.

**Properties:**
- `templateId: String` - A unique identifier for the associated template.
- `fields: [FileProperties.PropertyField]` - The actual properties associated with the template. There can be up to 32 property types per template.

---

## PropertyGroupUpdate

The PropertyGroupUpdate struct.

**Properties:**
- `templateId: String` - A unique identifier for a property template.
- `addOrUpdateFields: [FileProperties.PropertyField]?` - Property fields to update. If the property field already exists, it is updated. If the property field doesn't exist, the property group is added.
- `removeFields: [String]?` - Property fields to remove (by name), provided they exist.

---

## PropertyType

Data type of the given property field added.

**Cases:**
- `string_` - The associated property field will be of type string. Unicode is supported.
- `other` - An unspecified error.

---

## RemovePropertiesArg

The RemovePropertiesArg struct.

**Properties:**
- `path: String` - A unique identifier for the file or folder.
- `propertyTemplateIds: [String]` - A list of identifiers for a template created by templatesAddForUser or templatesAddForTeam.

---

## RemovePropertiesError

The RemovePropertiesError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `path` - FileProperties.LookupError
- `unsupportedFolder` - This folder cannot be tagged. Tagging folders is not supported for team-owned templates.
- `propertyGroupLookup` - FileProperties.LookUpPropertiesError

---

## RemoveTemplateArg

The RemoveTemplateArg struct.

**Properties:**
- `templateId: String` - An identifier for a template created by templatesAddForUser or templatesAddForTeam.

---

## TemplateFilterBase

The TemplateFilterBase union.

**Cases:**
- `filterSome` - [String] - Only templates with an ID in the supplied list will be returned (a subset of templates will be returned).
- `other` - An unspecified error.

---

## TemplateFilter

The TemplateFilter union.

**Cases:**
- `filterSome` - [String] - Only templates with an ID in the supplied list will be returned (a subset of templates will be returned).
- `other` - An unspecified error.
- `filterNone` - No templates will be filtered from the result (all templates will be returned).

---

## TemplateOwnerType

The TemplateOwnerType union.

**Cases:**
- `user` - Template will be associated with a user.
- `team` - Template will be associated with a team.
- `other` - An unspecified error.

---

## UpdatePropertiesArg

The UpdatePropertiesArg struct.

**Properties:**
- `path: String` - A unique identifier for the file or folder.
- `updatePropertyGroups: [FileProperties.PropertyGroupUpdate]` - The property groups "delta" updates to apply.

---

## UpdatePropertiesError

The UpdatePropertiesError union.

**Cases:**
- `templateNotFound` - String - Template does not exist for the given identifier.
- `restrictedContent` - You do not have permission to modify this template.
- `other` - An unspecified error.
- `path` - FileProperties.LookupError
- `unsupportedFolder` - This folder cannot be tagged. Tagging folders is not supported for team-owned templates.
- `propertyFieldTooLarge` - One or more of the supplied property field values is too large.
- `doesNotFitTemplate` - One or more of the supplied property fields does not conform to the template specifications.
- `duplicatePropertyGroups` - There are 2 or more property groups referring to the same templates in the input.
- `propertyGroupLookup` - FileProperties.LookUpPropertiesError

---

## UpdateTemplateArg

The UpdateTemplateArg struct.

**Properties:**
- `templateId: String` - An identifier for template added by templatesAddForUser or templatesAddForTeam.
- `name: String?` - A display name for the template. Template names can be up to 256 bytes.
- `description_: String?` - Description for the new template. Template descriptions can be up to 1024 bytes.
- `addFields: [FileProperties.PropertyFieldTemplate]?` - Property field templates to be added to the group template. There can be up to 32 properties in a single template.

---

## UpdateTemplateResult

The UpdateTemplateResult struct.

**Properties:**
- `templateId: String` - An identifier for template added by route templatesAddForUser or templatesAddForTeam.
