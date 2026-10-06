

# AdminOrgBillingContractPatchRequest

At least one contract field required (excluding reason alone).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**contractAmountCents** | **Integer** |  |  [optional] |
|**contractCurrency** | **String** |  |  [optional] |
|**contractBillingInterval** | [**ContractBillingIntervalEnum**](#ContractBillingIntervalEnum) |  |  [optional] |
|**contractEffectiveFrom** | **OffsetDateTime** |  |  [optional] |
|**contractNotes** | **String** |  |  [optional] |
|**reason** | **String** |  |  [optional] |



## Enum: ContractBillingIntervalEnum

| Name | Value |
|---- | -----|
| MONTHLY | &quot;monthly&quot; |
| YEARLY | &quot;yearly&quot; |



