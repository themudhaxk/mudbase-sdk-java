

# Message

Single message record (id, type, title, body, recipients, status, sentAt).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**type** | [**TypeEnum**](#TypeEnum) |  |  [optional] |
|**title** | **String** |  |  [optional] |
|**body** | **String** |  |  [optional] |
|**subject** | **String** |  |  [optional] |
|**recipients** | **Integer** |  |  [optional] |
|**successCount** | **Integer** |  |  [optional] |
|**failureCount** | **Integer** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**sentAt** | **OffsetDateTime** |  |  [optional] |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| PUSH | &quot;push&quot; |
| EMAIL | &quot;email&quot; |
| SMS | &quot;sms&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| SENT | &quot;sent&quot; |
| FAILED | &quot;failed&quot; |
| PENDING | &quot;pending&quot; |



