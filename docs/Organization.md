

# Organization

Organization (org) entity with plan, usage, limits, and billing.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**name** | **String** |  |  [optional] |
|**slug** | **String** |  |  [optional] |
|**description** | **String** |  |  [optional] |
|**logo** | **URI** | Optional logo URL. Org-related emails use the platform logo (env); this field is for legacy or future UI use only. |  [optional] |
|**website** | **String** |  |  [optional] |
|**plan** | [**Plan**](Plan.md) |  |  [optional] |
|**usage** | [**Usage**](Usage.md) |  |  [optional] |
|**limits** | [**Limits**](Limits.md) |  |  [optional] |
|**billing** | [**Billing**](Billing.md) |  |  [optional] |
|**settings** | **Object** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



