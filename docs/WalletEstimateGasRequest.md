

# WalletEstimateGasRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**chain** | [**ChainEnum**](#ChainEnum) | Chain id. For EVM, transaction is required. For non-EVM (UTXO, Solana, Tron, TON, Cardano) only chain is needed. |  |
|**transaction** | [**WalletEstimateGasRequestTransaction**](WalletEstimateGasRequestTransaction.md) |  |  [optional] |



## Enum: ChainEnum

| Name | Value |
|---- | -----|
| ETHEREUM | &quot;ethereum&quot; |
| BINANCE | &quot;binance&quot; |
| BSC | &quot;bsc&quot; |
| POLYGON | &quot;polygon&quot; |
| ARBITRUM | &quot;arbitrum&quot; |
| OPTIMISM | &quot;optimism&quot; |
| BASE | &quot;base&quot; |
| AVALANCHE | &quot;avalanche&quot; |
| CELO | &quot;celo&quot; |
| BITCOIN | &quot;bitcoin&quot; |
| LITECOIN | &quot;litecoin&quot; |
| DOGECOIN | &quot;dogecoin&quot; |
| SOLANA | &quot;solana&quot; |
| TRON | &quot;tron&quot; |
| TON | &quot;ton&quot; |
| CARDANO | &quot;cardano&quot; |



