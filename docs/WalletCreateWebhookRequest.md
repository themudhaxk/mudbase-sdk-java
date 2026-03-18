

# WalletCreateWebhookRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**url** | **URI** |  |  |
|**events** | [**List&lt;EventsEnum&gt;**](#List&lt;EventsEnum&gt;) |  |  |
|**secret** | **String** | Optional webhook secret for HMAC signing |  [optional] |
|**filters** | [**WalletCreateWebhookRequestFilters**](WalletCreateWebhookRequestFilters.md) |  |  [optional] |
|**projectId** | **String** | Optional project ID |  [optional] |



## Enum: List&lt;EventsEnum&gt;

| Name | Value |
|---- | -----|
| WALLET_BALANCE_UPDATED | &quot;wallet.balance.updated&quot; |
| WALLET_TRANSACTION_CONFIRMED | &quot;wallet.transaction.confirmed&quot; |
| WALLET_TRANSACTION_FAILED | &quot;wallet.transaction.failed&quot; |
| WALLET_TRANSACTION_DETECTED | &quot;wallet.transaction.detected&quot; |
| WALLET_TRANSACTION_BROADCAST | &quot;wallet.transaction.broadcast&quot; |
| WALLET_TOKEN_BALANCE_UPDATED | &quot;wallet.token.balance.updated&quot; |
| WALLET_ADDRESS_CREATED | &quot;wallet.address.created&quot; |
| WALLET_ADDRESS_DEACTIVATED | &quot;wallet.address.deactivated&quot; |



