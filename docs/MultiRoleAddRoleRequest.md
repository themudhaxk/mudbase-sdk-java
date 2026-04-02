

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
|**collectionPermissions** | [**Map&lt;String, MultiRoleUpdateRoleRequestCollectionPermissionsValue&gt;**](MultiRoleUpdateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; values are action arrays or objects with &#x60;actions&#x60; + optional &#x60;conditions&#x60;. |  [optional] |
|**metadata** | **Object** |  |  [optional] |
|**featurePermissions** | **Map&lt;String, Map&lt;String, Boolean&gt;&gt;** | App JWT feature toggles on &#x60;MultiRoleFeature.roles[].featurePermissions&#x60;: &#x60;{ [resource]: { [action]: boolean } }&#x60;. Canonical &#x60;(resource, action)&#x60; pairs: &#x60;services/appRoleFeatureMap.js&#x60;. Inventory: &#x60;node scripts/verify-app-role-feature-map.js&#x60;. Messaging accepts legacy keys (&#x60;email&#x60;, &#x60;sms&#x60;, …) and newer names (&#x60;send_email&#x60;, …) per &#x60;appRoleFeatureService.js&#x60;. Resources: messaging, integration, functions, data, search, usage, storage, chat, realtime, roleElevation, webhooks — see table in &#x60;openapi.yaml&#x60; component &#x60;AppRoleFeaturePermissions&#x60;.  |  [optional] |



