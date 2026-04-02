

# User

Authenticated user profile (id, email, name, roles, project access).

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



