

# MultiRoleAddRoleRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**slug** | **String** |  |  |
|**name** | **String** |  |  |
|**description** | **String** |  |  [optional] |
|**signupEndpoint** | **String** |  |  |
|**defaultPermissions** | [**List&lt;MultiRoleAddRoleRequestDefaultPermissionsInner&gt;**](MultiRoleAddRoleRequestDefaultPermissionsInner.md) | Optional global/base permissions. For collection-level CRUD use &#x60;collectionPermissions&#x60;. |  [optional] |
|**collectionPermissions** | [**Map&lt;String, MultiRoleUpdateRoleRequestCollectionPermissionsValue&gt;**](MultiRoleUpdateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; values are action arrays or objects with &#x60;actions&#x60; + optional &#x60;conditions&#x60;. |  [optional] |



