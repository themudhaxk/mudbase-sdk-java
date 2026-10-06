

# FunctionExecutionResponse

Response from Execute function / Simulate trigger. Both endpoints are async (202) and only hand back an executionId — see FunctionExecutionStatusResponse for the real outcome. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**success** | **Boolean** |  |  [optional] |
|**data** | [**FunctionExecutionResponseData**](FunctionExecutionResponseData.md) |  |  [optional] |



