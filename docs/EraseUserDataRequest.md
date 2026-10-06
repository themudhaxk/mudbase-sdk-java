

# EraseUserDataRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**confirm** | [**ConfirmEnum**](#ConfirmEnum) |  |  |
|**currentPassword** | **String** | Required unless the account has no password set (OAuth-only) |  [optional] |
|**totpToken** | **String** | Required only if the account has 2FA enabled |  [optional] |



## Enum: ConfirmEnum

| Name | Value |
|---- | -----|
| DELETE | &quot;DELETE&quot; |



