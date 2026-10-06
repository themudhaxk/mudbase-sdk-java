

# ProjectSmsByoPatchRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** |  |  [optional] |
|**provider** | [**ProviderEnum**](#ProviderEnum) |  |  [optional] |
|**defaultFrom** | **String** | Default sender (E.164 for Twilio; Termii/Africa&#39;s Talking may use alphanumeric or approved sender IDs per provider rules). |  [optional] |
|**config** | **Map&lt;String, Object&gt;** | Provider credentials and options (encrypted at rest). Required keys when enabling BYO: **twilio** — &#x60;accountSid&#x60;, &#x60;authToken&#x60;. Optional &#x60;from&#x60;. **termii** — &#x60;apiKey&#x60;. Optional &#x60;from&#x60;. **africastalking** — &#x60;username&#x60;, &#x60;apiKey&#x60;. Optional &#x60;from&#x60;.  |  [optional] |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| TWILIO | &quot;twilio&quot; |
| TERMII | &quot;termii&quot; |
| AFRICASTALKING | &quot;africastalking&quot; |
| NONE | &quot;none&quot; |



