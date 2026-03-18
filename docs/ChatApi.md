# ChatApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**chatAddParticipant**](ChatApi.md#chatAddParticipant) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/participants | Add participant to chat |
| [**chatAddReaction**](ChatApi.md#chatAddReaction) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Add reaction to message |
| [**chatCreate**](ChatApi.md#chatCreate) | **POST** /api/chat/projects/{projectId}/chats | Create new chat |
| [**chatDeleteMessage**](ChatApi.md#chatDeleteMessage) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Delete message |
| [**chatEditMessage**](ChatApi.md#chatEditMessage) | **PATCH** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Edit message |
| [**chatGet**](ChatApi.md#chatGet) | **GET** /api/chat/projects/{projectId}/chats/{chatId} | Get chat details |
| [**chatGetMessages**](ChatApi.md#chatGetMessages) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/messages | Get chat messages |
| [**chatList**](ChatApi.md#chatList) | **GET** /api/chat/projects/{projectId}/chats | Get user chats |
| [**chatMarkAsRead**](ChatApi.md#chatMarkAsRead) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/read | Mark messages as read |
| [**chatRemoveParticipant**](ChatApi.md#chatRemoveParticipant) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/participants | Remove participant from chat |
| [**chatRemoveReaction**](ChatApi.md#chatRemoveReaction) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Remove reaction from message |
| [**chatSendMessage**](ChatApi.md#chatSendMessage) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages | Send message |


<a id="chatAddParticipant"></a>
# **chatAddParticipant**
> ChatAddParticipant200Response chatAddParticipant(projectId, chatId, chatAddParticipantRequest)

Add participant to chat

Add a user to the chat with an optional role (admin or member).

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    ChatAddParticipantRequest chatAddParticipantRequest = new ChatAddParticipantRequest(); // ChatAddParticipantRequest | User ID to add and optional role (admin, member).
    try {
      ChatAddParticipant200Response result = apiInstance.chatAddParticipant(projectId, chatId, chatAddParticipantRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatAddParticipant");
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
| **chatId** | **String**| Chat ID. | |
| **chatAddParticipantRequest** | [**ChatAddParticipantRequest**](ChatAddParticipantRequest.md)| User ID to add and optional role (admin, member). | |

### Return type

[**ChatAddParticipant200Response**](ChatAddParticipant200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant added |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatAddReaction"></a>
# **chatAddReaction**
> ChatAddReaction200Response chatAddReaction(projectId, chatId, messageId, chatAddReactionRequest)

Add reaction to message

Add an emoji reaction to a message.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    String messageId = "messageId_example"; // String | Message ID.
    ChatAddReactionRequest chatAddReactionRequest = new ChatAddReactionRequest(); // ChatAddReactionRequest | Emoji reaction (e.g. 👍, ❤️).
    try {
      ChatAddReaction200Response result = apiInstance.chatAddReaction(projectId, chatId, messageId, chatAddReactionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatAddReaction");
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
| **chatId** | **String**| Chat ID. | |
| **messageId** | **String**| Message ID. | |
| **chatAddReactionRequest** | [**ChatAddReactionRequest**](ChatAddReactionRequest.md)| Emoji reaction (e.g. 👍, ❤️). | |

### Return type

[**ChatAddReaction200Response**](ChatAddReaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction added |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatCreate"></a>
# **chatCreate**
> ChatCreate201Response chatCreate(projectId, chatCreateRequest)

Create new chat

Create a new chat (direct, group, channel, or broadcast) with name, type, participants, and optional settings.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    ChatCreateRequest chatCreateRequest = new ChatCreateRequest(); // ChatCreateRequest | Chat name, type (direct/group/channel/broadcast), participants array, optional description and settings.
    try {
      ChatCreate201Response result = apiInstance.chatCreate(projectId, chatCreateRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatCreate");
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
| **chatCreateRequest** | [**ChatCreateRequest**](ChatCreateRequest.md)| Chat name, type (direct/group/channel/broadcast), participants array, optional description and settings. | |

### Return type

[**ChatCreate201Response**](ChatCreate201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Chat created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatDeleteMessage"></a>
# **chatDeleteMessage**
> MessageResponse chatDeleteMessage(projectId, chatId, messageId)

Delete message

Delete a message from the chat (sender or admin). May be soft-delete or permanent depending on implementation.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    String messageId = "messageId_example"; // String | Message ID.
    try {
      MessageResponse result = apiInstance.chatDeleteMessage(projectId, chatId, messageId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatDeleteMessage");
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
| **chatId** | **String**| Chat ID. | |
| **messageId** | **String**| Message ID. | |

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
| **200** | Message deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="chatEditMessage"></a>
# **chatEditMessage**
> ChatEditMessage200Response chatEditMessage(projectId, chatId, messageId, chatEditMessageRequest)

Edit message

Update the content of a message (sender only; supports edit history).

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    String messageId = "messageId_example"; // String | Message ID.
    ChatEditMessageRequest chatEditMessageRequest = new ChatEditMessageRequest(); // ChatEditMessageRequest | New message content.
    try {
      ChatEditMessage200Response result = apiInstance.chatEditMessage(projectId, chatId, messageId, chatEditMessageRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatEditMessage");
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
| **chatId** | **String**| Chat ID. | |
| **messageId** | **String**| Message ID. | |
| **chatEditMessageRequest** | [**ChatEditMessageRequest**](ChatEditMessageRequest.md)| New message content. | |

### Return type

[**ChatEditMessage200Response**](ChatEditMessage200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message edited |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="chatGet"></a>
# **chatGet**
> ChatGet200Response chatGet(projectId, chatId)

Get chat details

Returns full chat metadata including participants and roles for a single chat.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    try {
      ChatGet200Response result = apiInstance.chatGet(projectId, chatId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatGet");
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
| **chatId** | **String**| Chat ID. | |

### Return type

[**ChatGet200Response**](ChatGet200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Chat details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

<a id="chatGetMessages"></a>
# **chatGetMessages**
> ChatGetMessages200Response chatGetMessages(projectId, chatId, page, limit, before, after)

Get chat messages

Returns paginated messages for a chat with optional before/after cursor for time-based pagination.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 50; // Integer | Number of messages per page.
    OffsetDateTime before = OffsetDateTime.now(); // OffsetDateTime | Return messages before this timestamp (cursor).
    OffsetDateTime after = OffsetDateTime.now(); // OffsetDateTime | Return messages after this timestamp (cursor).
    try {
      ChatGetMessages200Response result = apiInstance.chatGetMessages(projectId, chatId, page, limit, before, after);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatGetMessages");
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
| **chatId** | **String**| Chat ID. | |
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Number of messages per page. | [optional] [default to 50] |
| **before** | **OffsetDateTime**| Return messages before this timestamp (cursor). | [optional] |
| **after** | **OffsetDateTime**| Return messages after this timestamp (cursor). | [optional] |

### Return type

[**ChatGetMessages200Response**](ChatGetMessages200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatList"></a>
# **chatList**
> ChatList200Response chatList(projectId, page, limit)

Get user chats

Returns paginated list of chats for the current user in the project, with last message and unread count.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    Integer page = 1; // Integer | Page number (1-based).
    Integer limit = 20; // Integer | Number of chats per page.
    try {
      ChatList200Response result = apiInstance.chatList(projectId, page, limit);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatList");
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
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **Integer**| Number of chats per page. | [optional] [default to 20] |

### Return type

[**ChatList200Response**](ChatList200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User chats list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatMarkAsRead"></a>
# **chatMarkAsRead**
> ChatMarkAsRead200Response chatMarkAsRead(projectId, chatId, chatMarkAsReadRequest)

Mark messages as read

Mark one or more messages as read for the current user in the chat.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    ChatMarkAsReadRequest chatMarkAsReadRequest = new ChatMarkAsReadRequest(); // ChatMarkAsReadRequest | Array of message IDs to mark as read.
    try {
      ChatMarkAsRead200Response result = apiInstance.chatMarkAsRead(projectId, chatId, chatMarkAsReadRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatMarkAsRead");
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
| **chatId** | **String**| Chat ID. | |
| **chatMarkAsReadRequest** | [**ChatMarkAsReadRequest**](ChatMarkAsReadRequest.md)| Array of message IDs to mark as read. | |

### Return type

[**ChatMarkAsRead200Response**](ChatMarkAsRead200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages marked as read |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatRemoveParticipant"></a>
# **chatRemoveParticipant**
> MessageResponse chatRemoveParticipant(projectId, chatId, chatRemoveParticipantRequest)

Remove participant from chat

Remove a user from the chat by userId.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    ChatRemoveParticipantRequest chatRemoveParticipantRequest = new ChatRemoveParticipantRequest(); // ChatRemoveParticipantRequest | User ID of the participant to remove.
    try {
      MessageResponse result = apiInstance.chatRemoveParticipant(projectId, chatId, chatRemoveParticipantRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatRemoveParticipant");
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
| **chatId** | **String**| Chat ID. | |
| **chatRemoveParticipantRequest** | [**ChatRemoveParticipantRequest**](ChatRemoveParticipantRequest.md)| User ID of the participant to remove. | |

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
| **200** | Participant removed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatRemoveReaction"></a>
# **chatRemoveReaction**
> ChatRemoveReaction200Response chatRemoveReaction(projectId, chatId, messageId, chatAddReactionRequest)

Remove reaction from message

Remove the current user&#39;s emoji reaction from a message.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    String messageId = "messageId_example"; // String | Message ID.
    ChatAddReactionRequest chatAddReactionRequest = new ChatAddReactionRequest(); // ChatAddReactionRequest | Emoji to remove (must match the reaction added by the user).
    try {
      ChatRemoveReaction200Response result = apiInstance.chatRemoveReaction(projectId, chatId, messageId, chatAddReactionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatRemoveReaction");
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
| **chatId** | **String**| Chat ID. | |
| **messageId** | **String**| Message ID. | |
| **chatAddReactionRequest** | [**ChatAddReactionRequest**](ChatAddReactionRequest.md)| Emoji to remove (must match the reaction added by the user). | |

### Return type

[**ChatRemoveReaction200Response**](ChatRemoveReaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction removed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

<a id="chatSendMessage"></a>
# **chatSendMessage**
> ChatSendMessage201Response chatSendMessage(projectId, chatId, chatSendMessageRequest)

Send message

Send a message (text, image, video, audio, file, location, contact) to a chat with optional replyTo and mentions.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ChatApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ChatApi apiInstance = new ChatApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID.
    String chatId = "chatId_example"; // String | Chat ID.
    ChatSendMessageRequest chatSendMessageRequest = new ChatSendMessageRequest(); // ChatSendMessageRequest | Message type, content, optional replyTo and mentions.
    try {
      ChatSendMessage201Response result = apiInstance.chatSendMessage(projectId, chatId, chatSendMessageRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ChatApi#chatSendMessage");
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
| **chatId** | **String**| Chat ID. | |
| **chatSendMessageRequest** | [**ChatSendMessageRequest**](ChatSendMessageRequest.md)| Message type, content, optional replyTo and mentions. | |

### Return type

[**ChatSendMessage201Response**](ChatSendMessage201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Message sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

