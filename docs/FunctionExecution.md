

# FunctionExecution

Single function execution record (id, executedAt, executionTime, success, payload, result, error).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**executedAt** | **OffsetDateTime** |  |  [optional] |
|**executionTime** | **Integer** |  |  [optional] |
|**success** | **Boolean** |  |  [optional] |
|**payload** | **Object** |  |  [optional] |
|**result** | **Object** |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**triggerType** | **String** |  |  [optional] |
|**triggerEvent** | **String** |  |  [optional] |
|**invokedBy** | [**InvokedByEnum**](#InvokedByEnum) |  |  [optional] |
|**retryCount** | **Integer** |  |  [optional] |



## Enum: InvokedByEnum

| Name | Value |
|---- | -----|
| MANUAL | &quot;manual&quot; |
| API_KEY | &quot;api_key&quot; |
| TRIGGER | &quot;trigger&quot; |
| CRON | &quot;cron&quot; |



