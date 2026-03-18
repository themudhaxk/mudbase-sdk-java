

# PaymentRefund

Payment refund record (id, paymentId, amount, status, reason, createdAt).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**paymentIntent** | **String** | Payment intent ID |  [optional] |
|**merchant** | **String** | Merchant ID |  [optional] |
|**amount** | **BigDecimal** | Refund amount |  [optional] |
|**reason** | **String** | Refund reason |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**isCrossChain** | **Boolean** | True if cross-chain refund |  [optional] |
|**sourceNetwork** | **String** | Source network for refund |  [optional] |
|**targetNetwork** | **String** | Target network for cross-chain refund |  [optional] |
|**approvedBy** | **String** | User ID who approved |  [optional] |
|**approvedAt** | **OffsetDateTime** |  |  [optional] |
|**refundTx** | **String** | Refund transaction hash |  [optional] |
|**refundedAt** | **OffsetDateTime** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| APPROVED | &quot;approved&quot; |
| REJECTED | &quot;rejected&quot; |
| PROCESSED | &quot;processed&quot; |
| FAILED | &quot;failed&quot; |



