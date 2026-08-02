

# GetTransaction200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**type** | [**TypeEnum**](#TypeEnum) |  |  [optional] |
|**currency** | **String** |  |  [optional] |
|**amount** | **BigDecimal** |  |  [optional] |
|**toAddress** | **String** |  |  [optional] |
|**fromAddress** | **String** |  |  [optional] |
|**mainTxHash** | **String** |  |  [optional] |
|**mainTxStatus** | [**MainTxStatusEnum**](#MainTxStatusEnum) |  |  [optional] |
|**networkFee** | **BigDecimal** |  |  [optional] |
|**platformFee** | **BigDecimal** |  |  [optional] |
|**projectFee** | **BigDecimal** |  |  [optional] |
|**refundTxHash** | **String** |  |  [optional] |
|**refundStatus** | [**RefundStatusEnum**](#RefundStatusEnum) |  |  [optional] |
|**status** | [**StatusEnum**](#StatusEnum) |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| WITHDRAWAL | &quot;withdrawal&quot; |
| DEPOSIT | &quot;deposit&quot; |
| FEE_REFUND | &quot;fee_refund&quot; |
| PLATFORM_FEE_DEDUCTION | &quot;platform_fee_deduction&quot; |



## Enum: MainTxStatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| BROADCAST | &quot;broadcast&quot; |
| CONFIRMED | &quot;confirmed&quot; |
| FAILED | &quot;failed&quot; |



## Enum: RefundStatusEnum

| Name | Value |
|---- | -----|
| PENDING | &quot;pending&quot; |
| BROADCAST | &quot;broadcast&quot; |
| CONFIRMED | &quot;confirmed&quot; |
| FAILED | &quot;failed&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| PROCESSING | &quot;processing&quot; |
| COMPLETED | &quot;completed&quot; |
| PARTIAL | &quot;partial&quot; |
| FAILED | &quot;failed&quot; |



