

# CreateRoleRequestPermissionsInner


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**resource** | [**ResourceEnum**](#ResourceEnum) |  |  [optional] |
|**actions** | [**List&lt;ActionsEnum&gt;**](#List&lt;ActionsEnum&gt;) |  |  [optional] |
|**conditions** | **Object** |  |  [optional] |



## Enum: ResourceEnum

| Name | Value |
|---- | -----|
| PROJECT | &quot;project&quot; |
| COLLECTION | &quot;collection&quot; |
| DATA | &quot;data&quot; |
| FILE | &quot;file&quot; |
| API_KEY | &quot;api_key&quot; |
| ORG | &quot;org&quot; |
| MEMBER | &quot;member&quot; |
| ROLE | &quot;role&quot; |



## Enum: List&lt;ActionsEnum&gt;

| Name | Value |
|---- | -----|
| CREATE | &quot;create&quot; |
| READ | &quot;read&quot; |
| UPDATE | &quot;update&quot; |
| DELETE | &quot;delete&quot; |
| MANAGE | &quot;manage&quot; |



