

# ChatSendMessageRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**content** | **String** | Plaintext body; omit when sending e2ee (use e2ee.ciphertext for E2EE text). |  [optional] |
|**e2ee** | [**ChatSendMessageRequestE2ee**](ChatSendMessageRequestE2ee.md) |  |  [optional] |
|**replyTo** | **String** |  |  [optional] |
|**mentions** | **List&lt;String&gt;** |  |  [optional] |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| TEXT | &quot;text&quot; |
| IMAGE | &quot;image&quot; |
| VIDEO | &quot;video&quot; |
| AUDIO | &quot;audio&quot; |
| FILE | &quot;file&quot; |
| LOCATION | &quot;location&quot; |
| CONTACT | &quot;contact&quot; |



