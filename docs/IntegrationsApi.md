# IntegrationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**integrationsExecute**](IntegrationsApi.md#integrationsExecute) | **POST** /api/integrations/projects/{projectId}/integrations/{integrationId}/execute | Execute integration |
| [**integrationsList**](IntegrationsApi.md#integrationsList) | **GET** /api/integrations/projects/{projectId}/integrations | Get project integrations |


<a id="integrationsExecute"></a>
# **integrationsExecute**
> WalletTestWebhook200Response integrationsExecute(projectId, integrationId, integrationsExecuteRequest)

Execute integration

Execute an integration action (API call) with specified endpoint and parameters. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String integrationId = "integrationId_example"; // String | Integration ID to execute.
    IntegrationsExecuteRequest integrationsExecuteRequest = new IntegrationsExecuteRequest(); // IntegrationsExecuteRequest | Endpoint path, HTTP method, optional params and body for the integration call.
    try {
      WalletTestWebhook200Response result = apiInstance.integrationsExecute(projectId, integrationId, integrationsExecuteRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#integrationsExecute");
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
| **integrationId** | **String**| Integration ID to execute. | |
| **integrationsExecuteRequest** | [**IntegrationsExecuteRequest**](IntegrationsExecuteRequest.md)| Endpoint path, HTTP method, optional params and body for the integration call. | |

### Return type

[**WalletTestWebhook200Response**](WalletTestWebhook200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration executed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="integrationsList"></a>
# **integrationsList**
> IntegrationsList200Response integrationsList(projectId)

Get project integrations

List all integrations configured for a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    try {
      IntegrationsList200Response result = apiInstance.integrationsList(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#integrationsList");
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

### Return type

[**IntegrationsList200Response**](IntegrationsList200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integrations list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

