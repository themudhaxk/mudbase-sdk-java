

# CreateWalletRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | [**CurrencyEnum**](#CurrencyEnum) | Currency. USDT requires network (ETH, BSC, TRX, SOL, POLYGON). All platform chains supported for testing non-custodial flows. |  |
|**projectId** | **String** | Optional project ID |  [optional] |
|**network** | **String** | Required for USDT; one of ETH, BSC, TRX, SOL, POLYGON |  [optional] |
|**privateKey** | **String** | Optional custom private key |  [optional] |
|**label** | **String** |  |  [optional] |



## Enum: CurrencyEnum

| Name | Value |
|---- | -----|
| BTC | &quot;BTC&quot; |
| LTC | &quot;LTC&quot; |
| DOGE | &quot;DOGE&quot; |
| ETH | &quot;ETH&quot; |
| CELO | &quot;CELO&quot; |
| SOL | &quot;SOL&quot; |
| TRX | &quot;TRX&quot; |
| TON | &quot;TON&quot; |
| MATIC | &quot;MATIC&quot; |
| BNB | &quot;BNB&quot; |
| AVAX | &quot;AVAX&quot; |
| ADA | &quot;ADA&quot; |
| USDT | &quot;USDT&quot; |



