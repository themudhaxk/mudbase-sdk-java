

# Withdraw200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**transactionId** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**signedTx** | **String** | Signed transaction (hex for EVM/UTXO, base64 for Solana, object for Tron). Send as-is in broadcast body. |  [optional] |
|**chain** | **String** | Chain id for broadcast (e.g. ethereum, bitcoin, solana). |  [optional] |
|**fromAddress** | **String** | Sender address; must be registered for org when broadcasting. |  [optional] |
|**currency** | **String** |  |  [optional] |
|**amount** | **BigDecimal** |  |  [optional] |
|**toAddress** | **String** |  |  [optional] |
|**message** | **String** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| READY_TO_BROADCAST | &quot;ready_to_broadcast&quot; |



