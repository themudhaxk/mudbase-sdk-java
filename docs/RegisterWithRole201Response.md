

# RegisterWithRole201Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**message** | **String** |  |  [optional] |
|**requireVerification** | **Boolean** | True when the project requires email verification before a session is issued - no token is returned in that case. |  [optional] |
|**token** | **String** | JWT access token. Absent when requireVerification is true. |  [optional] |
|**refreshToken** | **String** | JWT refresh token. Absent when requireVerification is true. |  [optional] |
|**expiresIn** | **Integer** | Access token TTL in seconds. Absent when requireVerification is true. |  [optional] |
|**user** | [**RegisterWithRole201ResponseUser**](RegisterWithRole201ResponseUser.md) |  |  [optional] |
|**role** | [**RegisterWithRole201ResponseRole**](RegisterWithRole201ResponseRole.md) |  |  [optional] |



