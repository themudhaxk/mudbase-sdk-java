

# EmailTemplateCatalogItem

One row from GET /email/templates (full catalog for the project).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  [optional] |
|**isCustomized** | **Boolean** | True if this project has a stored override for this template name. |  [optional] |
|**effectiveSource** | [**EffectiveSourceEnum**](#EffectiveSourceEnum) | Which layer is used at send time for this name. |  [optional] |
|**subjectSnippet** | **String** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |
|**version** | **Integer** |  |  [optional] |



## Enum: EffectiveSourceEnum

| Name | Value |
|---- | -----|
| PROJECT | &quot;project&quot; |
| GLOBAL | &quot;global&quot; |
| BUILTIN | &quot;builtin&quot; |



