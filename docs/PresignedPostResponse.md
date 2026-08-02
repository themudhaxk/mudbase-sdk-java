

# PresignedPostResponse


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**key** | **String** | Object key (S3) clients should upload to |  [optional] |
|**url** | **String** | Presigned URL to PUT the file body to directly |  [optional] |
|**method** | [**MethodEnum**](#MethodEnum) | HTTP method the client must use against &#x60;url&#x60; (always PUT - R2 does not implement the S3 POST Object API) |  [optional] |
|**headers** | **Object** | Headers the client must send with the PUT request (e.g. Content-Type) - mismatching these from what was signed causes a SignatureDoesNotMatch error |  [optional] |
|**expiresIn** | **Integer** | Expiration of the presigned URL in seconds |  [optional] |
|**maxFileUploadBytes** | **Long** | Maximum upload size in bytes for this org plan. Not enforced by the presigned URL itself (PUT has no content-length-range equivalent) - checked server-side by /api/files/upload/confirm after the upload completes |  [optional] |



## Enum: MethodEnum

| Name | Value |
|---- | -----|
| PUT | &quot;PUT&quot; |



