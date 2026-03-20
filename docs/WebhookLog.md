

# WebhookLog

Single webhook delivery log (url, method, event, status, payload, response, duration, attempts).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**url** | **String** |  |  [optional] |
|**method** | **String** |  |  [optional] |
|**event** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**statusCode** | **Integer** |  |  [optional] |
|**payload** | **Object** |  |  [optional] |
|**response** | **Object** |  |  [optional] |
|**duration** | **Integer** |  |  [optional] |
|**attempts** | **Integer** |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**nextRetry** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| SUCCESS | &quot;success&quot; |
| FAILED | &quot;failed&quot; |
| PENDING | &quot;pending&quot; |



