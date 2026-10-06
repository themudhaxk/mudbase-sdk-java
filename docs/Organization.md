

# Organization


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
|**settings** | **Object** | May include customDomainAddon (optional billing/legacy flag; not required for custom domains on Growth/Scale). |  [optional] |
|**deploymentType** | [**DeploymentTypeEnum**](#DeploymentTypeEnum) |  |  [optional] |
|**dedicated** | **Object** | Dedicated API/DB routing; may include edgeTlsStatus, infraMeteringLastReportAt. |  [optional] |
|**preferredRegion** | **String** |  |  [optional] |
|**infrastructureEnvironments** | **List&lt;Object&gt;** |  |  [optional] |
|**allowedDomains** | **List&lt;Object&gt;** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: DeploymentTypeEnum

| Name | Value |
|---- | -----|
| SHARED | &quot;shared&quot; |
| DEDICATED | &quot;dedicated&quot; |



