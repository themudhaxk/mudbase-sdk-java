

# DashboardOverviewDataRequests


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**today** | **Integer** | Billing trackApiCall count (UTC day) |  [optional] |
|**yesterday** | **Integer** |  |  [optional] |
|**latencyTrackedToday** | **Integer** | UsageStat latencyCount for this project (middleware-metered responses) |  [optional] |
|**latencyTrackedYesterday** | **Integer** |  |  [optional] |
|**meteringNote** | **String** |  |  [optional] |
|**changePct** | **BigDecimal** |  |  [optional] |
|**direction** | [**DirectionEnum**](#DirectionEnum) |  |  [optional] |



## Enum: DirectionEnum

| Name | Value |
|---- | -----|
| UP | &quot;up&quot; |
| DOWN | &quot;down&quot; |
| FLAT | &quot;flat&quot; |



