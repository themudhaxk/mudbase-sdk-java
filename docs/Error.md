

# Error

API error payload. The backend returns an **error** string (required); **code**, **details**, **timestamp**, **path**, and **requestId** are optional. The **error** message is exactly as returned by the backend and varies by endpoint (e.g. \"File not found\", \"Project not found\", \"Invalid token.\"). 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**error** | **String** | Exact error message from the backend |  |
|**code** | **String** |  |  [optional] |
|**details** | [**ErrorDetails**](ErrorDetails.md) |  |  [optional] |
|**timestamp** | **OffsetDateTime** |  |  [optional] |
|**path** | **String** |  |  [optional] |
|**requestId** | **String** |  |  [optional] |



