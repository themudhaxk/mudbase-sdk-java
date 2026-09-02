

# ApiKycWebhookConfigPutRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**webhookUrl** | **String** | Destination URL. Send null or empty string to clear. |  [optional] |
|**webhookSecret** | **String** | Explicit signing secret (min 16 chars). Send null or empty string to clear. |  [optional] |
|**generateSecret** | **Boolean** | When true, the server generates a new secret and returns it once. |  [optional] |



