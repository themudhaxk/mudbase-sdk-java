

# CreateApiKeyRequest

Payload to create an API key (name, projectId, permissions, rateLimit, expiresAt).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  |
|**projectId** | **String** | MongoDB ObjectId of the project |  |
|**permissions** | [**List&lt;ApiKeyPermission&gt;**](ApiKeyPermission.md) | Optional. Permission objects (resource + actions). Omit or pass [] for full access (all resources and actions). Include only the entries you want; remove resources or actions to restrict the key. |  [optional] |
|**rateLimit** | [**RateLimit**](RateLimit.md) |  |  [optional] |
|**expiresAt** | **OffsetDateTime** | Optional. When provided, must be a valid ISO 8601 date-time in the future. Omit for no expiration. |  [optional] |



