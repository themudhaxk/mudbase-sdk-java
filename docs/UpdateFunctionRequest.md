

# UpdateFunctionRequest

Fields to update on a function (name, description, code, trigger, environment, isActive, limits, retryPolicy).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  [optional] |
|**description** | **String** |  |  [optional] |
|**code** | **String** |  |  [optional] |
|**trigger** | [**FunctionTrigger**](FunctionTrigger.md) |  |  [optional] |
|**environment** | **Object** |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**limits** | [**UpdateFunctionRequestLimits**](UpdateFunctionRequestLimits.md) |  |  [optional] |
|**retryPolicy** | [**UpdateFunctionRequestRetryPolicy**](UpdateFunctionRequestRetryPolicy.md) |  |  [optional] |
|**versionComment** | **String** | Comment for version when code is updated |  [optional] |



