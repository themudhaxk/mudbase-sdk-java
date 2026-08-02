# WalletApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**broadcastNonCustodialTransaction**](WalletApi.md#broadcastNonCustodialTransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**calculateWalletFee**](WalletApi.md#calculateWalletFee) | **POST** /api/wallet/calculate-fee | Get network fee only (alias for POST /api/wallet/estimate-network-fee) |
| [**createWallet**](WalletApi.md#createWallet) | **POST** /api/wallet/create | Create new wallet (for testing non-custodial) |
| [**createWalletWebhook**](WalletApi.md#createWalletWebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**deleteNonCustodialAddress**](WalletApi.md#deleteNonCustodialAddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete or deactivate a monitored wallet address |
| [**deleteWalletWebhook**](WalletApi.md#deleteWalletWebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**estimateNetworkFee**](WalletApi.md#estimateNetworkFee) | **POST** /api/wallet/estimate-network-fee | Estimate network fee (preferred; reads from fee oracle cache) |
| [**estimateNonCustodialGas**](WalletApi.md#estimateNonCustodialGas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**generatePrivateKey**](WalletApi.md#generatePrivateKey) | **POST** /api/wallet/generate-key | Generate private key |
| [**getAllFees**](WalletApi.md#getAllFees) | **GET** /api/wallet/fees | Get all chain network fees (fee oracle snapshot) |
| [**getBalance**](WalletApi.md#getBalance) | **GET** /api/wallet/{walletId}/balance | Get wallet balance |
| [**getCancelParams**](WalletApi.md#getCancelParams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**getNetworkStatus**](WalletApi.md#getNetworkStatus) | **GET** /api/wallet/network-status | Get network status (congestion + fee metric per chain) |
| [**getNonCustodialAddress**](WalletApi.md#getNonCustodialAddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**getNonCustodialBalance**](WalletApi.md#getNonCustodialBalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**getNonCustodialTransactionByHash**](WalletApi.md#getNonCustodialTransactionByHash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**getNonCustodialTransactions**](WalletApi.md#getNonCustodialTransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**getSpeedUpParams**](WalletApi.md#getSpeedUpParams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**getSupportedCurrencies**](WalletApi.md#getSupportedCurrencies) | **GET** /api/wallet/currencies | Get supported currencies and chains |
| [**getTransaction**](WalletApi.md#getTransaction) | **GET** /api/wallet/transactions/{transactionId} | Get transaction details |
| [**getTransactionHistory**](WalletApi.md#getTransactionHistory) | **GET** /api/wallet/transactions | Get transaction history (custodial wallets; same monitoring as non-custodial) |
| [**getUserWallets**](WalletApi.md#getUserWallets) | **GET** /api/wallet | Get user wallets |
| [**getWalletFeeConfig**](WalletApi.md#getWalletFeeConfig) | **GET** /api/wallet/projects/{projectId}/fee-config | Get project fee configuration (for non-custodial / external users) |
| [**getWalletPrivateKey**](WalletApi.md#getWalletPrivateKey) | **GET** /api/wallet/{walletId}/private-key | Get wallet private key (WARNING: Sensitive data; for testing non-custodial) |
| [**getWalletWebhookLogs**](WalletApi.md#getWalletWebhookLogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**listNonCustodialAddresses**](WalletApi.md#listNonCustodialAddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**listWalletWebhooks**](WalletApi.md#listWalletWebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**registerNonCustodialAddress**](WalletApi.md#registerNonCustodialAddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**testWalletWebhook**](WalletApi.md#testWalletWebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**updateNonCustodialAddress**](WalletApi.md#updateNonCustodialAddress) | **PUT** /api/wallet/non-custodial/addresses/{addressId} | Update a monitored wallet address |
| [**updateWalletFeeConfig**](WalletApi.md#updateWalletFeeConfig) | **PATCH** /api/wallet/projects/{projectId}/fee-config | Update project fee configuration (for non-custodial / external users) |
| [**updateWalletWebhook**](WalletApi.md#updateWalletWebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |
| [**validateAddress**](WalletApi.md#validateAddress) | **POST** /api/wallet/validate-address | Validate cryptocurrency address |
| [**withdraw**](WalletApi.md#withdraw) | **POST** /api/wallet/{walletId}/withdraw | Prepare withdrawal (semi-transaction; broadcast via non-custodial) |


<a id="broadcastNonCustodialTransaction"></a>
# **broadcastNonCustodialTransaction**
> BroadcastNonCustodialTransaction200Response broadcastNonCustodialTransaction(broadcastNonCustodialTransactionRequest)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    BroadcastNonCustodialTransactionRequest broadcastNonCustodialTransactionRequest = new BroadcastNonCustodialTransactionRequest(); // BroadcastNonCustodialTransactionRequest | 
    try {
      BroadcastNonCustodialTransaction200Response result = apiInstance.broadcastNonCustodialTransaction(broadcastNonCustodialTransactionRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#broadcastNonCustodialTransaction");
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
| **broadcastNonCustodialTransactionRequest** | [**BroadcastNonCustodialTransactionRequest**](BroadcastNonCustodialTransactionRequest.md)|  | |

### Return type

[**BroadcastNonCustodialTransaction200Response**](BroadcastNonCustodialTransaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction broadcast successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="calculateWalletFee"></a>
# **calculateWalletFee**
> CalculateWalletFee200Response calculateWalletFee(estimateNetworkFeeRequest, fresh)

Get network fee only (alias for POST /api/wallet/estimate-network-fee)

Returns **network fee only**, estimated from the blockchain (RPC / fee APIs). No platform fee or project fee. **Same as POST /api/wallet/estimate-network-fee.** Prefer estimate-network-fee for clarity. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, &#x60;network&#x60; is required (ETH, BSC, TRX, SOL, POLYGON). Use &#x60;?fresh&#x3D;1&#x60; or header &#x60;X-Fee-Fresh: true&#x60; for a fresh estimate (bypass cache) right before building the transaction for broadcast. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    WalletApi apiInstance = new WalletApi(defaultClient);
    EstimateNetworkFeeRequest estimateNetworkFeeRequest = new EstimateNetworkFeeRequest(); // EstimateNetworkFeeRequest | 
    String fresh = "1"; // String | Bypass cache and fetch current fee (use right before building tx for broadcast)
    try {
      CalculateWalletFee200Response result = apiInstance.calculateWalletFee(estimateNetworkFeeRequest, fresh);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#calculateWalletFee");
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
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md)|  | |
| **fresh** | **String**| Bypass cache and fetch current fee (use right before building tx for broadcast) | [optional] [enum: 1] |

### Return type

[**CalculateWalletFee200Response**](CalculateWalletFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee only (from blockchain). No platform or project fee. |  -  |
| **400** | Bad request |  -  |

<a id="createWallet"></a>
# **createWallet**
> CreateWallet201Response createWallet(createWalletRequest)

Create new wallet (for testing non-custodial)

Create a custodial wallet. **Custodial is not used in production.** Use this to **test non-custodial flows**: create a wallet, get its private key (GET /api/wallet/{walletId}/private-key), register the same address with POST /api/wallet/non-custodial/register-address, then use estimate-network-fee and POST /api/wallet/non-custodial/broadcast to build and send a signed transaction. Transaction monitoring (pending/confirmed) applies to both custodial and non-custodial WalletTransaction records. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    CreateWalletRequest createWalletRequest = new CreateWalletRequest(); // CreateWalletRequest | 
    try {
      CreateWallet201Response result = apiInstance.createWallet(createWalletRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#createWallet");
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
| **createWalletRequest** | [**CreateWalletRequest**](CreateWalletRequest.md)|  | |

### Return type

[**CreateWallet201Response**](CreateWallet201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Wallet created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **500** | Internal server error |  -  |

<a id="createWalletWebhook"></a>
# **createWalletWebhook**
> CreateWalletWebhook201Response createWalletWebhook(createWalletWebhookRequest)

Create a wallet webhook

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    CreateWalletWebhookRequest createWalletWebhookRequest = new CreateWalletWebhookRequest(); // CreateWalletWebhookRequest | 
    try {
      CreateWalletWebhook201Response result = apiInstance.createWalletWebhook(createWalletWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#createWalletWebhook");
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
| **createWalletWebhookRequest** | [**CreateWalletWebhookRequest**](CreateWalletWebhookRequest.md)|  | |

### Return type

[**CreateWalletWebhook201Response**](CreateWalletWebhook201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Webhook created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="deleteNonCustodialAddress"></a>
# **deleteNonCustodialAddress**
> DeleteFunction200Response deleteNonCustodialAddress(addressId, permanent)

Delete or deactivate a monitored wallet address

**Soft delete (default):** Omit **permanent** or set to false. The address is deactivated (isActive &#x3D; false); it no longer appears in list or receives monitoring but the record remains for audit. **Permanent delete:** Set query **permanent&#x3D;true** to remove the address record from the database. Use when you need to fully remove the monitored address. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | 
    Boolean permanent = false; // Boolean | If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete)
    try {
      DeleteFunction200Response result = apiInstance.deleteNonCustodialAddress(addressId, permanent);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#deleteNonCustodialAddress");
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
| **addressId** | **String**|  | |
| **permanent** | **Boolean**| If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete) | [optional] [default to false] |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address deactivated or permanently deleted |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="deleteWalletWebhook"></a>
# **deleteWalletWebhook**
> DeleteFunction200Response deleteWalletWebhook(webhookId)

Delete a wallet webhook

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | 
    try {
      DeleteFunction200Response result = apiInstance.deleteWalletWebhook(webhookId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#deleteWalletWebhook");
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
| **webhookId** | **String**|  | |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook deleted successfully |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="estimateNetworkFee"></a>
# **estimateNetworkFee**
> EstimateNetworkFee200Response estimateNetworkFee(estimateNetworkFeeRequest, fresh)

Estimate network fee (preferred; reads from fee oracle cache)

Returns **network fee only** from the blockchain. **Preferred endpoint** for network fee. Uses a fee oracle: fees are polled every 15–20s and cached, so responses are fast and RPC load is minimal (same strategy as large wallets). No platform fee. Request/response identical to POST /api/wallet/calculate-fee (which is an alias). See docs/FEE_ARCHITECTURE.md. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, &#x60;network&#x60; is required (ETH, BSC, TRX, SOL, POLYGON). **Fresh fee before broadcast:** To avoid stuck transactions, get a fresh estimate right before building/signing: use query &#x60;?fresh&#x3D;1&#x60; or header &#x60;X-Fee-Fresh: true&#x60; to bypass cache. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    WalletApi apiInstance = new WalletApi(defaultClient);
    EstimateNetworkFeeRequest estimateNetworkFeeRequest = new EstimateNetworkFeeRequest(); // EstimateNetworkFeeRequest | 
    String fresh = "1"; // String | Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast)
    try {
      EstimateNetworkFee200Response result = apiInstance.estimateNetworkFee(estimateNetworkFeeRequest, fresh);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#estimateNetworkFee");
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
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md)|  | |
| **fresh** | **String**| Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast) | [optional] [enum: 1] |

### Return type

[**EstimateNetworkFee200Response**](EstimateNetworkFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee only (from blockchain). No platform or project fee. |  -  |
| **400** | Bad request |  -  |

<a id="estimateNonCustodialGas"></a>
# **estimateNonCustodialGas**
> EstimateNonCustodialGas200Response estimateNonCustodialGas(estimateNonCustodialGasRequest)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    EstimateNonCustodialGasRequest estimateNonCustodialGasRequest = new EstimateNonCustodialGasRequest(); // EstimateNonCustodialGasRequest | 
    try {
      EstimateNonCustodialGas200Response result = apiInstance.estimateNonCustodialGas(estimateNonCustodialGasRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#estimateNonCustodialGas");
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
| **estimateNonCustodialGasRequest** | [**EstimateNonCustodialGasRequest**](EstimateNonCustodialGasRequest.md)|  | |

### Return type

[**EstimateNonCustodialGas200Response**](EstimateNonCustodialGas200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee from blockchain RPC (not from Mudbase logic) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="generatePrivateKey"></a>
# **generatePrivateKey**
> GeneratePrivateKey200Response generatePrivateKey(generatePrivateKeyRequest)

Generate private key

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    GeneratePrivateKeyRequest generatePrivateKeyRequest = new GeneratePrivateKeyRequest(); // GeneratePrivateKeyRequest | 
    try {
      GeneratePrivateKey200Response result = apiInstance.generatePrivateKey(generatePrivateKeyRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#generatePrivateKey");
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
| **generatePrivateKeyRequest** | [**GeneratePrivateKeyRequest**](GeneratePrivateKeyRequest.md)|  | |

### Return type

[**GeneratePrivateKey200Response**](GeneratePrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Private key generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="getAllFees"></a>
# **getAllFees**
> GetAllFees200Response getAllFees()

Get all chain network fees (fee oracle snapshot)

Returns **all chain network fees** in one call. Reads from the fee oracle cache (no RPC during the request). Each chain returns the **full fee object** (networkFee, gasPriceGwei, congestion, estimatedTime, feeTiers for EVM, etc.) for frontend/UX. Use for dashboards or \&quot;current fees\&quot; screens. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    WalletApi apiInstance = new WalletApi(defaultClient);
    try {
      GetAllFees200Response result = apiInstance.getAllFees();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getAllFees");
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

[**GetAllFees200Response**](GetAllFees200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee oracle snapshot (chain -&gt; full fee object) |  -  |

<a id="getBalance"></a>
# **getBalance**
> GetBalance200Response getBalance(walletId)

Get wallet balance

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String walletId = "walletId_example"; // String | 
    try {
      GetBalance200Response result = apiInstance.getBalance(walletId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getBalance");
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
| **walletId** | **String**|  | |

### Return type

[**GetBalance200Response**](GetBalance200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Wallet balance |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getCancelParams"></a>
# **getCancelParams**
> GetCancelParams200Response getCancelParams(getCancelParamsRequest)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    GetCancelParamsRequest getCancelParamsRequest = new GetCancelParamsRequest(); // GetCancelParamsRequest | 
    try {
      GetCancelParams200Response result = apiInstance.getCancelParams(getCancelParamsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getCancelParams");
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
| **getCancelParamsRequest** | [**GetCancelParamsRequest**](GetCancelParamsRequest.md)|  | |

### Return type

[**GetCancelParams200Response**](GetCancelParams200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cancel tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getNetworkStatus"></a>
# **getNetworkStatus**
> GetNetworkStatus200Response getNetworkStatus()

Get network status (congestion + fee metric per chain)

Returns **network status** per chain (congestion and main fee metric). Use to show network health before sending transactions. Same data as GET /fees but trimmed to congestion + gasPriceGwei (EVM) or satPerVb (UTXO) and networkFee. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    WalletApi apiInstance = new WalletApi(defaultClient);
    try {
      GetNetworkStatus200Response result = apiInstance.getNetworkStatus();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getNetworkStatus");
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

[**GetNetworkStatus200Response**](GetNetworkStatus200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network status per chain |  -  |

<a id="getNonCustodialAddress"></a>
# **getNonCustodialAddress**
> NonCustodialAddressResponse getNonCustodialAddress(addressId)

Get non-custodial address by ID

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | 
    try {
      NonCustodialAddressResponse result = apiInstance.getNonCustodialAddress(addressId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getNonCustodialAddress");
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
| **addressId** | **String**|  | |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="getNonCustodialBalance"></a>
# **getNonCustodialBalance**
> GetNonCustodialBalance200Response getNonCustodialBalance(addressId)

Get balance for a non-custodial address

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | 
    try {
      GetNonCustodialBalance200Response result = apiInstance.getNonCustodialBalance(addressId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getNonCustodialBalance");
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
| **addressId** | **String**|  | |

### Return type

[**GetNonCustodialBalance200Response**](GetNonCustodialBalance200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Balance information |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="getNonCustodialTransactionByHash"></a>
# **getNonCustodialTransactionByHash**
> GetNonCustodialTransactionByHash200Response getNonCustodialTransactionByHash(txHash, chain)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String txHash = "txHash_example"; // String | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO)
    String chain = "ethereum"; // String | Chain the transaction belongs to (required for lookup)
    try {
      GetNonCustodialTransactionByHash200Response result = apiInstance.getNonCustodialTransactionByHash(txHash, chain);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getNonCustodialTransactionByHash");
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

[**GetNonCustodialTransactionByHash200Response**](GetNonCustodialTransactionByHash200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **400** | Bad Request - missing or invalid chain (add ?chain&#x3D;ethereum) |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="getNonCustodialTransactions"></a>
# **getNonCustodialTransactions**
> GetNonCustodialTransactions200Response getNonCustodialTransactions(addressId, limit, page)

Get transaction history for a non-custodial address

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | 
    Integer limit = 50; // Integer | 
    Integer page = 1; // Integer | 
    try {
      GetNonCustodialTransactions200Response result = apiInstance.getNonCustodialTransactions(addressId, limit, page);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getNonCustodialTransactions");
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
| **addressId** | **String**|  | |
| **limit** | **Integer**|  | [optional] [default to 50] |
| **page** | **Integer**|  | [optional] [default to 1] |

### Return type

[**GetNonCustodialTransactions200Response**](GetNonCustodialTransactions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="getSpeedUpParams"></a>
# **getSpeedUpParams**
> GetSpeedUpParams200Response getSpeedUpParams(getSpeedUpParamsRequest)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    GetSpeedUpParamsRequest getSpeedUpParamsRequest = new GetSpeedUpParamsRequest(); // GetSpeedUpParamsRequest | 
    try {
      GetSpeedUpParams200Response result = apiInstance.getSpeedUpParams(getSpeedUpParamsRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getSpeedUpParams");
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
| **getSpeedUpParamsRequest** | [**GetSpeedUpParamsRequest**](GetSpeedUpParamsRequest.md)|  | |

### Return type

[**GetSpeedUpParams200Response**](GetSpeedUpParams200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Replacement tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getSupportedCurrencies"></a>
# **getSupportedCurrencies**
> GetSupportedCurrencies200Response getSupportedCurrencies()

Get supported currencies and chains

Returns the list of **platform-supported cryptocurrencies and chains** for non-custodial wallets, broadcast, and multi-chain use. Custodial wallet is no longer used in production; this endpoint is the source of truth for supported chains and currencies. **Supported:** BTC, LTC, DOGE, ETH, ETC, CELO, SOL, TRX, TON, Polygon (MATIC), Arbitrum, Optimism, Base, BSC/BNB, Avalanche (AVAX), Cardano (ADA), USDT. Each item includes **code** (currency symbol), **name** (display name), **chain** (chain id for API calls). USDT includes **networks** (ETH, BSC, TRX, SOL, POLYGON). Use **chain** with non-custodial endpoints (register-address, broadcast, estimate-gas). Use **code** for display and fee/currency selection. This is a public endpoint - no authentication required. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.WalletApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");

    WalletApi apiInstance = new WalletApi(defaultClient);
    try {
      GetSupportedCurrencies200Response result = apiInstance.getSupportedCurrencies();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getSupportedCurrencies");
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

[**GetSupportedCurrencies200Response**](GetSupportedCurrencies200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Supported currencies and chains (currencies array and count) |  -  |

<a id="getTransaction"></a>
# **getTransaction**
> GetTransaction200Response getTransaction(transactionId)

Get transaction details

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String transactionId = "transactionId_example"; // String | 
    try {
      GetTransaction200Response result = apiInstance.getTransaction(transactionId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getTransaction");
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
| **transactionId** | **String**|  | |

### Return type

[**GetTransaction200Response**](GetTransaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

<a id="getTransactionHistory"></a>
# **getTransactionHistory**
> GetTransactionHistory200Response getTransactionHistory(walletId, limit, page)

Get transaction history (custodial wallets; same monitoring as non-custodial)

Returns transaction history for custodial wallets. Transactions are stored and monitored the same way as non-custodial (WalletTransaction); status updates (pending, broadcast, confirmed, failed) and stuck detection apply to both. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String walletId = "walletId_example"; // String | 
    Integer limit = 20; // Integer | 
    Integer page = 1; // Integer | 
    try {
      GetTransactionHistory200Response result = apiInstance.getTransactionHistory(walletId, limit, page);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getTransactionHistory");
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
| **walletId** | **String**|  | [optional] |
| **limit** | **Integer**|  | [optional] [default to 20] |
| **page** | **Integer**|  | [optional] [default to 1] |

### Return type

[**GetTransactionHistory200Response**](GetTransactionHistory200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Authentication required |  -  |

<a id="getUserWallets"></a>
# **getUserWallets**
> GetUserWallets200Response getUserWallets(projectId, currency)

Get user wallets

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    String currency = "currency_example"; // String | 
    try {
      GetUserWallets200Response result = apiInstance.getUserWallets(projectId, currency);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getUserWallets");
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
| **currency** | **String**|  | [optional] |

### Return type

[**GetUserWallets200Response**](GetUserWallets200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User wallets list (custodial; for testing) |  -  |
| **401** | Authentication required |  -  |

<a id="getWalletFeeConfig"></a>
# **getWalletFeeConfig**
> GetWalletFeeConfig200Response getWalletFeeConfig(projectId)

Get project fee configuration (for non-custodial / external users)

Get project-level fee settings (enabled flag and fee percentage). **For non-custodial / external users** — e.g. when your app charges a fee on payouts or transfers. Custodial wallet is no longer used in production. Applies to all supported chains/currencies for that project. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID
    try {
      GetWalletFeeConfig200Response result = apiInstance.getWalletFeeConfig(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getWalletFeeConfig");
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

### Return type

[**GetWalletFeeConfig200Response**](GetWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee configuration (applies to all supported currencies/chains for this project) |  -  |
| **404** | Resource not found |  -  |

<a id="getWalletPrivateKey"></a>
# **getWalletPrivateKey**
> GetWalletPrivateKey200Response getWalletPrivateKey(walletId)

Get wallet private key (WARNING: Sensitive data; for testing non-custodial)

Returns the wallet private key. **For testing non-custodial only:** use this key to sign a transaction locally, then register the wallet address via POST /api/wallet/non-custodial/register-address and broadcast the signed tx via POST /api/wallet/non-custodial/broadcast. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String walletId = "walletId_example"; // String | 
    try {
      GetWalletPrivateKey200Response result = apiInstance.getWalletPrivateKey(walletId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getWalletPrivateKey");
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
| **walletId** | **String**|  | |

### Return type

[**GetWalletPrivateKey200Response**](GetWalletPrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Private key (shown only once) |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getWalletWebhookLogs"></a>
# **getWalletWebhookLogs**
> GetWalletWebhookLogs200Response getWalletWebhookLogs(webhookId, limit)

Get webhook delivery logs

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | 
    Integer limit = 50; // Integer | 
    try {
      GetWalletWebhookLogs200Response result = apiInstance.getWalletWebhookLogs(webhookId, limit);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#getWalletWebhookLogs");
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
| **webhookId** | **String**|  | |
| **limit** | **Integer**|  | [optional] [default to 50] |

### Return type

[**GetWalletWebhookLogs200Response**](GetWalletWebhookLogs200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="listNonCustodialAddresses"></a>
# **listNonCustodialAddresses**
> ListNonCustodialAddresses200Response listNonCustodialAddresses(chain, projectId)

List registered non-custodial addresses

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String chain = "ethereum"; // String | Filter by chain (optional)
    String projectId = "projectId_example"; // String | 
    try {
      ListNonCustodialAddresses200Response result = apiInstance.listNonCustodialAddresses(chain, projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#listNonCustodialAddresses");
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
| **projectId** | **String**|  | [optional] |

### Return type

[**ListNonCustodialAddresses200Response**](ListNonCustodialAddresses200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of registered addresses |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="listWalletWebhooks"></a>
# **listWalletWebhooks**
> ListWalletWebhooks200Response listWalletWebhooks(projectId)

List wallet webhooks

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String projectId = "projectId_example"; // String | 
    try {
      ListWalletWebhooks200Response result = apiInstance.listWalletWebhooks(projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#listWalletWebhooks");
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

[**ListWalletWebhooks200Response**](ListWalletWebhooks200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of webhooks |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="registerNonCustodialAddress"></a>
# **registerNonCustodialAddress**
> NonCustodialAddressResponse registerNonCustodialAddress(registerNonCustodialAddressRequest)

Register a non-custodial wallet address

Register a public wallet address for monitoring and indexing. All key operations (generation, signing) occur client-side only. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    RegisterNonCustodialAddressRequest registerNonCustodialAddressRequest = new RegisterNonCustodialAddressRequest(); // RegisterNonCustodialAddressRequest | 
    try {
      NonCustodialAddressResponse result = apiInstance.registerNonCustodialAddress(registerNonCustodialAddressRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#registerNonCustodialAddress");
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
| **registerNonCustodialAddressRequest** | [**RegisterNonCustodialAddressRequest**](RegisterNonCustodialAddressRequest.md)|  | |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Address registered successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="testWalletWebhook"></a>
# **testWalletWebhook**
> TestWalletWebhook200Response testWalletWebhook(testWalletWebhookRequest)

Test a webhook delivery (sends a single test payload)

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    TestWalletWebhookRequest testWalletWebhookRequest = new TestWalletWebhookRequest(); // TestWalletWebhookRequest | 
    try {
      TestWalletWebhook200Response result = apiInstance.testWalletWebhook(testWalletWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#testWalletWebhook");
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
| **testWalletWebhookRequest** | [**TestWalletWebhookRequest**](TestWalletWebhookRequest.md)|  | |

### Return type

[**TestWalletWebhook200Response**](TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Test result |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="updateNonCustodialAddress"></a>
# **updateNonCustodialAddress**
> UpdateNonCustodialAddress200Response updateNonCustodialAddress(addressId, updateNonCustodialAddressRequest)

Update a monitored wallet address

Update metadata for a registered non-custodial address. Only **label** and **derivationPath** can be updated; address and chain are immutable. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String addressId = "addressId_example"; // String | 
    UpdateNonCustodialAddressRequest updateNonCustodialAddressRequest = new UpdateNonCustodialAddressRequest(); // UpdateNonCustodialAddressRequest | 
    try {
      UpdateNonCustodialAddress200Response result = apiInstance.updateNonCustodialAddress(addressId, updateNonCustodialAddressRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#updateNonCustodialAddress");
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
| **addressId** | **String**|  | |
| **updateNonCustodialAddressRequest** | [**UpdateNonCustodialAddressRequest**](UpdateNonCustodialAddressRequest.md)|  | [optional] |

### Return type

[**UpdateNonCustodialAddress200Response**](UpdateNonCustodialAddress200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address updated successfully |  -  |
| **400** | Validation error (e.g. label too long, invalid derivation path) |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="updateWalletFeeConfig"></a>
# **updateWalletFeeConfig**
> UpdateWalletFeeConfig200Response updateWalletFeeConfig(projectId, updateWalletFeeConfigRequest)

Update project fee configuration (for non-custodial / external users)

Update project-level fee settings. **For non-custodial / external users** — e.g. fee charged on payouts or transfers. Custodial wallet is no longer used in production. Applies to **all supported currencies** (BTC, ETH, BNB, LTC, SOL, TRX, USDT). **feePercentage** is a decimal: use &#x60;0.01&#x60; for 1%, &#x60;0.005&#x60; for 0.5%, etc. (min 0, max 1). 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String projectId = "projectId_example"; // String | Project ID
    UpdateWalletFeeConfigRequest updateWalletFeeConfigRequest = new UpdateWalletFeeConfigRequest(); // UpdateWalletFeeConfigRequest | 
    try {
      UpdateWalletFeeConfig200Response result = apiInstance.updateWalletFeeConfig(projectId, updateWalletFeeConfigRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#updateWalletFeeConfig");
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
| **updateWalletFeeConfigRequest** | [**UpdateWalletFeeConfigRequest**](UpdateWalletFeeConfigRequest.md)|  | [optional] |

### Return type

[**UpdateWalletFeeConfig200Response**](UpdateWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee configuration updated |  -  |
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |

<a id="updateWalletWebhook"></a>
# **updateWalletWebhook**
> UpdateWalletWebhook200Response updateWalletWebhook(webhookId, updateWalletWebhookRequest)

Update a wallet webhook

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String webhookId = "webhookId_example"; // String | 
    UpdateWalletWebhookRequest updateWalletWebhookRequest = new UpdateWalletWebhookRequest(); // UpdateWalletWebhookRequest | 
    try {
      UpdateWalletWebhook200Response result = apiInstance.updateWalletWebhook(webhookId, updateWalletWebhookRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#updateWalletWebhook");
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
| **webhookId** | **String**|  | |
| **updateWalletWebhookRequest** | [**UpdateWalletWebhookRequest**](UpdateWalletWebhookRequest.md)|  | |

### Return type

[**UpdateWalletWebhook200Response**](UpdateWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook updated successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="validateAddress"></a>
# **validateAddress**
> ValidateAddress200Response validateAddress(validateAddressRequest)

Validate cryptocurrency address

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    ValidateAddressRequest validateAddressRequest = new ValidateAddressRequest(); // ValidateAddressRequest | 
    try {
      ValidateAddress200Response result = apiInstance.validateAddress(validateAddressRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#validateAddress");
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
| **validateAddressRequest** | [**ValidateAddressRequest**](ValidateAddressRequest.md)|  | |

### Return type

[**ValidateAddress200Response**](ValidateAddress200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address validation result |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="withdraw"></a>
# **withdraw**
> Withdraw200Response withdraw(walletId, withdrawRequest)

Prepare withdrawal (semi-transaction; broadcast via non-custodial)

**Semi-transaction:** Builds and signs the withdrawal but does **not** broadcast. Returns &#x60;signedTx&#x60;, &#x60;chain&#x60;, and &#x60;fromAddress&#x60; so the client can broadcast via POST /api/wallet/non-custodial/broadcast. The wallet address must be registered for your organization before broadcasting. Supports all platform chains/currencies (EVM, UTXO, Tron, Solana, USDT on ETH/BSC/TRX/SOL/POLYGON). Use for testing the non-custodial flow: create custodial wallet, get private key, register address, then call withdraw to get signed tx and broadcast it manually. 

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
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    // Configure HTTP bearer authorization: ProjectBearerAuth
    HttpBearerAuth ProjectBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("ProjectBearerAuth");
    ProjectBearerAuth.setBearerToken("BEARER TOKEN");

    WalletApi apiInstance = new WalletApi(defaultClient);
    String walletId = "walletId_example"; // String | 
    WithdrawRequest withdrawRequest = new WithdrawRequest(); // WithdrawRequest | 
    try {
      Withdraw200Response result = apiInstance.withdraw(walletId, withdrawRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling WalletApi#withdraw");
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
| **walletId** | **String**|  | |
| **withdrawRequest** | [**WithdrawRequest**](WithdrawRequest.md)|  | |

### Return type

[**Withdraw200Response**](Withdraw200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Semi-transaction ready; broadcast via POST /api/wallet/non-custodial/broadcast |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **500** | Internal server error |  -  |

