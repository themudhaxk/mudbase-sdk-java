

# MultiRoleUpdateSettingsRequestSettings

Feature toggles for signup behavior (not per-role approval flags).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**allowMultipleRoles** | **Boolean** | Whether an end user may hold multiple app roles. |  [optional] |
|**requireRoleSelection** | **Boolean** | If true, signup must pick a role; if false and &#x60;autoAssignDefault&#x60; is true, &#x60;defaultRole&#x60; is used when omitted. |  [optional] |
|**autoAssignDefault** | **Boolean** | When true, assigns &#x60;defaultRole&#x60; when the client does not specify a role at signup. |  [optional] |



