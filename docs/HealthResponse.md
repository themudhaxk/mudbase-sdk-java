

# HealthResponse

Health check response (status, timestamp, services, version, uptime).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**timestamp** | **OffsetDateTime** |  |  [optional] |
|**services** | [**HealthResponseServices**](HealthResponseServices.md) |  |  [optional] |
|**version** | **String** |  |  [optional] |
|**uptime** | **Integer** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| HEALTHY | &quot;healthy&quot; |
| UNHEALTHY | &quot;unhealthy&quot; |



