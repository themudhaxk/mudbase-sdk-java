# SearchApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**searchGetAnalytics**](SearchApi.md#searchGetAnalytics) | **GET** /api/search/projects/{projectId}/search/analytics | Get search analytics |
| [**searchGetSuggestions**](SearchApi.md#searchGetSuggestions) | **GET** /api/search/projects/{projectId}/search/suggestions | Get search suggestions |
| [**searchSearch**](SearchApi.md#searchSearch) | **GET** /api/search/projects/{projectId}/search | Full-text search |


<a id="searchGetAnalytics"></a>
# **searchGetAnalytics**
> SearchGetAnalytics200Response searchGetAnalytics(projectId, timeframe)

Get search analytics

Get search analytics including top queries, search volume, and performance metrics. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.SearchApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    SearchApi apiInstance = new SearchApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID (MongoDB ObjectId) to get analytics for.
    String timeframe = "1d"; // String | Timeframe for analytics (1d, 7d, or 30d).
    try {
      SearchGetAnalytics200Response result = apiInstance.searchGetAnalytics(projectId, timeframe);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SearchApi#searchGetAnalytics");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to get analytics for. | |
| **timeframe** | **String**| Timeframe for analytics (1d, 7d, or 30d). | [optional] [default to 7d] [enum: 1d, 7d, 30d] |

### Return type

[**SearchGetAnalytics200Response**](SearchGetAnalytics200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search analytics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="searchGetSuggestions"></a>
# **searchGetSuggestions**
> SearchGetSuggestions200Response searchGetSuggestions(projectId, q, limit)

Get search suggestions

Get search query suggestions based on partial input. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.SearchApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    SearchApi apiInstance = new SearchApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID (MongoDB ObjectId) to get suggestions for.
    String q = "q_example"; // String | Partial search query (min 2 characters, max 50); suggestions are based on past queries and indexed content.
    Integer limit = 10; // Integer | Maximum number of suggestions to return (1–20).
    try {
      SearchGetSuggestions200Response result = apiInstance.searchGetSuggestions(projectId, q, limit);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SearchApi#searchGetSuggestions");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to get suggestions for. | |
| **q** | **String**| Partial search query (min 2 characters, max 50); suggestions are based on past queries and indexed content. | |
| **limit** | **Integer**| Maximum number of suggestions to return (1–20). | [optional] [default to 10] |

### Return type

[**SearchGetSuggestions200Response**](SearchGetSuggestions200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search suggestions |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="searchSearch"></a>
# **searchSearch**
> SearchResponse searchSearch(projectId, q, collections, fields, limit, page)

Full-text search

Perform full-text search across collections in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.SearchApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    SearchApi apiInstance = new SearchApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) to search within.
    String q = "q_example"; // String | Full-text search query string.
    String collections = "collections_example"; // String | Comma-separated collection slugs or IDs to limit search scope.
    String fields = "fields_example"; // String | Comma-separated field names to search or return in highlights.
    Integer limit = 20; // Integer | Maximum number of results to return per page.
    Integer page = 1; // Integer | Page number for pagination (1-based).
    try {
      SearchResponse result = apiInstance.searchSearch(projectId, q, collections, fields, limit, page);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SearchApi#searchSearch");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to search within. | |
| **q** | **String**| Full-text search query string. | |
| **collections** | **String**| Comma-separated collection slugs or IDs to limit search scope. | [optional] |
| **fields** | **String**| Comma-separated field names to search or return in highlights. | [optional] |
| **limit** | **Integer**| Maximum number of results to return per page. | [optional] [default to 20] |
| **page** | **Integer**| Page number for pagination (1-based). | [optional] [default to 1] |

### Return type

[**SearchResponse**](SearchResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search results |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

