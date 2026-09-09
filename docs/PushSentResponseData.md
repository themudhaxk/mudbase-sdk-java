

# PushSentResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**success** | **Boolean** | True when at least one recipient across any channel was delivered to. |  [optional] |
|**messageId** | **String** |  |  [optional] |
|**successCount** | **Integer** |  |  [optional] |
|**failureCount** | **Integer** |  |  [optional] |
|**channels** | [**PushSentResponseDataChannels**](PushSentResponseDataChannels.md) |  |  [optional] |
|**rejectedTokens** | **List&lt;String&gt;** | Device tokens that were passed but are not registered to the project, and so were dropped. Omitted when empty.  |  [optional] |



