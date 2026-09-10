

# DeviceRegisterRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**token** | **String** | The device push token issued to your app by its push client. |  |
|**platform** | [**PlatformEnum**](#PlatformEnum) | The device platform. Defaults to &#x60;unknown&#x60; when omitted or unrecognized. |  [optional] |



## Enum: PlatformEnum

| Name | Value |
|---- | -----|
| IOS | &quot;ios&quot; |
| ANDROID | &quot;android&quot; |
| WEB | &quot;web&quot; |
| UNKNOWN | &quot;unknown&quot; |



