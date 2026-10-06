# BillingApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**cancelSubscription**](BillingApi.md#cancelSubscription) | **POST** /api/billing/subscriptions/{subscriptionId}/cancel | Cancel subscription |
| [**checkFeatureAccess**](BillingApi.md#checkFeatureAccess) | **GET** /api/billing/public/projects/{projectId}/feature-access | Check feature access (public) |
| [**checkSubscription**](BillingApi.md#checkSubscription) | **GET** /api/billing/public/projects/{projectId}/subscription | Check subscription status (public) |
| [**createCheckoutSession**](BillingApi.md#createCheckoutSession) | **POST** /api/billing/public/projects/{projectId}/checkout | Create checkout session (fiat) |
| [**createPlan**](BillingApi.md#createPlan) | **POST** /api/billing/projects/{projectId}/plans | Create billing plan |
| [**deletePlan**](BillingApi.md#deletePlan) | **DELETE** /api/billing/projects/{projectId}/plans/{planId} | Delete billing plan |
| [**downloadInvoice**](BillingApi.md#downloadInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId}/download | Download invoice PDF |
| [**enablePaymentProcessing**](BillingApi.md#enablePaymentProcessing) | **POST** /api/orgs/{orgId}/payment-processing/enable | Submit payout onboarding for organization |
| [**exportInvoice**](BillingApi.md#exportInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId}/export | Export invoice (e.g. PDF URL or file) |
| [**getBillingEstimate**](BillingApi.md#getBillingEstimate) | **GET** /api/billing/estimate | Get billing estimate and forecast |
| [**getCheckoutPayment**](BillingApi.md#getCheckoutPayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details (not used for fiat billing) |
| [**getDashboard**](BillingApi.md#getDashboard) | **GET** /api/billing/projects/{projectId}/dashboard | Get billing dashboard data |
| [**getFeeBreakdown**](BillingApi.md#getFeeBreakdown) | **GET** /api/orgs/{orgId}/payment-processing/fee-breakdown | Preview the fee for a given amount |
| [**getInvoice**](BillingApi.md#getInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId} | Get single invoice |
| [**getInvoices**](BillingApi.md#getInvoices) | **GET** /api/billing/projects/{projectId}/invoices | List project invoices |
| [**getPaymentProcessingStatus**](BillingApi.md#getPaymentProcessingStatus) | **GET** /api/orgs/{orgId}/payment-processing/status | Get payout-onboarding status for organization |
| [**getPaymentRecords**](BillingApi.md#getPaymentRecords) | **GET** /api/orgs/{orgId}/payment-processing/records | List fiat payment records for organization |
| [**getPayoutBanks**](BillingApi.md#getPayoutBanks) | **GET** /api/orgs/{orgId}/payment-processing/banks | List settlement banks for a payout country |
| [**getPayoutCountries**](BillingApi.md#getPayoutCountries) | **GET** /api/orgs/{orgId}/payment-processing/countries | List supported payout countries |
| [**getPlans**](BillingApi.md#getPlans) | **GET** /api/billing/projects/{projectId}/plans | Get billing plans |
| [**getPublicPlans**](BillingApi.md#getPublicPlans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**getSubscriptionTierById**](BillingApi.md#getSubscriptionTierById) | **GET** /api/billing/plans/{planId} | Get one subscription tier by id |
| [**getSubscriptionTiers**](BillingApi.md#getSubscriptionTiers) | **GET** /api/billing/plans | Get subscription tiers (org-level BaaS plans) |
| [**getSubscriptions**](BillingApi.md#getSubscriptions) | **GET** /api/billing/projects/{projectId}/subscriptions | Get subscriptions |
| [**initializeOrgPlanCheckout**](BillingApi.md#initializeOrgPlanCheckout) | **POST** /api/billing/org/checkout | Initialize org-level BaaS plan payment (Basic, Starter, Growth, Scale) |
| [**initializePayment**](BillingApi.md#initializePayment) | **POST** /api/orgs/{orgId}/payment-processing/initialize-payment | Initialize fiat payment |
| [**initializePaymentForProject**](BillingApi.md#initializePaymentForProject) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (project-scoped) |
| [**recordUsage**](BillingApi.md#recordUsage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**updatePlan**](BillingApi.md#updatePlan) | **PATCH** /api/billing/projects/{projectId}/plans/{planId} | Update billing plan |
| [**verifyOrgPlanPayment**](BillingApi.md#verifyOrgPlanPayment) | **POST** /api/billing/org/verify-payment | Verify org-level plan payment |
| [**verifyPayment**](BillingApi.md#verifyPayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |


<a id="cancelSubscription"></a>
# **cancelSubscription**
> DeleteRole200Response cancelSubscription(subscriptionId, cancelSubscriptionRequest)

Cancel subscription

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String subscriptionId = "subscriptionId_example"; // String | 
    CancelSubscriptionRequest cancelSubscriptionRequest = new CancelSubscriptionRequest(); // CancelSubscriptionRequest | 
    try {
      DeleteRole200Response result = apiInstance.cancelSubscription(subscriptionId, cancelSubscriptionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#cancelSubscription");
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
| **subscriptionId** | **String**|  | |
| **cancelSubscriptionRequest** | [**CancelSubscriptionRequest**](CancelSubscriptionRequest.md)|  | [optional] |

### Return type

[**DeleteRole200Response**](DeleteRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Subscription cancelled |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

<a id="checkFeatureAccess"></a>
# **checkFeatureAccess**
> CheckFeatureAccess200Response checkFeatureAccess(projectId, email, feature)

Check feature access (public)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String email = "email_example"; // String | Customer email
    String feature = "feature_example"; // String | Feature slug to check access for
    try {
      CheckFeatureAccess200Response result = apiInstance.checkFeatureAccess(projectId, email, feature);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#checkFeatureAccess");
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
| **email** | **String**| Customer email | |
| **feature** | **String**| Feature slug to check access for | |

### Return type

[**CheckFeatureAccess200Response**](CheckFeatureAccess200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Feature access status |  -  |

<a id="checkSubscription"></a>
# **checkSubscription**
> CheckSubscription200Response checkSubscription(projectId, email)

Check subscription status (public)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String email = "email_example"; // String | Customer email to check subscription for
    try {
      CheckSubscription200Response result = apiInstance.checkSubscription(projectId, email);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#checkSubscription");
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
| **email** | **String**| Customer email to check subscription for | |

### Return type

[**CheckSubscription200Response**](CheckSubscription200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Subscription status |  -  |

<a id="createCheckoutSession"></a>
# **createCheckoutSession**
> CreateCheckoutSession200Response createCheckoutSession(projectId, createCheckoutSessionRequest)

Create checkout session (fiat)

**Customer subscription flow — Step 2.** Creates a fiat checkout session. Request body must include planId (from GET public plans), billingCycle (monthly|yearly), and customerInfo.email. Redirect the user to **checkoutUrl** (same URL as authorizationUrl). After payment, call verify-payment with **reference** (mudbase_...). Response includes only fiat fields (no paymentAddress, paymentOptions, network, asset, or pmt_ references). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID
    CreateCheckoutSessionRequest createCheckoutSessionRequest = new CreateCheckoutSessionRequest(); // CreateCheckoutSessionRequest | 
    try {
      CreateCheckoutSession200Response result = apiInstance.createCheckoutSession(projectId, createCheckoutSessionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#createCheckoutSession");
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
| **projectId** | **String**| Project ID | |
| **createCheckoutSessionRequest** | [**CreateCheckoutSessionRequest**](CreateCheckoutSessionRequest.md)|  | |

### Return type

[**CreateCheckoutSession200Response**](CreateCheckoutSession200Response.md)

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
| **500** | Internal server error |  -  |

<a id="createPlan"></a>
# **createPlan**
> CreatePlan201Response createPlan(projectId, createPlanRequest)

Create billing plan

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    CreatePlanRequest createPlanRequest = new CreatePlanRequest(); // CreatePlanRequest | 
    try {
      CreatePlan201Response result = apiInstance.createPlan(projectId, createPlanRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#createPlan");
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
| **createPlanRequest** | [**CreatePlanRequest**](CreatePlanRequest.md)|  | |

### Return type

[**CreatePlan201Response**](CreatePlan201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Plan created |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="deletePlan"></a>
# **deletePlan**
> MessageResponse deletePlan(projectId, planId)

Delete billing plan

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String planId = "planId_example"; // String | 
    try {
      MessageResponse result = apiInstance.deletePlan(projectId, planId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#deletePlan");
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
| **planId** | **String**|  | |

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
| **200** | Plan deleted |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="downloadInvoice"></a>
# **downloadInvoice**
> File downloadInvoice(projectId, invoiceId)

Download invoice PDF

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String invoiceId = "invoiceId_example"; // String | 
    try {
      File result = apiInstance.downloadInvoice(projectId, invoiceId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#downloadInvoice");
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
| **invoiceId** | **String**|  | |

### Return type

[**File**](File.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/pdf, application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invoice PDF file or redirect URL |  -  |
| **401** | Authentication required |  -  |
| **404** | Invoice not found |  -  |
| **500** | Internal server error |  -  |

<a id="enablePaymentProcessing"></a>
# **enablePaymentProcessing**
> EnablePaymentProcessing200Response enablePaymentProcessing(orgId, enablePaymentProcessingRequest)

Submit payout onboarding for organization

Validates and stores the org&#39;s payout account details, then queues the org for platform-admin review. This does not activate payments by itself; initialize-payment only starts succeeding once the org is approved. The required fields depend on the chosen country: call GET /payment-processing/countries first and collect exactly the fields that country&#39;s schema returns (bank code + account number for most African markets, plus a BVN for Nigeria, or routing number/sort code + account type + account holder name for the US/UK). Requires owner or admin role.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    EnablePaymentProcessingRequest enablePaymentProcessingRequest = new EnablePaymentProcessingRequest(); // EnablePaymentProcessingRequest | 
    try {
      EnablePaymentProcessing200Response result = apiInstance.enablePaymentProcessing(orgId, enablePaymentProcessingRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#enablePaymentProcessing");
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
| **orgId** | **String**|  | |
| **enablePaymentProcessingRequest** | [**EnablePaymentProcessingRequest**](EnablePaymentProcessingRequest.md)|  | |

### Return type

[**EnablePaymentProcessing200Response**](EnablePaymentProcessing200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Onboarding submitted (or already enabled) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **500** | Internal server error |  -  |

<a id="exportInvoice"></a>
# **exportInvoice**
> DownloadInvoice200Response exportInvoice(projectId, invoiceId)

Export invoice (e.g. PDF URL or file)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String invoiceId = "invoiceId_example"; // String | 
    try {
      DownloadInvoice200Response result = apiInstance.exportInvoice(projectId, invoiceId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#exportInvoice");
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
| **invoiceId** | **String**|  | |

### Return type

[**DownloadInvoice200Response**](DownloadInvoice200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Export result (URL or file) |  -  |
| **401** | Authentication required |  -  |
| **404** | Invoice not found |  -  |
| **500** | Internal server error |  -  |

<a id="getBillingEstimate"></a>
# **getBillingEstimate**
> GetBillingEstimate200Response getBillingEstimate()

Get billing estimate and forecast

Returns current-month overage estimate and an optional end-of-month forecast for the authenticated organization. Includes spend limit settings (soft/hard) and whether usage is currently blocked. Requires org-level JWT. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    try {
      GetBillingEstimate200Response result = apiInstance.getBillingEstimate();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getBillingEstimate");
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

[**GetBillingEstimate200Response**](GetBillingEstimate200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Billing estimate and forecast |  -  |
| **401** | Authentication required |  -  |
| **503** | Service temporarily unavailable. Returned when the organization is restricted (e.g. suspended due to unpaid overage, spend limit exceeded, or API usage limit reached). End-users see a generic message; the real reason is logged server-side only.  |  -  |

<a id="getCheckoutPayment"></a>
# **getCheckoutPayment**
> getCheckoutPayment(projectId, paymentId)

Get checkout payment details (not used for fiat billing)

**Fiat-only billing:** checkout is completed on the payment gateway&#39;s hosted page; there is no server-side payment intent to poll. The live API returns **404** for this route. Reserved for compatibility; do not rely on a success body for project billing. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String paymentId = "paymentId_example"; // String | Opaque id from checkout (fiat billing does not expose pollable payment state here)
    try {
      apiInstance.getCheckoutPayment(projectId, paymentId);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getCheckoutPayment");
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
| **paymentId** | **String**| Opaque id from checkout (fiat billing does not expose pollable payment state here) | |

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
| **404** | Payment not found |  -  |
| **500** | Internal server error |  -  |

<a id="getDashboard"></a>
# **getDashboard**
> GetDashboard200Response getDashboard(projectId)

Get billing dashboard data

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetDashboard200Response result = apiInstance.getDashboard(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getDashboard");
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

[**GetDashboard200Response**](GetDashboard200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Dashboard data |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

<a id="getFeeBreakdown"></a>
# **getFeeBreakdown**
> GetFeeBreakdown200Response getFeeBreakdown(orgId, amount, currency, country, method, international)

Preview the fee for a given amount

Returns the single all-in Mudbase fee, its effective rate, and what the org would net for the given amount, without creating a payment. Pass country/method/international to price a specific rail; omitting them uses a generic local-rail estimate. Never returns the underlying rail&#39;s own cost or any internal margin split.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    BigDecimal amount = new BigDecimal(78); // BigDecimal | 
    String currency = "USD"; // String | 
    String country = "country_example"; // String | ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries.
    String method = "card"; // String | 
    Boolean international = false; // Boolean | Set true for a cross-border/international card, Apple Pay, or Google Pay.
    try {
      GetFeeBreakdown200Response result = apiInstance.getFeeBreakdown(orgId, amount, currency, country, method, international);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getFeeBreakdown");
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
| **orgId** | **String**|  | |
| **amount** | **BigDecimal**|  | |
| **currency** | **String**|  | [optional] [default to USD] |
| **country** | **String**| ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries. | [optional] |
| **method** | **String**|  | [optional] [default to card] [enum: card, momo, bank_transfer, ussd, eft] |
| **international** | **Boolean**| Set true for a cross-border/international card, Apple Pay, or Google Pay. | [optional] [default to false] |

### Return type

[**GetFeeBreakdown200Response**](GetFeeBreakdown200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee breakdown |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="getInvoice"></a>
# **getInvoice**
> GetInvoice200Response getInvoice(projectId, invoiceId)

Get single invoice

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String invoiceId = "invoiceId_example"; // String | 
    try {
      GetInvoice200Response result = apiInstance.getInvoice(projectId, invoiceId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getInvoice");
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
| **invoiceId** | **String**|  | |

### Return type

[**GetInvoice200Response**](GetInvoice200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invoice details |  -  |
| **401** | Authentication required |  -  |
| **404** | Invoice not found |  -  |
| **500** | Internal server error |  -  |

<a id="getInvoices"></a>
# **getInvoices**
> GetInvoices200Response getInvoices(projectId)

List project invoices

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetInvoices200Response result = apiInstance.getInvoices(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getInvoices");
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

[**GetInvoices200Response**](GetInvoices200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invoices list |  -  |
| **401** | Authentication required |  -  |
| **500** | Internal server error |  -  |

<a id="getPaymentProcessingStatus"></a>
# **getPaymentProcessingStatus**
> GetPaymentProcessingStatus200Response getPaymentProcessingStatus(orgId)

Get payout-onboarding status for organization

Returns the current onboarding/approval state for the org&#39;s payout account. Poll this after calling enable, or before calling initialize-payment, to confirm the org is actually approved rather than assuming a 200 from enable means payments are live. Never returns the raw payout-account id, only whether one exists.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    try {
      GetPaymentProcessingStatus200Response result = apiInstance.getPaymentProcessingStatus(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPaymentProcessingStatus");
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
| **orgId** | **String**|  | |

### Return type

[**GetPaymentProcessingStatus200Response**](GetPaymentProcessingStatus200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payout-onboarding status |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

<a id="getPaymentRecords"></a>
# **getPaymentRecords**
> GetPaymentRecords200Response getPaymentRecords(orgId, page, limit, status)

List fiat payment records for organization

Paginated list of FiatPaymentRecord for this org (txRef, amount, orgReceives, status, paidAt).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    Integer page = 1; // Integer | 
    Integer limit = 20; // Integer | 
    String status = "pending"; // String | 
    try {
      GetPaymentRecords200Response result = apiInstance.getPaymentRecords(orgId, page, limit, status);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPaymentRecords");
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
| **orgId** | **String**|  | |
| **page** | **Integer**|  | [optional] [default to 1] |
| **limit** | **Integer**|  | [optional] [default to 20] |
| **status** | **String**|  | [optional] [enum: pending, successful, failed] |

### Return type

[**GetPaymentRecords200Response**](GetPaymentRecords200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Records and pagination |  -  |
| **401** | Authentication required |  -  |

<a id="getPayoutBanks"></a>
# **getPayoutBanks**
> GetPayoutBanks200Response getPayoutBanks(orgId, country)

List settlement banks for a payout country

Read-only lookup of the settlement-bank list for a country, only meaningful when that country&#39;s entry from GET /payment-processing/countries has banksListSupported: true. For a country where it is false, this returns an empty list and your onboarding form should fall back to the free-text bank/code field the countries response already describes for that country, rather than calling this endpoint.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String country = "country_example"; // String | ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries.
    try {
      GetPayoutBanks200Response result = apiInstance.getPayoutBanks(orgId, country);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPayoutBanks");
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
| **orgId** | **String**|  | |
| **country** | **String**| ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries. | |

### Return type

[**GetPayoutBanks200Response**](GetPayoutBanks200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bank list for the country |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

<a id="getPayoutCountries"></a>
# **getPayoutCountries**
> GetPayoutCountries200Response getPayoutCountries(orgId)

List supported payout countries

Returns the full supported payout-country set and each country&#39;s payout-account field schema. Drives a dynamic onboarding form: which fields to collect (bank code/routing number/sort code/IBAN, whether a BVN is required, whether a bank list or mobile-money network applies) comes straight from this response, so build your onboarding UI to render from it rather than hardcoding a country list.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    try {
      GetPayoutCountries200Response result = apiInstance.getPayoutCountries(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPayoutCountries");
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
| **orgId** | **String**|  | |

### Return type

[**GetPayoutCountries200Response**](GetPayoutCountries200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Supported countries and field schemas |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

<a id="getPlans"></a>
# **getPlans**
> GetPlans200Response getPlans(projectId)

Get billing plans

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetPlans200Response result = apiInstance.getPlans(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPlans");
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

[**GetPlans200Response**](GetPlans200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plans list |  -  |
| **401** | Authentication required |  -  |

<a id="getPublicPlans"></a>
# **getPublicPlans**
> GetPublicPlans200Response getPublicPlans(projectId)

Get public plans (no auth required)

**Customer subscription flow — Step 1.** Returns all active plans for the project. Use a plan&#39;s _id as planId in the checkout request. No authentication required (for pricing/checkout pages). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetPublicPlans200Response result = apiInstance.getPublicPlans(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getPublicPlans");
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

[**GetPublicPlans200Response**](GetPublicPlans200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Public plans list |  -  |

<a id="getSubscriptionTierById"></a>
# **getSubscriptionTierById**
> GetSubscriptionTierById200Response getSubscriptionTierById(planId)

Get one subscription tier by id

Returns a single org-level BaaS plan (free, basic, starter, growth, scale, enterprise). Public; no auth required.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String planId = "planId_example"; // String | Plan id (free, basic, starter, growth, scale, enterprise)
    try {
      GetSubscriptionTierById200Response result = apiInstance.getSubscriptionTierById(planId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getSubscriptionTierById");
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
| **planId** | **String**| Plan id (free, basic, starter, growth, scale, enterprise) | |

### Return type

[**GetSubscriptionTierById200Response**](GetSubscriptionTierById200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plan details |  -  |
| **404** | Plan not found |  -  |

<a id="getSubscriptionTiers"></a>
# **getSubscriptionTiers**
> GetSubscriptionTiers200Response getSubscriptionTiers()

Get subscription tiers (org-level BaaS plans)

**Org-level BaaS plan catalog** (source of truth in paymentService.js). Returns Free, Basic ($12), Starter ($29), Growth ($69), Scale ($199), Enterprise. Use for pricing page and to get plan ids for POST /api/billing/org/checkout. Public; no auth required. Each plan includes id (free|basic|starter|growth|scale|enterprise), name, description, price (cents), priceYearly (cents, 2 months free), currency, limits, overages, enforcement. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    try {
      GetSubscriptionTiers200Response result = apiInstance.getSubscriptionTiers();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getSubscriptionTiers");
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

[**GetSubscriptionTiers200Response**](GetSubscriptionTiers200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plan list |  -  |

<a id="getSubscriptions"></a>
# **getSubscriptions**
> GetSubscriptions200Response getSubscriptions(projectId)

Get subscriptions

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      GetSubscriptions200Response result = apiInstance.getSubscriptions(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#getSubscriptions");
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

[**GetSubscriptions200Response**](GetSubscriptions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Subscriptions list |  -  |
| **401** | Authentication required |  -  |

<a id="initializeOrgPlanCheckout"></a>
# **initializeOrgPlanCheckout**
> InitializeOrgPlanCheckout200Response initializeOrgPlanCheckout(initializeOrgPlanCheckoutRequest)

Initialize org-level BaaS plan payment (Basic, Starter, Growth, Scale)

**Org plan payment flow — Step 2.** Creates a payment link for the authenticated org to subscribe to a BaaS plan (basic, starter, growth, scale). Enterprise has no price; use contact-sales flow. Redirect the user to the returned link; after payment, call POST /api/billing/org/verify-payment with the tx_ref from the redirect. Requires org-level JWT. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    InitializeOrgPlanCheckoutRequest initializeOrgPlanCheckoutRequest = new InitializeOrgPlanCheckoutRequest(); // InitializeOrgPlanCheckoutRequest | 
    try {
      InitializeOrgPlanCheckout200Response result = apiInstance.initializeOrgPlanCheckout(initializeOrgPlanCheckoutRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#initializeOrgPlanCheckout");
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
| **initializeOrgPlanCheckoutRequest** | [**InitializeOrgPlanCheckoutRequest**](InitializeOrgPlanCheckoutRequest.md)|  | |

### Return type

[**InitializeOrgPlanCheckout200Response**](InitializeOrgPlanCheckout200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment link created |  -  |
| **400** | Invalid planName or payment gateway not configured |  -  |
| **401** | Organization context required |  -  |

<a id="initializePayment"></a>
# **initializePayment**
> InitializePayment200Response initializePayment(orgId, initializePaymentRequest)

Initialize fiat payment

Creates a payment link. The customer pays; Mudbase charges a single all-in, cost-plus fee (see GET /payment-processing/fee-breakdown for the exact rate for a given country/method) and the org receives the remainder. Requires payment processing enabled and approved for the org.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    InitializePaymentRequest initializePaymentRequest = new InitializePaymentRequest(); // InitializePaymentRequest | 
    try {
      InitializePayment200Response result = apiInstance.initializePayment(orgId, initializePaymentRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#initializePayment");
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
| **orgId** | **String**|  | |
| **initializePaymentRequest** | [**InitializePaymentRequest**](InitializePaymentRequest.md)|  | |

### Return type

[**InitializePayment200Response**](InitializePayment200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment link and fee breakdown |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **500** | Internal server error |  -  |

<a id="initializePaymentForProject"></a>
# **initializePaymentForProject**
> initializePaymentForProject(projectId, initializePaymentForProjectRequest)

Initialize fiat payment (project-scoped)

Same as org-level initialize-payment; projectId from path is used for scope and tx_ref. Resolves project to org and uses org&#39;s payment-processing subaccount.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    InitializePaymentForProjectRequest initializePaymentForProjectRequest = new InitializePaymentForProjectRequest(); // InitializePaymentForProjectRequest | 
    try {
      apiInstance.initializePaymentForProject(projectId, initializePaymentForProjectRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#initializePaymentForProject");
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
| **initializePaymentForProjectRequest** | [**InitializePaymentForProjectRequest**](InitializePaymentForProjectRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment link and fee breakdown (same shape as org-level) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **500** | Internal server error |  -  |

<a id="recordUsage"></a>
# **recordUsage**
> MessageResponse recordUsage(projectId, recordUsageRequest)

Record usage (public)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    RecordUsageRequest recordUsageRequest = new RecordUsageRequest(); // RecordUsageRequest | 
    try {
      MessageResponse result = apiInstance.recordUsage(projectId, recordUsageRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#recordUsage");
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
| **recordUsageRequest** | [**RecordUsageRequest**](RecordUsageRequest.md)|  | |

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
| **400** | Bad request |  -  |

<a id="updatePlan"></a>
# **updatePlan**
> CreatePlan201Response updatePlan(projectId, planId, updatePlanRequest)

Update billing plan

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

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

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String planId = "planId_example"; // String | 
    UpdatePlanRequest updatePlanRequest = new UpdatePlanRequest(); // UpdatePlanRequest | 
    try {
      CreatePlan201Response result = apiInstance.updatePlan(projectId, planId, updatePlanRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#updatePlan");
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
| **planId** | **String**|  | |
| **updatePlanRequest** | [**UpdatePlanRequest**](UpdatePlanRequest.md)|  | |

### Return type

[**CreatePlan201Response**](CreatePlan201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plan updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="verifyOrgPlanPayment"></a>
# **verifyOrgPlanPayment**
> VerifyOrgPlanPayment200Response verifyOrgPlanPayment(txRef, reference)

Verify org-level plan payment

**Org plan payment flow — Step 3.** Call after the user completes payment (redirect or webhook). Pass tx_ref (or reference) from the payment redirect. Updates org plan and billing; idempotent. No auth required (redirect callback can call this). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String txRef = "txRef_example"; // String | Payment reference (mudbase_org_...) from checkout redirect
    String reference = "reference_example"; // String | Alias for tx_ref
    try {
      VerifyOrgPlanPayment200Response result = apiInstance.verifyOrgPlanPayment(txRef, reference);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#verifyOrgPlanPayment");
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
| **txRef** | **String**| Payment reference (mudbase_org_...) from checkout redirect | [optional] |
| **reference** | **String**| Alias for tx_ref | [optional] |

### Return type

[**VerifyOrgPlanPayment200Response**](VerifyOrgPlanPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment verified and org plan updated |  -  |
| **400** | tx_ref required, invalid reference, or payment verification failed |  -  |

<a id="verifyPayment"></a>
# **verifyPayment**
> VerifyPayment200Response verifyPayment(projectId, reference)

Verify payment and create subscription

**Customer subscription flow — Step 3.** Call after the user completes payment. Pass **reference** as query (?reference&#x3D;mudbase_...). On success, a subscription is created. No auth required when using the platform gateway (mudbase_ refs). Org-level gateway verification may require JWT. References starting with pmt_ are rejected (crypto billing is not enabled on this API). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    BillingApi apiInstance = new BillingApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String reference = "reference_example"; // String | Payment transaction reference (mudbase_...)
    try {
      VerifyPayment200Response result = apiInstance.verifyPayment(projectId, reference);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#verifyPayment");
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
| **reference** | **String**| Payment transaction reference (mudbase_...) | |

### Return type

[**VerifyPayment200Response**](VerifyPayment200Response.md)

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
| **500** | Internal server error |  -  |

