

# ChatSendMessageRequestE2ee

Opaque end-to-end encrypted payload (base64 ciphertext). Server cannot decrypt. Only for type=text.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**version** | **Integer** |  |  [optional] |
|**scheme** | **String** |  |  [optional] |
|**ciphertext** | **String** | Base64-encoded ciphertext. |  [optional] |
|**nonce** | **String** |  |  [optional] |
|**ephemeralPublicKey** | **String** |  |  [optional] |
|**senderKeyId** | **String** |  |  [optional] |



