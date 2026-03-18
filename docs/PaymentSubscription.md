

# PaymentSubscription

Subscription record (id, plan, status, currentPeriodEnd, etc.).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**merchant** | **String** | Merchant ID |  [optional] |
|**project** | **String** | Project ID |  [optional] |
|**amount** | **BigDecimal** | Subscription amount |  [optional] |
|**interval** | [**IntervalEnum**](#IntervalEnum) |  |  [optional] |
|**network** | [**NetworkEnum**](#NetworkEnum) |  |  [optional] |
|**token** | [**TokenEnum**](#TokenEnum) |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**nextPaymentAt** | **OffsetDateTime** | Next payment due date |  [optional] |
|**gracePeriodDays** | **Integer** | Grace period in days |  [optional] |
|**earlyPaymentAllowed** | **Boolean** |  |  [optional] |
|**latePaymentAllowed** | **Boolean** |  |  [optional] |
|**prorationEnabled** | **Boolean** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**updatedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: IntervalEnum

| Name | Value |
|---- | -----|
| MONTH | &quot;month&quot; |
| YEAR | &quot;year&quot; |



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



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| PAUSED | &quot;paused&quot; |
| CANCELLED | &quot;cancelled&quot; |
| EXPIRED | &quot;expired&quot; |



