# MultiRoleApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**authOauthSignupWithRole**](MultiRoleApi.md#authOauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**authRegisterWithRole**](MultiRoleApi.md#authRegisterWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |
| [**multiRoleAddRole**](MultiRoleApi.md#multiRoleAddRole) | **POST** /api/projects/{projectId}/multi-role/roles | Add custom role |
| [**multiRoleGetAvailableRoles**](MultiRoleApi.md#multiRoleGetAvailableRoles) | **GET** /api/projects/{projectId}/multi-role/roles/available | Get available roles for signup |
| [**multiRoleGetConfig**](MultiRoleApi.md#multiRoleGetConfig) | **GET** /api/projects/{projectId}/multi-role | Get multi-role feature configuration |
| [**multiRoleToggleRole**](MultiRoleApi.md#multiRoleToggleRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/toggle | Toggle role on/off |
| [**multiRoleUpdateCollectionPermissions**](MultiRoleApi.md#multiRoleUpdateCollectionPermissions) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/collections/{collectionId}/permissions | Update collection permissions for a role |
| [**multiRoleUpdateRole**](MultiRoleApi.md#multiRoleUpdateRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug} | Update role configuration |
| [**multiRoleUpdateSettings**](MultiRoleApi.md#multiRoleUpdateSettings) | **PATCH** /api/projects/{projectId}/multi-role/settings | Update multi-role feature settings |


<a id="authOauthSignupWithRole"></a>
# **authOauthSignupWithRole**
> UsersLinkOAuthProvider200Response authOauthSignupWithRole(role, provider, projectId, redirectUrl)

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project&#39;s multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String role = "vendor"; // String | Role slug for signup (e.g. customer, vendor, seller).
    String provider = "google"; // String | OAuth provider (e.g. google, github).
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    URI redirectUrl = new URI(); // URI | The URL to redirect to after authentication
    try {
      UsersLinkOAuthProvider200Response result = apiInstance.authOauthSignupWithRole(role, provider, projectId, redirectUrl);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#authOauthSignupWithRole");
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
| **role** | **String**| Role slug for signup (e.g. customer, vendor, seller). | |
| **provider** | **String**| OAuth provider (e.g. google, github). | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **projectId** | **String**| Project ID. | |
| **redirectUrl** | **URI**| The URL to redirect to after authentication | [optional] |

### Return type

[**UsersLinkOAuthProvider200Response**](UsersLinkOAuthProvider200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth signup flow initiated; in most cases the server responds with 302 redirect). |  -  |
| **302** | Redirects to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, role not found, or validation error |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authRegisterWithRole"></a>
# **authRegisterWithRole**
> authRegisterWithRole(role, authRegisterWithRoleRequest)

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The role is specified in the URL path (e.g., /signup/customer, /signup/vendor). No authentication required - this is a public signup endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String role = "customer"; // String | Role slug for signup (e.g. customer, vendor).
    AuthRegisterWithRoleRequest authRegisterWithRoleRequest = new AuthRegisterWithRoleRequest(); // AuthRegisterWithRoleRequest | Registration payload (email, password, firstName, lastName, projectId).
    try {
      apiInstance.authRegisterWithRole(role, authRegisterWithRoleRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#authRegisterWithRole");
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
| **role** | **String**| Role slug for signup (e.g. customer, vendor). | |
| **authRegisterWithRoleRequest** | [**AuthRegisterWithRoleRequest**](AuthRegisterWithRoleRequest.md)| Registration payload (email, password, firstName, lastName, projectId). | |

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Registration successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Role not found or not enabled |  -  |

<a id="multiRoleAddRole"></a>
# **multiRoleAddRole**
> MultiRoleUpdateSettings200Response multiRoleAddRole(projectId, multiRoleAddRoleRequest)

Add custom role

Add a custom role to a project with specific permissions and signup endpoint. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    MultiRoleAddRoleRequest multiRoleAddRoleRequest = new MultiRoleAddRoleRequest(); // MultiRoleAddRoleRequest | Custom role definition (slug, name, description, signupEndpoint, hierarchy, defaultPermissions).
    try {
      MultiRoleUpdateSettings200Response result = apiInstance.multiRoleAddRole(projectId, multiRoleAddRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleAddRole");
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
| **multiRoleAddRoleRequest** | [**MultiRoleAddRoleRequest**](MultiRoleAddRoleRequest.md)| Custom role definition (slug, name, description, signupEndpoint, hierarchy, defaultPermissions). | |

### Return type

[**MultiRoleUpdateSettings200Response**](MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Custom role added |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleGetAvailableRoles"></a>
# **multiRoleGetAvailableRoles**
> MultiRoleGetAvailableRoles200Response multiRoleGetAvailableRoles(projectId)

Get available roles for signup

Get all available roles for user signup in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    try {
      MultiRoleGetAvailableRoles200Response result = apiInstance.multiRoleGetAvailableRoles(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleGetAvailableRoles");
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

[**MultiRoleGetAvailableRoles200Response**](MultiRoleGetAvailableRoles200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available roles |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleGetConfig"></a>
# **multiRoleGetConfig**
> MultiRoleGetConfig200Response multiRoleGetConfig(projectId)

Get multi-role feature configuration

Get the ready-to-use multi-role system configuration for a project

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    try {
      MultiRoleGetConfig200Response result = apiInstance.multiRoleGetConfig(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleGetConfig");
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

[**MultiRoleGetConfig200Response**](MultiRoleGetConfig200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Multi-role configuration |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleToggleRole"></a>
# **multiRoleToggleRole**
> MultiRoleUpdateSettings200Response multiRoleToggleRole(projectId, roleSlug, multiRoleToggleRoleRequest)

Toggle role on/off

Enable or disable a role for the project. When disabled, the role is no longer available for signup or assignment.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    String roleSlug = "vendor"; // String | Role slug to toggle (e.g. vendor, customer).
    MultiRoleToggleRoleRequest multiRoleToggleRoleRequest = new MultiRoleToggleRoleRequest(); // MultiRoleToggleRoleRequest | Whether the role is enabled (true) or disabled (false).
    try {
      MultiRoleUpdateSettings200Response result = apiInstance.multiRoleToggleRole(projectId, roleSlug, multiRoleToggleRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleToggleRole");
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
| **roleSlug** | **String**| Role slug to toggle (e.g. vendor, customer). | |
| **multiRoleToggleRoleRequest** | [**MultiRoleToggleRoleRequest**](MultiRoleToggleRoleRequest.md)| Whether the role is enabled (true) or disabled (false). | |

### Return type

[**MultiRoleUpdateSettings200Response**](MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role toggled |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleUpdateCollectionPermissions"></a>
# **multiRoleUpdateCollectionPermissions**
> MultiRoleUpdateSettings200Response multiRoleUpdateCollectionPermissions(projectId, roleSlug, collectionId, multiRoleUpdateCollectionPermissionsRequest)

Update collection permissions for a role

Update collection-specific permissions for a role in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    String roleSlug = "vendor"; // String | Role slug (e.g. vendor, customer).
    String collectionId = "696ba6e4f4a9422ac4be4f74"; // String | Collection ID to set permissions for.
    MultiRoleUpdateCollectionPermissionsRequest multiRoleUpdateCollectionPermissionsRequest = new MultiRoleUpdateCollectionPermissionsRequest(); // MultiRoleUpdateCollectionPermissionsRequest | Allowed actions and optional conditions for the role on this collection.
    try {
      MultiRoleUpdateSettings200Response result = apiInstance.multiRoleUpdateCollectionPermissions(projectId, roleSlug, collectionId, multiRoleUpdateCollectionPermissionsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleUpdateCollectionPermissions");
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
| **roleSlug** | **String**| Role slug (e.g. vendor, customer). | |
| **collectionId** | **String**| Collection ID to set permissions for. | |
| **multiRoleUpdateCollectionPermissionsRequest** | [**MultiRoleUpdateCollectionPermissionsRequest**](MultiRoleUpdateCollectionPermissionsRequest.md)| Allowed actions and optional conditions for the role on this collection. | |

### Return type

[**MultiRoleUpdateSettings200Response**](MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection permissions updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleUpdateRole"></a>
# **multiRoleUpdateRole**
> MultiRoleUpdateSettings200Response multiRoleUpdateRole(projectId, roleSlug, multiRoleUpdateRoleRequest)

Update role configuration

Update an existing role&#39;s metadata and requirements (name, description, hierarchy, approval/payment/KYC flags).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    String roleSlug = "vendor"; // String | Role slug to update (e.g. vendor, customer).
    MultiRoleUpdateRoleRequest multiRoleUpdateRoleRequest = new MultiRoleUpdateRoleRequest(); // MultiRoleUpdateRoleRequest | Role fields to update (name, description, hierarchy, requiresApproval, requiresPayment, requiresKYC).
    try {
      MultiRoleUpdateSettings200Response result = apiInstance.multiRoleUpdateRole(projectId, roleSlug, multiRoleUpdateRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleUpdateRole");
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
| **roleSlug** | **String**| Role slug to update (e.g. vendor, customer). | |
| **multiRoleUpdateRoleRequest** | [**MultiRoleUpdateRoleRequest**](MultiRoleUpdateRoleRequest.md)| Role fields to update (name, description, hierarchy, requiresApproval, requiresPayment, requiresKYC). | |

### Return type

[**MultiRoleUpdateSettings200Response**](MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="multiRoleUpdateSettings"></a>
# **multiRoleUpdateSettings**
> MultiRoleUpdateSettings200Response multiRoleUpdateSettings(projectId, multiRoleUpdateSettingsRequest)

Update multi-role feature settings

Update multi-role feature settings for a project, including enabling/disabling the feature and configuring default roles. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MultiRoleApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MultiRoleApi apiInstance = new MultiRoleApi(defaultClient);
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID.
    MultiRoleUpdateSettingsRequest multiRoleUpdateSettingsRequest = new MultiRoleUpdateSettingsRequest(); // MultiRoleUpdateSettingsRequest | Multi-role settings (e.g. isEnabled, defaultRole, allowMultipleRoles, requireApproval).
    try {
      MultiRoleUpdateSettings200Response result = apiInstance.multiRoleUpdateSettings(projectId, multiRoleUpdateSettingsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MultiRoleApi#multiRoleUpdateSettings");
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
| **multiRoleUpdateSettingsRequest** | [**MultiRoleUpdateSettingsRequest**](MultiRoleUpdateSettingsRequest.md)| Multi-role settings (e.g. isEnabled, defaultRole, allowMultipleRoles, requireApproval). | |

### Return type

[**MultiRoleUpdateSettings200Response**](MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Settings updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

