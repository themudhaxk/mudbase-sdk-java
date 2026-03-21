

# WalletWebhook

Wallet webhook config (id, url, events, chain, address, secret, isActive).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**url** | **URI** |  |  [optional] |
|**events** | [**List&lt;EventsEnum&gt;**](#List&lt;EventsEnum&gt;) |  |  [optional] |
|**filters** | [**WalletWebhookFilters**](WalletWebhookFilters.md) |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**stats** | [**WalletWebhookStats**](WalletWebhookStats.md) |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: List&lt;EventsEnum&gt;

| Name | Value |
|---- | -----|
| WALLET_BALANCE_UPDATED | &quot;wallet.balance.updated&quot; |
| WALLET_TRANSACTION_CONFIRMED | &quot;wallet.transaction.confirmed&quot; |
| WALLET_TRANSACTION_FAILED | &quot;wallet.transaction.failed&quot; |



