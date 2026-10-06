

# DashboardOverviewDataUptime

Organization-wide uptime KPI; platformProbe* is infra (Mongo); projectHttp* is this project only for comparison.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**scope** | [**ScopeEnum**](#ScopeEnum) |  |  [optional] |
|**displayPct30d** | **BigDecimal** |  |  [optional] |
|**displaySource** | **String** |  |  [optional] |
|**isPreliminary** | **Boolean** |  |  [optional] |
|**platformProbePct30d** | **BigDecimal** |  |  [optional] |
|**platformSamples** | **Integer** |  |  [optional] |
|**platformOkSamples** | **Integer** |  |  [optional] |
|**orgHttpNon5xxPct30d** | **BigDecimal** |  |  [optional] |
|**orgHttpSampled30d** | **Integer** |  |  [optional] |
|**orgHttp5xx30d** | **Integer** | Metered 5xx count from UsageStat (trackApiCall) |  [optional] |
|**projectHttp5xx30d** | **Integer** | This project’s metered 5xx count (30d) |  [optional] |
|**globalHttpNon5xxPct30d** | **BigDecimal** | Deprecated alias for orgHttpNon5xxPct30d |  [optional] |
|**globalHttpSampled30d** | **Integer** | Deprecated alias for orgHttpSampled30d |  [optional] |
|**requestNon5xxPct30d** | **BigDecimal** | Deprecated alias for orgHttpNon5xxPct30d |  [optional] |
|**requestSampled30d** | **Integer** | Deprecated alias for orgHttpSampled30d |  [optional] |
|**projectHttpNon5xxPct30d** | **BigDecimal** |  |  [optional] |
|**projectHttpSampled30d** | **Integer** |  |  [optional] |
|**help** | **String** |  |  [optional] |



## Enum: ScopeEnum

| Name | Value |
|---- | -----|
| ORGANIZATION | &quot;organization&quot; |



