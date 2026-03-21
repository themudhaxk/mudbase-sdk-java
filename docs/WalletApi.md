# WalletApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**walletBroadcastTransaction**](WalletApi.md#walletBroadcastTransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**walletCreateWebhook**](WalletApi.md#walletCreateWebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**walletDeleteAddress**](WalletApi.md#walletDeleteAddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete (soft-delete) a non-custodial address |
| [**walletDeleteWebhook**](WalletApi.md#walletDeleteWebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**walletEstimateGas**](WalletApi.md#walletEstimateGas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**walletGetAddress**](WalletApi.md#walletGetAddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**walletGetBalance**](WalletApi.md#walletGetBalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**walletGetCancelParams**](WalletApi.md#walletGetCancelParams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**walletGetSpeedUpParams**](WalletApi.md#walletGetSpeedUpParams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**walletGetTransactionByHash**](WalletApi.md#walletGetTransactionByHash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**walletGetTransactions**](WalletApi.md#walletGetTransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**walletGetWebhookLogs**](WalletApi.md#walletGetWebhookLogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**walletListAddresses**](WalletApi.md#walletListAddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**walletListWebhooks**](WalletApi.md#walletListWebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**walletRegisterAddress**](WalletApi.md#walletRegisterAddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**walletTestWebhook**](WalletApi.md#walletTestWebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**walletUpdateWebhook**](WalletApi.md#walletUpdateWebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |


<a id="walletBroadcastTransaction"></a>
# **walletBroadcastTransaction**
> WalletBroadcastTransaction200Response walletBroadcastTransaction(walletBroadcastTransactionRequest)

Broadcast a client-signed transaction

Broadcast a transaction that has been signed client-side. The transaction must be fully signed before sending. The fromAddress must be registered and belong to your organization (POST /api/wallet/non-custodial/register-address). **Supported chains:** EVM (ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo), UTXO (bitcoin, litecoin, dogecoin), and chain-specific (tron, solana, ton, cardano). Use &#x60;binance&#x60; or &#x60;bsc&#x60; for BNB Smart Chain. **Testing with custodial:** You can create a wallet via POST /api/wallet/create, get its private key via GET /api/wallet/{walletId}/private-key, register that address with POST /api/wallet/non-custodial/register-address, then build a signed tx (using POST /api/wallet/estimate-network-fee or estimate-gas for fees) and broadcast it here to test the non-custodial flow end-to-end. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletBroadcastTransactionRequest walletBroadcastTransactionRequest = new WalletBroadcastTransactionRequest(); // WalletBroadcastTransactionRequest | Chain, signed transaction (hex), and fromAddress (must be registered).
    try {
      WalletBroadcastTransaction200Response result = apiInstance.walletBroadcastTransaction(walletBroadcastTransactionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletBroadcastTransaction");
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
| **walletBroadcastTransactionRequest** | [**WalletBroadcastTransactionRequest**](WalletBroadcastTransactionRequest.md)| Chain, signed transaction (hex), and fromAddress (must be registered). | |

### Return type

[**WalletBroadcastTransaction200Response**](WalletBroadcastTransaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction broadcast successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletCreateWebhook"></a>
# **walletCreateWebhook**
> WalletCreateWebhook201Response walletCreateWebhook(walletCreateWebhookRequest)

Create a wallet webhook

Register a webhook URL to receive wallet events (balance updates, transaction confirmed/failed/detected/broadcast, token balance, address created/deactivated). Optional filters by addresses and chains. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletCreateWebhookRequest walletCreateWebhookRequest = new WalletCreateWebhookRequest(); // WalletCreateWebhookRequest | Webhook URL, events array, optional secret and filters (addresses, chains, projectId).
    try {
      WalletCreateWebhook201Response result = apiInstance.walletCreateWebhook(walletCreateWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletCreateWebhook");
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
| **walletCreateWebhookRequest** | [**WalletCreateWebhookRequest**](WalletCreateWebhookRequest.md)| Webhook URL, events array, optional secret and filters (addresses, chains, projectId). | |

### Return type

[**WalletCreateWebhook201Response**](WalletCreateWebhook201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Webhook created successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletDeleteAddress"></a>
# **walletDeleteAddress**
> FunctionsDelete200Response walletDeleteAddress(addressId)

Delete (soft-delete) a non-custodial address

Soft-deletes a registered non-custodial address. The address is marked inactive and no longer used for broadcasts or balance/transaction queries. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | Registered address ID to delete.
    try {
      FunctionsDelete200Response result = apiInstance.walletDeleteAddress(addressId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletDeleteAddress");
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
| **addressId** | **String**| Registered address ID to delete. | |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletDeleteWebhook"></a>
# **walletDeleteWebhook**
> FunctionsDelete200Response walletDeleteWebhook(webhookId)

Delete a wallet webhook

Permanently delete a wallet webhook. Delivery will stop immediately.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | Webhook ID (MongoDB ObjectId) to delete.
    try {
      FunctionsDelete200Response result = apiInstance.walletDeleteWebhook(webhookId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletDeleteWebhook");
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
| **webhookId** | **String**| Webhook ID (MongoDB ObjectId) to delete. | |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletEstimateGas"></a>
# **walletEstimateGas**
> WalletEstimateGas200Response walletEstimateGas(walletEstimateGasRequest)

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require &#x60;transaction&#x60; (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only &#x60;chain&#x60; is required; &#x60;transaction&#x60; is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletEstimateGasRequest walletEstimateGasRequest = new WalletEstimateGasRequest(); // WalletEstimateGasRequest | Chain and optional transaction shape (required for EVM). Returns network fee from blockchain.
    try {
      WalletEstimateGas200Response result = apiInstance.walletEstimateGas(walletEstimateGasRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletEstimateGas");
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
| **walletEstimateGasRequest** | [**WalletEstimateGasRequest**](WalletEstimateGasRequest.md)| Chain and optional transaction shape (required for EVM). Returns network fee from blockchain. | |

### Return type

[**WalletEstimateGas200Response**](WalletEstimateGas200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee from blockchain RPC (not from Mudbase logic) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletGetAddress"></a>
# **walletGetAddress**
> NonCustodialAddressResponse walletGetAddress(addressId)

Get non-custodial address by ID

Returns metadata and status for a single registered non-custodial address (ID, address, chain, label, org, project, derivationPath, isActive, timestamps). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | Registered address ID (MongoDB ObjectId).
    try {
      NonCustodialAddressResponse result = apiInstance.walletGetAddress(addressId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetAddress");
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
| **addressId** | **String**| Registered address ID (MongoDB ObjectId). | |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletGetBalance"></a>
# **walletGetBalance**
> WalletGetBalance200Response walletGetBalance(addressId)

Get balance for a non-custodial address

Returns native token balance (confirmed, unconfirmed, total, currency) for a registered non-custodial address. Updated periodically from the chain. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | Registered address ID.
    try {
      WalletGetBalance200Response result = apiInstance.walletGetBalance(addressId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetBalance");
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
| **addressId** | **String**| Registered address ID. | |

### Return type

[**WalletGetBalance200Response**](WalletGetBalance200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Balance information |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletGetCancelParams"></a>
# **walletGetCancelParams**
> WalletGetCancelParams200Response walletGetCancelParams(walletGetCancelParamsRequest)

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to&#x3D;self, value&#x3D;0, data&#x3D;0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletGetCancelParamsRequest walletGetCancelParamsRequest = new WalletGetCancelParamsRequest(); // WalletGetCancelParamsRequest | Stuck transaction identifier (txId or txHash) and EVM chain for cancel.
    try {
      WalletGetCancelParams200Response result = apiInstance.walletGetCancelParams(walletGetCancelParamsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetCancelParams");
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
| **walletGetCancelParamsRequest** | [**WalletGetCancelParamsRequest**](WalletGetCancelParamsRequest.md)| Stuck transaction identifier (txId or txHash) and EVM chain for cancel. | |

### Return type

[**WalletGetCancelParams200Response**](WalletGetCancelParams200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cancel tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |

<a id="walletGetSpeedUpParams"></a>
# **walletGetSpeedUpParams**
> WalletGetSpeedUpParams200Response walletGetSpeedUpParams(walletGetSpeedUpParamsRequest)

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending &gt;5 min (stuck). EVM chains only. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletGetSpeedUpParamsRequest walletGetSpeedUpParamsRequest = new WalletGetSpeedUpParamsRequest(); // WalletGetSpeedUpParamsRequest | Stuck transaction identifier (txId or txHash) and EVM chain.
    try {
      WalletGetSpeedUpParams200Response result = apiInstance.walletGetSpeedUpParams(walletGetSpeedUpParamsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetSpeedUpParams");
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
| **walletGetSpeedUpParamsRequest** | [**WalletGetSpeedUpParamsRequest**](WalletGetSpeedUpParamsRequest.md)| Stuck transaction identifier (txId or txHash) and EVM chain. | |

### Return type

[**WalletGetSpeedUpParams200Response**](WalletGetSpeedUpParams200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Replacement tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |

<a id="walletGetTransactionByHash"></a>
# **walletGetTransactionByHash**
> WalletGetTransactionByHash200Response walletGetTransactionByHash(txHash, chain)

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String txHash = "txHash_example"; // String | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO)
    String chain = "ethereum"; // String | Chain the transaction belongs to (required for lookup)
    try {
      WalletGetTransactionByHash200Response result = apiInstance.walletGetTransactionByHash(txHash, chain);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetTransactionByHash");
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
| **txHash** | **String**| Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO) | |
| **chain** | **String**| Chain the transaction belongs to (required for lookup) | [enum: ethereum, binance, polygon, celo, bitcoin, litecoin, solana, tron, ripple, cardano, dogecoin, ton] |

### Return type

[**WalletGetTransactionByHash200Response**](WalletGetTransactionByHash200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **400** | Bad Request - missing or invalid chain (add ?chain&#x3D;ethereum) |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletGetTransactions"></a>
# **walletGetTransactions**
> WalletGetTransactions200Response walletGetTransactions(addressId, limit, page)

Get transaction history for a non-custodial address

Returns paginated transaction history for a registered non-custodial address (incoming/outgoing, status, confirmations, amounts). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | Registered address ID.
    Integer limit = 50; // Integer | Number of transactions per page.
    Integer page = 1; // Integer | Page number (1-based).
    try {
      WalletGetTransactions200Response result = apiInstance.walletGetTransactions(addressId, limit, page);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetTransactions");
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
| **addressId** | **String**| Registered address ID. | |
| **limit** | **Integer**| Number of transactions per page. | [optional] [default to 50] |
| **page** | **Integer**| Page number (1-based). | [optional] [default to 1] |

### Return type

[**WalletGetTransactions200Response**](WalletGetTransactions200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletGetWebhookLogs"></a>
# **walletGetWebhookLogs**
> WalletGetWebhookLogs200Response walletGetWebhookLogs(webhookId, limit)

Get webhook delivery logs

List delivery attempts for a wallet webhook (success/failure, payload, response, duration). Paginated by limit.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | Webhook ID (MongoDB ObjectId) to get logs for.
    Integer limit = 50; // Integer | Maximum number of log entries to return.
    try {
      WalletGetWebhookLogs200Response result = apiInstance.walletGetWebhookLogs(webhookId, limit);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletGetWebhookLogs");
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
| **webhookId** | **String**| Webhook ID (MongoDB ObjectId) to get logs for. | |
| **limit** | **Integer**| Maximum number of log entries to return. | [optional] [default to 50] |

### Return type

[**WalletGetWebhookLogs200Response**](WalletGetWebhookLogs200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletListAddresses"></a>
# **walletListAddresses**
> WalletListAddresses200Response walletListAddresses(chain, projectId)

List registered non-custodial addresses

Returns all non-custodial addresses registered for the current project/organization. Optional filters by chain and projectId. Addresses must be registered via POST /api/wallet/non-custodial/register-address before use. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String chain = "ethereum"; // String | Filter by chain (optional)
    String projectId = "projectId_example"; // String | Filter by project ID (optional).
    try {
      WalletListAddresses200Response result = apiInstance.walletListAddresses(chain, projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletListAddresses");
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
| **chain** | **String**| Filter by chain (optional) | [optional] [enum: ethereum, binance, bsc, polygon, arbitrum, optimism, base, avalanche, celo, bitcoin, litecoin, dogecoin, solana, tron, ripple, cardano, ton] |
| **projectId** | **String**| Filter by project ID (optional). | [optional] |

### Return type

[**WalletListAddresses200Response**](WalletListAddresses200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of registered addresses |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletListWebhooks"></a>
# **walletListWebhooks**
> WalletListWebhooks200Response walletListWebhooks(projectId)

List wallet webhooks

Returns all wallet webhooks for the current context, optionally filtered by projectId. Includes delivery stats and active status. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String projectId = "projectId_example"; // String | Filter by project ID (optional).
    try {
      WalletListWebhooks200Response result = apiInstance.walletListWebhooks(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletListWebhooks");
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
| **projectId** | **String**| Filter by project ID (optional). | [optional] |

### Return type

[**WalletListWebhooks200Response**](WalletListWebhooks200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of webhooks |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletRegisterAddress"></a>
# **walletRegisterAddress**
> NonCustodialAddressResponse walletRegisterAddress(walletRegisterAddressRequest)

Register a non-custodial wallet address

Register a public wallet address for balance monitoring, transaction indexing, and webhook notifications. Keys are never sent to the server; generation and signing happen client-side only. Supports EVM, UTXO, Solana, Tron, TON, Cardano, and other chains. Optionally provide derivation path and label for multi-address tracking. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletRegisterAddressRequest walletRegisterAddressRequest = new WalletRegisterAddressRequest(); // WalletRegisterAddressRequest | Public address, chain identifier, and optional derivation path and label. projectId scopes the registration to a project.
    try {
      NonCustodialAddressResponse result = apiInstance.walletRegisterAddress(walletRegisterAddressRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletRegisterAddress");
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
| **walletRegisterAddressRequest** | [**WalletRegisterAddressRequest**](WalletRegisterAddressRequest.md)| Public address, chain identifier, and optional derivation path and label. projectId scopes the registration to a project. | |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Address registered successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletTestWebhook"></a>
# **walletTestWebhook**
> WalletTestWebhook200Response walletTestWebhook(walletTestWebhookRequest)

Test a webhook delivery (sends a single test payload)

Sends a test payload to the given URL to verify webhook connectivity and signature. Uses the same signing as real deliveries.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    WalletTestWebhookRequest walletTestWebhookRequest = new WalletTestWebhookRequest(); // WalletTestWebhookRequest | URL to send the test POST to; optional secret and projectId for scoping; optional event type to simulate.
    try {
      WalletTestWebhook200Response result = apiInstance.walletTestWebhook(walletTestWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletTestWebhook");
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
| **walletTestWebhookRequest** | [**WalletTestWebhookRequest**](WalletTestWebhookRequest.md)| URL to send the test POST to; optional secret and projectId for scoping; optional event type to simulate. | |

### Return type

[**WalletTestWebhook200Response**](WalletTestWebhook200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Test result |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

<a id="walletUpdateWebhook"></a>
# **walletUpdateWebhook**
> WalletUpdateWebhook200Response walletUpdateWebhook(webhookId, walletUpdateWebhookRequest)

Update a wallet webhook

Update webhook URL, events, secret, or filters. Partially applied; only provided fields are updated.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: ApiKeyAuth
    ApiKeyAuth ApiKeyAuth = (ApiKeyAuth) defaultClient.getAuthentication("ApiKeyAuth");
    ApiKeyAuth.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //ApiKeyAuth.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | Webhook ID (MongoDB ObjectId) to update.
    WalletUpdateWebhookRequest walletUpdateWebhookRequest = new WalletUpdateWebhookRequest(); // WalletUpdateWebhookRequest | Fields to update (url, events, secret, filters). Omitted fields are left unchanged.
    try {
      WalletUpdateWebhook200Response result = apiInstance.walletUpdateWebhook(webhookId, walletUpdateWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#walletUpdateWebhook");
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
| **webhookId** | **String**| Webhook ID (MongoDB ObjectId) to update. | |
| **walletUpdateWebhookRequest** | [**WalletUpdateWebhookRequest**](WalletUpdateWebhookRequest.md)| Fields to update (url, events, secret, filters). Omitted fields are left unchanged. | |

### Return type

[**WalletUpdateWebhook200Response**](WalletUpdateWebhook200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook updated successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

