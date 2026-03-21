# MultiRoleApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**authOauthSignupWithRole**](MultiRoleApi.md#authOauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**authRegisterWithRole**](MultiRoleApi.md#authRegisterWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |


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
    String role = "customer"; // String | Path segment must match the role's `signupEndpoint` (default `customer`; use each role's configured endpoint).
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
| **role** | **String**| Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). | |
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

Public endpoint for user registration with a specific role. The path segment must match a role&#39;s &#x60;signupEndpoint&#x60; (default starter is &#x60;customer&#x60;; add more roles via multi-role API). No authentication required - this is a public signup endpoint. 

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
    String role = "customer"; // String | Must match the role's `signupEndpoint` (default `customer`; other values for roles you add).
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
| **role** | **String**| Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). | |
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

