

# PresignedPostResponse

Presigned POST data for direct upload (key, url, fields, expiresIn).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**key** | **String** | Object key (S3) clients should upload to |  [optional] |
|**url** | **String** | URL to POST the multipart form to |  [optional] |
|**fields** | **Object** | Form fields required for the presigned POST (Policy, X-Amz-Signature, etc.) |  [optional] |
|**expiresIn** | **Integer** | Expiration of the presigned POST in seconds |  [optional] |



