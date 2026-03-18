# ComplianceApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**complianceLogSecurityEvent**](ComplianceApi.md#complianceLogSecurityEvent) | **POST** /api/compliance/security-event | Log security event |


<a id="complianceLogSecurityEvent"></a>
# **complianceLogSecurityEvent**
> ComplianceLogSecurityEvent200Response complianceLogSecurityEvent(complianceLogSecurityEventRequest)

Log security event

Log a security event for compliance and audit (e.g. SOC 2, GDPR). Event type and severity are required; optional details (userId, resource, ipAddress, etc.) for forensics.

### Example
```java
// Import classes:
import dev.mudbase.sdk.ApiClient;
import dev.mudbase.sdk.ApiException;
import dev.mudbase.sdk.Configuration;
import dev.mudbase.sdk.auth.*;
import dev.mudbase.sdk.models.*;
import dev.mudbase.sdk.ComplianceApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.dev.mudbase");
    
    // Configure HTTP bearer authorization: BearerToken
    HttpBearerAuth BearerToken = (HttpBearerAuth) defaultClient.getAuthentication("BearerToken");
    BearerToken.setBearerToken("BEARER TOKEN");

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    ComplianceLogSecurityEventRequest complianceLogSecurityEventRequest = new ComplianceLogSecurityEventRequest(); // ComplianceLogSecurityEventRequest | Event type (e.g. unauthorized_access_attempt, brute_force_attempt), severity (low–critical), and optional details object for context.
    try {
      ComplianceLogSecurityEvent200Response result = apiInstance.complianceLogSecurityEvent(complianceLogSecurityEventRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#complianceLogSecurityEvent");
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
| **complianceLogSecurityEventRequest** | [**ComplianceLogSecurityEventRequest**](ComplianceLogSecurityEventRequest.md)| Event type (e.g. unauthorized_access_attempt, brute_force_attempt), severity (low–critical), and optional details object for context. | |

### Return type

[**ComplianceLogSecurityEvent200Response**](ComplianceLogSecurityEvent200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Security event logged |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

