# AuthenticationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**acceptInvite**](AuthenticationApi.md#acceptInvite) | **POST** /api/auth/accept-invite | Accept organization invitation |
| [**confirmLocalPasswordResetWithOtp**](AuthenticationApi.md#confirmLocalPasswordResetWithOtp) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP (project-based) |
| [**convertAnonymousAccount**](AuthenticationApi.md#convertAnonymousAccount) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**createAnonymousSession**](AuthenticationApi.md#createAnonymousSession) | **POST** /api/auth/anonymous | Create anonymous session |
| [**getAvailableOAuthProviders**](AuthenticationApi.md#getAvailableOAuthProviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**getCurrentSession**](AuthenticationApi.md#getCurrentSession) | **GET** /api/auth/session | Get current session |
| [**getLocalSession**](AuthenticationApi.md#getLocalSession) | **GET** /api/auth/local/session | Get current session (project-based) |
| [**getOrgOAuthProviders**](AuthenticationApi.md#getOrgOAuthProviders) | **GET** /api/auth/oauth-org/providers | Get available OAuth providers for organization-based auth |
| [**initiateOAuth**](AuthenticationApi.md#initiateOAuth) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**initiateOrgOAuth**](AuthenticationApi.md#initiateOrgOAuth) | **GET** /api/auth/oauth-org/{provider} | Initiate OAuth authentication for organization |
| [**loginLocalUser**](AuthenticationApi.md#loginLocalUser) | **POST** /api/auth/local/login | Login user (project-based) |
| [**loginUser**](AuthenticationApi.md#loginUser) | **POST** /api/auth/login | Login user |
| [**logoutLocalUser**](AuthenticationApi.md#logoutLocalUser) | **POST** /api/auth/local/logout | Logout user (project-based) |
| [**logoutUser**](AuthenticationApi.md#logoutUser) | **POST** /api/auth/logout | Logout user |
| [**oauthCallback**](AuthenticationApi.md#oauthCallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler (project-based) |
| [**orgOAuthCallback**](AuthenticationApi.md#orgOAuthCallback) | **GET** /api/auth/oauth-org/callback/{provider} | OAuth callback handler for organization |
| [**refreshToken**](AuthenticationApi.md#refreshToken) | **POST** /api/auth/refresh | Refresh access token (org and project) |
| [**registerLocalUser**](AuthenticationApi.md#registerLocalUser) | **POST** /api/auth/local/register | Register new user (project-based) |
| [**registerUser**](AuthenticationApi.md#registerUser) | **POST** /api/auth/register | Register new user |
| [**requestLocalPasswordReset**](AuthenticationApi.md#requestLocalPasswordReset) | **POST** /api/auth/local/password-reset | Request password reset (project-based, OTP) |
| [**requestPasswordReset**](AuthenticationApi.md#requestPasswordReset) | **POST** /api/auth/password-reset | Request password reset (organization / platform) |
| [**resendVerificationAuth**](AuthenticationApi.md#resendVerificationAuth) | **POST** /api/auth/resend-verification | Resend verification email (no auth) |
| [**resetLocalPassword**](AuthenticationApi.md#resetLocalPassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (project-based, legacy) |
| [**resetPassword**](AuthenticationApi.md#resetPassword) | **POST** /api/auth/password-reset/{token} | Reset password with token (organization / platform) |
| [**sendMagicLink**](AuthenticationApi.md#sendMagicLink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**sendOTP**](AuthenticationApi.md#sendOTP) | **POST** /api/auth/otp/send | Send OTP code |
| [**validatePasswordResetToken**](AuthenticationApi.md#validatePasswordResetToken) | **POST** /api/auth/password-reset/validate | Validate password reset token |
| [**verifyEmailAuth**](AuthenticationApi.md#verifyEmailAuth) | **POST** /api/auth/verify-email | Verify email address (no auth) |
| [**verifyMagicLink**](AuthenticationApi.md#verifyMagicLink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**verifyOTP**](AuthenticationApi.md#verifyOTP) | **POST** /api/auth/otp/verify | Verify OTP code |


<a id="acceptInvite"></a>
# **acceptInvite**
> AcceptInvite201Response acceptInvite(acceptInviteRequest)

Accept organization invitation

Accept an organization invitation using the token from the invite email link (e.g. &#x60;/invite/{token}?orgId&#x3D;...&#x60;). Creates a new user with the invited email and adds them to the organization with the invited role. Returns a JWT and user so the client can log the user in immediately. No authentication required. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    AcceptInviteRequest acceptInviteRequest = new AcceptInviteRequest(); // AcceptInviteRequest | 
    try {
      AcceptInvite201Response result = apiInstance.acceptInvite(acceptInviteRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#acceptInvite");
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
| **acceptInviteRequest** | [**AcceptInviteRequest**](AcceptInviteRequest.md)|  | |

### Return type

[**AcceptInvite201Response**](AcceptInvite201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Invitation accepted; user created and added to organization |  -  |
| **400** | Invalid or expired token, or user already exists with this email |  -  |
| **404** | Organization not found |  -  |
| **500** | Internal server error |  -  |

<a id="confirmLocalPasswordResetWithOtp"></a>
# **confirmLocalPasswordResetWithOtp**
> MessageResponse confirmLocalPasswordResetWithOtp(confirmLocalPasswordResetWithOtpRequest)

Confirm password reset with OTP (project-based)

Set new password using the OTP sent to the user&#39;s email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user&#39;s email was not yet verified, it is marked as verified upon successful reset. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    ConfirmLocalPasswordResetWithOtpRequest confirmLocalPasswordResetWithOtpRequest = new ConfirmLocalPasswordResetWithOtpRequest(); // ConfirmLocalPasswordResetWithOtpRequest | 
    try {
      MessageResponse result = apiInstance.confirmLocalPasswordResetWithOtp(confirmLocalPasswordResetWithOtpRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#confirmLocalPasswordResetWithOtp");
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
| **confirmLocalPasswordResetWithOtpRequest** | [**ConfirmLocalPasswordResetWithOtpRequest**](ConfirmLocalPasswordResetWithOtpRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password reset successful |  -  |
| **400** | Invalid or expired OTP, or validation error |  -  |
| **404** | Resource not found |  -  |
| **429** | Too many attempts (rate limit) |  -  |
| **500** | Internal server error |  -  |

<a id="convertAnonymousAccount"></a>
# **convertAnonymousAccount**
> ConvertAnonymousAccount200Response convertAnonymousAccount(convertAnonymousAccountRequest)

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

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

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    ConvertAnonymousAccountRequest convertAnonymousAccountRequest = new ConvertAnonymousAccountRequest(); // ConvertAnonymousAccountRequest | 
    try {
      ConvertAnonymousAccount200Response result = apiInstance.convertAnonymousAccount(convertAnonymousAccountRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#convertAnonymousAccount");
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
| **convertAnonymousAccountRequest** | [**ConvertAnonymousAccountRequest**](ConvertAnonymousAccountRequest.md)|  | |

### Return type

[**ConvertAnonymousAccount200Response**](ConvertAnonymousAccount200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account converted successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="createAnonymousSession"></a>
# **createAnonymousSession**
> CreateAnonymousSession200Response createAnonymousSession(createAnonymousSessionRequest)

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    CreateAnonymousSessionRequest createAnonymousSessionRequest = new CreateAnonymousSessionRequest(); // CreateAnonymousSessionRequest | 
    try {
      CreateAnonymousSession200Response result = apiInstance.createAnonymousSession(createAnonymousSessionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#createAnonymousSession");
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
| **createAnonymousSessionRequest** | [**CreateAnonymousSessionRequest**](CreateAnonymousSessionRequest.md)|  | [optional] |

### Return type

[**CreateAnonymousSession200Response**](CreateAnonymousSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Anonymous session created |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getAvailableOAuthProviders"></a>
# **getAvailableOAuthProviders**
> GetAvailableOAuthProviders200Response getAvailableOAuthProviders()

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    try {
      GetAvailableOAuthProviders200Response result = apiInstance.getAvailableOAuthProviders();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#getAvailableOAuthProviders");
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

[**GetAvailableOAuthProviders200Response**](GetAvailableOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |

<a id="getCurrentSession"></a>
# **getCurrentSession**
> SessionResponse getCurrentSession()

Get current session

Get the current authenticated user session information. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

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

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    try {
      SessionResponse result = apiInstance.getCurrentSession();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#getCurrentSession");
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

[**SessionResponse**](SessionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |

<a id="getLocalSession"></a>
# **getLocalSession**
> GetLocalSession200Response getLocalSession(projectId)

Get current session (project-based)

Get the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

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

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetLocalSession200Response result = apiInstance.getLocalSession(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#getLocalSession");
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

### Return type

[**GetLocalSession200Response**](GetLocalSession200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getOrgOAuthProviders"></a>
# **getOrgOAuthProviders**
> GetOrgOAuthProviders200Response getOrgOAuthProviders()

Get available OAuth providers for organization-based auth

Returns a list of OAuth providers that are configured and available for organization-based authentication. Providers are configured via environment variables (e.g., GOOGLE_CLIENT_ID, GITHUB_CLIENT_ID). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    try {
      GetOrgOAuthProviders200Response result = apiInstance.getOrgOAuthProviders();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#getOrgOAuthProviders");
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

[**GetOrgOAuthProviders200Response**](GetOrgOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |

<a id="initiateOAuth"></a>
# **initiateOAuth**
> initiateOAuth(provider, projectId, redirectUrl)

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. Returns an HTTP 302 redirect to the OAuth provider&#39;s consent screen. Note: Swagger \&quot;Try it out\&quot; may show \&quot;Failed to fetch\&quot; for this endpoint due to browser CORS restrictions on cross-origin redirects. Use top-level browser navigation or curl to test. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String provider = "google"; // String | 
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    URI redirectUrl = new URI(); // URI | The URL to redirect to after authentication. Must be pre-registered in project settings.
    try {
      apiInstance.initiateOAuth(provider, projectId, redirectUrl);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#initiateOAuth");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **projectId** | **String**|  | |
| **redirectUrl** | **URI**| The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional] |

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
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, not enabled, or missing required server/provider credentials |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

<a id="initiateOrgOAuth"></a>
# **initiateOrgOAuth**
> initiateOrgOAuth(provider, redirectUrl)

Initiate OAuth authentication for organization

Initiates OAuth authentication flow for organization-level signup/login. The OAuth provider must be configured via environment variables (e.g., GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET). After successful authentication, creates a new organization and user account, or logs in existing user. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String provider = "google"; // String | 
    URI redirectUrl = new URI(); // URI | The URL to redirect to after authentication
    try {
      apiInstance.initiateOrgOAuth(provider, redirectUrl);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#initiateOrgOAuth");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, discord, linkedin] |
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
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured or not supported |  -  |
| **500** | Internal server error |  -  |

<a id="loginLocalUser"></a>
# **loginLocalUser**
> LoginLocalUser200Response loginLocalUser(loginLocalUserRequest)

Login user (project-based)

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    LoginLocalUserRequest loginLocalUserRequest = new LoginLocalUserRequest(); // LoginLocalUserRequest | 
    try {
      LoginLocalUser200Response result = apiInstance.loginLocalUser(loginLocalUserRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#loginLocalUser");
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
| **loginLocalUserRequest** | [**LoginLocalUserRequest**](LoginLocalUserRequest.md)|  | |

### Return type

[**LoginLocalUser200Response**](LoginLocalUser200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Login successful |  -  |
| **401** | Authentication required |  -  |
| **403** | Email verification required (project has requireEmailVerification and user has not verified) |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

<a id="loginUser"></a>
# **loginUser**
> AuthResponse loginUser(loginRequest)

Login user

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    LoginRequest loginRequest = new LoginRequest(); // LoginRequest | 
    try {
      AuthResponse result = apiInstance.loginUser(loginRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#loginUser");
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
| **loginRequest** | [**LoginRequest**](LoginRequest.md)|  | |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Login successful |  -  |
| **401** | Authentication required |  -  |

<a id="logoutLocalUser"></a>
# **logoutLocalUser**
> MessageResponse logoutLocalUser()

Logout user (project-based)

Logout the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

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

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    try {
      MessageResponse result = apiInstance.logoutLocalUser();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#logoutLocalUser");
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

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logout successful |  -  |

<a id="logoutUser"></a>
# **logoutUser**
> MessageResponse logoutUser()

Logout user

Logout the current authenticated user session. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

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

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    try {
      MessageResponse result = apiInstance.logoutUser();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#logoutUser");
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

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logout successful |  -  |

<a id="oauthCallback"></a>
# **oauthCallback**
> oauthCallback(provider)

OAuth callback handler (project-based)

Handles OAuth callback for project-based authentication. This route must be matched before /api/auth/oauth/{provider}/{projectId}. Redirects to frontend with query params token, refreshToken, and expiresIn. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String provider = "provider_example"; // String | 
    try {
      apiInstance.oauthCallback(provider);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#oauthCallback");
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
| **provider** | **String**|  | |

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
| **302** | Redirect with token, refreshToken, and expiresIn |  * Location - URL with token, refreshToken, expiresIn query params <br>  |
| **400** | Bad request |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="orgOAuthCallback"></a>
# **orgOAuthCallback**
> orgOAuthCallback(provider, code, state)

OAuth callback handler for organization

Handles OAuth callback for organization-based authentication. Creates a new organization and user account if the user doesn&#39;t exist, or logs in existing user. Redirects to frontend with query params token, refreshToken, and expiresIn. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String provider = "google"; // String | 
    String code = "code_example"; // String | Authorization code from OAuth provider
    String state = "state_example"; // String | State parameter for CSRF protection
    try {
      apiInstance.orgOAuthCallback(provider, code, state);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#orgOAuthCallback");
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
| **provider** | **String**|  | [enum: google, github, facebook, microsoft, discord, linkedin] |
| **code** | **String**| Authorization code from OAuth provider | [optional] |
| **state** | **String**| State parameter for CSRF protection | [optional] |

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
| **302** | Redirect with authentication result |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth authentication failed |  -  |
| **500** | Internal server error |  -  |

<a id="refreshToken"></a>
# **refreshToken**
> RefreshToken200Response refreshToken(refreshTokenRequest)

Refresh access token (org and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **org-based** (platform/dashboard) and **project-based** auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    RefreshTokenRequest refreshTokenRequest = new RefreshTokenRequest(); // RefreshTokenRequest | 
    try {
      RefreshToken200Response result = apiInstance.refreshToken(refreshTokenRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#refreshToken");
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
| **refreshTokenRequest** | [**RefreshTokenRequest**](RefreshTokenRequest.md)|  | |

### Return type

[**RefreshToken200Response**](RefreshToken200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | New token pair issued |  -  |
| **400** | Missing refresh token |  -  |
| **401** | Invalid or expired refresh token (or reuse detected) |  -  |

<a id="registerLocalUser"></a>
# **registerLocalUser**
> RegisterLocalUser201Response registerLocalUser(registerLocalUserRequest)

Register new user (project-based)

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    RegisterLocalUserRequest registerLocalUserRequest = new RegisterLocalUserRequest(); // RegisterLocalUserRequest | 
    try {
      RegisterLocalUser201Response result = apiInstance.registerLocalUser(registerLocalUserRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#registerLocalUser");
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
| **registerLocalUserRequest** | [**RegisterLocalUserRequest**](RegisterLocalUserRequest.md)|  | |

### Return type

[**RegisterLocalUser201Response**](RegisterLocalUser201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | When project.requireEmailVerification is on (default): no token returned; use requireVerification and message to prompt email verification, then user signs in via login. When off: token and refreshToken returned.  |  -  |
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

<a id="registerUser"></a>
# **registerUser**
> AuthResponse registerUser(registerRequest)

Register new user

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    RegisterRequest registerRequest = new RegisterRequest(); // RegisterRequest | 
    try {
      AuthResponse result = apiInstance.registerUser(registerRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#registerUser");
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
| **registerRequest** | [**RegisterRequest**](RegisterRequest.md)|  | |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | User registered successfully |  -  |
| **400** | Bad request |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

<a id="requestLocalPasswordReset"></a>
# **requestLocalPasswordReset**
> MessageResponse requestLocalPasswordReset(requestLocalPasswordResetRequest)

Request password reset (project-based, OTP)

When projectId is provided, sends a 6-digit OTP to the user&#39;s email (project-based reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    RequestLocalPasswordResetRequest requestLocalPasswordResetRequest = new RequestLocalPasswordResetRequest(); // RequestLocalPasswordResetRequest | 
    try {
      MessageResponse result = apiInstance.requestLocalPasswordReset(requestLocalPasswordResetRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#requestLocalPasswordReset");
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
| **requestLocalPasswordResetRequest** | [**RequestLocalPasswordResetRequest**](RequestLocalPasswordResetRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OTP or reset email sent (generic message to prevent enumeration) |  -  |
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |
| **429** | Too many requests (rate limit) |  -  |
| **500** | Internal server error |  -  |

<a id="requestPasswordReset"></a>
# **requestPasswordReset**
> MessageResponse requestPasswordReset(requestPasswordResetRequest)

Request password reset (organization / platform)

Sends a password reset link to the user&#39;s email. Use this for organization (platform) accounts. For project-based accounts use POST /api/auth/local/password-reset with projectId (sends OTP instead). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    RequestPasswordResetRequest requestPasswordResetRequest = new RequestPasswordResetRequest(); // RequestPasswordResetRequest | 
    try {
      MessageResponse result = apiInstance.requestPasswordReset(requestPasswordResetRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#requestPasswordReset");
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
| **requestPasswordResetRequest** | [**RequestPasswordResetRequest**](RequestPasswordResetRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password reset email sent (or generic message to prevent enumeration) |  -  |

<a id="resendVerificationAuth"></a>
# **resendVerificationAuth**
> MessageResponse resendVerificationAuth(resendVerificationAuthRequest)

Resend verification email (no auth)

Sends a new verification email to the given email (and optional project). For unauthenticated users who have not verified yet. Rate limited (e.g. 3 per 15 min per IP). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    ResendVerificationAuthRequest resendVerificationAuthRequest = new ResendVerificationAuthRequest(); // ResendVerificationAuthRequest | 
    try {
      MessageResponse result = apiInstance.resendVerificationAuth(resendVerificationAuthRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#resendVerificationAuth");
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
| **resendVerificationAuthRequest** | [**ResendVerificationAuthRequest**](ResendVerificationAuthRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Verification email sent (or generic message to prevent enumeration) |  -  |
| **400** | Email required |  -  |
| **429** | Too many requests (rate limit) |  -  |

<a id="resetLocalPassword"></a>
# **resetLocalPassword**
> MessageResponse resetLocalPassword(token, resetLocalPasswordRequest)

Reset password with token (project-based, legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for project-based resets. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String token = "token_example"; // String | 
    ResetLocalPasswordRequest resetLocalPasswordRequest = new ResetLocalPasswordRequest(); // ResetLocalPasswordRequest | 
    try {
      MessageResponse result = apiInstance.resetLocalPassword(token, resetLocalPasswordRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#resetLocalPassword");
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
| **token** | **String**|  | |
| **resetLocalPasswordRequest** | [**ResetLocalPasswordRequest**](ResetLocalPasswordRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password reset successful |  -  |
| **400** | Bad request |  -  |
| **500** | Internal server error |  -  |

<a id="resetPassword"></a>
# **resetPassword**
> MessageResponse resetPassword(token, resetPasswordRequest)

Reset password with token (organization / platform)

Set new password using the token from the reset link. Validate the token first with POST /api/auth/password-reset/validate before showing the form. If the user&#39;s email was not yet verified, it is marked as verified upon successful reset. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    String token = "token_example"; // String | 
    ResetPasswordRequest resetPasswordRequest = new ResetPasswordRequest(); // ResetPasswordRequest | 
    try {
      MessageResponse result = apiInstance.resetPassword(token, resetPasswordRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#resetPassword");
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
| **token** | **String**|  | |
| **resetPasswordRequest** | [**ResetPasswordRequest**](ResetPasswordRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password reset successful |  -  |

<a id="sendMagicLink"></a>
# **sendMagicLink**
> MessageResponse sendMagicLink(magicLinkRequest)

Send magic link

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    MagicLinkRequest magicLinkRequest = new MagicLinkRequest(); // MagicLinkRequest | 
    try {
      MessageResponse result = apiInstance.sendMagicLink(magicLinkRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#sendMagicLink");
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
| **magicLinkRequest** | [**MagicLinkRequest**](MagicLinkRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Magic link sent |  -  |

<a id="sendOTP"></a>
# **sendOTP**
> MessageResponse sendOTP(otPSendRequest)

Send OTP code

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    OTPSendRequest otPSendRequest = new OTPSendRequest(); // OTPSendRequest | 
    try {
      MessageResponse result = apiInstance.sendOTP(otPSendRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#sendOTP");
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
| **otPSendRequest** | [**OTPSendRequest**](OTPSendRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OTP sent |  -  |

<a id="validatePasswordResetToken"></a>
# **validatePasswordResetToken**
> ValidatePasswordResetToken200Response validatePasswordResetToken(validatePasswordResetTokenRequest)

Validate password reset token

Call before showing the \&quot;set new password\&quot; form. Validates that the token from the reset link is still valid and not expired. Organization (platform) reset only. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    ValidatePasswordResetTokenRequest validatePasswordResetTokenRequest = new ValidatePasswordResetTokenRequest(); // ValidatePasswordResetTokenRequest | 
    try {
      ValidatePasswordResetToken200Response result = apiInstance.validatePasswordResetToken(validatePasswordResetTokenRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#validatePasswordResetToken");
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
| **validatePasswordResetTokenRequest** | [**ValidatePasswordResetTokenRequest**](ValidatePasswordResetTokenRequest.md)|  | |

### Return type

[**ValidatePasswordResetToken200Response**](ValidatePasswordResetToken200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Token is valid |  -  |
| **400** | Token invalid or expired |  -  |

<a id="verifyEmailAuth"></a>
# **verifyEmailAuth**
> MessageResponse verifyEmailAuth(verifyEmailAuthRequest)

Verify email address (no auth)

Verifies the user&#39;s email using the token from the link sent at signup. Use this for both organization and project signups (unauthenticated). Same behavior as POST /api/users/verify-email. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    VerifyEmailAuthRequest verifyEmailAuthRequest = new VerifyEmailAuthRequest(); // VerifyEmailAuthRequest | 
    try {
      MessageResponse result = apiInstance.verifyEmailAuth(verifyEmailAuthRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#verifyEmailAuth");
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
| **verifyEmailAuthRequest** | [**VerifyEmailAuthRequest**](VerifyEmailAuthRequest.md)|  | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Email verified |  -  |
| **400** | Invalid or missing token |  -  |

<a id="verifyMagicLink"></a>
# **verifyMagicLink**
> AuthResponse verifyMagicLink(verifyMagicLinkRequest)

Verify magic link

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    VerifyMagicLinkRequest verifyMagicLinkRequest = new VerifyMagicLinkRequest(); // VerifyMagicLinkRequest | 
    try {
      AuthResponse result = apiInstance.verifyMagicLink(verifyMagicLinkRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#verifyMagicLink");
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
| **verifyMagicLinkRequest** | [**VerifyMagicLinkRequest**](VerifyMagicLinkRequest.md)|  | |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Magic link verified |  -  |

<a id="verifyOTP"></a>
# **verifyOTP**
> AuthResponse verifyOTP(otPVerifyRequest)

Verify OTP code

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.AuthenticationApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthenticationApi apiInstance = new AuthenticationApi(defaultClient);
    OTPVerifyRequest otPVerifyRequest = new OTPVerifyRequest(); // OTPVerifyRequest | 
    try {
      AuthResponse result = apiInstance.verifyOTP(otPVerifyRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthenticationApi#verifyOTP");
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
| **otPVerifyRequest** | [**OTPVerifyRequest**](OTPVerifyRequest.md)|  | |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OTP verified |  -  |

