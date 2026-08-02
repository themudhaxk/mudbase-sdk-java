

# RestoreBackupRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**restoreMode** | [**RestoreModeEnum**](#RestoreModeEnum) |  |  [optional] |
|**collections** | **List&lt;String&gt;** | Optional: specific collections to restore |  [optional] |
|**confirmation** | [**ConfirmationEnum**](#ConfirmationEnum) |  |  |



## Enum: RestoreModeEnum

| Name | Value |
|---- | -----|
| REPLACE | &quot;replace&quot; |
| MERGE | &quot;merge&quot; |



## Enum: ConfirmationEnum

| Name | Value |
|---- | -----|
| RESTORE_DATA | &quot;RESTORE_DATA&quot; |



