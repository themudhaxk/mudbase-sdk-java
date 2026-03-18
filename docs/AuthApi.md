# AuthApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**authConfirmPasswordReset**](AuthApi.md#authConfirmPasswordReset) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP |
| [**authConvertAnonymous**](AuthApi.md#authConvertAnonymous) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**authCreateAnonymous**](AuthApi.md#authCreateAnonymous) | **POST** /api/auth/anonymous | Create anonymous session |
| [**authGetOAuthProviders**](AuthApi.md#authGetOAuthProviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**authGetSession**](AuthApi.md#authGetSession) | **GET** /api/auth/local/session | Get current session |
| [**authLogin**](AuthApi.md#authLogin) | **POST** /api/auth/local/login | Login user |
| [**authLogout**](AuthApi.md#authLogout) | **POST** /api/auth/local/logout | Logout user |
| [**authOauthCallback**](AuthApi.md#authOauthCallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler |
| [**authOauthInitiate**](AuthApi.md#authOauthInitiate) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**authRefresh**](AuthApi.md#authRefresh) | **POST** /api/auth/refresh | Refresh access token (org and project) |
| [**authRegister**](AuthApi.md#authRegister) | **POST** /api/auth/local/register | Register new user |
| [**authRequestPasswordReset**](AuthApi.md#authRequestPasswordReset) | **POST** /api/auth/local/password-reset | Request password reset (OTP) |
| [**authResetPassword**](AuthApi.md#authResetPassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (legacy) |
| [**authSendMagicLink**](AuthApi.md#authSendMagicLink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**authSendOtp**](AuthApi.md#authSendOtp) | **POST** /api/auth/otp/send | Send OTP code |
| [**authVerifyMagicLink**](AuthApi.md#authVerifyMagicLink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**authVerifyOtp**](AuthApi.md#authVerifyOtp) | **POST** /api/auth/otp/verify | Verify OTP code |


<a id="authConfirmPasswordReset"></a>
# **authConfirmPasswordReset**
> MessageResponse authConfirmPasswordReset(authConfirmPasswordResetRequest)

Confirm password reset with OTP

Set new password using the OTP sent to the user&#39;s email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user&#39;s email was not yet verified, it is marked as verified upon successful reset. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthConfirmPasswordResetRequest authConfirmPasswordResetRequest = new AuthConfirmPasswordResetRequest(); // AuthConfirmPasswordResetRequest | Email, projectId, OTP code, and new password.
    try {
      MessageResponse result = apiInstance.authConfirmPasswordReset(authConfirmPasswordResetRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authConfirmPasswordReset");
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
| **authConfirmPasswordResetRequest** | [**AuthConfirmPasswordResetRequest**](AuthConfirmPasswordResetRequest.md)| Email, projectId, OTP code, and new password. | |

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
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Too many attempts (rate limit) |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authConvertAnonymous"></a>
# **authConvertAnonymous**
> AuthConvertAnonymous200Response authConvertAnonymous(authConvertAnonymousRequest)

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthConvertAnonymousRequest authConvertAnonymousRequest = new AuthConvertAnonymousRequest(); // AuthConvertAnonymousRequest | Email, password, and optional firstName, lastName for the new full account.
    try {
      AuthConvertAnonymous200Response result = apiInstance.authConvertAnonymous(authConvertAnonymousRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authConvertAnonymous");
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
| **authConvertAnonymousRequest** | [**AuthConvertAnonymousRequest**](AuthConvertAnonymousRequest.md)| Email, password, and optional firstName, lastName for the new full account. | |

### Return type

[**AuthConvertAnonymous200Response**](AuthConvertAnonymous200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account converted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="authCreateAnonymous"></a>
# **authCreateAnonymous**
> AuthCreateAnonymous200Response authCreateAnonymous(authCreateAnonymousRequest)

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthCreateAnonymousRequest authCreateAnonymousRequest = new AuthCreateAnonymousRequest(); // AuthCreateAnonymousRequest | Optional projectId and deviceId for the anonymous session.
    try {
      AuthCreateAnonymous200Response result = apiInstance.authCreateAnonymous(authCreateAnonymousRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authCreateAnonymous");
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
| **authCreateAnonymousRequest** | [**AuthCreateAnonymousRequest**](AuthCreateAnonymousRequest.md)| Optional projectId and deviceId for the anonymous session. | [optional] |

### Return type

[**AuthCreateAnonymous200Response**](AuthCreateAnonymous200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Anonymous session created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="authGetOAuthProviders"></a>
# **authGetOAuthProviders**
> AuthGetOAuthProviders200Response authGetOAuthProviders()

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    try {
      AuthGetOAuthProviders200Response result = apiInstance.authGetOAuthProviders();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authGetOAuthProviders");
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

[**AuthGetOAuthProviders200Response**](AuthGetOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="authGetSession"></a>
# **authGetSession**
> AuthGetSession200Response authGetSession(projectId)

Get current session

Get the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    AuthApi apiInstance = new AuthApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID to get session for.
    try {
      AuthGetSession200Response result = apiInstance.authGetSession(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authGetSession");
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
| **projectId** | **String**| Project ID to get session for. | |

### Return type

[**AuthGetSession200Response**](AuthGetSession200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="authLogin"></a>
# **authLogin**
> AuthLogin200Response authLogin(authLoginRequest)

Login user

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again). 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthLoginRequest authLoginRequest = new AuthLoginRequest(); // AuthLoginRequest | Login credentials (email, password) and project ID.
    try {
      AuthLogin200Response result = apiInstance.authLogin(authLoginRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authLogin");
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
| **authLoginRequest** | [**AuthLoginRequest**](AuthLoginRequest.md)| Login credentials (email, password) and project ID. | |

### Return type

[**AuthLogin200Response**](AuthLogin200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Login successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Email verification required (project has requireEmailVerification and user has not verified) |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authLogout"></a>
# **authLogout**
> MessageResponse authLogout()

Logout user

Logout the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    AuthApi apiInstance = new AuthApi(defaultClient);
    try {
      MessageResponse result = apiInstance.authLogout();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authLogout");
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

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logout successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="authOauthCallback"></a>
# **authOauthCallback**
> AuthOauthCallback200Response authOauthCallback(provider)

OAuth callback handler

OAuth provider redirects the user here after consent. The server exchanges the code for tokens, creates or finds the user, and redirects to the client with token, refreshToken, and expiresIn in query params. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    String provider = "provider_example"; // String | OAuth provider identifier (e.g. google, github).
    try {
      AuthOauthCallback200Response result = apiInstance.authOauthCallback(provider);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authOauthCallback");
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
| **provider** | **String**| OAuth provider identifier (e.g. google, github). | |

### Return type

[**AuthOauthCallback200Response**](AuthOauthCallback200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (in most cases the server responds with 302 redirect to client with token). |  -  |
| **302** | Redirect with token, refreshToken, and expiresIn |  * Location - URL with token, refreshToken, expiresIn query params <br>  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="authOauthInitiate"></a>
# **authOauthInitiate**
> AuthOauthInitiate200Response authOauthInitiate(provider, projectId, redirectUrl)

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. After user authentication, redirects to the OAuth provider&#39;s consent screen. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    String provider = "google"; // String | OAuth provider identifier (e.g. google, github).
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID for which OAuth is configured.
    URI redirectUrl = new URI(); // URI | The URL to redirect to after authentication. Must be pre-registered in project settings.
    try {
      AuthOauthInitiate200Response result = apiInstance.authOauthInitiate(provider, projectId, redirectUrl);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authOauthInitiate");
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
| **provider** | **String**| OAuth provider identifier (e.g. google, github). | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin, dropbox, slack, reddit, twitch, figma, zoom, bitbucket, salesforce, shopify, line, spotify, strava, paypal, asana, trello, okta, gitea, yandex, yahoo, vk, meetup] |
| **projectId** | **String**| Project ID for which OAuth is configured. | |
| **redirectUrl** | **URI**| The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional] |

### Return type

[**AuthOauthInitiate200Response**](AuthOauthInitiate200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth flow initiated; in most cases the server responds with 302 redirect). |  -  |
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured or not enabled for this project |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authRefresh"></a>
# **authRefresh**
> AuthRefresh200Response authRefresh(authRefreshRequest)

Refresh access token (org and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **organization** (platform/dashboard) and **app** auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection). 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthRefreshRequest authRefreshRequest = new AuthRefreshRequest(); // AuthRefreshRequest | JSON body containing the refresh token to exchange for a new access token and refresh token (token rotation).
    try {
      AuthRefresh200Response result = apiInstance.authRefresh(authRefreshRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authRefresh");
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
| **authRefreshRequest** | [**AuthRefreshRequest**](AuthRefreshRequest.md)| JSON body containing the refresh token to exchange for a new access token and refresh token (token rotation). | |

### Return type

[**AuthRefresh200Response**](AuthRefresh200Response.md)

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

<a id="authRegister"></a>
# **authRegister**
> AuthRegister201Response authRegister(authRegisterRequest)

Register new user

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthRegisterRequest authRegisterRequest = new AuthRegisterRequest(); // AuthRegisterRequest | Registration payload (email, password, firstName, lastName, projectId).
    try {
      AuthRegister201Response result = apiInstance.authRegister(authRegisterRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authRegister");
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
| **authRegisterRequest** | [**AuthRegisterRequest**](AuthRegisterRequest.md)| Registration payload (email, password, firstName, lastName, projectId). | |

### Return type

[**AuthRegister201Response**](AuthRegister201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | When project.requireEmailVerification is on (default): no token returned; use requireVerification and message to prompt email verification, then user signs in via login. When off: token and refreshToken returned.  |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authRequestPasswordReset"></a>
# **authRequestPasswordReset**
> MessageResponse authRequestPasswordReset(authRequestPasswordResetRequest)

Request password reset (OTP)

When projectId is provided, sends a 6-digit OTP to the user&#39;s email (app reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthRequestPasswordResetRequest authRequestPasswordResetRequest = new AuthRequestPasswordResetRequest(); // AuthRequestPasswordResetRequest | Email and optional projectId for app OTP or org token link.
    try {
      MessageResponse result = apiInstance.authRequestPasswordReset(authRequestPasswordResetRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authRequestPasswordReset");
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
| **authRequestPasswordResetRequest** | [**AuthRequestPasswordResetRequest**](AuthRequestPasswordResetRequest.md)| Email and optional projectId for app OTP or org token link. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Too many requests (rate limit) |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authResetPassword"></a>
# **authResetPassword**
> MessageResponse authResetPassword(token, authResetPasswordRequest)

Reset password with token (legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for app resets. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    String token = "token_example"; // String | Password reset token from email link.
    AuthResetPasswordRequest authResetPasswordRequest = new AuthResetPasswordRequest(); // AuthResetPasswordRequest | New password and optional projectId.
    try {
      MessageResponse result = apiInstance.authResetPassword(token, authResetPasswordRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authResetPassword");
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
| **token** | **String**| Password reset token from email link. | |
| **authResetPasswordRequest** | [**AuthResetPasswordRequest**](AuthResetPasswordRequest.md)| New password and optional projectId. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="authSendMagicLink"></a>
# **authSendMagicLink**
> MessageResponse authSendMagicLink(magicLinkRequest)

Send magic link

Sends a one-time magic link to the given email for the project. The user clicks the link and is authenticated without a password. Use verify endpoint with the token from the link. Public endpoint; rate limited. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    MagicLinkRequest magicLinkRequest = new MagicLinkRequest(); // MagicLinkRequest | Email, projectId, and optional redirect URL for the magic link.
    try {
      MessageResponse result = apiInstance.authSendMagicLink(magicLinkRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authSendMagicLink");
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
| **magicLinkRequest** | [**MagicLinkRequest**](MagicLinkRequest.md)| Email, projectId, and optional redirect URL for the magic link. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="authSendOtp"></a>
# **authSendOtp**
> MessageResponse authSendOtp(otPSendRequest)

Send OTP code

Sends a one-time code via SMS or email for the given project. Use verify endpoint to exchange the code for a session. Public endpoint; rate limited. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    OTPSendRequest otPSendRequest = new OTPSendRequest(); // OTPSendRequest | Project ID, delivery method (sms/email), and phone or email.
    try {
      MessageResponse result = apiInstance.authSendOtp(otPSendRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authSendOtp");
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
| **otPSendRequest** | [**OTPSendRequest**](OTPSendRequest.md)| Project ID, delivery method (sms/email), and phone or email. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="authVerifyMagicLink"></a>
# **authVerifyMagicLink**
> AuthResponse authVerifyMagicLink(authVerifyMagicLinkRequest)

Verify magic link

Exchanges the magic link token (from the link sent by send) for a session. Returns token and user on success. Token is short-lived and single-use. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    AuthVerifyMagicLinkRequest authVerifyMagicLinkRequest = new AuthVerifyMagicLinkRequest(); // AuthVerifyMagicLinkRequest | The token from the magic link URL.
    try {
      AuthResponse result = apiInstance.authVerifyMagicLink(authVerifyMagicLinkRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authVerifyMagicLink");
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
| **authVerifyMagicLinkRequest** | [**AuthVerifyMagicLinkRequest**](AuthVerifyMagicLinkRequest.md)| The token from the magic link URL. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="authVerifyOtp"></a>
# **authVerifyOtp**
> AuthResponse authVerifyOtp(otPVerifyRequest)

Verify OTP code

Verifies the OTP code and returns a session token and user. Public endpoint. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.AuthApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    AuthApi apiInstance = new AuthApi(defaultClient);
    OTPVerifyRequest otPVerifyRequest = new OTPVerifyRequest(); // OTPVerifyRequest | Identifier (phone/email), OTP code, and project ID.
    try {
      AuthResponse result = apiInstance.authVerifyOtp(otPVerifyRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling AuthApi#authVerifyOtp");
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
| **otPVerifyRequest** | [**OTPVerifyRequest**](OTPVerifyRequest.md)| Identifier (phone/email), OTP code, and project ID. | |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

