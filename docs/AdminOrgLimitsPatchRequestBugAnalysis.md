

# AdminOrgLimitsPatchRequestBugAnalysis


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**scansPerMonth** | **Integer** |  |  [optional] |
|**maxUploadBytes** | **Integer** |  |  [optional] |
|**maxRuntimeMinutes** | **Integer** |  |  [optional] |
|**queueType** | [**QueueTypeEnum**](#QueueTypeEnum) |  |  [optional] |
|**logRetentionDays** | **Integer** |  |  [optional] |



## Enum: QueueTypeEnum

| Name | Value |
|---- | -----|
| NONE | &quot;none&quot; |
| STANDARD | &quot;standard&quot; |
| PRIORITY | &quot;priority&quot; |
| DEDICATED | &quot;dedicated&quot; |



