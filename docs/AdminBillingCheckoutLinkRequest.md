

# AdminBillingCheckoutLinkRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**plan** | [**PlanEnum**](#PlanEnum) |  |  |
|**billingCycle** | [**BillingCycleEnum**](#BillingCycleEnum) |  |  [optional] |
|**amountCents** | **Integer** | Monthly amount in cents (overrides catalog; enterprise default is contract) |  [optional] |
|**chargeAmountCents** | **Integer** | Exact charge in cents for this checkout (overrides monthly math) |  [optional] |
|**currency** | **String** |  |  [optional] |
|**email** | **String** |  |  [optional] |
|**name** | **String** |  |  [optional] |
|**redirectUrl** | **URI** |  |  [optional] |
|**sendEmail** | **Boolean** |  |  [optional] |
|**toEmail** | **String** |  |  [optional] |
|**message** | **String** | Optional note shown in org_billing_checkout email |  [optional] |



## Enum: PlanEnum

| Name | Value |
|---- | -----|
| STARTER | &quot;starter&quot; |
| GROWTH | &quot;growth&quot; |
| SCALE | &quot;scale&quot; |
| ENTERPRISE | &quot;enterprise&quot; |



## Enum: BillingCycleEnum

| Name | Value |
|---- | -----|
| MONTHLY | &quot;monthly&quot; |
| YEARLY | &quot;yearly&quot; |



