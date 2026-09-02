

# DashboardOverviewDataLatency

Per-project weighted mean latency from UsageStat for routes in openapi-docs.yaml (customer/project API only).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**scope** | [**ScopeEnum**](#ScopeEnum) |  |  [optional] |
|**avgMsToday** | **Integer** |  |  [optional] |
|**avgMs7d** | **Integer** |  |  [optional] |
|**latencySamplesToday** | **Integer** | Count of openapi-docs–scoped latency samples for this project (UTC today) |  [optional] |
|**latencyNeedsTraffic** | **Boolean** |  |  [optional] |
|**interpretation** | **String** | Why mean can differ from typical latency; points to latency-insights |  [optional] |
|**instanceRollup** | [**DashboardOverviewDataLatencyInstanceRollup**](DashboardOverviewDataLatencyInstanceRollup.md) |  |  [optional] |
|**topRoutesByImpactHint** | [**List&lt;DashboardOverviewDataLatencyTopRoutesByImpactHintInner&gt;**](DashboardOverviewDataLatencyTopRoutesByImpactHintInner.md) | Top route templates by impact score on this instance (debugging hint) |  [optional] |



## Enum: ScopeEnum

| Name | Value |
|---- | -----|
| PROJECT_OPENAPI_DOC | &quot;project_openapi_doc&quot; |



