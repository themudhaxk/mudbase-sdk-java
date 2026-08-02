# MonitoringApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createMonitoringAlert**](MonitoringApi.md#createMonitoringAlert) | **POST** /api/monitoring/alerts | Create monitoring alert |
| [**getMonitoringAnalytics**](MonitoringApi.md#getMonitoringAnalytics) | **GET** /api/monitoring/analytics | Get usage analytics (time series) |
| [**getMonitoringErrors**](MonitoringApi.md#getMonitoringErrors) | **GET** /api/monitoring/errors | Get error logs |
| [**getMonitoringLatencyInsights**](MonitoringApi.md#getMonitoringLatencyInsights) | **GET** /api/monitoring/latency-insights | Latency insights (route templates, percentiles, impact scores) |
| [**getMonitoringLogs**](MonitoringApi.md#getMonitoringLogs) | **GET** /api/monitoring/logs | Get audit logs |
| [**getMonitoringPerformance**](MonitoringApi.md#getMonitoringPerformance) | **GET** /api/monitoring/performance | Get performance metrics |
| [**getMonitoringQueueMetrics**](MonitoringApi.md#getMonitoringQueueMetrics) | **GET** /api/monitoring/queue-metrics | Usage metering queue job counts |
| [**getScannerMetrics**](MonitoringApi.md#getScannerMetrics) | **GET** /api/monitoring/scanner-metrics | Get block scanner metrics |
| [**listMonitoringAlerts**](MonitoringApi.md#listMonitoringAlerts) | **GET** /api/monitoring/alerts | List monitoring alerts |


<a id="createMonitoringAlert"></a>
# **createMonitoringAlert**
> createMonitoringAlert(createMonitoringAlertRequest)

Create monitoring alert

Create a monitoring alert (plan limit alertsPerProject enforced).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    CreateMonitoringAlertRequest createMonitoringAlertRequest = new CreateMonitoringAlertRequest(); // CreateMonitoringAlertRequest | 
    try {
      apiInstance.createMonitoringAlert(createMonitoringAlertRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#createMonitoringAlert");
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
| **createMonitoringAlertRequest** | [**CreateMonitoringAlertRequest**](CreateMonitoringAlertRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Alert created |  -  |
| **401** | Authentication required |  -  |
| **403** | Alert limit reached for your plan |  -  |

<a id="getMonitoringAnalytics"></a>
# **getMonitoringAnalytics**
> MonitoringAnalyticsResponse getMonitoringAnalytics(projectId, period, granularity, days)

Get usage analytics (time series)

Aggregates UsageStat by day/week/month. Optional **projectId** scopes to one project. Query **days** (1–90) for a rolling window (e.g. **days&#x3D;14**); when set, overrides **period**. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String period = "day"; // String | 
    String granularity = "day"; // String | 
    Integer days = 56; // Integer | Rolling window in days (1–90); when set, period becomes last_N_days
    try {
      MonitoringAnalyticsResponse result = apiInstance.getMonitoringAnalytics(projectId, period, granularity, days);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringAnalytics");
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
| **projectId** | **String**|  | [optional] |
| **period** | **String**|  | [optional] [default to month] [enum: day, week, month] |
| **granularity** | **String**|  | [optional] [default to day] [enum: day, week, month] |
| **days** | **Integer**| Rolling window in days (1–90); when set, period becomes last_N_days | [optional] |

### Return type

[**MonitoringAnalyticsResponse**](MonitoringAnalyticsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stats series and totals |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

<a id="getMonitoringErrors"></a>
# **getMonitoringErrors**
> getMonitoringErrors()

Get error logs

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    try {
      apiInstance.getMonitoringErrors();
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringErrors");
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

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Error logs |  -  |
| **401** | Authentication required |  -  |

<a id="getMonitoringLatencyInsights"></a>
# **getMonitoringLatencyInsights**
> getMonitoringLatencyInsights()

Latency insights (route templates, percentiles, impact scores)

Per-process snapshot: normalized **routeKey** (METHOD + path template), **p50/p95/p99**, 4xx/5xx counts, **impactScore**, **alertsSuggested**, **rps**, **inFlight**, **eventLoopLagP99Ms**. One buffer per server instance. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    try {
      apiInstance.getMonitoringLatencyInsights();
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringLatencyInsights");
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

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Latency insights payload |  -  |
| **401** | Authentication required |  -  |

<a id="getMonitoringLogs"></a>
# **getMonitoringLogs**
> MonitoringLogsResponse getMonitoringLogs(page, limit, projectId, userId, level, startDate, endDate, action, resource)

Get audit logs

Paginated audit trail for the org. Use **projectId** to scope to one project; **level&#x3D;all** or **audit** for full activity feed. Each entry includes **activityTitle** and **activityDetail** for dashboard copy. Requires monitoring read permission. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String projectId = "projectId_example"; // String | Filter to this project (must belong to org)
    String userId = "userId_example"; // String | Filter to this user's audit entries
    String level = "error"; // String | error|security|all|audit|low|medium|high|critical
    OffsetDateTime startDate = OffsetDateTime.now(); // OffsetDateTime | 
    OffsetDateTime endDate = OffsetDateTime.now(); // OffsetDateTime | 
    String action = "action_example"; // String | 
    String resource = "resource_example"; // String | 
    try {
      MonitoringLogsResponse result = apiInstance.getMonitoringLogs(page, limit, projectId, userId, level, startDate, endDate, action, resource);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringLogs");
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
| **projectId** | **String**| Filter to this project (must belong to org) | [optional] |
| **userId** | **String**| Filter to this user&#39;s audit entries | [optional] |
| **level** | **String**| error|security|all|audit|low|medium|high|critical | [optional] [default to error] |
| **startDate** | **OffsetDateTime**|  | [optional] |
| **endDate** | **OffsetDateTime**|  | [optional] |
| **action** | **String**|  | [optional] |
| **resource** | **String**|  | [optional] |

### Return type

[**MonitoringLogsResponse**](MonitoringLogsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Audit logs with pagination |  -  |
| **400** | Invalid userId format |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

<a id="getMonitoringPerformance"></a>
# **getMonitoringPerformance**
> MonitoringPerformanceResponse getMonitoringPerformance(projectId, period)

Get performance metrics

Response time stats from AuditLog where available. With **projectId**, falls back to UsageStat latency averages when audit data is sparse (**latencySource** may be **usage_stat**). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String period = "hour"; // String | 
    try {
      MonitoringPerformanceResponse result = apiInstance.getMonitoringPerformance(projectId, period);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringPerformance");
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
| **projectId** | **String**|  | [optional] |
| **period** | **String**|  | [optional] [default to hour] [enum: hour, day, week] |

### Return type

[**MonitoringPerformanceResponse**](MonitoringPerformanceResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Performance metrics |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

<a id="getMonitoringQueueMetrics"></a>
# **getMonitoringQueueMetrics**
> getMonitoringQueueMetrics()

Usage metering queue job counts

BullMQ **usage-events** queue counts when &#x60;USE_METERING_QUEUE&#x60; and &#x60;REDIS_URL&#x60; are set.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    try {
      apiInstance.getMonitoringQueueMetrics();
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getMonitoringQueueMetrics");
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

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Queue depth snapshot |  -  |
| **401** | Authentication required |  -  |

<a id="getScannerMetrics"></a>
# **getScannerMetrics**
> GetScannerMetrics200Response getScannerMetrics()

Get block scanner metrics

Returns per-chain block scanner lag and health. Used for observability of ETH/UTXO block-based wallet monitoring. Alerts when lag exceeds threshold.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

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

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    try {
      GetScannerMetrics200Response result = apiInstance.getScannerMetrics();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#getScannerMetrics");
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

[**GetScannerMetrics200Response**](GetScannerMetrics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Scanner metrics and optional lag alerts |  -  |
| **401** | Authentication required |  -  |
| **500** | Failed to fetch scanner metrics |  -  |

<a id="listMonitoringAlerts"></a>
# **listMonitoringAlerts**
> listMonitoringAlerts()

List monitoring alerts

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MonitoringApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    MonitoringApi apiInstance = new MonitoringApi(defaultClient);
    try {
      apiInstance.listMonitoringAlerts();
    } catch (ApiException e) {
      System.err.println("Exception when calling MonitoringApi#listMonitoringAlerts");
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

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of alerts |  -  |
| **401** | Authentication required |  -  |

