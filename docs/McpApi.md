# McpApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**mcpConfigGet**](McpApi.md#mcpConfigGet) | **GET** /mcp/config | MCP connection status for the current org |


<a id="mcpConfigGet"></a>
# **mcpConfigGet**
> McpConfigGet200Response mcpConfigGet()

MCP connection status for the current org

Whether the org&#39;s plan includes MCP access and, when enabled, the endpoint URL an MCP client should connect to (the org&#39;s dedicated API host if it has dedicated infrastructure, otherwise the shared platform host). Auth here is the normal dashboard session - this powers the console&#39;s MCP settings page, distinct from the API-key-authenticated POST / endpoint an actual MCP client calls.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.McpApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    McpApi apiInstance = new McpApi(defaultClient);
    try {
      McpConfigGet200Response result = apiInstance.mcpConfigGet();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling McpApi#mcpConfigGet");
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

[**McpConfigGet200Response**](McpConfigGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | MCP status for the current org |  -  |
| **401** | Authentication required |  -  |

