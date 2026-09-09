

# UpdateCollectionPermissionsRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**actions** | [**List&lt;ActionsEnum&gt;**](#List&lt;ActionsEnum&gt;) |  |  [optional] |
|**conditions** | **Object** |  |  [optional] |
|**dataScope** | [**DataScopeEnum**](#DataScopeEnum) | &#x60;all&#x60; &#x3D; no automatic row-owner filter. &#x60;own&#x60; &#x3D; only documents where the owner field matches the authenticated app user. |  [optional] |
|**ownerField** | **String** | Optional override for the document field when dataScope is &#x60;own&#x60; (default &#x60;settings.dataOwnerField&#x60;, usually &#x60;createdBy&#x60;). |  [optional] |



## Enum: List&lt;ActionsEnum&gt;

| Name | Value |
|---- | -----|
| CREATE | &quot;create&quot; |
| READ | &quot;read&quot; |
| UPDATE | &quot;update&quot; |
| DELETE | &quot;delete&quot; |



## Enum: DataScopeEnum

| Name | Value |
|---- | -----|
| ALL | &quot;all&quot; |
| OWN | &quot;own&quot; |



