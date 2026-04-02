# OrganizationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**organizationsAddDomain**](OrganizationsApi.md#organizationsAddDomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add custom domain |
| [**organizationsListDomains**](OrganizationsApi.md#organizationsListDomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS TXT hints |
| [**organizationsPatchDomain**](OrganizationsApi.md#organizationsPatchDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Patch domain status or regenerate token |
| [**organizationsRemoveDomain**](OrganizationsApi.md#organizationsRemoveDomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove custom domain |
| [**organizationsReportDomainPlatformReady**](OrganizationsApi.md#organizationsReportDomainPlatformReady) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops hosting / edge ready |
| [**organizationsSetPrimaryDomain**](OrganizationsApi.md#organizationsSetPrimaryDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**organizationsVerifyDomainDns**](OrganizationsApi.md#organizationsVerifyDomainDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain via DNS TXT |


<a id="organizationsAddDomain"></a>
# **organizationsAddDomain**
> organizationsAddDomain(orgId, projectId, organizationsAddDomainRequest)

Add custom domain

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    OrganizationsAddDomainRequest organizationsAddDomainRequest = new OrganizationsAddDomainRequest(); // OrganizationsAddDomainRequest | 
    try {
      apiInstance.organizationsAddDomain(orgId, projectId, organizationsAddDomainRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsAddDomain");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **organizationsAddDomainRequest** | [**OrganizationsAddDomainRequest**](OrganizationsAddDomainRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |

<a id="organizationsListDomains"></a>
# **organizationsListDomains**
> organizationsListDomains(orgId, projectId)

List custom domains and DNS TXT hints

Owner/admin. Domains are per project. Returns dnsTxtHost, dnsTxtValue, platformActivationPending (dns_verified waiting for ops), and customDomainLiveForApiTraffic (active or legacy verified). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    try {
      apiInstance.organizationsListDomains(orgId, projectId);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsListDomains");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="organizationsPatchDomain"></a>
# **organizationsPatchDomain**
> organizationsPatchDomain(orgId, projectId, hostname, organizationsPatchDomainRequest)

Patch domain status or regenerate token

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    OrganizationsPatchDomainRequest organizationsPatchDomainRequest = new OrganizationsPatchDomainRequest(); // OrganizationsPatchDomainRequest | 
    try {
      apiInstance.organizationsPatchDomain(orgId, projectId, hostname, organizationsPatchDomainRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsPatchDomain");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |
| **organizationsPatchDomainRequest** | [**OrganizationsPatchDomainRequest**](OrganizationsPatchDomainRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

<a id="organizationsRemoveDomain"></a>
# **organizationsRemoveDomain**
> organizationsRemoveDomain(orgId, projectId, hostname)

Remove custom domain

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      apiInstance.organizationsRemoveDomain(orgId, projectId, hostname);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsRemoveDomain");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Removed |  -  |

<a id="organizationsReportDomainPlatformReady"></a>
# **organizationsReportDomainPlatformReady**
> organizationsReportDomainPlatformReady(orgId, projectId, hostname, organizationsReportDomainPlatformReadyRequest)

Notify platform ops hosting / edge ready

Legacy optional ops email. First Mudbase TXT success already emails ops. Allowed during platform setup after Mudbase TXT. Recipients default to admin@mudhaxkservices.com and admin@mudbase.dev when CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS is unset. Returns 503 email_provider_not_configured if no email provider is configured. Does not change domain status.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    OrganizationsReportDomainPlatformReadyRequest organizationsReportDomainPlatformReadyRequest = new OrganizationsReportDomainPlatformReadyRequest(); // OrganizationsReportDomainPlatformReadyRequest | 
    try {
      apiInstance.organizationsReportDomainPlatformReady(orgId, projectId, hostname, organizationsReportDomainPlatformReadyRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsReportDomainPlatformReady");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |
| **organizationsReportDomainPlatformReadyRequest** | [**OrganizationsReportDomainPlatformReadyRequest**](OrganizationsReportDomainPlatformReadyRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Ops notified |  -  |
| **400** | custom_domain_invalid_state or other validation |  -  |
| **503** | email_provider_not_configured |  -  |

<a id="organizationsSetPrimaryDomain"></a>
# **organizationsSetPrimaryDomain**
> organizationsSetPrimaryDomain(orgId, projectId, organizationsSetPrimaryDomainRequest)

Set primary custom domain

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    OrganizationsSetPrimaryDomainRequest organizationsSetPrimaryDomainRequest = new OrganizationsSetPrimaryDomainRequest(); // OrganizationsSetPrimaryDomainRequest | 
    try {
      apiInstance.organizationsSetPrimaryDomain(orgId, projectId, organizationsSetPrimaryDomainRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsSetPrimaryDomain");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **organizationsSetPrimaryDomainRequest** | [**OrganizationsSetPrimaryDomainRequest**](OrganizationsSetPrimaryDomainRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

<a id="organizationsVerifyDomainDns"></a>
# **organizationsVerifyDomainDns**
> organizationsVerifyDomainDns(orgId, projectId, hostname)

Verify domain via DNS TXT

On first success from pending/failed, status becomes cname_pending_staff; ops email once; audit org.domain.txt_verified and org.domain.cname_staff_queued.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      apiInstance.organizationsVerifyDomainDns(orgId, projectId, hostname);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#organizationsVerifyDomainDns");
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
| **orgId** | **String**|  | |
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Verified; status typically cname_pending_staff after first TXT success |  -  |
| **400** | dns_verification_failed |  -  |

