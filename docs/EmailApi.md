# EmailApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**enqueueProjectEmail**](EmailApi.md#enqueueProjectEmail) | **POST** /api/projects/{projectId}/email/send | Enqueue project email (worker delivery) |
| [**getProjectEmailAnalytics**](EmailApi.md#getProjectEmailAnalytics) | **GET** /api/projects/{projectId}/analytics/email | Email analytics for a project |
| [**getProjectEmailSmtp**](EmailApi.md#getProjectEmailSmtp) | **GET** /api/projects/{projectId}/email/smtp | Get project SMTP settings (masked) |
| [**getProjectEmailTemplate**](EmailApi.md#getProjectEmailTemplate) | **GET** /api/projects/{projectId}/email/templates/{name} | Get one email template (effective content) |
| [**listProjectEmailTemplates**](EmailApi.md#listProjectEmailTemplates) | **GET** /api/projects/{projectId}/email/templates | List email templates (full catalog for the project) |
| [**patchProjectEmailSmtp**](EmailApi.md#patchProjectEmailSmtp) | **PATCH** /api/projects/{projectId}/email/smtp | Update project SMTP relay (BYO) |
| [**previewProjectEmailTemplate**](EmailApi.md#previewProjectEmailTemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/preview | Render template preview (sanitized HTML, no send) |
| [**restoreDefaultProjectEmailTemplate**](EmailApi.md#restoreDefaultProjectEmailTemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/restore-default | Restore from platform global default or remove project override |
| [**testProjectEmailSmtp**](EmailApi.md#testProjectEmailSmtp) | **POST** /api/projects/{projectId}/email/smtp/test | Verify SMTP and send a test message |
| [**upsertProjectEmailTemplate**](EmailApi.md#upsertProjectEmailTemplate) | **PUT** /api/projects/{projectId}/email/templates/{name} | Upsert project email template (HTML sanitized; variables must cover {{placeholders}}) |
| [**verifyProjectEmailSmtpDomain**](EmailApi.md#verifyProjectEmailSmtpDomain) | **POST** /api/projects/{projectId}/email/smtp/verify-domain | Check DNS (MX + SPF) for sending domain |


<a id="enqueueProjectEmail"></a>
# **enqueueProjectEmail**
> EnqueueProjectEmail202Response enqueueProjectEmail(projectId, projectEmailSendRequest)

Enqueue project email (worker delivery)

Queues a transactional email for sending through the email worker and configured provider (platform or per-project SMTP). Provide either &#x60;template&#x60; (with &#x60;data&#x60;) or both &#x60;subject&#x60; and &#x60;html&#x60;. Returns **202** with &#x60;jobId&#x60; when accepted. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    ProjectEmailSendRequest projectEmailSendRequest = new ProjectEmailSendRequest(); // ProjectEmailSendRequest | 
    try {
      EnqueueProjectEmail202Response result = apiInstance.enqueueProjectEmail(projectId, projectEmailSendRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#enqueueProjectEmail");
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
| **projectEmailSendRequest** | [**ProjectEmailSendRequest**](ProjectEmailSendRequest.md)|  | |

### Return type

[**EnqueueProjectEmail202Response**](EnqueueProjectEmail202Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Job accepted |  -  |
| **400** | Bad request |  -  |
| **503** | Email queue unavailable |  -  |

<a id="getProjectEmailAnalytics"></a>
# **getProjectEmailAnalytics**
> GetProjectEmailAnalytics200Response getProjectEmailAnalytics(projectId, from, to)

Email analytics for a project

Aggregated email log stats for the project. Optional &#x60;from&#x60; and &#x60;to&#x60; query params filter by date range (ISO 8601). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    OffsetDateTime from = OffsetDateTime.now(); // OffsetDateTime | 
    OffsetDateTime to = OffsetDateTime.now(); // OffsetDateTime | 
    try {
      GetProjectEmailAnalytics200Response result = apiInstance.getProjectEmailAnalytics(projectId, from, to);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#getProjectEmailAnalytics");
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
| **from** | **OffsetDateTime**|  | [optional] |
| **to** | **OffsetDateTime**|  | [optional] |

### Return type

[**GetProjectEmailAnalytics200Response**](GetProjectEmailAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Analytics payload |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

<a id="getProjectEmailSmtp"></a>
# **getProjectEmailSmtp**
> GetProjectEmailSmtp200Response getProjectEmailSmtp(projectId)

Get project SMTP settings (masked)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetProjectEmailSmtp200Response result = apiInstance.getProjectEmailSmtp(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#getProjectEmailSmtp");
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

[**GetProjectEmailSmtp200Response**](GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | SMTP configuration without secrets |  -  |

<a id="getProjectEmailTemplate"></a>
# **getProjectEmailTemplate**
> GetProjectEmailTemplate200Response getProjectEmailTemplate(projectId, name)

Get one email template (effective content)

Returns the template body that would be used when sending: project override if present, else global default, else built-in fallback. **&#x60;isProjectOverride&#x60;** is true only when this project has a stored row; **&#x60;effectiveSource&#x60;** is &#x60;project&#x60;, &#x60;global&#x60;, or &#x60;builtin&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String name = "name_example"; // String | 
    try {
      GetProjectEmailTemplate200Response result = apiInstance.getProjectEmailTemplate(projectId, name);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#getProjectEmailTemplate");
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
| **name** | **String**|  | |

### Return type

[**GetProjectEmailTemplate200Response**](GetProjectEmailTemplate200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Template document (resolved for send) |  -  |
| **404** | Resource not found |  -  |

<a id="listProjectEmailTemplates"></a>
# **listProjectEmailTemplates**
> ListProjectEmailTemplates200Response listProjectEmailTemplates(projectId)

List email templates (full catalog for the project)

Returns every template name the worker can resolve for this project: **built-in** defaults, **global** platform rows (&#x60;project: null&#x60; in DB), and **project** overrides. Use **&#x60;isCustomized&#x60;** to see if this project has its own stored copy; **&#x60;effectiveSource&#x60;** shows which layer would be used at send time (&#x60;project&#x60; wins over &#x60;global&#x60; over &#x60;builtin&#x60;). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      ListProjectEmailTemplates200Response result = apiInstance.listProjectEmailTemplates(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#listProjectEmailTemplates");
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

[**ListProjectEmailTemplates200Response**](ListProjectEmailTemplates200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Template catalog with customization flags |  -  |

<a id="patchProjectEmailSmtp"></a>
# **patchProjectEmailSmtp**
> GetProjectEmailSmtp200Response patchProjectEmailSmtp(projectId, projectSmtpPatchRequest)

Update project SMTP relay (BYO)

Set &#x60;authPass&#x60; in the body to store an encrypted password (never returned on GET). Validates host/user when enabling. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    ProjectSmtpPatchRequest projectSmtpPatchRequest = new ProjectSmtpPatchRequest(); // ProjectSmtpPatchRequest | 
    try {
      GetProjectEmailSmtp200Response result = apiInstance.patchProjectEmailSmtp(projectId, projectSmtpPatchRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#patchProjectEmailSmtp");
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
| **projectSmtpPatchRequest** | [**ProjectSmtpPatchRequest**](ProjectSmtpPatchRequest.md)|  | |

### Return type

[**GetProjectEmailSmtp200Response**](GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated settings (masked) |  -  |
| **400** | Bad request |  -  |

<a id="previewProjectEmailTemplate"></a>
# **previewProjectEmailTemplate**
> previewProjectEmailTemplate(projectId, name, previewProjectEmailTemplateRequest)

Render template preview (sanitized HTML, no send)

Body **&#x60;sampleData&#x60;** is merged with layout defaults; keys should match &#x60;{{placeholders}}&#x60; in the template (see **Email** tag for the catalog). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String name = "name_example"; // String | 
    PreviewProjectEmailTemplateRequest previewProjectEmailTemplateRequest = new PreviewProjectEmailTemplateRequest(); // PreviewProjectEmailTemplateRequest | 
    try {
      apiInstance.previewProjectEmailTemplate(projectId, name, previewProjectEmailTemplateRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#previewProjectEmailTemplate");
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
| **name** | **String**|  | |
| **previewProjectEmailTemplateRequest** | [**PreviewProjectEmailTemplateRequest**](PreviewProjectEmailTemplateRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Rendered subject and HTML |  -  |

<a id="restoreDefaultProjectEmailTemplate"></a>
# **restoreDefaultProjectEmailTemplate**
> restoreDefaultProjectEmailTemplate(projectId, name)

Restore from platform global default or remove project override

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String name = "name_example"; // String | 
    try {
      apiInstance.restoreDefaultProjectEmailTemplate(projectId, name);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#restoreDefaultProjectEmailTemplate");
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
| **name** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Restored or deleted override |  -  |

<a id="testProjectEmailSmtp"></a>
# **testProjectEmailSmtp**
> DeleteFunction200Response testProjectEmailSmtp(projectId, projectSmtpTestRequest)

Verify SMTP and send a test message

Rate-limited. With &#x60;useSaved: true&#x60; (default), uses stored credentials; otherwise pass &#x60;host&#x60;, &#x60;authUser&#x60;, &#x60;authPass&#x60;, etc. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    ProjectSmtpTestRequest projectSmtpTestRequest = new ProjectSmtpTestRequest(); // ProjectSmtpTestRequest | 
    try {
      DeleteFunction200Response result = apiInstance.testProjectEmailSmtp(projectId, projectSmtpTestRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#testProjectEmailSmtp");
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
| **projectSmtpTestRequest** | [**ProjectSmtpTestRequest**](ProjectSmtpTestRequest.md)|  | |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | SMTP verified and test mail sent |  -  |
| **400** | Bad request |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="upsertProjectEmailTemplate"></a>
# **upsertProjectEmailTemplate**
> upsertProjectEmailTemplate(projectId, name, upsertProjectEmailTemplateRequest)

Upsert project email template (HTML sanitized; variables must cover {{placeholders}})

Saves a **project override** for &#x60;name&#x60;. HTML is sanitized. **&#x60;variables&#x60;** must list every &#x60;{{token}}&#x60; used in &#x60;subject&#x60;, &#x60;htmlBody&#x60;, and &#x60;textBody&#x60; (see **Email** tag description for the full placeholder catalog). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String name = "name_example"; // String | 
    UpsertProjectEmailTemplateRequest upsertProjectEmailTemplateRequest = new UpsertProjectEmailTemplateRequest(); // UpsertProjectEmailTemplateRequest | 
    try {
      apiInstance.upsertProjectEmailTemplate(projectId, name, upsertProjectEmailTemplateRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#upsertProjectEmailTemplate");
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
| **name** | **String**|  | |
| **upsertProjectEmailTemplateRequest** | [**UpsertProjectEmailTemplateRequest**](UpsertProjectEmailTemplateRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Saved template |  -  |
| **400** | Bad request |  -  |

<a id="verifyProjectEmailSmtpDomain"></a>
# **verifyProjectEmailSmtpDomain**
> verifyProjectEmailSmtpDomain(projectId, verifyProjectEmailSmtpDomainRequest)

Check DNS (MX + SPF) for sending domain

Resolves the domain from &#x60;domain&#x60;, &#x60;fromEmail&#x60;, or saved &#x60;emailSmtp.fromEmail&#x60;. Returns whether MX and SPF TXT exist. With &#x60;persist: true&#x60; and checks passed, sets &#x60;emailSmtp.domainVerifiedAt&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.EmailApi;

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

    EmailApi apiInstance = new EmailApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    VerifyProjectEmailSmtpDomainRequest verifyProjectEmailSmtpDomainRequest = new VerifyProjectEmailSmtpDomainRequest(); // VerifyProjectEmailSmtpDomainRequest | 
    try {
      apiInstance.verifyProjectEmailSmtpDomain(projectId, verifyProjectEmailSmtpDomainRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling EmailApi#verifyProjectEmailSmtpDomain");
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
| **verifyProjectEmailSmtpDomainRequest** | [**VerifyProjectEmailSmtpDomainRequest**](VerifyProjectEmailSmtpDomainRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | DNS check result |  -  |
| **400** | Bad request |  -  |

