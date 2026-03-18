

# BillingCreateCheckoutSession200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**checkoutUrl** | **String** | Checkout/page URL (crypto) or null when Flutterwave |  [optional] |
|**authorizationUrl** | **String** | Flutterwave redirect URL (when Flutterwave is used) |  [optional] |
|**accessCode** | **String** | Flutterwave access code |  [optional] |
|**reference** | **String** | Payment reference (e.g. mudbase_xxx or pmt_xxx) |  [optional] |
|**paymentId** | **String** | Payment intent ID (crypto) |  [optional] |
|**paymentOptions** | [**List&lt;BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner&gt;**](BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner.md) | Multi-chain payment options (crypto) |  [optional] |
|**paymentAddress** | **String** |  |  [optional] |
|**network** | **String** |  |  [optional] |
|**asset** | **String** |  |  [optional] |
|**amount** | **BigDecimal** |  |  [optional] |
|**currency** | **String** |  |  [optional] |



