

# NonCustodialAddress

Registered non-custodial wallet address (id, address, chain, label, projectId).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**address** | **String** |  |  [optional] |
|**chain** | [**ChainEnum**](#ChainEnum) |  |  [optional] |
|**org** | **String** |  |  [optional] |
|**project** | **String** |  |  [optional] |
|**derivationPath** | **String** |  |  [optional] |
|**label** | **String** |  |  [optional] |
|**isActive** | **Boolean** |  |  [optional] |
|**registeredAt** | **OffsetDateTime** |  |  [optional] |
|**lastSyncedAt** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: ChainEnum

| Name | Value |
|---- | -----|
| ETHEREUM | &quot;ethereum&quot; |
| BINANCE | &quot;binance&quot; |
| POLYGON | &quot;polygon&quot; |
| CELO | &quot;celo&quot; |
| BITCOIN | &quot;bitcoin&quot; |



