# BillingApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**billingCheckFeatureAccess**](BillingApi.md#billingCheckFeatureAccess) | **GET** /api/billing/public/projects/{projectId}/feature-access | Check feature access (public) |
| [**billingCheckSubscription**](BillingApi.md#billingCheckSubscription) | **GET** /api/billing/public/projects/{projectId}/subscription | Check subscription status (public) |
| [**billingCreateCheckoutSession**](BillingApi.md#billingCreateCheckoutSession) | **POST** /api/billing/public/projects/{projectId}/checkout | Create checkout session (Flutterwave or crypto) |
| [**billingGetCheckoutPayment**](BillingApi.md#billingGetCheckoutPayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details |
| [**billingGetPublicPlans**](BillingApi.md#billingGetPublicPlans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**billingHandleCryptoWebhook**](BillingApi.md#billingHandleCryptoWebhook) | **POST** /api/billing/webhooks/crypto | Crypto payment processor webhook |
| [**billingHandleFlutterwaveWebhook**](BillingApi.md#billingHandleFlutterwaveWebhook) | **POST** /api/billing/webhooks/flutterwave | Flutterwave webhook |
| [**billingInitializePayment**](BillingApi.md#billingInitializePayment) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (app-scoped) |
| [**billingRecordUsage**](BillingApi.md#billingRecordUsage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**billingVerifyPayment**](BillingApi.md#billingVerifyPayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |


<a id="billingCheckFeatureAccess"></a>
# **billingCheckFeatureAccess**
> BillingCheckFeatureAccess200Response billingCheckFeatureAccess(projectId, email, feature)

Check feature access (public)

Check whether a customer has access to a feature (by plan or entitlement). Public; no auth required.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    String email = "email_example"; // String | Customer email
    String feature = "feature_example"; // String | Feature slug to check access for
    try {
      BillingCheckFeatureAccess200Response result = apiInstance.billingCheckFeatureAccess(projectId, email, feature);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingCheckFeatureAccess");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **email** | **String**| Customer email | |
| **feature** | **String**| Feature slug to check access for | |

### Return type

[**BillingCheckFeatureAccess200Response**](BillingCheckFeatureAccess200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Feature access status |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="billingCheckSubscription"></a>
# **billingCheckSubscription**
> BillingCheckSubscription200Response billingCheckSubscription(projectId, email)

Check subscription status (public)

Check whether a customer (by email) has an active subscription for the project. Public; no auth required.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    String email = "email_example"; // String | Customer email to check subscription for
    try {
      BillingCheckSubscription200Response result = apiInstance.billingCheckSubscription(projectId, email);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingCheckSubscription");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **email** | **String**| Customer email to check subscription for | |

### Return type

[**BillingCheckSubscription200Response**](BillingCheckSubscription200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Subscription status |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="billingCreateCheckoutSession"></a>
# **billingCreateCheckoutSession**
> BillingCreateCheckoutSession200Response billingCreateCheckoutSession(projectId, billingCreateCheckoutSessionRequest)

Create checkout session (Flutterwave or crypto)

Creates a checkout session for subscription billing. When Flutterwave is configured (platform), returns authorizationUrl and accessCode for redirect. When using crypto payment processor, returns checkoutUrl, paymentOptions (multi-chain USDC/USDT/BTC Lightning), and reference. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    BillingCreateCheckoutSessionRequest billingCreateCheckoutSessionRequest = new BillingCreateCheckoutSessionRequest(); // BillingCreateCheckoutSessionRequest | Plan to subscribe to, billing cycle, customer email/name, and optional success/cancel redirect URLs.
    try {
      BillingCreateCheckoutSession200Response result = apiInstance.billingCreateCheckoutSession(projectId, billingCreateCheckoutSessionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingCreateCheckoutSession");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **billingCreateCheckoutSessionRequest** | [**BillingCreateCheckoutSessionRequest**](BillingCreateCheckoutSessionRequest.md)| Plan to subscribe to, billing cycle, customer email/name, and optional success/cancel redirect URLs. | |

### Return type

[**BillingCreateCheckoutSession200Response**](BillingCreateCheckoutSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Checkout session created |  -  |
| **400** | Missing planId, billingCycle, or customerInfo.email |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="billingGetCheckoutPayment"></a>
# **billingGetCheckoutPayment**
> BillingGetCheckoutPayment200Response billingGetCheckoutPayment(projectId, paymentId)

Get checkout payment details

Returns payment intent/checkout status (for refresh or deep link). No auth required.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    String paymentId = "paymentId_example"; // String | Payment ID or reference from checkout session
    try {
      BillingGetCheckoutPayment200Response result = apiInstance.billingGetCheckoutPayment(projectId, paymentId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingGetCheckoutPayment");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **paymentId** | **String**| Payment ID or reference from checkout session | |

### Return type

[**BillingGetCheckoutPayment200Response**](BillingGetCheckoutPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Payment not found (exact backend message for payment admin endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="billingGetPublicPlans"></a>
# **billingGetPublicPlans**
> BillingGetPublicPlans200Response billingGetPublicPlans(projectId)

Get public plans (no auth required)

Returns subscription plans available for the project. Public; no authentication required. Use for pricing pages and checkout flow.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) to list plans for.
    try {
      BillingGetPublicPlans200Response result = apiInstance.billingGetPublicPlans(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingGetPublicPlans");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) to list plans for. | |

### Return type

[**BillingGetPublicPlans200Response**](BillingGetPublicPlans200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Public plans list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="billingHandleCryptoWebhook"></a>
# **billingHandleCryptoWebhook**
> BillingHandleCryptoWebhook200Response billingHandleCryptoWebhook(billingHandleCryptoWebhookRequest)

Crypto payment processor webhook

Receives crypto payment events (payment.completed, etc.) for platform billing. No auth; verified by provider signature.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    BillingHandleCryptoWebhookRequest billingHandleCryptoWebhookRequest = new BillingHandleCryptoWebhookRequest(); // BillingHandleCryptoWebhookRequest | Crypto payment webhook payload (event type and data with paymentId, reference, amount, currency, network, status, metadata).
    try {
      BillingHandleCryptoWebhook200Response result = apiInstance.billingHandleCryptoWebhook(billingHandleCryptoWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingHandleCryptoWebhook");
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
| **billingHandleCryptoWebhookRequest** | [**BillingHandleCryptoWebhookRequest**](BillingHandleCryptoWebhookRequest.md)| Crypto payment webhook payload (event type and data with paymentId, reference, amount, currency, network, status, metadata). | |

### Return type

[**BillingHandleCryptoWebhook200Response**](BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook processed |  -  |
| **400** | Event type is required or invalid payload |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="billingHandleFlutterwaveWebhook"></a>
# **billingHandleFlutterwaveWebhook**
> BillingHandleCryptoWebhook200Response billingHandleFlutterwaveWebhook(billingHandleFlutterwaveWebhookRequest)

Flutterwave webhook

Receives Flutterwave webhook events (charge.completed, payment.successful). No auth; verified by verif-hash header. - Subscription billing: meta without isPaymentProcessing triggers verifyPaymentAndCreateSubscription (mudbase_xxx refs). - Payment processing: meta.isPaymentProcessing &#x3D;&#x3D;&#x3D; true triggers fiat payment record (mudbase_fiat_xxx refs); org share goes to org subaccount, platform fee to main or configured subaccounts. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    BillingHandleFlutterwaveWebhookRequest billingHandleFlutterwaveWebhookRequest = new BillingHandleFlutterwaveWebhookRequest(); // BillingHandleFlutterwaveWebhookRequest | Flutterwave webhook payload (event and data with id, tx_ref, amount, currency, status, customer, meta for subscription or payment-processing).
    try {
      BillingHandleCryptoWebhook200Response result = apiInstance.billingHandleFlutterwaveWebhook(billingHandleFlutterwaveWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingHandleFlutterwaveWebhook");
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
| **billingHandleFlutterwaveWebhookRequest** | [**BillingHandleFlutterwaveWebhookRequest**](BillingHandleFlutterwaveWebhookRequest.md)| Flutterwave webhook payload (event and data with id, tx_ref, amount, currency, status, customer, meta for subscription or payment-processing). | |

### Return type

[**BillingHandleCryptoWebhook200Response**](BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook received |  -  |
| **400** | Invalid or missing event |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="billingInitializePayment"></a>
# **billingInitializePayment**
> billingInitializePayment(projectId, billingInitializePaymentRequest)

Initialize fiat payment (app-scoped)

Same as org-level initialize-payment; projectId from path is used for scope and tx_ref. Resolves project to org and uses org&#39;s Flutterwave subaccount.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.auth.*;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID for payment scope and tx_ref.
    BillingInitializePaymentRequest billingInitializePaymentRequest = new BillingInitializePaymentRequest(); // BillingInitializePaymentRequest | Payment amount, currency, customer (email, name), and optional metadata.
    try {
      apiInstance.billingInitializePayment(projectId, billingInitializePaymentRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingInitializePayment");
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
| **projectId** | **String**| Project ID for payment scope and tx_ref. | |
| **billingInitializePaymentRequest** | [**BillingInitializePaymentRequest**](BillingInitializePaymentRequest.md)| Payment amount, currency, customer (email, name), and optional metadata. | |

### Return type

null (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment link and fee breakdown (same shape as org-level) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

<a id="billingRecordUsage"></a>
# **billingRecordUsage**
> MessageResponse billingRecordUsage(projectId, billingRecordUsageRequest)

Record usage (public)

Record metered usage for a customer (e.g. api_calls, storage_mb). Used for usage-based billing. Public endpoint; optionally secured by webhook or API key in production.

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    BillingRecordUsageRequest billingRecordUsageRequest = new BillingRecordUsageRequest(); // BillingRecordUsageRequest | Customer email, metric name (e.g. api_calls, storage_mb), and quantity to record.
    try {
      MessageResponse result = apiInstance.billingRecordUsage(projectId, billingRecordUsageRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingRecordUsage");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **billingRecordUsageRequest** | [**BillingRecordUsageRequest**](BillingRecordUsageRequest.md)| Customer email, metric name (e.g. api_calls, storage_mb), and quantity to record. | |

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
| **200** | Usage recorded |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

<a id="billingVerifyPayment"></a>
# **billingVerifyPayment**
> BillingVerifyPayment200Response billingVerifyPayment(projectId, reference)

Verify payment and create subscription

Verifies payment by reference (Flutterwave mudbase_xxx or crypto pmt_xxx) and creates or updates the subscription. Call after redirect from payment provider; pass reference as query (e.g. ?reference&#x3D;mudbase_abc123). Idempotent for same reference. 

### Example
```java
// Import classes:
import org.openapitools.client.ApiClient;
import org.openapitools.client.ApiException;
import org.openapitools.client.Configuration;
import org.openapitools.client.models.*;
import org.openapitools.client.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID (MongoDB ObjectId) for the billing project.
    String reference = "reference_example"; // String | Payment reference (e.g. mudbase_abc123 or pmt_abc123)
    try {
      BillingVerifyPayment200Response result = apiInstance.billingVerifyPayment(projectId, reference);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#billingVerifyPayment");
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
| **projectId** | **String**| Project ID (MongoDB ObjectId) for the billing project. | |
| **reference** | **String**| Payment reference (e.g. mudbase_abc123 or pmt_abc123) | |

### Return type

[**BillingVerifyPayment200Response**](BillingVerifyPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment verified and subscription created |  -  |
| **400** | reference is required or organization context missing |  -  |
| **403** | Payment does not belong to your organization |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

