# MessagingApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getMessageHistory**](MessagingApi.md#getMessageHistory) | **GET** /api/messaging/projects/{projectId}/messaging/history | Get message history |
| [**getMessageStats**](MessagingApi.md#getMessageStats) | **GET** /api/messaging/projects/{projectId}/messaging/stats | Get message statistics |
| [**getProjectFcmConfig**](MessagingApi.md#getProjectFcmConfig) | **GET** /api/messaging/projects/{projectId}/messaging/push-config | Get bring-your-own push credentials status (masked) |
| [**getProjectSmsByo**](MessagingApi.md#getProjectSmsByo) | **GET** /api/messaging/projects/{projectId}/messaging/sms-provider | Get BYO SMS provider configuration (masked) |
| [**listDeviceTokens**](MessagingApi.md#listDeviceTokens) | **GET** /api/messaging/projects/{projectId}/messaging/devices | List registered device tokens |
| [**patchProjectFcmConfig**](MessagingApi.md#patchProjectFcmConfig) | **PATCH** /api/messaging/projects/{projectId}/messaging/push-config | Set or clear your own push service account (optional) |
| [**patchProjectSmsByo**](MessagingApi.md#patchProjectSmsByo) | **PATCH** /api/messaging/projects/{projectId}/messaging/sms-provider | Update BYO SMS provider credentials |
| [**registerDeviceToken**](MessagingApi.md#registerDeviceToken) | **POST** /api/messaging/projects/{projectId}/messaging/devices | Register a device push token |
| [**sendEmail**](MessagingApi.md#sendEmail) | **POST** /api/messaging/projects/{projectId}/messaging/email | Send email |
| [**sendPushNotification**](MessagingApi.md#sendPushNotification) | **POST** /api/messaging/projects/{projectId}/messaging/push | Send push notification |
| [**sendSMS**](MessagingApi.md#sendSMS) | **POST** /api/messaging/projects/{projectId}/messaging/sms | Send SMS |
| [**unregisterDeviceToken**](MessagingApi.md#unregisterDeviceToken) | **DELETE** /api/messaging/projects/{projectId}/messaging/devices | Unregister a device push token |


<a id="getMessageHistory"></a>
# **getMessageHistory**
> MessageHistoryResponse getMessageHistory(projectId, type, page, limit, status)

Get message history

Get message history (push, email, SMS) with filtering and pagination. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String type = "push"; // String | 
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String status = "sent"; // String | 
    try {
      MessageHistoryResponse result = apiInstance.getMessageHistory(projectId, type, page, limit, status);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#getMessageHistory");
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
| **type** | **String**|  | [optional] [enum: push, email, sms] |
| **page** | **Integer**|  | [optional] [default to 1] |
| **limit** | **Integer**|  | [optional] [default to 20] |
| **status** | **String**|  | [optional] [enum: sent, failed, pending] |

### Return type

[**MessageHistoryResponse**](MessageHistoryResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message history |  -  |
| **403** | App role feature permission denied |  -  |

<a id="getMessageStats"></a>
# **getMessageStats**
> MessageStatsResponse getMessageStats(projectId, startDate, endDate)

Get message statistics

Get messaging statistics including total messages, success rates, and breakdown by type (push, email, SMS). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    OffsetDateTime startDate = OffsetDateTime.now(); // OffsetDateTime | 
    OffsetDateTime endDate = OffsetDateTime.now(); // OffsetDateTime | 
    try {
      MessageStatsResponse result = apiInstance.getMessageStats(projectId, startDate, endDate);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#getMessageStats");
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
| **startDate** | **OffsetDateTime**|  | [optional] |
| **endDate** | **OffsetDateTime**|  | [optional] |

### Return type

[**MessageStatsResponse**](MessageStatsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message statistics |  -  |
| **403** | App role feature permission denied |  -  |

<a id="getProjectFcmConfig"></a>
# **getProjectFcmConfig**
> GetProjectFcmConfig200Response getProjectFcmConfig(projectId)

Get bring-your-own push credentials status (masked)

Returns whether this project has its own push provider credentials stored (encrypted). This is an optional, advanced override - push works out of the box with platform-managed credentials, so when no per-project credentials are stored, push is sent with the platform-managed credentials.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetProjectFcmConfig200Response result = apiInstance.getProjectFcmConfig(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#getProjectFcmConfig");
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

[**GetProjectFcmConfig200Response**](GetProjectFcmConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bring-your-own push credentials flags |  -  |

<a id="getProjectSmsByo"></a>
# **getProjectSmsByo**
> GetProjectSmsByo200Response getProjectSmsByo(projectId)

Get BYO SMS provider configuration (masked)

Returns enabled flag, provider kind, default sender, and whether credentials are stored. Secrets are never returned. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetProjectSmsByo200Response result = apiInstance.getProjectSmsByo(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#getProjectSmsByo");
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

[**GetProjectSmsByo200Response**](GetProjectSmsByo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | SMS BYO settings |  -  |

<a id="listDeviceTokens"></a>
# **listDeviceTokens**
> DeviceListResponse listDeviceTokens(projectId)

List registered device tokens

List the device push tokens registered to a project, most-recently-seen first.  Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      DeviceListResponse result = apiInstance.listDeviceTokens(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#listDeviceTokens");
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

[**DeviceListResponse**](DeviceListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Registered device tokens |  -  |

<a id="patchProjectFcmConfig"></a>
# **patchProjectFcmConfig**
> patchProjectFcmConfig(projectId, patchProjectFcmConfigRequest)

Set or clear your own push service account (optional)

Optional advanced step - push works out of the box with platform-managed credentials, so most projects never call this. Use it only to deliver push from your own push provider account. Body &#x60;serviceAccountJson&#x60; is the Firebase service account JSON you download from your own Firebase project (stored encrypted). Send &#x60;clear: true&#x60; to remove it and go back to the platform-managed credentials. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    PatchProjectFcmConfigRequest patchProjectFcmConfigRequest = new PatchProjectFcmConfigRequest(); // PatchProjectFcmConfigRequest | 
    try {
      apiInstance.patchProjectFcmConfig(projectId, patchProjectFcmConfigRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#patchProjectFcmConfig");
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
| **patchProjectFcmConfigRequest** | [**PatchProjectFcmConfigRequest**](PatchProjectFcmConfigRequest.md)|  | |

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
| **200** | Updated |  -  |
| **400** | Bad request |  -  |

<a id="patchProjectSmsByo"></a>
# **patchProjectSmsByo**
> GetProjectSmsByo200Response patchProjectSmsByo(projectId, projectSmsByoPatchRequest)

Update BYO SMS provider credentials

Body &#x60;config&#x60; is provider-specific JSON stored encrypted per organization: - **twilio** — &#x60;accountSid&#x60;, &#x60;authToken&#x60; (required). Optional &#x60;from&#x60; sender override used if the send request does not specify &#x60;from&#x60; and &#x60;defaultFrom&#x60; is empty. - **termii** — &#x60;apiKey&#x60; (required). Optional &#x60;from&#x60; sender name (e.g. brand label). - **africastalking** — &#x60;username&#x60;, &#x60;apiKey&#x60; (both required). Optional &#x60;from&#x60; shortcode or sender ID. On enable, the API validates credentials with a lightweight ping (no SMS sent). See request body **Examples** for sample payloads. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    ProjectSmsByoPatchRequest projectSmsByoPatchRequest = new ProjectSmsByoPatchRequest(); // ProjectSmsByoPatchRequest | 
    try {
      GetProjectSmsByo200Response result = apiInstance.patchProjectSmsByo(projectId, projectSmsByoPatchRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#patchProjectSmsByo");
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
| **projectSmsByoPatchRequest** | [**ProjectSmsByoPatchRequest**](ProjectSmsByoPatchRequest.md)|  | |

### Return type

[**GetProjectSmsByo200Response**](GetProjectSmsByo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated configuration |  -  |
| **400** | Bad request |  -  |

<a id="registerDeviceToken"></a>
# **registerDeviceToken**
> DeviceRegisteredResponse registerDeviceToken(projectId, deviceRegisterRequest)

Register a device push token

Register a device&#39;s push token with a project so it can receive push notifications. A client registers its token here first; the send endpoint (&#x60;/messaging/push&#x60;) only delivers to tokens that are registered to the project, so a caller cannot push to arbitrary or other-tenant tokens.  Registration is idempotent - re-registering a token that already exists just refreshes it (updates &#x60;platform&#x60; and &#x60;lastSeenAt&#x60;) instead of creating a duplicate. Each project has a cap on the number of registered tokens; when the cap is reached, the least-recently-seen tokens are evicted to make room, so a register-on-launch call never fails.  Push works out of the box with platform-managed credentials - no provider setup is required to start registering tokens and sending push.  Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    DeviceRegisterRequest deviceRegisterRequest = new DeviceRegisterRequest(); // DeviceRegisterRequest | 
    try {
      DeviceRegisteredResponse result = apiInstance.registerDeviceToken(projectId, deviceRegisterRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#registerDeviceToken");
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
| **deviceRegisterRequest** | [**DeviceRegisterRequest**](DeviceRegisterRequest.md)|  | |

### Return type

[**DeviceRegisteredResponse**](DeviceRegisteredResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Device token registered |  -  |
| **400** | Bad request |  -  |
| **403** | App role feature permission denied |  -  |
| **429** | Device registration rate limit exceeded |  -  |

<a id="sendEmail"></a>
# **sendEmail**
> MessageSentResponse sendEmail(projectId, emailRequest)

Send email

Send an email message to one or more recipients. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    EmailRequest emailRequest = new EmailRequest(); // EmailRequest | 
    try {
      MessageSentResponse result = apiInstance.sendEmail(projectId, emailRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#sendEmail");
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
| **emailRequest** | [**EmailRequest**](EmailRequest.md)|  | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Email sent |  -  |
| **403** | App role feature permission denied |  -  |
| **429** | Per-project messaging send rate limit exceeded |  -  |

<a id="sendPushNotification"></a>
# **sendPushNotification**
> MessageSentResponse sendPushNotification(projectId, pushNotificationRequest)

Send push notification

Send a push notification to one or more devices. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    PushNotificationRequest pushNotificationRequest = new PushNotificationRequest(); // PushNotificationRequest | 
    try {
      MessageSentResponse result = apiInstance.sendPushNotification(projectId, pushNotificationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#sendPushNotification");
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
| **pushNotificationRequest** | [**PushNotificationRequest**](PushNotificationRequest.md)|  | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Push notification sent |  -  |
| **403** | App role feature permission denied |  -  |
| **429** | Per-project messaging send rate limit exceeded |  -  |

<a id="sendSMS"></a>
# **sendSMS**
> MessageSentResponse sendSMS(projectId, smSRequest)

Send SMS

Send an SMS message to one or more phone numbers. Uses project BYO SMS when configured; otherwise the platform SMS provider if set. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    SMSRequest smSRequest = new SMSRequest(); // SMSRequest | 
    try {
      MessageSentResponse result = apiInstance.sendSMS(projectId, smSRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#sendSMS");
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
| **smSRequest** | [**SMSRequest**](SMSRequest.md)|  | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | SMS sent |  -  |
| **403** | App role feature permission denied |  -  |
| **429** | Per-project messaging send rate limit exceeded |  -  |

<a id="unregisterDeviceToken"></a>
# **unregisterDeviceToken**
> DeviceUnregisteredResponse unregisterDeviceToken(projectId, deviceUnregisterRequest)

Unregister a device push token

Remove a device push token from a project - call this on logout or when a token rotates, so the send endpoint stops delivering to it.  The token to remove is sent in the request body. Removing a token that is not registered is a no-op and still returns 200 (with &#x60;removed: false&#x60;).  Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.MessagingApi;

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

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    DeviceUnregisterRequest deviceUnregisterRequest = new DeviceUnregisterRequest(); // DeviceUnregisterRequest | 
    try {
      DeviceUnregisteredResponse result = apiInstance.unregisterDeviceToken(projectId, deviceUnregisterRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#unregisterDeviceToken");
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
| **deviceUnregisterRequest** | [**DeviceUnregisterRequest**](DeviceUnregisterRequest.md)|  | |

### Return type

[**DeviceUnregisteredResponse**](DeviceUnregisteredResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Device token removed (or already absent) |  -  |

