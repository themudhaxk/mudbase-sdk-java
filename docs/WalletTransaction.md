

# WalletTransaction

Wallet transaction record (txHash, address, chain, from, to, amount, status, confirmations, etc.).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**txHash** | **String** |  |  [optional] |
|**mainTxHash** | **String** |  |  [optional] |
|**address** | **String** |  |  [optional] |
|**chain** | **String** |  |  [optional] |
|**from** | **String** |  |  [optional] |
|**to** | **String** |  |  [optional] |
|**fromAddress** | **String** |  |  [optional] |
|**toAddress** | **String** |  |  [optional] |
|**amount** | **String** | Transaction amount (string to handle large numbers) |  [optional] |
|**currency** | **String** |  |  [optional] |
|**type** | **String** |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**mainTxStatus** | [**MainTxStatusEnum**](#MainTxStatusEnum) |  |  [optional] |
|**confirmations** | **Integer** |  |  [optional] |
|**blockNumber** | **Integer** |  |  [optional] |
|**blockHash** | **String** |  |  [optional] |
|**networkFee** | **String** | Network fee (string to handle large numbers) |  [optional] |
|**mainTxConfirmedAt** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| COMPLETED | &quot;completed&quot; |
| FAILED | &quot;failed&quot; |



## Enum: MainTxStatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| CONFIRMED | &quot;confirmed&quot; |
| FAILED | &quot;failed&quot; |



