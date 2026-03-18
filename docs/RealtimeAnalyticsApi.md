# RealtimeAnalyticsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**realtimeAnalyticsCheckUserPresence**](RealtimeAnalyticsApi.md#realtimeAnalyticsCheckUserPresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**realtimeAnalyticsGetActiveUsers**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetActiveUsers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**realtimeAnalyticsGetEventThroughput**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetEventThroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**realtimeAnalyticsGetHistoricalAnalytics**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetHistoricalAnalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**realtimeAnalyticsGetProject**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetProject) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |


<a id="realtimeAnalyticsCheckUserPresence"></a>
# **realtimeAnalyticsCheckUserPresence**
> RealtimeAnalyticsCheckUserPresence200Response realtimeAnalyticsCheckUserPresence(projectId, realtimeAnalyticsCheckUserPresenceRequest)

Check presence status for users

Returns online status for specified user IDs

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RealtimeAnalyticsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RealtimeAnalyticsApi apiInstance = new RealtimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    RealtimeAnalyticsCheckUserPresenceRequest realtimeAnalyticsCheckUserPresenceRequest = new RealtimeAnalyticsCheckUserPresenceRequest(); // RealtimeAnalyticsCheckUserPresenceRequest | Array of user IDs to check presence for.
    try {
      RealtimeAnalyticsCheckUserPresence200Response result = apiInstance.realtimeAnalyticsCheckUserPresence(projectId, realtimeAnalyticsCheckUserPresenceRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealtimeAnalyticsApi#realtimeAnalyticsCheckUserPresence");
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
| **realtimeAnalyticsCheckUserPresenceRequest** | [**RealtimeAnalyticsCheckUserPresenceRequest**](RealtimeAnalyticsCheckUserPresenceRequest.md)| Array of user IDs to check presence for. | |

### Return type

[**RealtimeAnalyticsCheckUserPresence200Response**](RealtimeAnalyticsCheckUserPresence200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presence status for each user |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="realtimeAnalyticsGetActiveUsers"></a>
# **realtimeAnalyticsGetActiveUsers**
> RealtimeAnalyticsGetActiveUsers200Response realtimeAnalyticsGetActiveUsers(projectId)

Get active users for a project

Returns list of currently connected users

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RealtimeAnalyticsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RealtimeAnalyticsApi apiInstance = new RealtimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    try {
      RealtimeAnalyticsGetActiveUsers200Response result = apiInstance.realtimeAnalyticsGetActiveUsers(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealtimeAnalyticsApi#realtimeAnalyticsGetActiveUsers");
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

[**RealtimeAnalyticsGetActiveUsers200Response**](RealtimeAnalyticsGetActiveUsers200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of active users |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="realtimeAnalyticsGetEventThroughput"></a>
# **realtimeAnalyticsGetEventThroughput**
> RealtimeAnalyticsGetEventThroughput200Response realtimeAnalyticsGetEventThroughput(projectId, window)

Get event throughput metrics

Returns event throughput for a project

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RealtimeAnalyticsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RealtimeAnalyticsApi apiInstance = new RealtimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    Integer window = 60000; // Integer | Time window in milliseconds
    try {
      RealtimeAnalyticsGetEventThroughput200Response result = apiInstance.realtimeAnalyticsGetEventThroughput(projectId, window);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealtimeAnalyticsApi#realtimeAnalyticsGetEventThroughput");
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
| **window** | **Integer**| Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**RealtimeAnalyticsGetEventThroughput200Response**](RealtimeAnalyticsGetEventThroughput200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Throughput metrics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="realtimeAnalyticsGetHistoricalAnalytics"></a>
# **realtimeAnalyticsGetHistoricalAnalytics**
> RealtimeAnalyticsGetHistoricalAnalytics200Response realtimeAnalyticsGetHistoricalAnalytics(projectId, period)

Get historical analytics

Returns historical analytics for charting

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RealtimeAnalyticsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RealtimeAnalyticsApi apiInstance = new RealtimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String period = "hour"; // String | Time period for historical data
    try {
      RealtimeAnalyticsGetHistoricalAnalytics200Response result = apiInstance.realtimeAnalyticsGetHistoricalAnalytics(projectId, period);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealtimeAnalyticsApi#realtimeAnalyticsGetHistoricalAnalytics");
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
| **period** | **String**| Time period for historical data | [optional] [default to hour] [enum: hour, day, week] |

### Return type

[**RealtimeAnalyticsGetHistoricalAnalytics200Response**](RealtimeAnalyticsGetHistoricalAnalytics200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Historical analytics data |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="realtimeAnalyticsGetProject"></a>
# **realtimeAnalyticsGetProject**
> RealtimeAnalyticsGetProject200Response realtimeAnalyticsGetProject(projectId)

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.RealtimeAnalyticsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    RealtimeAnalyticsApi apiInstance = new RealtimeAnalyticsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID (MongoDB ObjectId) to get real-time analytics for.
    try {
      RealtimeAnalyticsGetProject200Response result = apiInstance.realtimeAnalyticsGetProject(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealtimeAnalyticsApi#realtimeAnalyticsGetProject");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to get real-time analytics for. | |

### Return type

[**RealtimeAnalyticsGetProject200Response**](RealtimeAnalyticsGetProject200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project analytics data |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

