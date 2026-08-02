

# GetOrganizationUsers200ResponseUsersInner


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**firstName** | **String** |  |  [optional] |
|**lastName** | **String** |  |  [optional] |
|**email** | **String** |  |  [optional] |
|**avatar** | **String** |  |  [optional] |
|**emailVerified** | **Boolean** |  |  [optional] |
|**role** | **String** |  |  [optional] |
|**customRole** | **String** |  |  [optional] |
|**phone** | **String** |  |  [optional] |
|**phoneVerified** | **Boolean** |  |  [optional] |
|**lastLogin** | **OffsetDateTime** |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**accountStatus** | [**AccountStatusEnum**](#AccountStatusEnum) |  |  [optional] |
|**isAnonymous** | **Boolean** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**project** | [**GetOrganizationUsers200ResponseUsersInnerProject**](GetOrganizationUsers200ResponseUsersInnerProject.md) |  |  [optional] |



## Enum: AccountStatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| ACTIVE | &quot;active&quot; |
| SUSPENDED | &quot;suspended&quot; |



