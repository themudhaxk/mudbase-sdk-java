

# PaymentIntent

Payment intent for checkout (id, amount, currency, status, etc.).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**paymentId** | **String** | Unique payment identifier |  [optional] |
|**merchant** | **String** | Merchant ID |  [optional] |
|**project** | **String** | Project ID |  [optional] |
|**amount** | **BigDecimal** | Payment amount |  [optional] |
|**currency** | **String** |  |  [optional] |
|**network** | [**NetworkEnum**](#NetworkEnum) |  |  [optional] |
|**token** | [**TokenEnum**](#TokenEnum) |  |  [optional] |
|**type** | [**TypeEnum**](#TypeEnum) |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**finalityStatus** | [**FinalityStatusEnum**](#FinalityStatusEnum) |  |  [optional] |
|**totalDue** | **BigDecimal** | Total amount due including fees |  [optional] |
|**commission** | **BigDecimal** | Platform commission |  [optional] |
|**merchantReceives** | **BigDecimal** | Amount merchant receives after commission |  [optional] |
|**expiresAt** | **OffsetDateTime** |  |  [optional] |
|**metadata** | **Object** | Additional metadata |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: NetworkEnum

| Name | Value |
|---- | -----|
| POLYGON | &quot;polygon&quot; |
| ARBITRUM | &quot;arbitrum&quot; |
| TRON | &quot;tron&quot; |
| SOLANA | &quot;solana&quot; |
| LIGHTNING | &quot;lightning&quot; |
| TON | &quot;ton&quot; |



## Enum: TokenEnum

| Name | Value |
|---- | -----|
| USDC | &quot;USDC&quot; |
| USDT | &quot;USDT&quot; |
| BTC | &quot;BTC&quot; |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| ONE_TIME | &quot;one_time&quot; |
| SUBSCRIPTION | &quot;subscription&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| CREATED | &quot;created&quot; |
| AWAITING_PAYMENT | &quot;awaiting_payment&quot; |
| PARTIALLY_PAID | &quot;partially_paid&quot; |
| CONFIRMED | &quot;confirmed&quot; |
| COMPLETED | &quot;completed&quot; |
| EXPIRED | &quot;expired&quot; |
| FAILED | &quot;failed&quot; |



## Enum: FinalityStatusEnum

| Name | Value |
|---- | -----|
| PENDING_CONFIRMATION | &quot;pending_confirmation&quot; |
| CONFIRMED | &quot;confirmed&quot; |
| FINALIZED | &quot;finalized&quot; |



