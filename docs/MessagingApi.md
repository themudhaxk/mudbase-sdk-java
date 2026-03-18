# MessagingApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**messagingGetHistory**](MessagingApi.md#messagingGetHistory) | **GET** /api/messaging/projects/{projectId}/messaging/history | Get message history |
| [**messagingGetStats**](MessagingApi.md#messagingGetStats) | **GET** /api/messaging/projects/{projectId}/messaging/stats | Get message statistics |
| [**messagingSendEmail**](MessagingApi.md#messagingSendEmail) | **POST** /api/messaging/projects/{projectId}/messaging/email | Send transactional email |
| [**messagingSendPush**](MessagingApi.md#messagingSendPush) | **POST** /api/messaging/projects/{projectId}/messaging/push | Send push notification |
| [**messagingSendSms**](MessagingApi.md#messagingSendSms) | **POST** /api/messaging/projects/{projectId}/messaging/sms | Send SMS to one or more recipients (E.164 format) |


<a id="messagingGetHistory"></a>
# **messagingGetHistory**
> MessageHistoryResponse messagingGetHistory(projectId, type, page, limit, status)

Get message history

Get message history (push, email, SMS) with filtering and pagination. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.MessagingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the messaging project.
    String type = "push"; // String | Filter by message type (push, email, or sms).
    Integer page = 1; // Integer | Page number for pagination (1-based).
    Integer limit = 20; // Integer | Maximum number of messages per page.
    String status = "sent"; // String | Filter by delivery status.
    try {
      MessageHistoryResponse result = apiInstance.messagingGetHistory(projectId, type, page, limit, status);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#messagingGetHistory");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **type** | **String**| Filter by message type (push, email, or sms). | [optional] [enum: push, email, sms] |
| **page** | **Integer**| Page number for pagination (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Maximum number of messages per page. | [optional] [default to 20] |
| **status** | **String**| Filter by delivery status. | [optional] [enum: sent, failed, pending] |

### Return type

[**MessageHistoryResponse**](MessageHistoryResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message history |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="messagingGetStats"></a>
# **messagingGetStats**
> MessageStatsResponse messagingGetStats(projectId, startDate, endDate)

Get message statistics

Get messaging statistics including total messages, success rates, and breakdown by type (push, email, SMS). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.MessagingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the messaging project.
    OffsetDateTime startDate = OffsetDateTime.now(); // OffsetDateTime | Start of the date range for statistics (ISO 8601).
    OffsetDateTime endDate = OffsetDateTime.now(); // OffsetDateTime | End of the date range for statistics (ISO 8601).
    try {
      MessageStatsResponse result = apiInstance.messagingGetStats(projectId, startDate, endDate);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#messagingGetStats");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **startDate** | **OffsetDateTime**| Start of the date range for statistics (ISO 8601). | [optional] |
| **endDate** | **OffsetDateTime**| End of the date range for statistics (ISO 8601). | [optional] |

### Return type

[**MessageStatsResponse**](MessageStatsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message statistics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="messagingSendEmail"></a>
# **messagingSendEmail**
> MessageSentResponse messagingSendEmail(projectId, emailRequest)

Send transactional email

Send a transactional email to one or more recipients. Supports HTML and plain text. Use for verification emails, password resets, notifications, and marketing. Attachments and templates can be configured per project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.MessagingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the messaging project.
    EmailRequest emailRequest = new EmailRequest(); // EmailRequest | Recipient(s), subject, HTML and/or plain text body; optional reply-to and attachments.
    try {
      MessageSentResponse result = apiInstance.messagingSendEmail(projectId, emailRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#messagingSendEmail");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **emailRequest** | [**EmailRequest**](EmailRequest.md)| Recipient(s), subject, HTML and/or plain text body; optional reply-to and attachments. | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Email sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="messagingSendPush"></a>
# **messagingSendPush**
> MessageSentResponse messagingSendPush(projectId, pushNotificationRequest)

Send push notification

Send a push notification to one or more devices. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.MessagingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the messaging project.
    PushNotificationRequest pushNotificationRequest = new PushNotificationRequest(); // PushNotificationRequest | Device tokens, notification title/body, optional data payload and image URL.
    try {
      MessageSentResponse result = apiInstance.messagingSendPush(projectId, pushNotificationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#messagingSendPush");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **pushNotificationRequest** | [**PushNotificationRequest**](PushNotificationRequest.md)| Device tokens, notification title/body, optional data payload and image URL. | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Push notification sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="messagingSendSms"></a>
# **messagingSendSms**
> MessageSentResponse messagingSendSms(projectId, smSRequest)

Send SMS to one or more recipients (E.164 format)

Send an SMS message to one or more phone numbers in E.164 format. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.MessagingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    MessagingApi apiInstance = new MessagingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the messaging project.
    SMSRequest smSRequest = new SMSRequest(); // SMSRequest | Recipient phone number(s), message body, and optional sender ID.
    try {
      MessageSentResponse result = apiInstance.messagingSendSms(projectId, smSRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MessagingApi#messagingSendSms");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **smSRequest** | [**SMSRequest**](SMSRequest.md)| Recipient phone number(s), message body, and optional sender ID. | |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | SMS sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

