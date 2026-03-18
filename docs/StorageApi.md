# StorageApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**storageConfirmUpload**](StorageApi.md#storageConfirmUpload) | **POST** /api/files/upload/confirm | Confirm direct upload (scan + finalize metadata) |
| [**storageCreateBucket**](StorageApi.md#storageCreateBucket) | **POST** /api/bucket/projects/{projectId}/buckets | Create a new bucket |
| [**storageDeleteBucket**](StorageApi.md#storageDeleteBucket) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId} | Delete bucket |
| [**storageDeleteFile**](StorageApi.md#storageDeleteFile) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Delete file |
| [**storageDownloadBucketFile**](StorageApi.md#storageDownloadBucketFile) | **GET** /api/bucket/files/{fileId}/download | Download file from bucket |
| [**storageDownloadFile**](StorageApi.md#storageDownloadFile) | **GET** /api/files/{fileId}/download | Generate a presigned URL for downloading a file |
| [**storageGetBucket**](StorageApi.md#storageGetBucket) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId} | Get bucket details |
| [**storageGetFile**](StorageApi.md#storageGetFile) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Get file metadata |
| [**storageGetPresignedUpload**](StorageApi.md#storageGetPresignedUpload) | **POST** /api/files/upload/presigned | Generate presigned POST data for direct browser upload |
| [**storageGetSignedUrl**](StorageApi.md#storageGetSignedUrl) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId}/signed-url | Generate signed URL for file |
| [**storageListBuckets**](StorageApi.md#storageListBuckets) | **GET** /api/bucket/projects/{projectId}/buckets | List buckets in a project |
| [**storageListFiles**](StorageApi.md#storageListFiles) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | List files in bucket |
| [**storageUpdateBucket**](StorageApi.md#storageUpdateBucket) | **PATCH** /api/bucket/projects/{projectId}/buckets/{bucketId} | Update bucket |
| [**storageUploadFiles**](StorageApi.md#storageUploadFiles) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | Upload files to bucket |


<a id="storageConfirmUpload"></a>
# **storageConfirmUpload**
> ConfirmUploadResponse storageConfirmUpload(storageConfirmUploadRequest)

Confirm direct upload (scan + finalize metadata)

After a client uploads directly to S3 using the presigned POST, call this endpoint to have the server scan the object, create the File record, and optionally quarantine if infected.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    StorageConfirmUploadRequest storageConfirmUploadRequest = new StorageConfirmUploadRequest(); // StorageConfirmUploadRequest | S3 key from presigned response, projectId, and optional originalName, contentType, size, bucket, isPublic.
    try {
      ConfirmUploadResponse result = apiInstance.storageConfirmUpload(storageConfirmUploadRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageConfirmUpload");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **storageConfirmUploadRequest** | [**StorageConfirmUploadRequest**](StorageConfirmUploadRequest.md)| S3 key from presigned response, projectId, and optional originalName, contentType, size, bucket, isPublic. | |

### Return type

[**ConfirmUploadResponse**](ConfirmUploadResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | File confirmed and metadata stored |  -  |
| **400** | Bad request or file quarantined |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageCreateBucket"></a>
# **storageCreateBucket**
> BucketResponse storageCreateBucket(projectId, createBucketRequest)

Create a new bucket

Create a new storage bucket in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    CreateBucketRequest createBucketRequest = new CreateBucketRequest(); // CreateBucketRequest | Bucket name, isPublic flag, and optional settings.
    try {
      BucketResponse result = apiInstance.storageCreateBucket(projectId, createBucketRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageCreateBucket");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **createBucketRequest** | [**CreateBucketRequest**](CreateBucketRequest.md)| Bucket name, isPublic flag, and optional settings. | |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Bucket created successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageDeleteBucket"></a>
# **storageDeleteBucket**
> MessageResponse storageDeleteBucket(projectId, bucketId)

Delete bucket

Delete a storage bucket permanently. This is a destructive operation that will also delete all files in the bucket. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    try {
      MessageResponse result = apiInstance.storageDeleteBucket(projectId, bucketId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageDeleteBucket");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bucket deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageDeleteFile"></a>
# **storageDeleteFile**
> MessageResponse storageDeleteFile(projectId, bucketId, fileId)

Delete file

Delete a file from a bucket permanently. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    String fileId = "fileId_example"; // String | File ID.
    try {
      MessageResponse result = apiInstance.storageDeleteFile(projectId, bucketId, fileId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageDeleteFile");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **fileId** | **String**| File ID. | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | File deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | File not found (exact backend message for file/storage endpoints). |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageDownloadBucketFile"></a>
# **storageDownloadBucketFile**
> File storageDownloadBucketFile(fileId, token)

Download file from bucket

Download a file from a bucket. For public files, no authentication is required. For private files, a download token (obtained via signed URL endpoint) is required in the query parameter. Accepts: Token-based authentication via query parameter (for private files), or no authentication (for public files). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String fileId = "685af8b85d73a104065b6a77"; // String | File ID to download.
    String token = "token_example"; // String | Download token for private files (from signed URL endpoint).
    try {
      File result = apiInstance.storageDownloadBucketFile(fileId, token);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageDownloadBucketFile");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **fileId** | **String**| File ID to download. | |
| **token** | **String**| Download token for private files (from signed URL endpoint). | [optional] |

### Return type

[**File**](File.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/octet-stream, application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | File download |  * Content-Type -  <br>  * Content-Length -  <br>  * Content-Disposition -  <br>  |
| **403** | Access denied or invalid token |  -  |
| **404** | File not found |  -  |

<a id="storageDownloadFile"></a>
# **storageDownloadFile**
> SignedUrlResponse storageDownloadFile(fileId, token)

Generate a presigned URL for downloading a file

Returns a time-limited provider-signed URL (S3) for direct download. Server enforces RBAC before issuing the URL.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String fileId = "fileId_example"; // String | File ID.
    String token = "token_example"; // String | Optional one-time download token (if provided by upload flow).
    try {
      SignedUrlResponse result = apiInstance.storageDownloadFile(fileId, token);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageDownloadFile");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **fileId** | **String**| File ID. | |
| **token** | **String**| Optional one-time download token (if provided by upload flow). | [optional] |

### Return type

[**SignedUrlResponse**](SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed URL generated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | File not found (exact backend message for file/storage endpoints). |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageGetBucket"></a>
# **storageGetBucket**
> BucketResponse storageGetBucket(projectId, bucketId)

Get bucket details

Retrieve metadata and configuration for a single storage bucket, including name, project, public/private status, and settings. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    try {
      BucketResponse result = apiInstance.storageGetBucket(projectId, bucketId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageGetBucket");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bucket details |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageGetFile"></a>
# **storageGetFile**
> FileResponse storageGetFile(projectId, bucketId, fileId)

Get file metadata

Get metadata for a specific file in a bucket. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    String fileId = "fileId_example"; // String | File ID.
    try {
      FileResponse result = apiInstance.storageGetFile(projectId, bucketId, fileId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageGetFile");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **fileId** | **String**| File ID. | |

### Return type

[**FileResponse**](FileResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | File metadata |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | File not found (exact backend message for file/storage endpoints). |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageGetPresignedUpload"></a>
# **storageGetPresignedUpload**
> PresignedPostResponse storageGetPresignedUpload(storageGetPresignedUploadRequest)

Generate presigned POST data for direct browser upload

Issue a presigned POST (fields + url) for clients to upload directly to S3. The server stores the issued key with expiry and RBAC is enforced.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    StorageGetPresignedUploadRequest storageGetPresignedUploadRequest = new StorageGetPresignedUploadRequest(); // StorageGetPresignedUploadRequest | projectId, originalName, optional bucket, contentType, isPublic.
    try {
      PresignedPostResponse result = apiInstance.storageGetPresignedUpload(storageGetPresignedUploadRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageGetPresignedUpload");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **storageGetPresignedUploadRequest** | [**StorageGetPresignedUploadRequest**](StorageGetPresignedUploadRequest.md)| projectId, originalName, optional bucket, contentType, isPublic. | |

### Return type

[**PresignedPostResponse**](PresignedPostResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presigned POST data |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageGetSignedUrl"></a>
# **storageGetSignedUrl**
> SignedUrlResponse storageGetSignedUrl(projectId, bucketId, fileId, storageGetSignedUrlRequest)

Generate signed URL for file

Generate a time-limited signed URL for downloading a private file. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    String fileId = "fileId_example"; // String | File ID.
    StorageGetSignedUrlRequest storageGetSignedUrlRequest = new StorageGetSignedUrlRequest(); // StorageGetSignedUrlRequest | Optional expiresIn (seconds) for the signed URL.
    try {
      SignedUrlResponse result = apiInstance.storageGetSignedUrl(projectId, bucketId, fileId, storageGetSignedUrlRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageGetSignedUrl");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **fileId** | **String**| File ID. | |
| **storageGetSignedUrlRequest** | [**StorageGetSignedUrlRequest**](StorageGetSignedUrlRequest.md)| Optional expiresIn (seconds) for the signed URL. | [optional] |

### Return type

[**SignedUrlResponse**](SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed URL generated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageListBuckets"></a>
# **storageListBuckets**
> BucketListResponse storageListBuckets(projectId, page, limit, search)

List buckets in a project

List all storage buckets in a project with pagination and search. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 20; // Integer | Number of buckets per page.
    String search = "search_example"; // String | Search by bucket name.
    try {
      BucketListResponse result = apiInstance.storageListBuckets(projectId, page, limit, search);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageListBuckets");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Number of buckets per page. | [optional] [default to 20] |
| **search** | **String**| Search by bucket name. | [optional] |

### Return type

[**BucketListResponse**](BucketListResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of buckets |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageListFiles"></a>
# **storageListFiles**
> FileListResponse storageListFiles(projectId, bucketId, page, limit, search, type)

List files in bucket

List files in a bucket with pagination, search, and optional type filter. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 20; // Integer | Number of files per page.
    String search = "search_example"; // String | Search by filename.
    String type = "type_example"; // String | Filter by MIME type or file type.
    try {
      FileListResponse result = apiInstance.storageListFiles(projectId, bucketId, page, limit, search, type);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageListFiles");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Number of files per page. | [optional] [default to 20] |
| **search** | **String**| Search by filename. | [optional] |
| **type** | **String**| Filter by MIME type or file type. | [optional] |

### Return type

[**FileListResponse**](FileListResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of files |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageUpdateBucket"></a>
# **storageUpdateBucket**
> BucketResponse storageUpdateBucket(projectId, bucketId, updateBucketRequest)

Update bucket

Update bucket configuration (name, public/private status, settings). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    UpdateBucketRequest updateBucketRequest = new UpdateBucketRequest(); // UpdateBucketRequest | Fields to update (name, isPublic, settings).
    try {
      BucketResponse result = apiInstance.storageUpdateBucket(projectId, bucketId, updateBucketRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageUpdateBucket");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **updateBucketRequest** | [**UpdateBucketRequest**](UpdateBucketRequest.md)| Fields to update (name, isPublic, settings). | |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bucket updated successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="storageUploadFiles"></a>
# **storageUploadFiles**
> FileUploadResponse storageUploadFiles(projectId, bucketId, uploadFilesToBucketRequest)

Upload files to bucket

Upload one or more files to a storage bucket using multipart/form-data. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.StorageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    StorageApi apiInstance = new StorageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String bucketId = "bucketId_example"; // String | Bucket ID.
    UploadFilesToBucketRequest uploadFilesToBucketRequest = new UploadFilesToBucketRequest(); // UploadFilesToBucketRequest | Use multipart/form-data for file upload (files required; optional folder, tags). application/json uses the same schema for metadata-only or tooling that prefers JSON.
    try {
      FileUploadResponse result = apiInstance.storageUploadFiles(projectId, bucketId, uploadFilesToBucketRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling StorageApi#storageUploadFiles");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **projectId** | **String**| Project ID. | |
| **bucketId** | **String**| Bucket ID. | |
| **uploadFilesToBucketRequest** | [**UploadFilesToBucketRequest**](UploadFilesToBucketRequest.md)| Use multipart/form-data for file upload (files required; optional folder, tags). application/json uses the same schema for metadata-only or tooling that prefers JSON. | |

### Return type

[**FileUploadResponse**](FileUploadResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json, multipart/form-data
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Files uploaded successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **409** | Resource conflict (e.g. \&quot;Project with this slug already exists\&quot;, \&quot;Webhook already succeeded\&quot;). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

