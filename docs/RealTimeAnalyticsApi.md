# RealTimeAnalyticsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**checkUserPresence**](RealTimeAnalyticsApi.md#checkUserPresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**getActiveUsers**](RealTimeAnalyticsApi.md#getActiveUsers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**getEventThroughput**](RealTimeAnalyticsApi.md#getEventThroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**getGlobalAnalytics**](RealTimeAnalyticsApi.md#getGlobalAnalytics) | **GET** /api/realtime/analytics | Get global real-time analytics |
| [**getHistoricalAnalytics**](RealTimeAnalyticsApi.md#getHistoricalAnalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**getProjectAnalytics**](RealTimeAnalyticsApi.md#getProjectAnalytics) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |


<a id="checkUserPresence"></a>
# **checkUserPresence**
> CheckUserPresence200Response checkUserPresence(projectId, checkUserPresenceRequest)

Check presence status for users

Returns online status for specified user IDs

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    CheckUserPresenceRequest checkUserPresenceRequest = new CheckUserPresenceRequest(); // CheckUserPresenceRequest | 
    try {
      CheckUserPresence200Response result = apiInstance.checkUserPresence(projectId, checkUserPresenceRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#checkUserPresence");
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
| **checkUserPresenceRequest** | [**CheckUserPresenceRequest**](CheckUserPresenceRequest.md)|  | |

### Return type

[**CheckUserPresence200Response**](CheckUserPresence200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presence status for each user |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getActiveUsers"></a>
# **getActiveUsers**
> GetActiveUsers200Response getActiveUsers(projectId)

Get active users for a project

Returns list of currently connected users

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetActiveUsers200Response result = apiInstance.getActiveUsers(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#getActiveUsers");
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

[**GetActiveUsers200Response**](GetActiveUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of active users |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getEventThroughput"></a>
# **getEventThroughput**
> GetEventThroughput200Response getEventThroughput(projectId, window)

Get event throughput metrics

Returns event throughput for a project

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    Integer window = 60000; // Integer | Time window in milliseconds
    try {
      GetEventThroughput200Response result = apiInstance.getEventThroughput(projectId, window);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#getEventThroughput");
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
| **window** | **Integer**| Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**GetEventThroughput200Response**](GetEventThroughput200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Throughput metrics |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getGlobalAnalytics"></a>
# **getGlobalAnalytics**
> GetGlobalAnalytics200Response getGlobalAnalytics()

Get global real-time analytics

Returns system-wide real-time metrics (admin only)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    try {
      GetGlobalAnalytics200Response result = apiInstance.getGlobalAnalytics();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#getGlobalAnalytics");
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

[**GetGlobalAnalytics200Response**](GetGlobalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Global analytics data |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

<a id="getHistoricalAnalytics"></a>
# **getHistoricalAnalytics**
> GetHistoricalAnalytics200Response getHistoricalAnalytics(projectId, period)

Get historical analytics

Returns historical analytics for charting

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String period = "hour"; // String | Time period for historical data
    try {
      GetHistoricalAnalytics200Response result = apiInstance.getHistoricalAnalytics(projectId, period);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#getHistoricalAnalytics");
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
| **period** | **String**| Time period for historical data | [optional] [default to hour] [enum: hour, day, week] |

### Return type

[**GetHistoricalAnalytics200Response**](GetHistoricalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Historical analytics data |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getProjectAnalytics"></a>
# **getProjectAnalytics**
> GetProjectAnalytics200Response getProjectAnalytics(projectId)

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.RealTimeAnalyticsApi;

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

    RealTimeAnalyticsApi apiInstance = new RealTimeAnalyticsApi(defaultClient);
    String projectId = "65f1a2b3c4d5e6f7a8b9c0d1"; // String | 
    try {
      GetProjectAnalytics200Response result = apiInstance.getProjectAnalytics(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RealTimeAnalyticsApi#getProjectAnalytics");
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

[**GetProjectAnalytics200Response**](GetProjectAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project analytics data |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

