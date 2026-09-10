

# WebhookLog

One **outbound delivery attempt** (Mudbase HTTP client → your `url`). **`_id`** is what the API calls **`webhookId`** in **`POST /api/webhooks/trigger`** and **`POST /api/webhooks/retry/{webhookId}`**. The string field **`webhookId`** below is an internal correlation id (e.g. `manual-<timestamp>`), not the path parameter for retry. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** | MongoDB id — use as &#x60;webhookId&#x60; path param for retry |  [optional] |
|**org** | **String** | Organization that owns the project |  [optional] |
|**project** | **String** | Project id this delivery belongs to |  [optional] |
|**webhookId** | **String** | Internal correlation string (e.g. manual-173…), not the retry path id |  [optional] |
|**url** | **String** |  |  [optional] |
|**method** | [**MethodEnum**](#MethodEnum) |  |  [optional] |
|**event** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**payload** | **Object** | JSON body sent to your endpoint |  [optional] |
|**headers** | **Object** | Outbound request headers (e.g. X-MUDBASE-Event, Content-Type) |  [optional] |
|**response** | [**WebhookLogResponse**](WebhookLogResponse.md) |  |  [optional] |
|**duration** | **Integer** | Round-trip time in milliseconds |  [optional] |
|**attempts** | **Integer** |  |  [optional] |
|**maxAttempts** | **Integer** |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**nextRetry** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: MethodEnum

| Name | Value |
|---- | -----|
| GET | &quot;GET&quot; |
| POST | &quot;POST&quot; |
| PUT | &quot;PUT&quot; |
| PATCH | &quot;PATCH&quot; |
| DELETE | &quot;DELETE&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| SUCCESS | &quot;success&quot; |
| FAILED | &quot;failed&quot; |
| RETRYING | &quot;retrying&quot; |



