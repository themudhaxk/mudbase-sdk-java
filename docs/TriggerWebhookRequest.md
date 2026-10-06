

# TriggerWebhookRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**projectId** | **String** | Target project (must belong to your org) |  |
|**url** | **URI** | HTTPS URL validated against SSRF rules |  |
|**event** | **String** | Event name (sent as X-MUDBASE-Event) |  |
|**payload** | **Object** | JSON body POSTed to your endpoint |  |
|**method** | [**MethodEnum**](#MethodEnum) |  |  [optional] |



## Enum: MethodEnum

| Name | Value |
|---- | -----|
| GET | &quot;GET&quot; |
| POST | &quot;POST&quot; |
| PUT | &quot;PUT&quot; |
| PATCH | &quot;PATCH&quot; |
| DELETE | &quot;DELETE&quot; |



