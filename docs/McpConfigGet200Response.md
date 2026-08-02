

# McpConfigGet200Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** |  |  [optional] |
|**plan** | **String** |  |  [optional] |
|**allowedPlans** | **List&lt;String&gt;** |  |  [optional] |
|**freePromoActive** | **Boolean** | True if this org is on the free plan and MCP is temporarily enabled via the launch promo |  [optional] |
|**freePromoEndsAt** | **OffsetDateTime** | When the free-plan MCP promo ends (null if not active) |  [optional] |
|**endpoint** | **String** |  |  [optional] |
|**tools** | [**List&lt;McpConfigGet200ResponseToolsInner&gt;**](McpConfigGet200ResponseToolsInner.md) |  |  [optional] |



