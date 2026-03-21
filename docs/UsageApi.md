# UsageApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**usageGetProject**](UsageApi.md#usageGetProject) | **GET** /api/usage/projects/{projectId} | Get project usage |
| [**usageGetTrends**](UsageApi.md#usageGetTrends) | **GET** /api/usage/trends | Get usage trends |


<a id="usageGetProject"></a>
# **usageGetProject**
> ProjectUsageStatsResponse usageGetProject(projectId, period)

Get project usage

Get usage statistics for a project (API calls, storage, bandwidth, database operations). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsageApi apiInstance = new UsageApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) to get usage for.
    String period = "day"; // String | Aggregation period for usage (day, week, or month).
    try {
      ProjectUsageStatsResponse result = apiInstance.usageGetProject(projectId, period);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsageApi#usageGetProject");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to get usage for. | |
| **period** | **String**| Aggregation period for usage (day, week, or month). | [optional] [default to month] [enum: day, week, month] |

### Return type

[**ProjectUsageStatsResponse**](ProjectUsageStatsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project usage statistics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usageGetTrends"></a>
# **usageGetTrends**
> UsageTrendsResponse usageGetTrends(days)

Get usage trends

Get usage trends over time for the authenticated organization or project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsageApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsageApi apiInstance = new UsageApi(defaultClient);
    Integer days = 30; // Integer | Number of days of trend data to return (default 30).
    try {
      UsageTrendsResponse result = apiInstance.usageGetTrends(days);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsageApi#usageGetTrends");
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
| **days** | **Integer**| Number of days of trend data to return (default 30). | [optional] [default to 30] |

### Return type

[**UsageTrendsResponse**](UsageTrendsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage trends |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

