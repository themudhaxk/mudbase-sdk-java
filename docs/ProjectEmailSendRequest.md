

# ProjectEmailSendRequest

Either `template` (with optional `data`) or both `subject` and `html` must be provided. `to` may be a string or array of strings. For named templates, **`data`** should supply values for `{{placeholders}}` (see **Email** tag description for the full list). 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**template** | **String** | Registered template name resolved by the email worker |  [optional] |
|**to** | [**EmailRequestTo**](EmailRequestTo.md) |  |  [optional] |
|**data** | **Map&lt;String, Object&gt;** |  |  [optional] |
|**subject** | **String** |  |  [optional] |
|**html** | **String** |  |  [optional] |
|**idempotencyKey** | **String** |  |  [optional] |
|**brandingScope** | [**BrandingScopeEnum**](#BrandingScopeEnum) | Email layout branding; defaults from project context when omitted |  [optional] |



## Enum: BrandingScopeEnum

| Name | Value |
|---- | -----|
| PLATFORM | &quot;platform&quot; |
| PROJECT | &quot;project&quot; |



