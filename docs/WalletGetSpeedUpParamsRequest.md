

# WalletGetSpeedUpParamsRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**txId** | **String** | WalletTransaction _id (MongoDB ObjectId) |  [optional] |
|**txHash** | **String** | mainTxHash or txHash of the stuck transaction |  [optional] |
|**chain** | [**ChainEnum**](#ChainEnum) | EVM chain (speed-up is EVM only) |  |



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



