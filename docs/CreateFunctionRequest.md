

# CreateFunctionRequest

Payload to create a function (name, description, code, trigger, environment).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  |
|**description** | **String** |  |  [optional] |
|**code** | **String** | Function body (async, has access to payload, db, files, messaging, wallet, utils, env, console) |  |
|**trigger** | [**FunctionTrigger**](FunctionTrigger.md) |  |  |
|**environment** | **Map&lt;String, String&gt;** | Per-function env vars injected into sandbox |  [optional] |



