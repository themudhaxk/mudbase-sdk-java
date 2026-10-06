

# EnablePaymentProcessing200ResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**onboarded** | **Boolean** |  |  [optional] |
|**alreadyEnabled** | **Boolean** |  |  [optional] |
|**approvalStatus** | **String** | pending_review, approved, or rejected. Payments only start succeeding once this is approved, poll GET /payment-processing/status to track it. |  [optional] |



