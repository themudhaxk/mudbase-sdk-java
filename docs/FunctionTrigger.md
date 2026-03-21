

# FunctionTrigger

Function trigger config (type, event, schedule, path, method, collectionId, bucketId).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**type** | [**TypeEnum**](#TypeEnum) | Trigger type |  |
|**event** | **String** | Event name (e.g. create, update, delete for document; uploaded, deleted for file; tx, balance for wallet) |  [optional] |
|**schedule** | **String** | For cron - minutely, hourly, daily, weekly, or custom cron expression |  [optional] |
|**path** | **String** | HTTP path for http triggers |  [optional] |
|**method** | [**MethodEnum**](#MethodEnum) |  |  [optional] |
|**collectionId** | **String** | For document triggers - filter by collection |  [optional] |
|**bucketId** | **String** | For file triggers - filter by bucket |  [optional] |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| HTTP | &quot;http&quot; |
| EVENT | &quot;event&quot; |
| DOCUMENT | &quot;document&quot; |
| FILE | &quot;file&quot; |
| WEBHOOK | &quot;webhook&quot; |
| WALLET | &quot;wallet&quot; |
| CRON | &quot;cron&quot; |
| MESSAGING | &quot;messaging&quot; |



## Enum: MethodEnum

| Name | Value |
|---- | -----|
| GET | &quot;GET&quot; |
| POST | &quot;POST&quot; |
| PUT | &quot;PUT&quot; |
| DELETE | &quot;DELETE&quot; |



