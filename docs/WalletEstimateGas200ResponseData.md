

# WalletEstimateGas200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**chain** | **String** | Chain id (e.g. bsc, ethereum, bitcoin) |  [optional] |
|**gasLimit** | **String** | (EVM only) Estimated gas limit from RPC eth_estimateGas |  [optional] |
|**gasPrice** | **String** | (EVM only) Gas price in wei |  [optional] |
|**gasPriceGwei** | **BigDecimal** | (EVM only) Gas price in Gwei |  [optional] |
|**estimatedCost** | **String** | (EVM only) Total cost in wei (gasLimit * gasPrice) |  [optional] |
|**networkFee** | **String** | Human-readable network fee from blockchain (e.g. \&quot;0.00063 ETH\&quot;, \&quot;0.00001 BTC\&quot;) |  [optional] |
|**estimatedTime** | **String** | Estimated confirmation time when available |  [optional] |
|**currency** | **String** | Native currency for the chain (ETH, BNB, MATIC, BTC, SOL, TRX, etc.) |  [optional] |
|**satPerVb** | **Integer** | (UTXO only) Satoshis per virtual byte |  [optional] |
|**feeSat** | **Integer** | (UTXO only) Estimated fee in satoshis |  [optional] |
|**lamports** | **Integer** | (Solana only) Fee in lamports |  [optional] |



