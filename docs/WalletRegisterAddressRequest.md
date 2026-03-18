

# WalletRegisterAddressRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**address** | **String** | Public wallet address |  |
|**chain** | [**ChainEnum**](#ChainEnum) | Blockchain network (EVM, UTXO, or chain-specific). Use bsc or binance for BNB Smart Chain; avalanche for Avalanche C-Chain. |  |
|**derivationPath** | **String** | HD wallet derivation path (metadata only) |  [optional] |
|**label** | **String** | Optional label for the address |  [optional] |
|**projectId** | **String** | Optional project ID |  [optional] |



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
| RIPPLE | &quot;ripple&quot; |
| CARDANO | &quot;cardano&quot; |
| TON | &quot;ton&quot; |



