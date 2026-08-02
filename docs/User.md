

# User


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**email** | **String** |  |  [optional] |
|**firstName** | **String** |  |  [optional] |
|**lastName** | **String** |  |  [optional] |
|**fullName** | **String** |  |  [optional] |
|**avatar** | **String** |  |  [optional] |
|**role** | [**RoleEnum**](#RoleEnum) |  |  [optional] |
|**customRole** | **String** | Application-level role slug from the project&#39;s Multi-Role feature (e.g. \&quot;customer\&quot;, \&quot;seller\&quot;). Null for org-level (org/admin/member/viewer) users who aren&#39;t project end-users. |  [optional] |
|**isAnonymous** | **Boolean** | True for a guest session created via POST /api/auth/anonymous that hasn&#39;t been converted to a full account yet. |  [optional] |
|**emailVerified** | **Boolean** |  |  [optional] |
|**phoneVerified** | **Boolean** |  |  [optional] |
|**twoFactorEnabled** | **Boolean** |  |  [optional] |
|**lastLogin** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |
|**org** | [**OrganizationSummary**](OrganizationSummary.md) |  |  [optional] |



## Enum: RoleEnum

| Name | Value |
|---- | -----|
| OWNER | &quot;owner&quot; |
| ADMIN | &quot;admin&quot; |
| MEMBER | &quot;member&quot; |
| VIEWER | &quot;viewer&quot; |



