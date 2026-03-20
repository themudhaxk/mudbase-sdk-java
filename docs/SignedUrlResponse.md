

# SignedUrlResponse

Signed URL for temporary file access (url, expiresAt or expiresIn).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**success** | **Boolean** |  |  [optional] |
|**url** | **String** | Signed URL for file access |  [optional] |
|**expiresAt** | **OffsetDateTime** | Expiration time of the signed URL (optional - some endpoints return expiresIn instead) |  [optional] |
|**expiresIn** | **Integer** | Time-to-live in seconds for the signed URL (optional) |  [optional] |



