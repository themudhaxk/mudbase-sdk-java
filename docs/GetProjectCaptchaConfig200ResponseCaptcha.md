

# GetProjectCaptchaConfig200ResponseCaptcha


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** | Whether CAPTCHA is enabled for this project |  [optional] |
|**version** | [**VersionEnum**](#VersionEnum) | reCAPTCHA version (v2 or v3) |  [optional] |
|**siteKey** | **String** | Public site key for frontend integration |  [optional] |
|**minScore** | **BigDecimal** | Minimum score threshold for reCAPTCHA v3 |  [optional] |



## Enum: VersionEnum

| Name | Value |
|---- | -----|
| V2 | &quot;v2&quot; |
| V3 | &quot;v3&quot; |



