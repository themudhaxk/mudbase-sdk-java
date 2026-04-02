

# MultiRoleAddRoleRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**slug** | **String** |  |  |
|**name** | **String** |  |  |
|**description** | **String** |  |  [optional] |
|**signupEndpoint** | **String** |  |  |
|**requiresApproval** | **Boolean** |  |  [optional] |
|**requiresPayment** | **Boolean** |  |  [optional] |
|**requiresKYC** | **Boolean** |  |  [optional] |
|**defaultPermissions** | [**List&lt;MultiRoleAddRoleRequestDefaultPermissionsInner&gt;**](MultiRoleAddRoleRequestDefaultPermissionsInner.md) | Optional global/base permissions. For collection-level CRUD use &#x60;collectionPermissions&#x60;. |  [optional] |
|**collectionPermissions** | [**Map&lt;String, AppRoleCollectionPermissionValue&gt;**](AppRoleCollectionPermissionValue.md) | Per-collection CRUD map. Keys are collection slugs; values are action arrays or objects with &#x60;actions&#x60; + optional &#x60;conditions&#x60;. |  [optional] |
|**metadata** | **Object** |  |  [optional] |
|**featurePermissions** | **Map&lt;String, Map&lt;String, Boolean&gt;&gt;** | Per-role feature toggles for app JWTs: &#x60;{ [resource]: { [action]: boolean } }&#x60;. Use resource and action names that match the public API contract (see multi-role guide and simulate-permissions). **Messaging** accepts legacy keys (&#x60;email&#x60;, &#x60;sms&#x60;, &#x60;push&#x60;, …) and newer names (&#x60;send_email&#x60;, &#x60;send_sms&#x60;, …) as synonyms. Common resources: &#x60;messaging&#x60;, &#x60;integration&#x60;, &#x60;functions&#x60;, &#x60;data&#x60;, &#x60;search&#x60;, &#x60;usage&#x60;, &#x60;storage&#x60;, &#x60;chat&#x60;, &#x60;realtime&#x60;, &#x60;roleElevation&#x60;, &#x60;webhooks&#x60;.  |  [optional] |



