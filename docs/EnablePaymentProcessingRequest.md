

# EnablePaymentProcessingRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**country** | **String** | ISO-3166 alpha-2 payout country code, one of the codes returned by GET /payment-processing/countries (e.g. NG, GH, KE, US, GB). |  |
|**businessName** | **String** |  |  |
|**businessMobile** | **String** | Optional, used for payout provider account notifications. |  [optional] |
|**accountBank** | **String** | Bank code, mobile-money network code, routing number, or sort code, depending on country. |  [optional] |
|**accountNumber** | **String** | Bank/mobile-money account number, IBAN, or similar, depending on country. |  [optional] |
|**bvn** | **String** | Required only when country is NG (Nigeria). |  [optional] |
|**accountType** | **String** | Required only when country is US (checking or savings). |  [optional] |
|**accountHolderName** | **String** | Required only when country is US or GB. |  [optional] |



