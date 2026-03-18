

# ApiKeyWithSecret

API key with secret (returned only on create; store secret securely).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**name** | **String** |  |  [optional] |
|**project** | [**ProjectSummary**](ProjectSummary.md) |  |  [optional] |
|**permissions** | [**List&lt;ApiKeyPermission&gt;**](ApiKeyPermission.md) |  |  [optional] |
|**rateLimit** | [**RateLimit**](RateLimit.md) |  |  [optional] |
|**usage** | [**ApiKeyUsage**](ApiKeyUsage.md) |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**expiresAt** | **OffsetDateTime** |  |  [optional] |
|**createdBy** | [**UserSummary**](UserSummary.md) |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**secret** | **String** |  |  [optional] |



