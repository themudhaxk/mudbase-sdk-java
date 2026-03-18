

# OTPSendRequest

Request to send OTP via SMS or email for the given project.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**phone** | **String** |  |  [optional] |
|**email** | **String** |  |  [optional] |
|**projectId** | **String** |  |  |
|**method** | [**MethodEnum**](#MethodEnum) |  |  |



## Enum: MethodEnum

| Name | Value |
|---- | -----|
| SMS | &quot;sms&quot; |
| EMAIL | &quot;email&quot; |



