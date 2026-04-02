

# MultiRoleUpdateSettingsRequestSettings

Feature toggles for signup behavior (not per-role approval flags).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**allowMultipleRoles** | **Boolean** | Whether an end user may hold multiple app roles. |  [optional] |
|**requireRoleSelection** | **Boolean** | If true, signup must pick a role; if false and &#x60;autoAssignDefault&#x60; is true, &#x60;defaultRole&#x60; is used when omitted. |  [optional] |
|**autoAssignDefault** | **Boolean** | When true, assigns &#x60;defaultRole&#x60; when the client does not specify a role at signup. |  [optional] |
|**dataOwnerField** | **String** | Default document field for &#x60;dataScope: own&#x60; (e.g. &#x60;createdBy&#x60;, &#x60;userId&#x60;). |  [optional] |



