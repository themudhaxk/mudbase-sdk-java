# VerifiedRoleUpgradeApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**verifiedRoleUpgrade**](VerifiedRoleUpgradeApi.md#verifiedRoleUpgrade) | **POST** /api/orgs/{orgId}/users/{userId}/upgrade | Verified role upgrade with payment verification |


<a id="verifiedRoleUpgrade"></a>
# **verifiedRoleUpgrade**
> VerifiedRoleUpgrade200Response verifiedRoleUpgrade(orgId, userId, verifiedRoleUpgradeRequest)

Verified role upgrade with payment verification

Upgrade user role after verifying payment and KYC. Prevents replay attacks.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.VerifiedRoleUpgradeApi;

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

    VerifiedRoleUpgradeApi apiInstance = new VerifiedRoleUpgradeApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String userId = "userId_example"; // String | 
    VerifiedRoleUpgradeRequest verifiedRoleUpgradeRequest = new VerifiedRoleUpgradeRequest(); // VerifiedRoleUpgradeRequest | 
    try {
      VerifiedRoleUpgrade200Response result = apiInstance.verifiedRoleUpgrade(orgId, userId, verifiedRoleUpgradeRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling VerifiedRoleUpgradeApi#verifiedRoleUpgrade");
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
| **userId** | **String**|  | |
| **verifiedRoleUpgradeRequest** | [**VerifiedRoleUpgradeRequest**](VerifiedRoleUpgradeRequest.md)|  | |

### Return type

[**VerifiedRoleUpgrade200Response**](VerifiedRoleUpgrade200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role upgraded successfully |  -  |
| **403** | Payment verification failed or insufficient permissions |  -  |
| **404** | User or role not found |  -  |

