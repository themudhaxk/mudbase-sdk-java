

# WalletEstimateGasRequestTransaction

Required for EVM chains. Optional for non-EVM (ignored). Supports 1) Token transfer { from, tokenAddress, to, amount }, 2) Native transfer { from, to, value }, 3) Raw { from, to, value, data }. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**from** | **String** | Sender address |  |
|**to** | **String** | For native transfers: recipient address. For token transfers: recipient address (tokenAddress must be provided separately). For raw format: contract or recipient address.  |  [optional] |
|**value** | **String** | Amount in native currency (ETH/BNB/MATIC). Can be provided as decimal string (e.g., \&quot;1.0\&quot;) or wei string. Required for native transfers.  |  [optional] |
|**data** | **String** | Raw transaction data (hex string starting with 0x). Used for raw format or contract calls. For token transfers, this is auto-generated from tokenAddress, to, and amount.  |  [optional] |
|**tokenAddress** | **String** | Token contract address (for token transfers). When provided with &#39;amount&#39;, automatically encodes the transfer.  |  [optional] |
|**amount** | **String** | Token amount in human-readable format (e.g., \&quot;1.0\&quot; for 1 token). Used with tokenAddress for user-friendly token transfers. Automatically converted to token units based on token decimals.  |  [optional] |



