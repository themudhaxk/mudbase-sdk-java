

# InitializeOrgPlanCheckoutRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**planName** | [**PlanNameEnum**](#PlanNameEnum) | Plan id from GET /api/billing/plans (excludes free and enterprise) |  |
|**billingCycle** | [**BillingCycleEnum**](#BillingCycleEnum) | Yearly &#x3D; 2 months free (~16.67% discount) |  [optional] |
|**redirectUrl** | **URI** | Override redirect after payment (default FRONTEND_URL/billing/callback) |  [optional] |



## Enum: PlanNameEnum

| Name | Value |
|---- | -----|
| STARTER | &quot;starter&quot; |
| GROWTH | &quot;growth&quot; |
| SCALE | &quot;scale&quot; |



## Enum: BillingCycleEnum

| Name | Value |
|---- | -----|
| MONTHLY | &quot;monthly&quot; |
| YEARLY | &quot;yearly&quot; |



