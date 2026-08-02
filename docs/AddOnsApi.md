# AddOnsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**apiAddonsGet**](AddOnsApi.md#apiAddonsGet) | **GET** /api/addons | List the add-on catalog |
| [**apiProjectsProjectIdAddonsAddonInvokePost**](AddOnsApi.md#apiProjectsProjectIdAddonsAddonInvokePost) | **POST** /api/projects/{projectId}/addons/{addon}/invoke | Invoke an add-on for a project |
| [**apiProjectsProjectIdAddonsJobsIdGet**](AddOnsApi.md#apiProjectsProjectIdAddonsJobsIdGet) | **GET** /api/projects/{projectId}/addons/jobs/{id} | Get an add-on job status |


<a id="apiAddonsGet"></a>
# **apiAddonsGet**
> ApiAddonsGet200Response apiAddonsGet()

List the add-on catalog

Returns the available add-ons (key, metadata, pricing) the caller can invoke.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AddOnsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    AddOnsApi apiInstance = new AddOnsApi(defaultClient);
    try {
      ApiAddonsGet200Response result = apiInstance.apiAddonsGet();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AddOnsApi#apiAddonsGet");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**ApiAddonsGet200Response**](ApiAddonsGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on catalog |  -  |
| **401** | Authentication required |  -  |

<a id="apiProjectsProjectIdAddonsAddonInvokePost"></a>
# **apiProjectsProjectIdAddonsAddonInvokePost**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response apiProjectsProjectIdAddonsAddonInvokePost(projectId, addon, body)

Invoke an add-on for a project

Runs the named add-on against the project. Returns the job synchronously (200) when it completes immediately, or 202 with a pending job when processing continues in the background.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AddOnsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    AddOnsApi apiInstance = new AddOnsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String addon = "addon_example"; // String | Add-on key from the catalog.
    Object body = null; // Object | 
    try {
      ApiProjectsProjectIdAddonsAddonInvokePost200Response result = apiInstance.apiProjectsProjectIdAddonsAddonInvokePost(projectId, addon, body);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AddOnsApi#apiProjectsProjectIdAddonsAddonInvokePost");
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
| **addon** | **String**| Add-on key from the catalog. | |
| **body** | **Object**|  | [optional] |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on job completed |  -  |
| **202** | Add-on job accepted and processing |  -  |
| **400** | Invalid add-on key or input |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |

<a id="apiProjectsProjectIdAddonsJobsIdGet"></a>
# **apiProjectsProjectIdAddonsJobsIdGet**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response apiProjectsProjectIdAddonsJobsIdGet(projectId, id)

Get an add-on job status

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AddOnsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    AddOnsApi apiInstance = new AddOnsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String id = "id_example"; // String | Add-on job id.
    try {
      ApiProjectsProjectIdAddonsAddonInvokePost200Response result = apiInstance.apiProjectsProjectIdAddonsJobsIdGet(projectId, id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AddOnsApi#apiProjectsProjectIdAddonsJobsIdGet");
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
| **id** | **String**| Add-on job id. | |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The add-on job |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |
| **404** | Add-on job not found |  -  |

