# DataApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**dataCreate**](DataApi.md#dataCreate) | **POST** /api/data/projects/{projectId}/collections/{collectionId}/data | Create data in collection |
| [**dataDelete**](DataApi.md#dataDelete) | **DELETE** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Delete document |
| [**dataGet**](DataApi.md#dataGet) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Get single document |
| [**dataList**](DataApi.md#dataList) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data | List data in collection |
| [**dataUpdate**](DataApi.md#dataUpdate) | **PATCH** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Update document |


<a id="dataCreate"></a>
# **dataCreate**
> DataResponse dataCreate(projectId, collectionId, body)

Create data in collection

Create a new document in a collection. Request body must match the collection schema. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.DataApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    DataApi apiInstance = new DataApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String collectionId = "collectionId_example"; // String | Collection ID.
    Object body = {"email":"john.doe@example.com","firstName":"John","lastName":"Doe","role":"developer","status":"active"}; // Object | Document fields matching the collection schema.
    try {
      DataResponse result = apiInstance.dataCreate(projectId, collectionId, body);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling DataApi#dataCreate");
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
| **collectionId** | **String**| Collection ID. | |
| **body** | **Object**| Document fields matching the collection schema. | |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Data created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="dataDelete"></a>
# **dataDelete**
> MessageResponse dataDelete(projectId, collectionId, documentId)

Delete document

Delete a document from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.DataApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    DataApi apiInstance = new DataApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String collectionId = "collectionId_example"; // String | Collection ID.
    String documentId = "documentId_example"; // String | Document ID.
    try {
      MessageResponse result = apiInstance.dataDelete(projectId, collectionId, documentId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling DataApi#dataDelete");
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
| **collectionId** | **String**| Collection ID. | |
| **documentId** | **String**| Document ID. | |

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
| **200** | Data deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="dataGet"></a>
# **dataGet**
> DataResponse dataGet(projectId, collectionId, documentId)

Get single document

Get a document by ID from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.DataApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    DataApi apiInstance = new DataApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String collectionId = "collectionId_example"; // String | Collection ID.
    String documentId = "documentId_example"; // String | Document ID.
    try {
      DataResponse result = apiInstance.dataGet(projectId, collectionId, documentId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling DataApi#dataGet");
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
| **collectionId** | **String**| Collection ID. | |
| **documentId** | **String**| Document ID. | |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Document data |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="dataList"></a>
# **dataList**
> DataListResponse dataList(projectId, collectionId, page, limit, sort, filter)

List data in collection

List all documents in a collection with optional pagination, sort, and filter. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.DataApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    DataApi apiInstance = new DataApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String collectionId = "collectionId_example"; // String | Collection ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 20; // Integer | Number of documents per page.
    String sort = "-createdAt"; // String | Sort field and order (e.g. -createdAt, name).
    String filter = "filter_example"; // String | JSON string for filtering documents (e.g. {\"status\":\"active\"}).
    try {
      DataListResponse result = apiInstance.dataList(projectId, collectionId, page, limit, sort, filter);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling DataApi#dataList");
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
| **collectionId** | **String**| Collection ID. | |
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Number of documents per page. | [optional] [default to 20] |
| **sort** | **String**| Sort field and order (e.g. -createdAt, name). | [optional] [default to -createdAt] |
| **filter** | **String**| JSON string for filtering documents (e.g. {\&quot;status\&quot;:\&quot;active\&quot;}). | [optional] |

### Return type

[**DataListResponse**](DataListResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="dataUpdate"></a>
# **dataUpdate**
> DataResponse dataUpdate(projectId, collectionId, documentId, body)

Update document

Update a document in a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.DataApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    DataApi apiInstance = new DataApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String collectionId = "collectionId_example"; // String | Collection ID.
    String documentId = "documentId_example"; // String | Document ID.
    Object body = {"firstName":"Sarah","lastName":"Chen","email":"sarah.chen@example.com","role":"admin","status":"active"}; // Object | Partial document fields to update.
    try {
      DataResponse result = apiInstance.dataUpdate(projectId, collectionId, documentId, body);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling DataApi#dataUpdate");
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
| **collectionId** | **String**| Collection ID. | |
| **documentId** | **String**| Document ID. | |
| **body** | **Object**| Partial document fields to update. | |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

