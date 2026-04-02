

# WalletBroadcastTransactionRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**chain** | [**ChainEnum**](#ChainEnum) | Blockchain for broadcast (EVM, UTXO, or chain-specific) |  |
|**signedTx** | **String** | Fully signed transaction (hex string) |  |
|**fromAddress** | **String** | Address that signed the transaction (must be registered) |  |



## Enum: ChainEnum

| Name | Value |
|---- | -----|
| ETHEREUM | &quot;ethereum&quot; |
| POLYGON | &quot;polygon&quot; |
| ARBITRUM | &quot;arbitrum&quot; |
| OPTIMISM | &quot;optimism&quot; |
| BASE | &quot;base&quot; |
| BSC | &quot;bsc&quot; |
| BINANCE | &quot;binance&quot; |
| AVALANCHE | &quot;avalanche&quot; |
| CELO | &quot;celo&quot; |
| BITCOIN | &quot;bitcoin&quot; |
| LITECOIN | &quot;litecoin&quot; |
| DOGECOIN | &quot;dogecoin&quot; |
| TRON | &quot;tron&quot; |
| SOLANA | &quot;solana&quot; |
| TON | &quot;ton&quot; |
| CARDANO | &quot;cardano&quot; |



