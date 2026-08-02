# FunctionsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**activateFunction**](FunctionsApi.md#activateFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**createFunction**](FunctionsApi.md#createFunction) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**deactivateFunction**](FunctionsApi.md#deactivateFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**deleteFunction**](FunctionsApi.md#deleteFunction) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**executeFunction**](FunctionsApi.md#executeFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**getFunction**](FunctionsApi.md#getFunction) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**getFunctionExecution**](FunctionsApi.md#getFunctionExecution) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId} | Get execution status |
| [**getFunctionLogs**](FunctionsApi.md#getFunctionLogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**getFunctionVersions**](FunctionsApi.md#getFunctionVersions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**listFunctions**](FunctionsApi.md#listFunctions) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**retryFunctionExecution**](FunctionsApi.md#retryFunctionExecution) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**rollbackFunction**](FunctionsApi.md#rollbackFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**simulateFunctionTrigger**](FunctionsApi.md#simulateFunctionTrigger) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**triggerFunctionWebhook**](FunctionsApi.md#triggerFunctionWebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**updateFunction**](FunctionsApi.md#updateFunction) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |


<a id="activateFunction"></a>
# **activateFunction**
> FunctionResponse activateFunction(projectId, functionId)

Activate function

Activate a deactivated function. Active functions can be triggered.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    try {
      FunctionResponse result = apiInstance.activateFunction(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#activateFunction");
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
| **functionId** | **String**|  | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function activated |  -  |

<a id="createFunction"></a>
# **createFunction**
> FunctionResponse createFunction(projectId, createFunctionRequest)

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, wallet, cron, messaging. Sandbox globals available today: &#x60;payload&#x60;, &#x60;context&#x60;, &#x60;env&#x60;, &#x60;console&#x60;. Function code runs in an isolated worker with no ambient network or database access — it can only read its trigger payload, the &#x60;env&#x60; vars you configure, and return a JSON-serializable result; it cannot yet call back into your project&#39;s database, storage, messaging, or wallet APIs from inside the function body. If you need to read or write project data from a function, call the regular REST API (with your own API key) from your own backend in response to the function&#39;s returned result, rather than from within the function&#39;s own code. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    CreateFunctionRequest createFunctionRequest = new CreateFunctionRequest(); // CreateFunctionRequest | 
    try {
      FunctionResponse result = apiInstance.createFunction(projectId, createFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#createFunction");
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
| **createFunctionRequest** | [**CreateFunctionRequest**](CreateFunctionRequest.md)|  | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Function created |  -  |

<a id="deactivateFunction"></a>
# **deactivateFunction**
> FunctionResponse deactivateFunction(projectId, functionId)

Deactivate function

Deactivate a function. Deactivated functions will not be triggered.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    try {
      FunctionResponse result = apiInstance.deactivateFunction(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#deactivateFunction");
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
| **functionId** | **String**|  | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deactivated |  -  |

<a id="deleteFunction"></a>
# **deleteFunction**
> DeleteFunction200Response deleteFunction(projectId, functionId)

Delete function

Delete a function permanently. This is a destructive operation.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    try {
      DeleteFunction200Response result = apiInstance.deleteFunction(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#deleteFunction");
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
| **functionId** | **String**|  | |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deleted |  -  |

<a id="executeFunction"></a>
# **executeFunction**
> FunctionExecutionResponse executeFunction(projectId, functionId, executeFunctionRequest)

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour.  This endpoint is asynchronous: it returns 202 immediately with an &#x60;executionId&#x60;, before the function has necessarily finished running. Poll &#x60;GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}&#x60; until &#x60;status&#x60; leaves &#x60;queued&#x60;/&#x60;running&#x60; to get the real result, error, and duration. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    ExecuteFunctionRequest executeFunctionRequest = new ExecuteFunctionRequest(); // ExecuteFunctionRequest | 
    try {
      FunctionExecutionResponse result = apiInstance.executeFunction(projectId, functionId, executeFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#executeFunction");
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
| **functionId** | **String**|  | |
| **executeFunctionRequest** | [**ExecuteFunctionRequest**](ExecuteFunctionRequest.md)|  | [optional] |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Execution accepted (queued or run synchronously) — poll the executions endpoint for the outcome |  -  |
| **400** | Payload exceeds the function&#39;s configured max payload size |  -  |
| **429** | Rate limit exceeded (maxExecutionsPerMinute/maxExecutionsPerHour, or the data-mutation rate limiter) |  -  |

<a id="getFunction"></a>
# **getFunction**
> FunctionResponse getFunction(projectId, functionId)

Get function

Get function details by ID including createdBy/updatedBy.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    try {
      FunctionResponse result = apiInstance.getFunction(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#getFunction");
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
| **functionId** | **String**|  | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function details |  -  |
| **404** | Function not found |  -  |

<a id="getFunctionExecution"></a>
# **getFunctionExecution**
> FunctionExecutionStatusResponse getFunctionExecution(projectId, functionId, executionId)

Get execution status

Poll this after Execute function or Simulate trigger to get the real outcome — both of those endpoints return 202 immediately and do not carry the result themselves. &#x60;status&#x60; is one of &#x60;queued&#x60;, &#x60;provisioning&#x60;, &#x60;running&#x60;, &#x60;success&#x60;, &#x60;failed&#x60;, &#x60;timeout&#x60;; &#x60;result&#x60;/&#x60;error&#x60;/&#x60;durationMs&#x60;/&#x60;logs&#x60; are only populated once &#x60;status&#x60; leaves &#x60;queued&#x60;/&#x60;running&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    String executionId = "executionId_example"; // String | 
    try {
      FunctionExecutionStatusResponse result = apiInstance.getFunctionExecution(projectId, functionId, executionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#getFunctionExecution");
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
| **functionId** | **String**|  | |
| **executionId** | **String**|  | |

### Return type

[**FunctionExecutionStatusResponse**](FunctionExecutionStatusResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Execution status |  -  |
| **404** | Execution not found |  -  |

<a id="getFunctionLogs"></a>
# **getFunctionLogs**
> FunctionLogsResponse getFunctionLogs(projectId, functionId, limit, offset)

Get function execution logs

Get execution logs with pagination. Includes stats (totalExecutions, successful, failed, successRate, avgExecutionTime, lastRun).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

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

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    Integer limit = 50; // Integer | 
    Integer offset = 0; // Integer | 
    try {
      FunctionLogsResponse result = apiInstance.getFunctionLogs(projectId, functionId, limit, offset);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#getFunctionLogs");
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
| **functionId** | **String**|  | |
| **limit** | **Integer**|  | [optional] [default to 50] |
| **offset** | **Integer**|  | [optional] [default to 0] |

### Return type

[**FunctionLogsResponse**](FunctionLogsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function logs and stats |  -  |

<a id="getFunctionVersions"></a>
# **getFunctionVersions**
> GetFunctionVersions200Response getFunctionVersions(projectId, functionId)

Get function versions

List all code versions for a function. Used for rollback.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    try {
      GetFunctionVersions200Response result = apiInstance.getFunctionVersions(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#getFunctionVersions");
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
| **functionId** | **String**|  | |

### Return type

[**GetFunctionVersions200Response**](GetFunctionVersions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function versions |  -  |
| **404** | Function not found |  -  |

<a id="listFunctions"></a>
# **listFunctions**
> FunctionListResponse listFunctions(projectId, page, limit, search, triggerType, isActive)

List functions

List serverless functions in a project with optional search and filters. Supports trigger types: http, event, document, file, webhook, wallet, cron, messaging. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String search = "search_example"; // String | Search by name or description
    String triggerType = "http"; // String | Filter by trigger type
    Boolean isActive = true; // Boolean | Filter by active status (true/false)
    try {
      FunctionListResponse result = apiInstance.listFunctions(projectId, page, limit, search, triggerType, isActive);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#listFunctions");
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
| **page** | **Integer**|  | [optional] [default to 1] |
| **limit** | **Integer**|  | [optional] [default to 20] |
| **search** | **String**| Search by name or description | [optional] |
| **triggerType** | **String**| Filter by trigger type | [optional] [enum: http, event, document, file, webhook, wallet, cron, messaging] |
| **isActive** | **Boolean**| Filter by active status (true/false) | [optional] |

### Return type

[**FunctionListResponse**](FunctionListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions list |  -  |

<a id="retryFunctionExecution"></a>
# **retryFunctionExecution**
> FunctionExecutionResponse retryFunctionExecution(projectId, functionId, executionIndex)

Retry failed execution

Retry a failed execution by its index (0-based) in the logs. Cannot retry successful executions.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    Integer executionIndex = 56; // Integer | 0-based index of the execution in logs
    try {
      FunctionExecutionResponse result = apiInstance.retryFunctionExecution(projectId, functionId, executionIndex);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#retryFunctionExecution");
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
| **functionId** | **String**|  | |
| **executionIndex** | **Integer**| 0-based index of the execution in logs | |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry result |  -  |
| **400** | Cannot retry successful execution |  -  |
| **404** | Function or execution not found |  -  |

<a id="rollbackFunction"></a>
# **rollbackFunction**
> FunctionResponse rollbackFunction(projectId, functionId, rollbackFunctionRequest)

Rollback to previous version

Rollback function code to a previous version. Version number is required.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    RollbackFunctionRequest rollbackFunctionRequest = new RollbackFunctionRequest(); // RollbackFunctionRequest | 
    try {
      FunctionResponse result = apiInstance.rollbackFunction(projectId, functionId, rollbackFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#rollbackFunction");
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
| **functionId** | **String**|  | |
| **rollbackFunctionRequest** | [**RollbackFunctionRequest**](RollbackFunctionRequest.md)|  | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function rolled back |  -  |
| **400** | Version number is required |  -  |
| **404** | Function or version not found |  -  |

<a id="simulateFunctionTrigger"></a>
# **simulateFunctionTrigger**
> FunctionExecutionResponse simulateFunctionTrigger(projectId, functionId, simulateFunctionTriggerRequest)

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, wallet, or cron payloads. Executes the function with the provided eventContext merged into the payload.  Asynchronous, same pattern as Execute function: returns 202 immediately with an &#x60;executionId&#x60;. Poll &#x60;GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}&#x60; for the real result. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    SimulateFunctionTriggerRequest simulateFunctionTriggerRequest = new SimulateFunctionTriggerRequest(); // SimulateFunctionTriggerRequest | 
    try {
      FunctionExecutionResponse result = apiInstance.simulateFunctionTrigger(projectId, functionId, simulateFunctionTriggerRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#simulateFunctionTrigger");
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
| **functionId** | **String**|  | |
| **simulateFunctionTriggerRequest** | [**SimulateFunctionTriggerRequest**](SimulateFunctionTriggerRequest.md)|  | [optional] |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Simulation accepted — poll the executions endpoint for the outcome |  -  |
| **404** | Function not found or inactive |  -  |

<a id="triggerFunctionWebhook"></a>
# **triggerFunctionWebhook**
> TriggerFunctionWebhook200Response triggerFunctionWebhook(projectId, xWebhookSecret, body)

Trigger webhook functions

Public endpoint for external services to trigger functions with &#x60;trigger.type: webhook&#x60;. No authentication required. Optionally verify using &#x60;X-Webhook-Secret&#x60; header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 120 requests per 15 minutes per IP (per-org adjustable). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String xWebhookSecret = "xWebhookSecret_example"; // String | Optional webhook secret for verification
    Object body = {"event":"user.created","userId":"507f1f77bcf86cd799439011","timestamp":"2026-04-03T12:00:00.000Z"}; // Object | 
    try {
      TriggerFunctionWebhook200Response result = apiInstance.triggerFunctionWebhook(projectId, xWebhookSecret, body);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#triggerFunctionWebhook");
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
| **xWebhookSecret** | **String**| Optional webhook secret for verification | [optional] |
| **body** | **Object**|  | [optional] |

### Return type

[**TriggerFunctionWebhook200Response**](TriggerFunctionWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, application/x-www-form-urlencoded, text/plain
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions triggered successfully |  -  |
| **400** | Invalid project ID |  -  |
| **401** | Invalid webhook secret |  -  |
| **404** | Project not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="updateFunction"></a>
# **updateFunction**
> FunctionResponse updateFunction(projectId, functionId, updateFunctionRequest)

Update function

Update function configuration. Code changes are versioned automatically.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.FunctionsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String functionId = "functionId_example"; // String | 
    UpdateFunctionRequest updateFunctionRequest = new UpdateFunctionRequest(); // UpdateFunctionRequest | 
    try {
      FunctionResponse result = apiInstance.updateFunction(projectId, functionId, updateFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#updateFunction");
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
| **functionId** | **String**|  | |
| **updateFunctionRequest** | [**UpdateFunctionRequest**](UpdateFunctionRequest.md)|  | [optional] |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function updated |  -  |
| **404** | Function not found |  -  |

