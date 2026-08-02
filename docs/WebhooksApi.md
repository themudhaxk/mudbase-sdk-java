# WebhooksApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**configureWebhook**](WebhooksApi.md#configureWebhook) | **PUT** /api/webhooks/projects/{projectId}/config | Create or update project webhook |
| [**getWebhookConfig**](WebhooksApi.md#getWebhookConfig) | **GET** /api/webhooks/projects/{projectId}/config | Get project webhook configuration |
| [**getWebhookStats**](WebhooksApi.md#getWebhookStats) | **GET** /api/webhooks/stats | Get webhook delivery statistics |
| [**listProjectWebhookLogs**](WebhooksApi.md#listProjectWebhookLogs) | **GET** /api/webhooks/projects/{projectId} | List webhook delivery logs (project) |
| [**listWebhooks**](WebhooksApi.md#listWebhooks) | **GET** /api/webhooks | List webhook delivery logs (organization) |
| [**retryWebhook**](WebhooksApi.md#retryWebhook) | **POST** /api/webhooks/retry/{webhookId} | Retry a failed webhook delivery |
| [**testWebhookTransformation**](WebhooksApi.md#testWebhookTransformation) | **POST** /api/webhooks/projects/{projectId}/test-transformation | Test webhook transformation |
| [**triggerWebhook**](WebhooksApi.md#triggerWebhook) | **POST** /api/webhooks/trigger | Manually trigger an outbound webhook |


<a id="configureWebhook"></a>
# **configureWebhook**
> ConfigureWebhook200Response configureWebhook(projectId, configureWebhookRequest)

Create or update project webhook

Set or update the project webhook URL and options. This is how you **add** or **create** a webhook for a project: provide **webhookUrl** to enable delivery; omit or set to null to disable. Optionally set **webhookSecret**, **webhookEvents**, **webhookVersion**, and **transformations**. Plan limits (webhooks per project) apply when adding a new URL. Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project update access. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

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

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    ConfigureWebhookRequest configureWebhookRequest = new ConfigureWebhookRequest(); // ConfigureWebhookRequest | 
    try {
      ConfigureWebhook200Response result = apiInstance.configureWebhook(projectId, configureWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#configureWebhook");
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
| **configureWebhookRequest** | [**ConfigureWebhookRequest**](ConfigureWebhookRequest.md)|  | [optional] |

### Return type

[**ConfigureWebhook200Response**](ConfigureWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook configuration updated |  -  |
| **403** | Project webhook limit reached for your plan |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

<a id="getWebhookConfig"></a>
# **getWebhookConfig**
> GetWebhookConfig200Response getWebhookConfig(projectId)

Get project webhook configuration

Get the current webhook URL, events, version, and transformations for a project. This is **where Mudbase POSTs event payloads**; it does **not** return a &#x60;webhookId&#x60;. Delivery ids (&#x60;WebhookLog._id&#x60;) come from **&#x60;POST /api/webhooks/trigger&#x60;** or automatic deliveries, and from **list logs** endpoints.  Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project read access. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

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

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetWebhookConfig200Response result = apiInstance.getWebhookConfig(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#getWebhookConfig");
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

[**GetWebhookConfig200Response**](GetWebhookConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook configuration |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

<a id="getWebhookStats"></a>
# **getWebhookStats**
> WebhookStatsResponse getWebhookStats(projectId, days)

Get webhook delivery statistics

Aggregates **&#x60;WebhookLog&#x60;** rows for your organization over the last **&#x60;days&#x60;** (default 7). Optional **&#x60;projectId&#x60;** filters to a project in your org.  Returns **&#x60;statusStats&#x60;** (counts and average duration per delivery **status**) and **&#x60;eventStats&#x60;** (counts and success rate per **event** name).  **Auth:** Organization JWT only (&#x60;authRequired&#x60;). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String projectId = "projectId_example"; // String | Optional; limit stats to this project.
    Integer days = 7; // Integer | 
    try {
      WebhookStatsResponse result = apiInstance.getWebhookStats(projectId, days);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#getWebhookStats");
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
| **projectId** | **String**| Optional; limit stats to this project. | [optional] |
| **days** | **Integer**|  | [optional] [default to 7] |

### Return type

[**WebhookStatsResponse**](WebhookStatsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Aggregated webhook log statistics |  -  |
| **400** | Bad request |  -  |
| **404** | Project not found or not in your org |  -  |
| **500** | Internal server error |  -  |

<a id="listProjectWebhookLogs"></a>
# **listProjectWebhookLogs**
> WebhookListResponse listProjectWebhookLogs(projectId, page, limit, status, event)

List webhook delivery logs (project)

Same **&#x60;WebhookLog&#x60;** documents as **&#x60;GET /api/webhooks&#x60;**, scoped to **&#x60;projectId&#x60;** in the path. Accepts **org JWT**, **project JWT**, or **project API key** with project read access.  Each item’s **&#x60;_id&#x60;** is the id returned as **&#x60;webhookId&#x60;** from **&#x60;POST /api/webhooks/trigger&#x60;** and used in **&#x60;POST /api/webhooks/retry/{webhookId}&#x60;**. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

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

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String status = "pending"; // String | 
    String event = "event_example"; // String | 
    try {
      WebhookListResponse result = apiInstance.listProjectWebhookLogs(projectId, page, limit, status, event);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#listProjectWebhookLogs");
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
| **status** | **String**|  | [optional] [enum: pending, success, failed, retrying] |
| **event** | **String**|  | [optional] |

### Return type

[**WebhookListResponse**](WebhookListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs for the project |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **500** | Internal server error |  -  |

<a id="listWebhooks"></a>
# **listWebhooks**
> WebhookListResponse listWebhooks(page, limit, status, event, projectId)

List webhook delivery logs (organization)

Paginated **webhook delivery logs** for your organization (each row is one outbound HTTP attempt). Optional **&#x60;projectId&#x60;** query filters to a project that belongs to your org.  Use each log document’s **&#x60;_id&#x60;** (MongoDB ObjectId) as **&#x60;webhookId&#x60;** when calling **&#x60;POST /api/webhooks/retry/{webhookId}&#x60;** after a failed delivery. Organization **JWT only** (&#x60;OrgBearerAuth&#x60;); project API keys are not accepted on this route. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String status = "pending"; // String | 
    String event = "event_example"; // String | 
    String projectId = "projectId_example"; // String | Optional; restrict logs to this project (must belong to your org).
    try {
      WebhookListResponse result = apiInstance.listWebhooks(page, limit, status, event, projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#listWebhooks");
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
| **page** | **Integer**|  | [optional] [default to 1] |
| **limit** | **Integer**|  | [optional] [default to 20] |
| **status** | **String**|  | [optional] [enum: pending, success, failed, retrying] |
| **event** | **String**|  | [optional] |
| **projectId** | **String**| Optional; restrict logs to this project (must belong to your org). | [optional] |

### Return type

[**WebhookListResponse**](WebhookListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **500** | Internal server error |  -  |

<a id="retryWebhook"></a>
# **retryWebhook**
> RetryWebhookResponse retryWebhook(webhookId)

Retry a failed webhook delivery

**&#x60;webhookId&#x60;** (path) &#x3D; **&#x60;WebhookLog._id&#x60;** (MongoDB ObjectId)—the same value returned as **&#x60;webhookId&#x60;** from **&#x60;POST /api/webhooks/trigger&#x60;** and as **&#x60;_id&#x60;** on **&#x60;GET /api/webhooks&#x60;** / **&#x60;GET /api/webhooks/projects/{projectId}&#x60;**.  **Not** the string **&#x60;webhookId&#x60;** field stored on the log document (e.g. &#x60;manual-173…&#x60;); use the document **&#x60;_id&#x60;** for this path.  Resets a non-success log to **pending** and re-delivers. **400** if status is already **&#x60;success&#x60;**.  **Auth:** Organization JWT only; project API keys are not accepted. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String webhookId = "webhookId_example"; // String | WebhookLog document `_id` (delivery log id).
    try {
      RetryWebhookResponse result = apiInstance.retryWebhook(webhookId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#retryWebhook");
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
| **webhookId** | **String**| WebhookLog document &#x60;_id&#x60; (delivery log id). | |

### Return type

[**RetryWebhookResponse**](RetryWebhookResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry queued |  -  |
| **400** | Log already succeeded |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Log not found or not in your org |  -  |
| **500** | Internal server error |  -  |

<a id="testWebhookTransformation"></a>
# **testWebhookTransformation**
> TestWebhookTransformation200Response testWebhookTransformation(projectId, testWebhookTransformationRequest)

Test webhook transformation

Apply transformation rules to a sample payload and return original and transformed payloads. Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project update access. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

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

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    TestWebhookTransformationRequest testWebhookTransformationRequest = new TestWebhookTransformationRequest(); // TestWebhookTransformationRequest | 
    try {
      TestWebhookTransformation200Response result = apiInstance.testWebhookTransformation(projectId, testWebhookTransformationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#testWebhookTransformation");
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
| **testWebhookTransformationRequest** | [**TestWebhookTransformationRequest**](TestWebhookTransformationRequest.md)|  | |

### Return type

[**TestWebhookTransformation200Response**](TestWebhookTransformation200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transformation result |  -  |
| **400** | payload and transformations are required |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

<a id="triggerWebhook"></a>
# **triggerWebhook**
> TriggerWebhookResponse triggerWebhook(triggerWebhookRequest)

Manually trigger an outbound webhook

Queues an HTTP delivery to **&#x60;url&#x60;** for **&#x60;projectId&#x60;** (must belong to your org). Creates a **&#x60;WebhookLog&#x60;** row, runs delivery, and returns the new log’s **&#x60;_id&#x60;**.  **Response field &#x60;webhookId&#x60;:** This is the **MongoDB &#x60;_id&#x60; of the delivery log** (same as the log’s **&#x60;_id&#x60;** in list endpoints). It is **not** part of the request body and is **not** the project &#x60;webhookSecret&#x60; from **&#x60;PUT .../config&#x60;**.  **Auth:** Org JWT, project JWT, or project API key with **project &#x60;update&#x60;** permission. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WebhooksApi;

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

    WebhooksApi apiInstance = new WebhooksApi(defaultClient);
    TriggerWebhookRequest triggerWebhookRequest = new TriggerWebhookRequest(); // TriggerWebhookRequest | 
    try {
      TriggerWebhookResponse result = apiInstance.triggerWebhook(triggerWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WebhooksApi#triggerWebhook");
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
| **triggerWebhookRequest** | [**TriggerWebhookRequest**](TriggerWebhookRequest.md)|  | |

### Return type

[**TriggerWebhookResponse**](TriggerWebhookResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Delivery queued; **&#x60;webhookId&#x60;** is the new log document **&#x60;_id&#x60;** |  -  |
| **400** | Missing projectId, invalid project id, or invalid URL (SSRF guard) |  -  |
| **404** | Project not found or not in your org |  -  |
| **500** | Internal server error |  -  |

