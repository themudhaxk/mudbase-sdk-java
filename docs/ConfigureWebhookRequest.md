

# ConfigureWebhookRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**webhookUrl** | **URI** | URL to receive webhook payloads; set to null or omit to disable |  [optional] |
|**webhookSecret** | **String** | Optional secret for signing payloads (e.g. X-Webhook-Signature) |  [optional] |
|**webhookEvents** | **List&lt;String&gt;** | Event types to send (e.g. collection.insert, collection.update) |  [optional] |
|**webhookVersion** | **String** | Version string for payload format |  [optional] |
|**transformations** | [**List&lt;GetWebhookConfig200ResponseDataTransformationsInner&gt;**](GetWebhookConfig200ResponseDataTransformationsInner.md) | Transformation rules to apply to payloads before delivery |  [optional] |



