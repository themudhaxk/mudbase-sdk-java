

# CreateRoleRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  |
|**description** | **String** |  |  [optional] |
|**permissions** | [**List&lt;CreateRoleRequestPermissionsInner&gt;**](CreateRoleRequestPermissionsInner.md) | Legacy resource-level permissions. For data CRUD, prefer &#x60;collectionPermissions&#x60; below. |  [optional] |
|**hierarchy** | **BigDecimal** |  |  [optional] |
|**collectionPermissions** | [**Map&lt;String, CreateRoleRequestCollectionPermissionsValue&gt;**](CreateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; value can be action array or object with actions + conditions. |  [optional] |



