

# CalculateWalletFee200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | **String** | Request currency / native currency for the chain |  [optional] |
|**network** | **String** |  |  [optional] |
|**amount** | **BigDecimal** |  |  [optional] |
|**chain** | **String** | Chain id used for estimation |  [optional] |
|**networkFee** | **String** | Human-readable network fee from blockchain |  [optional] |
|**estimatedTime** | **String** |  |  [optional] |
|**congestion** | [**CongestionEnum**](#CongestionEnum) | Network congestion level (EVM from gas price; UTXO from sat/vB) |  [optional] |
|**gasLimit** | **String** | (EVM only) Gas limit |  [optional] |
|**gasPrice** | **String** | (EVM only) Gas price in wei |  [optional] |
|**gasPriceGwei** | **BigDecimal** | (EVM only) Gas price in Gwei |  [optional] |
|**estimatedCost** | **String** | (EVM only) Cost in wei |  [optional] |
|**satPerVb** | **Integer** | (UTXO only) Satoshis per vbyte |  [optional] |
|**feeSat** | **Integer** | (UTXO only) Fee in satoshis |  [optional] |
|**lamports** | **Integer** | (Solana only) Fee in lamports |  [optional] |
|**feeTiers** | [**Map&lt;String, CalculateWalletFee200ResponseDataFeeTiersValue&gt;**](CalculateWalletFee200ResponseDataFeeTiersValue.md) | (EVM only) slow / normal / fast tiers; each has gasPriceGwei, networkFee |  [optional] |
|**gasSpikeWarning** | **Boolean** | True when current gas is ≥5× chain minimum (consider warning user) |  [optional] |



## Enum: CongestionEnum

| Name | Value |
|---- | -----|
| LOW | &quot;low&quot; |
| NORMAL | &quot;normal&quot; |
| HIGH | &quot;high&quot; |



