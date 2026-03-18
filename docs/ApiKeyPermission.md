

# ApiKeyPermission

Permission scope (resource, actions).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**resource** | [**ResourceEnum**](#ResourceEnum) | Resource scope for this permission (auth, database, storage, functions, realtime, messaging) |  |
|**actions** | [**List&lt;ActionsEnum&gt;**](#List&lt;ActionsEnum&gt;) | Allowed actions on the resource |  |



## Enum: ResourceEnum

| Name | Value |
|---- | -----|
| AUTH | &quot;auth&quot; |
| DATABASE | &quot;database&quot; |
| STORAGE | &quot;storage&quot; |
| FUNCTIONS | &quot;functions&quot; |
| REALTIME | &quot;realtime&quot; |
| MESSAGING | &quot;messaging&quot; |



## Enum: List&lt;ActionsEnum&gt;

| Name | Value |
|---- | -----|
| CREATE | &quot;create&quot; |
| READ | &quot;read&quot; |
| UPDATE | &quot;update&quot; |
| DELETE | &quot;delete&quot; |



