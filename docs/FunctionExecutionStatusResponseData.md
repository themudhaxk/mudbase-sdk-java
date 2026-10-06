

# FunctionExecutionStatusResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**executionId** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**durationMs** | **Integer** | Duration in milliseconds (null until completed) |  [optional] |
|**result** | **Object** |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**errorClass** | **String** |  |  [optional] |
|**logs** | [**FunctionExecutionStatusResponseDataLogs**](FunctionExecutionStatusResponseDataLogs.md) |  |  [optional] |
|**machine** | **Object** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**startedAt** | **OffsetDateTime** |  |  [optional] |
|**completedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| QUEUED | &quot;queued&quot; |
| PROVISIONING | &quot;provisioning&quot; |
| RUNNING | &quot;running&quot; |
| SUCCESS | &quot;success&quot; |
| FAILED | &quot;failed&quot; |
| TIMEOUT | &quot;timeout&quot; |



