

# SimulateAppPermissions200Response


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**success** | **Boolean** |  |  [optional] |
|**allowed** | **Boolean** |  |  [optional] |
|**reason** | [**ReasonEnum**](#ReasonEnum) |  |  [optional] |
|**evaluated** | **SimulateAppPermissions200ResponseEvaluated** |  |  [optional] |



## Enum: ReasonEnum

| Name | Value |
|---- | -----|
| ALLOWED | &quot;allowed&quot; |
| FEATURE_NOT_ALLOWED | &quot;feature_not_allowed&quot; |
| NO_FEATURE_GATE_FOR_PATH | &quot;no_feature_gate_for_path&quot; |
| NO_FEATURE_GATE_FOR_OPERATION_ID | &quot;no_feature_gate_for_operation_id&quot; |



