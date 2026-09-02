

# CreatePlanRequest

OpenAPI-style body normalized server-side into Plan.pricing (monthly/yearly amounts), features (objects with name/included), and optional limits/trial/metadata. Slug is derived from projectId + name unless a collision occurs. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** | Display name; also used to generate a unique slug per project. |  |
|**description** | **String** |  |  [optional] |
|**price** | **BigDecimal** | Amount for the chosen interval. The server fills the other billing period (e.g. yearly ≈ monthly × 12 × 0.8 when interval is month).  |  |
|**currency** | **String** | ISO currency code (stored lowercased). |  |
|**interval** | [**IntervalEnum**](#IntervalEnum) | Which period &#x60;price&#x60; applies to; drives pricing.monthly vs pricing.yearly. |  |
|**features** | [**List&lt;CreatePlanRequestFeaturesInner&gt;**](CreatePlanRequestFeaturesInner.md) | Strings become &#x60;{ name, included: true }&#x60;. You may send full feature objects instead.  |  [optional] |
|**limits** | [**CreatePlanRequestLimits**](CreatePlanRequestLimits.md) |  |  [optional] |
|**trial** | [**CreatePlanRequestTrial**](CreatePlanRequestTrial.md) |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**isDefault** | **Boolean** | Only one default plan per project is allowed server-side. |  [optional] |
|**sortOrder** | **BigDecimal** | Lower numbers list first in UIs. |  [optional] |
|**metadata** | **Map&lt;String, Object&gt;** | Arbitrary key/value data stored on the plan document. |  [optional] |



## Enum: IntervalEnum

| Name | Value |
|---- | -----|
| MONTH | &quot;month&quot; |
| YEAR | &quot;year&quot; |



