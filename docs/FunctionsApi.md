# FunctionsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**functionsActivate**](FunctionsApi.md#functionsActivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**functionsCreate**](FunctionsApi.md#functionsCreate) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**functionsDeactivate**](FunctionsApi.md#functionsDeactivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**functionsDelete**](FunctionsApi.md#functionsDelete) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**functionsExecute**](FunctionsApi.md#functionsExecute) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**functionsGet**](FunctionsApi.md#functionsGet) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**functionsGetLogs**](FunctionsApi.md#functionsGetLogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**functionsGetVersions**](FunctionsApi.md#functionsGetVersions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**functionsList**](FunctionsApi.md#functionsList) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**functionsRetry**](FunctionsApi.md#functionsRetry) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**functionsRollback**](FunctionsApi.md#functionsRollback) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**functionsSimulate**](FunctionsApi.md#functionsSimulate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**functionsTriggerWebhook**](FunctionsApi.md#functionsTriggerWebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**functionsUpdate**](FunctionsApi.md#functionsUpdate) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |


<a id="functionsActivate"></a>
# **functionsActivate**
> FunctionResponse functionsActivate(projectId, functionId)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to activate.
    try {
      FunctionResponse result = apiInstance.functionsActivate(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsActivate");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to activate. | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function activated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsCreate"></a>
# **functionsCreate**
> FunctionResponse functionsCreate(projectId, createFunctionRequest)

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, wallet, cron, messaging. Sandbox utilities available: db, files, messaging, wallet, utils, env, console. 

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    CreateFunctionRequest createFunctionRequest = new CreateFunctionRequest(); // CreateFunctionRequest | Function name, description, code, trigger config, and optional environment.
    try {
      FunctionResponse result = apiInstance.functionsCreate(projectId, createFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsCreate");
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
| **createFunctionRequest** | [**CreateFunctionRequest**](CreateFunctionRequest.md)| Function name, description, code, trigger config, and optional environment. | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Function created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsDeactivate"></a>
# **functionsDeactivate**
> FunctionResponse functionsDeactivate(projectId, functionId)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to deactivate.
    try {
      FunctionResponse result = apiInstance.functionsDeactivate(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsDeactivate");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to deactivate. | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deactivated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsDelete"></a>
# **functionsDelete**
> FunctionsDelete200Response functionsDelete(projectId, functionId)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String functionId = "functionId_example"; // String | Function ID to delete.
    try {
      FunctionsDelete200Response result = apiInstance.functionsDelete(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsDelete");
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
| **functionId** | **String**| Function ID to delete. | |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsExecute"></a>
# **functionsExecute**
> FunctionExecutionResponse functionsExecute(projectId, functionId, functionsExecuteRequest)

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour. 

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to execute.
    FunctionsExecuteRequest functionsExecuteRequest = new FunctionsExecuteRequest(); // FunctionsExecuteRequest | Optional JSON payload merged with trigger context (e.g. document, file, webhook body). Omit for no custom input.
    try {
      FunctionExecutionResponse result = apiInstance.functionsExecute(projectId, functionId, functionsExecuteRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsExecute");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to execute. | |
| **functionsExecuteRequest** | [**FunctionsExecuteRequest**](FunctionsExecuteRequest.md)| Optional JSON payload merged with trigger context (e.g. document, file, webhook body). Omit for no custom input. | [optional] |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function executed successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="functionsGet"></a>
# **functionsGet**
> FunctionResponse functionsGet(projectId, functionId)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String functionId = "functionId_example"; // String | Function ID.
    try {
      FunctionResponse result = apiInstance.functionsGet(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsGet");
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
| **functionId** | **String**| Function ID. | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

<a id="functionsGetLogs"></a>
# **functionsGetLogs**
> FunctionLogsResponse functionsGetLogs(projectId, functionId, limit, offset)

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
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to get logs for.
    Integer limit = 50; // Integer | Maximum number of log entries to return.
    Integer offset = 0; // Integer | Number of log entries to skip for pagination.
    try {
      FunctionLogsResponse result = apiInstance.functionsGetLogs(projectId, functionId, limit, offset);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsGetLogs");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to get logs for. | |
| **limit** | **Integer**| Maximum number of log entries to return. | [optional] [default to 50] |
| **offset** | **Integer**| Number of log entries to skip for pagination. | [optional] [default to 0] |

### Return type

[**FunctionLogsResponse**](FunctionLogsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function logs and stats |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsGetVersions"></a>
# **functionsGetVersions**
> FunctionsGetVersions200Response functionsGetVersions(projectId, functionId)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to list versions for.
    try {
      FunctionsGetVersions200Response result = apiInstance.functionsGetVersions(projectId, functionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsGetVersions");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to list versions for. | |

### Return type

[**FunctionsGetVersions200Response**](FunctionsGetVersions200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function versions |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

<a id="functionsList"></a>
# **functionsList**
> FunctionListResponse functionsList(projectId, page, limit, search, triggerType, isActive)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 20; // Integer | Number of functions per page.
    String search = "search_example"; // String | Search by name or description
    String triggerType = "http"; // String | Filter by trigger type
    Boolean isActive = true; // Boolean | Filter by active status (true/false)
    try {
      FunctionListResponse result = apiInstance.functionsList(projectId, page, limit, search, triggerType, isActive);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsList");
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
| **limit** | **Integer**| Number of functions per page. | [optional] [default to 20] |
| **search** | **String**| Search by name or description | [optional] |
| **triggerType** | **String**| Filter by trigger type | [optional] [enum: http, event, document, file, webhook, wallet, cron, messaging] |
| **isActive** | **Boolean**| Filter by active status (true/false) | [optional] |

### Return type

[**FunctionListResponse**](FunctionListResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsRetry"></a>
# **functionsRetry**
> FunctionExecutionResponse functionsRetry(projectId, functionId, executionIndex)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to retry execution for.
    Integer executionIndex = 56; // Integer | 0-based index of the execution in logs
    try {
      FunctionExecutionResponse result = apiInstance.functionsRetry(projectId, functionId, executionIndex);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsRetry");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to retry execution for. | |
| **executionIndex** | **Integer**| 0-based index of the execution in logs | |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry result |  -  |
| **400** | Cannot retry successful execution |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

<a id="functionsRollback"></a>
# **functionsRollback**
> FunctionResponse functionsRollback(projectId, functionId, functionsRollbackRequest)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to rollback.
    FunctionsRollbackRequest functionsRollbackRequest = new FunctionsRollbackRequest(); // FunctionsRollbackRequest | Version number (integer) to rollback to; use GET .../versions to list available versions.
    try {
      FunctionResponse result = apiInstance.functionsRollback(projectId, functionId, functionsRollbackRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsRollback");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to rollback. | |
| **functionsRollbackRequest** | [**FunctionsRollbackRequest**](FunctionsRollbackRequest.md)| Version number (integer) to rollback to; use GET .../versions to list available versions. | |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function rolled back |  -  |
| **400** | Version number is required |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

<a id="functionsSimulate"></a>
# **functionsSimulate**
> FunctionExecutionResponse functionsSimulate(projectId, functionId, functionsSimulateRequest)

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, wallet, or cron payloads. Executes the function with the provided eventContext merged into the payload. 

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) that owns the function.
    String functionId = "functionId_example"; // String | Function ID (MongoDB ObjectId) to simulate.
    FunctionsSimulateRequest functionsSimulateRequest = new FunctionsSimulateRequest(); // FunctionsSimulateRequest | Simulated trigger (type, event) and eventContext (document, file, webhook, wallet, message, or cron). Merged into the function payload for testing.
    try {
      FunctionExecutionResponse result = apiInstance.functionsSimulate(projectId, functionId, functionsSimulateRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsSimulate");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) that owns the function. | |
| **functionId** | **String**| Function ID (MongoDB ObjectId) to simulate. | |
| **functionsSimulateRequest** | [**FunctionsSimulateRequest**](FunctionsSimulateRequest.md)| Simulated trigger (type, event) and eventContext (document, file, webhook, wallet, message, or cron). Merged into the function payload for testing. | [optional] |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Simulation result |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="functionsTriggerWebhook"></a>
# **functionsTriggerWebhook**
> FunctionsTriggerWebhook200Response functionsTriggerWebhook(projectId, xWebhookSecret, body)

Trigger webhook functions

Public endpoint for external services to trigger functions with &#x60;trigger.type: webhook&#x60;. No authentication required. Optionally verify using &#x60;X-Webhook-Secret&#x60; header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 30 requests per 15 minutes per IP. 

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
    String projectId = "projectId_example"; // String | Project ID.
    String xWebhookSecret = "xWebhookSecret_example"; // String | Optional webhook secret for verification
    Object body = null; // Object | Payload sent to the triggered function(s).
    try {
      FunctionsTriggerWebhook200Response result = apiInstance.functionsTriggerWebhook(projectId, xWebhookSecret, body);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsTriggerWebhook");
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
| **xWebhookSecret** | **String**| Optional webhook secret for verification | [optional] |
| **body** | **Object**| Payload sent to the triggered function(s). | [optional] |

### Return type

[**FunctionsTriggerWebhook200Response**](FunctionsTriggerWebhook200Response.md)

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
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="functionsUpdate"></a>
# **functionsUpdate**
> FunctionResponse functionsUpdate(projectId, functionId, updateFunctionRequest)

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
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    FunctionsApi apiInstance = new FunctionsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String functionId = "functionId_example"; // String | Function ID.
    UpdateFunctionRequest updateFunctionRequest = new UpdateFunctionRequest(); // UpdateFunctionRequest | Fields to update (name, description, code, trigger, environment, isActive, limits, retryPolicy).
    try {
      FunctionResponse result = apiInstance.functionsUpdate(projectId, functionId, updateFunctionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling FunctionsApi#functionsUpdate");
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
| **functionId** | **String**| Function ID. | |
| **updateFunctionRequest** | [**UpdateFunctionRequest**](UpdateFunctionRequest.md)| Fields to update (name, description, code, trigger, environment, isActive, limits, retryPolicy). | [optional] |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

