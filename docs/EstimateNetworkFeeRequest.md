

# EstimateNetworkFeeRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | [**CurrencyEnum**](#CurrencyEnum) | Currency code |  |
|**amount** | **BigDecimal** | Transaction amount (used for display; fee is chain-based) |  |
|**network** | [**NetworkEnum**](#NetworkEnum) | Required for USDT; network on which USDT is sent |  [optional] |



## Enum: CurrencyEnum

| Name | Value |
|---- | -----|
| BTC | &quot;BTC&quot; |
| ETH | &quot;ETH&quot; |
| BNB | &quot;BNB&quot; |
| LTC | &quot;LTC&quot; |
| SOL | &quot;SOL&quot; |
| TRX | &quot;TRX&quot; |
| USDT | &quot;USDT&quot; |
| MATIC | &quot;MATIC&quot; |
| AVAX | &quot;AVAX&quot; |
| CELO | &quot;CELO&quot; |
| DOGE | &quot;DOGE&quot; |
| TON | &quot;TON&quot; |
| ADA | &quot;ADA&quot; |



## Enum: NetworkEnum

| Name | Value |
|---- | -----|
| ETH | &quot;ETH&quot; |
| BSC | &quot;BSC&quot; |
| TRX | &quot;TRX&quot; |
| SOL | &quot;SOL&quot; |
| POLYGON | &quot;POLYGON&quot; |



