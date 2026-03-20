

# AuthLogin200Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**message** | **String** |  |  [optional] |
|**token** | **String** | JWT access token (use in Authorization Bearer header) |  [optional] |
|**refreshToken** | **String** | JWT refresh token (use with POST /api/auth/refresh to get new token pair) |  [optional] |
|**expiresIn** | **Integer** | Access token TTL in seconds (e.g. 1800 for 30 minutes) |  [optional] |
|**user** | [**AuthLogin200ResponseUser**](AuthLogin200ResponseUser.md) |  |  [optional] |



