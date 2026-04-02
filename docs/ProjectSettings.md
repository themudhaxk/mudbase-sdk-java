

# ProjectSettings

Project-level settings. Toggles for verification and default user status apply to app and role-based signup. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**allowAnonymousAuth** | **Boolean** | Allow anonymous (unauthenticated) users |  [optional] |
|**requireEmailVerification** | **Boolean** | When true, users who sign up with email do not receive a token until they verify their email; login is blocked until verified. |  [optional] |
|**requirePhoneVerification** | **Boolean** | When true, users who sign in with phone (e.g. OTP) must have verified their phone before receiving a token. |  [optional] |
|**defaultUserAccountStatus** | [**DefaultUserAccountStatusEnum**](#DefaultUserAccountStatusEnum) | Default account status for new signups. **active** &#x3D; user can use the app immediately. **pending** &#x3D; user must be approved by an org owner/admin (PATCH org user status to active) before they can perform protected operations.  |  [optional] |
|**enableRealtime** | **Boolean** |  |  [optional] |
|**enableStorage** | **Boolean** |  |  [optional] |
|**enableFunctions** | **Boolean** |  |  [optional] |



## Enum: DefaultUserAccountStatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| ACTIVE | &quot;active&quot; |



