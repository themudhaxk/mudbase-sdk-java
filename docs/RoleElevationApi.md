# RoleElevationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**roleElevationGetStatus**](RoleElevationApi.md#roleElevationGetStatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**roleElevationRequest**](RoleElevationApi.md#roleElevationRequest) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**roleElevationUploadDocuments**](RoleElevationApi.md#roleElevationUploadDocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |


<a id="roleElevationGetStatus"></a>
# **roleElevationGetStatus**
> RoleElevationGetStatus200Response roleElevationGetStatus(projectId, roleSlug)

Get role elevation status

Get status of pending role elevation requests for current user

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RoleElevationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String roleSlug = "roleSlug_example"; // String | Optional filter by role slug.
    try {
      RoleElevationGetStatus200Response result = apiInstance.roleElevationGetStatus(projectId, roleSlug);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#roleElevationGetStatus");
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
| **roleSlug** | **String**| Optional filter by role slug. | [optional] |

### Return type

[**RoleElevationGetStatus200Response**](RoleElevationGetStatus200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of role elevation requests |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="roleElevationRequest"></a>
# **roleElevationRequest**
> RoleElevationRequest200Response roleElevationRequest(projectId, roleElevationRequestRequest)

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RoleElevationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    RoleElevationRequestRequest roleElevationRequestRequest = new RoleElevationRequestRequest(); // RoleElevationRequestRequest | Role slug to request elevation to (e.g. vendor).
    try {
      RoleElevationRequest200Response result = apiInstance.roleElevationRequest(projectId, roleElevationRequestRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#roleElevationRequest");
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
| **roleElevationRequestRequest** | [**RoleElevationRequestRequest**](RoleElevationRequestRequest.md)| Role slug to request elevation to (e.g. vendor). | |

### Return type

[**RoleElevationRequest200Response**](RoleElevationRequest200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role elevation request created or auto-approved |  -  |
| **400** | Invalid request or already has role |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Cannot request role with higher hierarchy |  -  |
| **404** | Role not found (exact backend message for role-elevation endpoints). |  -  |

<a id="roleElevationUploadDocuments"></a>
# **roleElevationUploadDocuments**
> roleElevationUploadDocuments(projectId, roleElevationUploadDocumentsRequest)

Upload verification documents

Upload KYC/verification documents for role elevation

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RoleElevationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    RoleElevationUploadDocumentsRequest roleElevationUploadDocumentsRequest = new RoleElevationUploadDocumentsRequest(); // RoleElevationUploadDocumentsRequest | Role slug and array of document objects (type, url).
    try {
      apiInstance.roleElevationUploadDocuments(projectId, roleElevationUploadDocumentsRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#roleElevationUploadDocuments");
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
| **roleElevationUploadDocumentsRequest** | [**RoleElevationUploadDocumentsRequest**](RoleElevationUploadDocumentsRequest.md)| Role slug and array of document objects (type, url). | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Documents uploaded successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

