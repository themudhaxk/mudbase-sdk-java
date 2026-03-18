# UsersApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**usersChangePassword**](UsersApi.md#usersChangePassword) | **PATCH** /api/users/password | Change password |
| [**usersDisable2fa**](UsersApi.md#usersDisable2fa) | **POST** /api/users/2fa/disable | Disable 2FA |
| [**usersEraseData**](UsersApi.md#usersEraseData) | **POST** /api/users/me/erase | Delete user data (GDPR Article 17) |
| [**usersExportData**](UsersApi.md#usersExportData) | **GET** /api/users/me/export | Export user data (GDPR Article 15) |
| [**usersGet**](UsersApi.md#usersGet) | **GET** /api/users/me | Get current user profile |
| [**usersLinkOAuthProvider**](UsersApi.md#usersLinkOAuthProvider) | **GET** /api/users/me/oauth-providers/link/{provider} | Link OAuth provider to account |
| [**usersListOAuthProviders**](UsersApi.md#usersListOAuthProviders) | **GET** /api/users/me/oauth-providers | List linked OAuth providers |
| [**usersResendVerification**](UsersApi.md#usersResendVerification) | **POST** /api/users/resend-verification | Resend verification email |
| [**usersSetup2fa**](UsersApi.md#usersSetup2fa) | **POST** /api/users/2fa/setup | Initiate two-factor authentication setup (secret, QR code, backup codes) |
| [**usersUnlinkOAuthProvider**](UsersApi.md#usersUnlinkOAuthProvider) | **DELETE** /api/users/me/oauth-providers/{provider} | Unlink OAuth provider |
| [**usersUpdate**](UsersApi.md#usersUpdate) | **PATCH** /api/users/update | Update user profile |
| [**usersVerify2fa**](UsersApi.md#usersVerify2fa) | **POST** /api/users/2fa/verify | Verify and enable 2FA |
| [**usersVerifyEmail**](UsersApi.md#usersVerifyEmail) | **POST** /api/users/verify-email | Verify email address (organization and project) |


<a id="usersChangePassword"></a>
# **usersChangePassword**
> MessageResponse usersChangePassword(changePasswordRequest)

Change password

Change the current user&#39;s password. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    ChangePasswordRequest changePasswordRequest = new ChangePasswordRequest(); // ChangePasswordRequest | Current password and new password.
    try {
      MessageResponse result = apiInstance.usersChangePassword(changePasswordRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersChangePassword");
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
| **changePasswordRequest** | [**ChangePasswordRequest**](ChangePasswordRequest.md)| Current password and new password. | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password changed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersDisable2fa"></a>
# **usersDisable2fa**
> MessageResponse usersDisable2fa(usersDisable2faRequest)

Disable 2FA

Disable two-factor authentication for the current user. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    UsersDisable2faRequest usersDisable2faRequest = new UsersDisable2faRequest(); // UsersDisable2faRequest | Current password and one-time code to confirm disable.
    try {
      MessageResponse result = apiInstance.usersDisable2fa(usersDisable2faRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersDisable2fa");
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
| **usersDisable2faRequest** | [**UsersDisable2faRequest**](UsersDisable2faRequest.md)| Current password and one-time code to confirm disable. | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA disabled |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersEraseData"></a>
# **usersEraseData**
> UsersEraseData200Response usersEraseData(usersEraseDataRequest)

Delete user data (GDPR Article 17)

Request account erasure (right to be forgotten). Anonymizes PII and deactivates account with 7-day grace period. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    UsersEraseDataRequest usersEraseDataRequest = new UsersEraseDataRequest(); // UsersEraseDataRequest | Confirmation string (DELETE_MY_ACCOUNT) and optional reason for erasure.
    try {
      UsersEraseData200Response result = apiInstance.usersEraseData(usersEraseDataRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersEraseData");
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
| **usersEraseDataRequest** | [**UsersEraseDataRequest**](UsersEraseDataRequest.md)| Confirmation string (DELETE_MY_ACCOUNT) and optional reason for erasure. | |

### Return type

[**UsersEraseData200Response**](UsersEraseData200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account erasure initiated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="usersExportData"></a>
# **usersExportData**
> UsersExportData200Response usersExportData()

Export user data (GDPR Article 15)

Export all user data in JSON format for GDPR data portability compliance. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    try {
      UsersExportData200Response result = apiInstance.usersExportData();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersExportData");
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

[**UsersExportData200Response**](UsersExportData200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User data export |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersGet"></a>
# **usersGet**
> UsersGet200Response usersGet()

Get current user profile

Get the current authenticated user&#39;s profile. Accepts JWT Bearer token (BearerToken). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    try {
      UsersGet200Response result = apiInstance.usersGet();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersGet");
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

[**UsersGet200Response**](UsersGet200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User profile |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersLinkOAuthProvider"></a>
# **usersLinkOAuthProvider**
> UsersLinkOAuthProvider200Response usersLinkOAuthProvider(provider, projectId)

Link OAuth provider to account

Initiate OAuth flow to link a new provider to the current account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    String provider = "google"; // String | OAuth provider to link (e.g. google, github).
    String projectId = "685ad30be129932fbb7a1047"; // String | Project ID for the OAuth link context.
    try {
      UsersLinkOAuthProvider200Response result = apiInstance.usersLinkOAuthProvider(provider, projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersLinkOAuthProvider");
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
| **provider** | **String**| OAuth provider to link (e.g. google, github). | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin] |
| **projectId** | **String**| Project ID for the OAuth link context. | [optional] |

### Return type

[**UsersLinkOAuthProvider200Response**](UsersLinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth link flow initiated; in most cases the server responds with 302 redirect to provider). |  -  |
| **302** | Redirect to OAuth provider |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="usersListOAuthProviders"></a>
# **usersListOAuthProviders**
> UsersListOAuthProviders200Response usersListOAuthProviders()

List linked OAuth providers

Get all OAuth providers linked to the current user&#39;s account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    try {
      UsersListOAuthProviders200Response result = apiInstance.usersListOAuthProviders();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersListOAuthProviders");
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

[**UsersListOAuthProviders200Response**](UsersListOAuthProviders200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of linked OAuth providers |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="usersResendVerification"></a>
# **usersResendVerification**
> MessageResponse usersResendVerification()

Resend verification email

Sends a new verification email to the authenticated user. Rate limited (e.g. 3 requests per 15 minutes per user). For app users the link includes project context. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    try {
      MessageResponse result = apiInstance.usersResendVerification();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersResendVerification");
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
| **200** | Verification email sent |  -  |
| **400** | Email already verified |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Too many requests (rate limit) |  -  |

<a id="usersSetup2fa"></a>
# **usersSetup2fa**
> TwoFASetupResponse usersSetup2fa()

Initiate two-factor authentication setup (secret, QR code, backup codes)

Initiates two-factor authentication setup for the current user. Returns a secret, QR code, and manual entry key for the user to add to an authenticator app. Requires JWT Bearer token (BearerToken). API keys are not supported. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    try {
      TwoFASetupResponse result = apiInstance.usersSetup2fa();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersSetup2fa");
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

[**TwoFASetupResponse**](TwoFASetupResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA setup data |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersUnlinkOAuthProvider"></a>
# **usersUnlinkOAuthProvider**
> UsersUnlinkOAuthProvider200Response usersUnlinkOAuthProvider(provider)

Unlink OAuth provider

Remove an OAuth provider from the current account. Cannot unlink if it&#39;s the only authentication method. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    String provider = "google"; // String | OAuth provider to unlink (e.g. google, github).
    try {
      UsersUnlinkOAuthProvider200Response result = apiInstance.usersUnlinkOAuthProvider(provider);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersUnlinkOAuthProvider");
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
| **provider** | **String**| OAuth provider to unlink (e.g. google, github). | [enum: google, github, facebook, microsoft, apple, twitter, discord, linkedin] |

### Return type

[**UsersUnlinkOAuthProvider200Response**](UsersUnlinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Provider unlinked successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="usersUpdate"></a>
# **usersUpdate**
> UsersUpdate200Response usersUpdate(updateUserRequest)

Update user profile

Update the current user&#39;s profile. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    UpdateUserRequest updateUserRequest = new UpdateUserRequest(); // UpdateUserRequest | Profile fields to update (firstName, lastName, avatar).
    try {
      UsersUpdate200Response result = apiInstance.usersUpdate(updateUserRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersUpdate");
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
| **updateUserRequest** | [**UpdateUserRequest**](UpdateUserRequest.md)| Profile fields to update (firstName, lastName, avatar). | |

### Return type

[**UsersUpdate200Response**](UsersUpdate200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Profile updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersVerify2fa"></a>
# **usersVerify2fa**
> MessageResponse usersVerify2fa(usersVerify2faRequest)

Verify and enable 2FA

Verify and enable two-factor authentication for the current user. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    UsersApi apiInstance = new UsersApi(defaultClient);
    UsersVerify2faRequest usersVerify2faRequest = new UsersVerify2faRequest(); // UsersVerify2faRequest | One-time code from the authenticator app.
    try {
      MessageResponse result = apiInstance.usersVerify2fa(usersVerify2faRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersVerify2fa");
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
| **usersVerify2faRequest** | [**UsersVerify2faRequest**](UsersVerify2faRequest.md)| One-time code from the authenticator app. | |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA enabled |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="usersVerifyEmail"></a>
# **usersVerifyEmail**
> MessageResponse usersVerifyEmail(usersVerifyEmailRequest)

Verify email address (organization and project)

Verifies the user&#39;s email using the token from the link sent at signup. Works for both organization (platform) and app signups; the token is from the verification link (e.g. verify-email?token&#x3D;... for org, or verify-email?token&#x3D;...&amp;project&#x3D;... for project). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.UsersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    UsersApi apiInstance = new UsersApi(defaultClient);
    UsersVerifyEmailRequest usersVerifyEmailRequest = new UsersVerifyEmailRequest(); // UsersVerifyEmailRequest | Verification token from the email link; optional projectId for project context.
    try {
      MessageResponse result = apiInstance.usersVerifyEmail(usersVerifyEmailRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling UsersApi#usersVerifyEmail");
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
| **usersVerifyEmailRequest** | [**UsersVerifyEmailRequest**](UsersVerifyEmailRequest.md)| Verification token from the email link; optional projectId for project context. | |

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
| **400** | Invalid verification token |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

