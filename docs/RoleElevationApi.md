# RoleElevationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**approveRoleElevation**](RoleElevationApi.md#approveRoleElevation) | **POST** /api/orgs/{orgId}/role-elevation/{requestId}/approve | Approve/reject role elevation request (admin only) |
| [**getPendingRoleElevationRequests**](RoleElevationApi.md#getPendingRoleElevationRequests) | **GET** /api/orgs/{orgId}/role-elevation/pending | Get pending role elevation requests (admin only) |
| [**getRoleElevationStatus**](RoleElevationApi.md#getRoleElevationStatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**requestRoleElevation**](RoleElevationApi.md#requestRoleElevation) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**uploadVerificationDocuments**](RoleElevationApi.md#uploadVerificationDocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |


<a id="approveRoleElevation"></a>
# **approveRoleElevation**
> ApproveRoleElevation200Response approveRoleElevation(orgId, requestId, approveRoleElevationRequest)

Approve/reject role elevation request (admin only)

Admin approves or rejects a role elevation request

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RoleElevationApi;

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

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String requestId = "requestId_example"; // String | 
    ApproveRoleElevationRequest approveRoleElevationRequest = new ApproveRoleElevationRequest(); // ApproveRoleElevationRequest | 
    try {
      ApproveRoleElevation200Response result = apiInstance.approveRoleElevation(orgId, requestId, approveRoleElevationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#approveRoleElevation");
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
| **orgId** | **String**|  | |
| **requestId** | **String**|  | |
| **approveRoleElevationRequest** | [**ApproveRoleElevationRequest**](ApproveRoleElevationRequest.md)|  | |

### Return type

[**ApproveRoleElevation200Response**](ApproveRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Request approved/rejected |  -  |
| **400** | Requirements not met |  -  |
| **403** | Insufficient permissions |  -  |
| **404** | Request not found |  -  |

<a id="getPendingRoleElevationRequests"></a>
# **getPendingRoleElevationRequests**
> GetPendingRoleElevationRequests200Response getPendingRoleElevationRequests(orgId, status, page, limit)

Get pending role elevation requests (admin only)

Get all pending role elevation requests requiring admin approval

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RoleElevationApi;

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

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String status = "pending"; // String | 
    Integer page = 1; // Integer | 
    Integer limit = 50; // Integer | 
    try {
      GetPendingRoleElevationRequests200Response result = apiInstance.getPendingRoleElevationRequests(orgId, status, page, limit);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#getPendingRoleElevationRequests");
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
| **orgId** | **String**|  | |
| **status** | **String**|  | [optional] [default to pending] [enum: pending, approved, rejected] |
| **page** | **Integer**|  | [optional] [default to 1] |
| **limit** | **Integer**|  | [optional] [default to 50] |

### Return type

[**GetPendingRoleElevationRequests200Response**](GetPendingRoleElevationRequests200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of pending requests |  -  |
| **403** | Insufficient permissions |  -  |

<a id="getRoleElevationStatus"></a>
# **getRoleElevationStatus**
> GetRoleElevationStatus200Response getRoleElevationStatus(projectId, roleSlug)

Get role elevation status

Get status of pending role elevation requests for current user

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RoleElevationApi;

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

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String roleSlug = "roleSlug_example"; // String | 
    try {
      GetRoleElevationStatus200Response result = apiInstance.getRoleElevationStatus(projectId, roleSlug);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#getRoleElevationStatus");
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
| **roleSlug** | **String**|  | [optional] |

### Return type

[**GetRoleElevationStatus200Response**](GetRoleElevationStatus200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of role elevation requests |  -  |

<a id="requestRoleElevation"></a>
# **requestRoleElevation**
> RequestRoleElevation200Response requestRoleElevation(projectId, requestRoleElevationRequest)

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RoleElevationApi;

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

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    RequestRoleElevationRequest requestRoleElevationRequest = new RequestRoleElevationRequest(); // RequestRoleElevationRequest | 
    try {
      RequestRoleElevation200Response result = apiInstance.requestRoleElevation(projectId, requestRoleElevationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#requestRoleElevation");
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
| **requestRoleElevationRequest** | [**RequestRoleElevationRequest**](RequestRoleElevationRequest.md)|  | |

### Return type

[**RequestRoleElevation200Response**](RequestRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role elevation request created or auto-approved |  -  |
| **400** | Invalid request or already has role |  -  |
| **403** | Cannot request role with higher hierarchy |  -  |
| **404** | Role not found |  -  |

<a id="uploadVerificationDocuments"></a>
# **uploadVerificationDocuments**
> uploadVerificationDocuments(projectId, uploadVerificationDocumentsRequest)

Upload verification documents

Upload KYC/verification documents for role elevation

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RoleElevationApi;

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

    RoleElevationApi apiInstance = new RoleElevationApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    UploadVerificationDocumentsRequest uploadVerificationDocumentsRequest = new UploadVerificationDocumentsRequest(); // UploadVerificationDocumentsRequest | 
    try {
      apiInstance.uploadVerificationDocuments(projectId, uploadVerificationDocumentsRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling RoleElevationApi#uploadVerificationDocuments");
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
| **uploadVerificationDocumentsRequest** | [**UploadVerificationDocumentsRequest**](UploadVerificationDocumentsRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Documents uploaded successfully |  -  |

