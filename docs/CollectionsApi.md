# CollectionsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createCollection**](CollectionsApi.md#createCollection) | **POST** /api/schemas/projects/{projectId}/collections | Create new collection |
| [**deleteCollection**](CollectionsApi.md#deleteCollection) | **DELETE** /api/schemas/projects/{projectId}/collections/{collectionId} | Delete collection |
| [**getCollection**](CollectionsApi.md#getCollection) | **GET** /api/schemas/projects/{projectId}/collections/{collectionId} | Get single collection |
| [**listCollections**](CollectionsApi.md#listCollections) | **GET** /api/schemas/projects/{projectId}/collections | List collections in project |
| [**updateCollection**](CollectionsApi.md#updateCollection) | **PATCH** /api/schemas/projects/{projectId}/collections/{collectionId} | Update collection |


<a id="createCollection"></a>
# **createCollection**
> CreateCollection201Response createCollection(projectId, createCollectionRequest)

Create new collection

Create a new collection in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.CollectionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    CollectionsApi apiInstance = new CollectionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    CreateCollectionRequest createCollectionRequest = new CreateCollectionRequest(); // CreateCollectionRequest | 
    try {
      CreateCollection201Response result = apiInstance.createCollection(projectId, createCollectionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CollectionsApi#createCollection");
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
| **projectId** | **String**|  | |
| **createCollectionRequest** | [**CreateCollectionRequest**](CreateCollectionRequest.md)|  | |

### Return type

[**CreateCollection201Response**](CreateCollection201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Collection created |  -  |

<a id="deleteCollection"></a>
# **deleteCollection**
> MessageResponse deleteCollection(projectId, collectionId)

Delete collection

Delete a collection permanently. This is a destructive operation. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.CollectionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    CollectionsApi apiInstance = new CollectionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String collectionId = "collectionId_example"; // String | 
    try {
      MessageResponse result = apiInstance.deleteCollection(projectId, collectionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CollectionsApi#deleteCollection");
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
| **projectId** | **String**|  | |
| **collectionId** | **String**|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection deleted |  -  |

<a id="getCollection"></a>
# **getCollection**
> Collection getCollection(projectId, collectionId)

Get single collection

Get collection details by ID. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.CollectionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    CollectionsApi apiInstance = new CollectionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String collectionId = "collectionId_example"; // String | 
    try {
      Collection result = apiInstance.getCollection(projectId, collectionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CollectionsApi#getCollection");
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
| **projectId** | **String**|  | |
| **collectionId** | **String**|  | |

### Return type

[**Collection**](Collection.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection details |  -  |

<a id="listCollections"></a>
# **listCollections**
> ListCollections200Response listCollections(projectId)

List collections in project

List all collections in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.CollectionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    CollectionsApi apiInstance = new CollectionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      ListCollections200Response result = apiInstance.listCollections(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CollectionsApi#listCollections");
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
| **projectId** | **String**|  | |

### Return type

[**ListCollections200Response**](ListCollections200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collections list |  -  |

<a id="updateCollection"></a>
# **updateCollection**
> CreateCollection201Response updateCollection(projectId, collectionId, updateCollectionRequest)

Update collection

Update collection configuration (name, fields, permissions). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.CollectionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    CollectionsApi apiInstance = new CollectionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String collectionId = "collectionId_example"; // String | 
    UpdateCollectionRequest updateCollectionRequest = new UpdateCollectionRequest(); // UpdateCollectionRequest | 
    try {
      CreateCollection201Response result = apiInstance.updateCollection(projectId, collectionId, updateCollectionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling CollectionsApi#updateCollection");
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
| **projectId** | **String**|  | |
| **collectionId** | **String**|  | |
| **updateCollectionRequest** | [**UpdateCollectionRequest**](UpdateCollectionRequest.md)|  | |

### Return type

[**CreateCollection201Response**](CreateCollection201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection updated |  -  |

