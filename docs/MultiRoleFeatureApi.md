# MultiRoleFeatureApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**addCustomRole**](MultiRoleFeatureApi.md#addCustomRole) | **POST** /api/projects/{projectId}/multi-role/roles | Add custom role |
| [**applyRoleFeaturePreset**](MultiRoleFeatureApi.md#applyRoleFeaturePreset) | **POST** /api/projects/{projectId}/multi-role/roles/{roleSlug}/apply-preset | Apply Admin / User / Viewer feature permission preset |
| [**getAvailableRoles**](MultiRoleFeatureApi.md#getAvailableRoles) | **GET** /api/projects/{projectId}/multi-role/roles/available | Get available roles for signup |
| [**getMultiRoleConfig**](MultiRoleFeatureApi.md#getMultiRoleConfig) | **GET** /api/projects/{projectId}/multi-role | Get multi-role feature configuration |
| [**getPermissionsMatrix**](MultiRoleFeatureApi.md#getPermissionsMatrix) | **GET** /api/projects/{projectId}/permissions-matrix | Get permissions matrix (collections + featurePermissions) |
| [**oauthSignupWithRole**](MultiRoleFeatureApi.md#oauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**registerWithRole**](MultiRoleFeatureApi.md#registerWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |
| [**simulateAppPermissions**](MultiRoleFeatureApi.md#simulateAppPermissions) | **POST** /api/projects/{projectId}/multi-role/simulate-permissions | Simulate app-role feature permission for a path |
| [**toggleRole**](MultiRoleFeatureApi.md#toggleRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/toggle | Toggle role on/off |
| [**updateCollectionPermissions**](MultiRoleFeatureApi.md#updateCollectionPermissions) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/collections/{collectionId}/permissions | Update collection permissions for a role |
| [**updateMultiRoleSettings**](MultiRoleFeatureApi.md#updateMultiRoleSettings) | **PATCH** /api/projects/{projectId}/multi-role/settings | Update multi-role feature settings |
| [**updateProjectRole**](MultiRoleFeatureApi.md#updateProjectRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug} | Update role configuration |


<a id="addCustomRole"></a>
# **addCustomRole**
> ApplyRoleFeaturePreset200Response addCustomRole(projectId, addCustomRoleRequest)

Add custom role

Add a custom role to a project with specific permissions and signup endpoint. Optional **&#x60;featurePermissions&#x60;** must align with app JWT gates — see &#x60;components/schemas/AppRoleFeaturePermissions&#x60; and &#x60;services/appRoleFeatureMap.js&#x60;. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    AddCustomRoleRequest addCustomRoleRequest = new AddCustomRoleRequest(); // AddCustomRoleRequest | 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.addCustomRole(projectId, addCustomRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#addCustomRole");
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
| **addCustomRoleRequest** | [**AddCustomRoleRequest**](AddCustomRoleRequest.md)|  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Custom role added |  -  |

<a id="applyRoleFeaturePreset"></a>
# **applyRoleFeaturePreset**
> ApplyRoleFeaturePreset200Response applyRoleFeaturePreset(projectId, roleSlug, applyRoleFeaturePresetRequest)

Apply Admin / User / Viewer feature permission preset

Sets &#x60;featurePermissions&#x60; on the role from a bundled preset (&#x60;admin&#x60;, &#x60;user&#x60;, &#x60;viewer&#x60;). Does not change collection CRUD or &#x60;dataScope&#x60;; use collection permission APIs for those. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String roleSlug = "roleSlug_example"; // String | 
    ApplyRoleFeaturePresetRequest applyRoleFeaturePresetRequest = new ApplyRoleFeaturePresetRequest(); // ApplyRoleFeaturePresetRequest | 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.applyRoleFeaturePreset(projectId, roleSlug, applyRoleFeaturePresetRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#applyRoleFeaturePreset");
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
| **roleSlug** | **String**|  | |
| **applyRoleFeaturePresetRequest** | [**ApplyRoleFeaturePresetRequest**](ApplyRoleFeaturePresetRequest.md)|  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Preset applied |  -  |
| **400** | Bad request |  -  |

<a id="getAvailableRoles"></a>
# **getAvailableRoles**
> GetAvailableRoles200Response getAvailableRoles(projectId)

Get available roles for signup

Get all available roles for user signup in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    try {
      GetAvailableRoles200Response result = apiInstance.getAvailableRoles(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#getAvailableRoles");
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

[**GetAvailableRoles200Response**](GetAvailableRoles200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available roles |  -  |

<a id="getMultiRoleConfig"></a>
# **getMultiRoleConfig**
> GetMultiRoleConfig200Response getMultiRoleConfig(projectId)

Get multi-role feature configuration

Returns project app roles (default one editable &#x60;customer&#x60; starter until you add more) and settings

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    try {
      GetMultiRoleConfig200Response result = apiInstance.getMultiRoleConfig(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#getMultiRoleConfig");
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

[**GetMultiRoleConfig200Response**](GetMultiRoleConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Multi-role configuration |  -  |

<a id="getPermissionsMatrix"></a>
# **getPermissionsMatrix**
> GetPermissionsMatrix200Response getPermissionsMatrix(projectId)

Get permissions matrix (collections + featurePermissions)

Dashboard helper: per-collection permission rows (role actions, &#x60;dataScope&#x60;, conditions) and a per-role &#x60;featurePermissions&#x60; snapshot used by app-role feature gates (messaging, integrations, storage, etc.). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    try {
      GetPermissionsMatrix200Response result = apiInstance.getPermissionsMatrix(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#getPermissionsMatrix");
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

[**GetPermissionsMatrix200Response**](GetPermissionsMatrix200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Matrix payload |  -  |

<a id="oauthSignupWithRole"></a>
# **oauthSignupWithRole**
> oauthSignupWithRole(role, provider, projectId, redirectUrl)

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project&#39;s multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String role = "customer"; // String | Path segment must match the role's `signupEndpoint` (default `customer`; use each role's configured endpoint).
    String provider = "google"; // String | 
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    URI redirectUrl = new URI(); // URI | The URL to redirect to after authentication
    try {
      apiInstance.oauthSignupWithRole(role, provider, projectId, redirectUrl);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#oauthSignupWithRole");
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
| **role** | **String**| Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). | |
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **projectId** | **String**|  | |
| **redirectUrl** | **URI**| The URL to redirect to after authentication | [optional] |

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirects to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, role not found, or validation error |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

<a id="registerWithRole"></a>
# **registerWithRole**
> RegisterWithRole201Response registerWithRole(role, registerWithRoleRequest)

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The path segment must match a role&#39;s &#x60;signupEndpoint&#x60; (default starter is &#x60;customer&#x60;; add more roles via multi-role API). No authentication required - this is a public signup endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String role = "customer"; // String | Must match the role's `signupEndpoint` (default `customer`; other values for roles you add).
    RegisterWithRoleRequest registerWithRoleRequest = new RegisterWithRoleRequest(); // RegisterWithRoleRequest | 
    try {
      RegisterWithRole201Response result = apiInstance.registerWithRole(role, registerWithRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#registerWithRole");
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
| **role** | **String**| Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). | |
| **registerWithRoleRequest** | [**RegisterWithRoleRequest**](RegisterWithRoleRequest.md)|  | |

### Return type

[**RegisterWithRole201Response**](RegisterWithRole201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Registration successful. Two response shapes depending on the project&#39;s &#x60;requireEmailVerification&#x60; setting - see &#x60;requireVerification&#x60; to distinguish them; &#x60;token&#x60;/&#x60;refreshToken&#x60;/&#x60;expiresIn&#x60; are only present when a session was issued immediately. |  -  |
| **400** | Validation failed, or a user with this email already exists for the project |  -  |
| **403** | Role requires approval, payment, or KYC before it can be self-assigned |  -  |
| **404** | Role not found or not enabled |  -  |

<a id="simulateAppPermissions"></a>
# **simulateAppPermissions**
> SimulateAppPermissions200Response simulateAppPermissions(projectId, simulateAppPermissionsRequest)

Simulate app-role feature permission for a path

Dashboard-only. Given an app role slug and either an OpenAPI &#x60;operationId&#x60; **or** HTTP method + pathname, returns whether the role&#39;s &#x60;featurePermissions&#x60; would allow the operation for paths that have a feature gate. Unmapped paths or unknown operation IDs return &#x60;allowed: true&#x60; with reason &#x60;no_feature_gate_for_path&#x60; or &#x60;no_feature_gate_for_operation_id&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    SimulateAppPermissionsRequest simulateAppPermissionsRequest = new SimulateAppPermissionsRequest(); // SimulateAppPermissionsRequest | 
    try {
      SimulateAppPermissions200Response result = apiInstance.simulateAppPermissions(projectId, simulateAppPermissionsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#simulateAppPermissions");
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
| **simulateAppPermissionsRequest** | [**SimulateAppPermissionsRequest**](SimulateAppPermissionsRequest.md)|  | |

### Return type

[**SimulateAppPermissions200Response**](SimulateAppPermissions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Simulation result |  -  |

<a id="toggleRole"></a>
# **toggleRole**
> ApplyRoleFeaturePreset200Response toggleRole(projectId, roleSlug, toggleRoleRequest)

Toggle role on/off

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String roleSlug = "customer"; // String | Role slug to toggle (e.g. starter `customer` or a role you added).
    ToggleRoleRequest toggleRoleRequest = new ToggleRoleRequest(); // ToggleRoleRequest | 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.toggleRole(projectId, roleSlug, toggleRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#toggleRole");
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
| **roleSlug** | **String**| Role slug to toggle (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **toggleRoleRequest** | [**ToggleRoleRequest**](ToggleRoleRequest.md)|  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role toggled |  -  |

<a id="updateCollectionPermissions"></a>
# **updateCollectionPermissions**
> ApplyRoleFeaturePreset200Response updateCollectionPermissions(projectId, roleSlug, collectionId, updateCollectionPermissionsRequest)

Update collection permissions for a role

Update collection-specific permissions for a role in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String roleSlug = "customer"; // String | Role slug (e.g. starter `customer` or a role you added).
    String collectionId = "696ba6e4f4a9422ac4be4f74"; // String | 
    UpdateCollectionPermissionsRequest updateCollectionPermissionsRequest = new UpdateCollectionPermissionsRequest(); // UpdateCollectionPermissionsRequest | 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.updateCollectionPermissions(projectId, roleSlug, collectionId, updateCollectionPermissionsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#updateCollectionPermissions");
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
| **roleSlug** | **String**| Role slug (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **collectionId** | **String**|  | |
| **updateCollectionPermissionsRequest** | [**UpdateCollectionPermissionsRequest**](UpdateCollectionPermissionsRequest.md)|  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection permissions updated |  -  |

<a id="updateMultiRoleSettings"></a>
# **updateMultiRoleSettings**
> UpdateMultiRoleSettings200Response updateMultiRoleSettings(projectId, updateMultiRoleSettingsRequest)

Update multi-role feature settings

Update multi-role feature settings for a project: enable/disable the feature, set which app role is the default at signup, and tune &#x60;settings&#x60; (&#x60;allowMultipleRoles&#x60;, &#x60;requireRoleSelection&#x60;, &#x60;autoAssignDefault&#x60;). This endpoint does **not** edit role definitions or permissions — use &#x60;POST/PATCH .../multi-role/roles&#x60; for that (same shape as **Add custom role**). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    UpdateMultiRoleSettingsRequest updateMultiRoleSettingsRequest = new UpdateMultiRoleSettingsRequest(); // UpdateMultiRoleSettingsRequest | 
    try {
      UpdateMultiRoleSettings200Response result = apiInstance.updateMultiRoleSettings(projectId, updateMultiRoleSettingsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#updateMultiRoleSettings");
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
| **updateMultiRoleSettingsRequest** | [**UpdateMultiRoleSettingsRequest**](UpdateMultiRoleSettingsRequest.md)|  | |

### Return type

[**UpdateMultiRoleSettings200Response**](UpdateMultiRoleSettings200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Settings updated |  -  |

<a id="updateProjectRole"></a>
# **updateProjectRole**
> ApplyRoleFeaturePreset200Response updateProjectRole(projectId, roleSlug, updateProjectRoleRequest)

Update role configuration

Partial update of an app role. **&#x60;featurePermissions&#x60;** keys must match the app-role gate map (&#x60;services/appRoleFeatureMap.js&#x60;); schema: &#x60;components/schemas/AppRoleFeaturePermissions&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleFeatureApi;

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

    MultiRoleFeatureApi apiInstance = new MultiRoleFeatureApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String roleSlug = "customer"; // String | Role slug to update (e.g. starter `customer` or a role you added).
    UpdateProjectRoleRequest updateProjectRoleRequest = new UpdateProjectRoleRequest(); // UpdateProjectRoleRequest | Same fields as **Add custom role** — send only fields you want to change. `defaultPermissions` / `collectionPermissions` are normalized the same way as on create. **`featurePermissions`:** `components/schemas/AppRoleFeaturePermissions` (aligned with `services/appRoleFeatureMap.js`). 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.updateProjectRole(projectId, roleSlug, updateProjectRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleFeatureApi#updateProjectRole");
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
| **roleSlug** | **String**| Role slug to update (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **updateProjectRoleRequest** | [**UpdateProjectRoleRequest**](UpdateProjectRoleRequest.md)| Same fields as **Add custom role** — send only fields you want to change. &#x60;defaultPermissions&#x60; / &#x60;collectionPermissions&#x60; are normalized the same way as on create. **&#x60;featurePermissions&#x60;:** &#x60;components/schemas/AppRoleFeaturePermissions&#x60; (aligned with &#x60;services/appRoleFeatureMap.js&#x60;).  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

