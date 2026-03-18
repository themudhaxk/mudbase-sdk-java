

# BillingCreateCheckoutSessionRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**planId** | **String** | Plan ID to subscribe to |  |
|**billingCycle** | [**BillingCycleEnum**](#BillingCycleEnum) | Billing interval |  |
|**customerInfo** | [**BillingCreateCheckoutSessionRequestCustomerInfo**](BillingCreateCheckoutSessionRequestCustomerInfo.md) |  |  |
|**successUrl** | **URI** | Redirect URL after successful payment |  [optional] |
|**cancelUrl** | **URI** | Redirect URL if user cancels |  [optional] |



## Enum: BillingCycleEnum

| Name | Value |
|---- | -----|
| MONTHLY | &quot;monthly&quot; |
| YEARLY | &quot;yearly&quot; |



