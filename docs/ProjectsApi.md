# ProjectsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**configureOAuthProvider**](ProjectsApi.md#configureOAuthProvider) | **POST** /api/auth/oauth/projects/{projectId}/providers/{provider} | Configure OAuth provider for a project |
| [**createProject**](ProjectsApi.md#createProject) | **POST** /api/projects/{orgId}/projects | Create new project |
| [**deleteProject**](ProjectsApi.md#deleteProject) | **DELETE** /api/projects/{orgId}/projects/{id} | Delete project |
| [**getOAuthProviderConfig**](ProjectsApi.md#getOAuthProviderConfig) | **GET** /api/auth/oauth/projects/{projectId}/providers/{provider} | Get OAuth provider configuration |
| [**getProject**](ProjectsApi.md#getProject) | **GET** /api/projects/{orgId}/projects/{id} | Get single project |
| [**getProjectCaptchaConfig**](ProjectsApi.md#getProjectCaptchaConfig) | **GET** /api/projects/{orgId}/projects/{id}/auth/captcha | Get project CAPTCHA configuration |
| [**getProjectDashboardOverview**](ProjectsApi.md#getProjectDashboardOverview) | **GET** /api/projects/{projectId}/dashboard/overview | Project dashboard overview |
| [**getProjectOAuthProviders**](ProjectsApi.md#getProjectOAuthProviders) | **GET** /api/auth/oauth/projects/{projectId}/providers | Get configured OAuth providers for a project |
| [**getProjectUsage**](ProjectsApi.md#getProjectUsage) | **GET** /api/projects/{orgId}/projects/{id}/usage | Get project usage statistics |
| [**listProjects**](ProjectsApi.md#listProjects) | **GET** /api/projects/{orgId}/projects | List all projects |
| [**updateOAuthProviderConfig**](ProjectsApi.md#updateOAuthProviderConfig) | **PATCH** /api/auth/oauth/projects/{projectId}/providers/{provider} | Update OAuth provider configuration |
| [**updateProject**](ProjectsApi.md#updateProject) | **PATCH** /api/projects/{orgId}/projects/{id} | Update project |
| [**uploadProjectLogo**](ProjectsApi.md#uploadProjectLogo) | **POST** /api/projects/{id}/logo | Upload project logo (by project ID) |
| [**uploadProjectLogoByOrg**](ProjectsApi.md#uploadProjectLogoByOrg) | **POST** /api/projects/{orgId}/projects/{id}/logo | Upload project logo (by org and project ID) |


<a id="configureOAuthProvider"></a>
# **configureOAuthProvider**
> ConfigureOAuthProvider200Response configureOAuthProvider(projectId, provider, configureOAuthProviderRequest)

Configure OAuth provider for a project

Creates or updates the configuration for an OAuth provider for the specified project

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String provider = "google"; // String | 
    ConfigureOAuthProviderRequest configureOAuthProviderRequest = new ConfigureOAuthProviderRequest(); // ConfigureOAuthProviderRequest | 
    try {
      ConfigureOAuthProvider200Response result = apiInstance.configureOAuthProvider(projectId, provider, configureOAuthProviderRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#configureOAuthProvider");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **configureOAuthProviderRequest** | [**ConfigureOAuthProviderRequest**](ConfigureOAuthProviderRequest.md)|  | |

### Return type

[**ConfigureOAuthProvider200Response**](ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configured successfully |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

<a id="createProject"></a>
# **createProject**
> CreateProject201Response createProject(orgId, createProjectRequest)

Create new project

Create a new project in an organization. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    CreateProjectRequest createProjectRequest = new CreateProjectRequest(); // CreateProjectRequest | 
    try {
      CreateProject201Response result = apiInstance.createProject(orgId, createProjectRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#createProject");
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
| **orgId** | **String**| Organization ID | |
| **createProjectRequest** | [**CreateProjectRequest**](CreateProjectRequest.md)|  | |

### Return type

[**CreateProject201Response**](CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Project created |  -  |

<a id="deleteProject"></a>
# **deleteProject**
> MessageResponse deleteProject(orgId, id)

Delete project

Delete a project permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    try {
      MessageResponse result = apiInstance.deleteProject(orgId, id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#deleteProject");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project deleted |  -  |

<a id="getOAuthProviderConfig"></a>
# **getOAuthProviderConfig**
> GetOAuthProviderConfig200Response getOAuthProviderConfig(projectId, provider)

Get OAuth provider configuration

Returns the configuration for a specific OAuth provider for the project (without sensitive data)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String provider = "google"; // String | 
    try {
      GetOAuthProviderConfig200Response result = apiInstance.getOAuthProviderConfig(projectId, provider);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getOAuthProviderConfig");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |

### Return type

[**GetOAuthProviderConfig200Response**](GetOAuthProviderConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configuration |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getProject"></a>
# **getProject**
> Project getProject(orgId, id)

Get single project

Get project details by ID. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    try {
      Project result = apiInstance.getProject(orgId, id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getProject");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |

### Return type

[**Project**](Project.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project details |  -  |
| **404** | Resource not found |  -  |

<a id="getProjectCaptchaConfig"></a>
# **getProjectCaptchaConfig**
> GetProjectCaptchaConfig200Response getProjectCaptchaConfig(orgId, id)

Get project CAPTCHA configuration

Get CAPTCHA configuration for a project. This is a public endpoint that returns the site key  and settings needed for frontend integration. Secret key is never returned. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    try {
      GetProjectCaptchaConfig200Response result = apiInstance.getProjectCaptchaConfig(orgId, id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getProjectCaptchaConfig");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |

### Return type

[**GetProjectCaptchaConfig200Response**](GetProjectCaptchaConfig200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | CAPTCHA configuration |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

<a id="getProjectDashboardOverview"></a>
# **getProjectDashboardOverview**
> ProjectDashboardOverviewResponse getProjectDashboardOverview(projectId)

Project dashboard overview

Single response for the project overview UI: project info, request counts and day-over-day % change, active users (distinct JWT users with project activity; realtime socket count when available), **Uptime** (30d headline) is organization-wide when enough HTTP samples exist, else DB heartbeat probes. **Average latency** (today / 7d) is **per project** and counts only routes documented in &#x60;openapi-docs.yaml&#x60; for customer/project API (excludes auth, &#x60;/api/users&#x60;, &#x60;/api/orgs&#x60;, role-elevation, and multi-role admin routes). Request volume and active users remain per-project. 14-day API call volume and recent audit activity are per-project. See docs/dashboard-overview-api.md. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    try {
      ProjectDashboardOverviewResponse result = apiInstance.getProjectDashboardOverview(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getProjectDashboardOverview");
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

[**ProjectDashboardOverviewResponse**](ProjectDashboardOverviewResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Dashboard overview |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getProjectOAuthProviders"></a>
# **getProjectOAuthProviders**
> GetProjectOAuthProviders200Response getProjectOAuthProviders(projectId)

Get configured OAuth providers for a project

Returns a list of OAuth providers that are configured and enabled for the specified project

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    try {
      GetProjectOAuthProviders200Response result = apiInstance.getProjectOAuthProviders(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getProjectOAuthProviders");
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

[**GetProjectOAuthProviders200Response**](GetProjectOAuthProviders200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of configured OAuth providers |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getProjectUsage"></a>
# **getProjectUsage**
> ProjectUsageResponse getProjectUsage(orgId, id)

Get project usage statistics

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    try {
      ProjectUsageResponse result = apiInstance.getProjectUsage(orgId, id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#getProjectUsage");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |

### Return type

[**ProjectUsageResponse**](ProjectUsageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project usage statistics |  -  |

<a id="listProjects"></a>
# **listProjects**
> ListProjects200Response listProjects(orgId)

List all projects

List all projects in an organization. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    try {
      ListProjects200Response result = apiInstance.listProjects(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#listProjects");
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
| **orgId** | **String**| Organization ID | |

### Return type

[**ListProjects200Response**](ListProjects200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Projects list |  -  |

<a id="updateOAuthProviderConfig"></a>
# **updateOAuthProviderConfig**
> ConfigureOAuthProvider200Response updateOAuthProviderConfig(projectId, provider, updateOAuthProviderConfigRequest)

Update OAuth provider configuration

Updates the configuration for an OAuth provider for the specified project

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String provider = "google"; // String | 
    UpdateOAuthProviderConfigRequest updateOAuthProviderConfigRequest = new UpdateOAuthProviderConfigRequest(); // UpdateOAuthProviderConfigRequest | 
    try {
      ConfigureOAuthProvider200Response result = apiInstance.updateOAuthProviderConfig(projectId, provider, updateOAuthProviderConfigRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#updateOAuthProviderConfig");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **updateOAuthProviderConfigRequest** | [**UpdateOAuthProviderConfigRequest**](UpdateOAuthProviderConfigRequest.md)|  | |

### Return type

[**ConfigureOAuthProvider200Response**](ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configuration updated successfully |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

<a id="updateProject"></a>
# **updateProject**
> CreateProject201Response updateProject(orgId, id, updateProjectRequest)

Update project

Update project configuration (name, description, settings). **Settings toggles:** **requireEmailVerification** (default true) — when on, new email signups do not get a token until they verify; login is blocked until verified. **requirePhoneVerification** (default false) — when on, phone/OTP users must verify before token. **defaultUserAccountStatus** — **active** (default) or **pending**; when pending, new users must be approved by org owner/admin before they can perform data/storage operations. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    UpdateProjectRequest updateProjectRequest = new UpdateProjectRequest(); // UpdateProjectRequest | 
    try {
      CreateProject201Response result = apiInstance.updateProject(orgId, id, updateProjectRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#updateProject");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |
| **updateProjectRequest** | [**UpdateProjectRequest**](UpdateProjectRequest.md)|  | |

### Return type

[**CreateProject201Response**](CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project updated |  -  |

<a id="uploadProjectLogo"></a>
# **uploadProjectLogo**
> UploadProjectLogo200Response uploadProjectLogo(id, logo)

Upload project logo (by project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project&#39;s **logoUrl** field and used in project-related emails and UI. Project is resolved from the authenticated user&#39;s org. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String id = "id_example"; // String | Project ID
    File logo = new File("/path/to/file"); // File | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)
    try {
      UploadProjectLogo200Response result = apiInstance.uploadProjectLogo(id, logo);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#uploadProjectLogo");
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
| **id** | **String**| Project ID | |
| **logo** | **File**| Logo image (PNG, JPEG, GIF, or WebP; max 2MB) | |

### Return type

[**UploadProjectLogo200Response**](UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logo uploaded and project logoUrl updated |  -  |
| **400** | No file, invalid type, or size exceeded |  -  |
| **404** | Project not found |  -  |
| **503** | Object storage not configured |  -  |

<a id="uploadProjectLogoByOrg"></a>
# **uploadProjectLogoByOrg**
> UploadProjectLogo200Response uploadProjectLogoByOrg(orgId, id, logo)

Upload project logo (by org and project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project&#39;s **logoUrl** field. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. Requires project update permission and membership in the organization. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ProjectsApi;

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

    ProjectsApi apiInstance = new ProjectsApi(defaultClient);
    String orgId = "orgId_example"; // String | Organization ID
    String id = "id_example"; // String | Project ID
    File logo = new File("/path/to/file"); // File | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)
    try {
      UploadProjectLogo200Response result = apiInstance.uploadProjectLogoByOrg(orgId, id, logo);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ProjectsApi#uploadProjectLogoByOrg");
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
| **orgId** | **String**| Organization ID | |
| **id** | **String**| Project ID | |
| **logo** | **File**| Logo image (PNG, JPEG, GIF, or WebP; max 2MB) | |

### Return type

[**UploadProjectLogo200Response**](UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logo uploaded and project logoUrl updated |  -  |
| **400** | No file, invalid type, or size exceeded |  -  |
| **404** | Project or organization not found |  -  |
| **503** | Object storage not configured |  -  |

