

# ConfirmUploadResponse

Result of upload confirmation (fileId, status, scan).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**fileId** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**scan** | [**ConfirmUploadResponseScan**](ConfirmUploadResponseScan.md) |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| OK | &quot;ok&quot; |
| QUARANTINED | &quot;quarantined&quot; |
| ERROR | &quot;error&quot; |



