

# RegisterLocalUser201Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**message** | **String** |  |  [optional] |
|**requireVerification** | **Boolean** | true when email verification is required; no token in response |  [optional] |
|**token** | **String** | Present only when requireEmailVerification is false |  [optional] |
|**refreshToken** | **String** | Present only when requireEmailVerification is false |  [optional] |
|**expiresIn** | **Integer** | Present only when token is returned |  [optional] |
|**user** | [**RegisterLocalUser201ResponseUser**](RegisterLocalUser201ResponseUser.md) |  |  [optional] |



