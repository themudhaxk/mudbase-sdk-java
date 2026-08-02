

# EmailTemplateResolved

Effective template body (project override, else global, else built-in).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  [optional] |
|**subject** | **String** |  |  [optional] |
|**htmlBody** | **String** |  |  [optional] |
|**textBody** | **String** |  |  [optional] |
|**variables** | **List&lt;String&gt;** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |
|**version** | **Integer** |  |  [optional] |
|**isProjectOverride** | **Boolean** |  |  [optional] |
|**effectiveSource** | [**EffectiveSourceEnum**](#EffectiveSourceEnum) |  |  [optional] |



## Enum: EffectiveSourceEnum

| Name | Value |
|---- | -----|
| PROJECT | &quot;project&quot; |
| GLOBAL | &quot;global&quot; |
| BUILTIN | &quot;builtin&quot; |



