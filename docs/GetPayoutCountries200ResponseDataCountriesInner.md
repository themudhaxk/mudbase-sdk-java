

# GetPayoutCountries200ResponseDataCountriesInner


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**code** | **String** | ISO-3166 alpha-2 country code (e.g. NG, GH, KE, US, GB). |  [optional] |
|**name** | **String** |  |  [optional] |
|**currency** | **String** |  |  [optional] |
|**banksListSupported** | **Boolean** | Whether GET /payment-processing/banks returns a live bank list for this country. |  [optional] |
|**mobileMoney** | **Boolean** |  |  [optional] |
|**international** | **Boolean** | True for a market whose settlement rail requires an account-level capability beyond the standard local-rail onboarding (currently US, GB). |  [optional] |
|**fields** | [**List&lt;GetPayoutCountries200ResponseDataCountriesInnerFieldsInner&gt;**](GetPayoutCountries200ResponseDataCountriesInnerFieldsInner.md) |  |  [optional] |



