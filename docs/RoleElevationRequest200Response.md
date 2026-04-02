

# RoleElevationRequest200Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**message** | **String** |  |  [optional] |
|**requestId** | **String** |  |  [optional] |
|**workflow** | [**WorkflowEnum**](#WorkflowEnum) |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**nextSteps** | **List&lt;String&gt;** |  |  [optional] |
|**estimatedApprovalTime** | **String** |  |  [optional] |



## Enum: WorkflowEnum

| Name | Value |
|---- | -----|
| AUTO_APPROVED | &quot;auto_approved&quot; |
| PENDING_ADMIN_APPROVAL | &quot;pending_admin_approval&quot; |
| PENDING_REQUIREMENTS | &quot;pending_requirements&quot; |
| MANUAL_APPROVAL | &quot;manual_approval&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| APPROVED | &quot;approved&quot; |
| PENDING | &quot;pending&quot; |



