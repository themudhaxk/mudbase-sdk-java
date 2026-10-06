# ComplianceApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**apiGdprErasePost**](ComplianceApi.md#apiGdprErasePost) | **POST** /api/gdpr/erase | Erase my personal data (GDPR Art. 17) |
| [**apiGdprExportGet**](ComplianceApi.md#apiGdprExportGet) | **GET** /api/gdpr/export | Export my personal data (GDPR Art. 15) |
| [**generateAccessReview**](ComplianceApi.md#generateAccessReview) | **POST** /api/compliance/access-review | Generate access review report (SOC 2) |
| [**generateDataProcessingRecord**](ComplianceApi.md#generateDataProcessingRecord) | **POST** /api/compliance/data-processing-record | Generate data processing record (GDPR Article 30) |
| [**getComplianceSummary**](ComplianceApi.md#getComplianceSummary) | **GET** /api/compliance/summary | Get compliance summary |
| [**logSecurityEvent**](ComplianceApi.md#logSecurityEvent) | **POST** /api/compliance/security-event | Log security event |


<a id="apiGdprErasePost"></a>
# **apiGdprErasePost**
> ApplyRoleFeaturePreset200Response apiGdprErasePost(apiGdprErasePostRequest)

Erase my personal data (GDPR Art. 17)

Anonymizes the subject&#39;s PII, revokes sessions/tokens, and anonymizes (never hard-deletes) financial/legal-retention records. Idempotent and self-scoped.  Requires re-proving your current password (skipped only for OAuth-only accounts with no password set) and, if 2FA is enabled, a fresh TOTP code - the same step-up re-authentication already required by the less-destructive &#x60;PATCH /api/users/password&#x60; and &#x60;POST /api/users/2fa/disable&#x60;. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    ApiGdprErasePostRequest apiGdprErasePostRequest = new ApiGdprErasePostRequest(); // ApiGdprErasePostRequest | 
    try {
      ApplyRoleFeaturePreset200Response result = apiInstance.apiGdprErasePost(apiGdprErasePostRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#apiGdprErasePost");
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
| **apiGdprErasePostRequest** | [**ApiGdprErasePostRequest**](ApiGdprErasePostRequest.md)|  | |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data anonymized (or already anonymized — idempotent) |  -  |
| **400** | Confirmation field missing/not equal to \&quot;DELETE\&quot;, or currentPassword/totpToken missing or invalid |  -  |
| **401** | Authentication required |  -  |
| **409** | Sole owner of one or more organizations - transfer or delete them first |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="apiGdprExportGet"></a>
# **apiGdprExportGet**
> Object apiGdprExportGet()

Export my personal data (GDPR Art. 15)

Returns the authenticated subject&#39;s personal data as a downloadable JSON attachment. Self-scoped — a caller can only export their own data.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    try {
      Object result = apiInstance.apiGdprExportGet();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#apiGdprExportGet");
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

**Object**

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | JSON attachment containing the subject&#39;s personal data |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

<a id="generateAccessReview"></a>
# **generateAccessReview**
> GenerateAccessReview200Response generateAccessReview(generateAccessReviewRequest)

Generate access review report (SOC 2)

Generate access review report for compliance audits (SOC 2, ISO 27001, etc.). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

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

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    GenerateAccessReviewRequest generateAccessReviewRequest = new GenerateAccessReviewRequest(); // GenerateAccessReviewRequest | 
    try {
      GenerateAccessReview200Response result = apiInstance.generateAccessReview(generateAccessReviewRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#generateAccessReview");
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
| **generateAccessReviewRequest** | [**GenerateAccessReviewRequest**](GenerateAccessReviewRequest.md)|  | |

### Return type

[**GenerateAccessReview200Response**](GenerateAccessReview200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Access review report generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="generateDataProcessingRecord"></a>
# **generateDataProcessingRecord**
> GenerateDataProcessingRecord200Response generateDataProcessingRecord(generateDataProcessingRecordRequest)

Generate data processing record (GDPR Article 30)

Generate GDPR Article 30 compliant data processing record

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

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

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    GenerateDataProcessingRecordRequest generateDataProcessingRecordRequest = new GenerateDataProcessingRecordRequest(); // GenerateDataProcessingRecordRequest | 
    try {
      GenerateDataProcessingRecord200Response result = apiInstance.generateDataProcessingRecord(generateDataProcessingRecordRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#generateDataProcessingRecord");
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
| **generateDataProcessingRecordRequest** | [**GenerateDataProcessingRecordRequest**](GenerateDataProcessingRecordRequest.md)|  | |

### Return type

[**GenerateDataProcessingRecord200Response**](GenerateDataProcessingRecord200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data processing record generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

<a id="getComplianceSummary"></a>
# **getComplianceSummary**
> GetComplianceSummary200Response getComplianceSummary()

Get compliance summary

Get compliance dashboard data (GDPR, SOC 2, security status). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

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

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    try {
      GetComplianceSummary200Response result = apiInstance.getComplianceSummary();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#getComplianceSummary");
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

[**GetComplianceSummary200Response**](GetComplianceSummary200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Compliance summary |  -  |
| **401** | Authentication required |  -  |

<a id="logSecurityEvent"></a>
# **logSecurityEvent**
> LogSecurityEvent200Response logSecurityEvent(logSecurityEventRequest)

Log security event

Log a security event for compliance and audit purposes

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.ComplianceApi;

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

    ComplianceApi apiInstance = new ComplianceApi(defaultClient);
    LogSecurityEventRequest logSecurityEventRequest = new LogSecurityEventRequest(); // LogSecurityEventRequest | 
    try {
      LogSecurityEvent200Response result = apiInstance.logSecurityEvent(logSecurityEventRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComplianceApi#logSecurityEvent");
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
| **logSecurityEventRequest** | [**LogSecurityEventRequest**](LogSecurityEventRequest.md)|  | |

### Return type

[**LogSecurityEvent200Response**](LogSecurityEvent200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Security event logged |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

