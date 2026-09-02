# OrganizationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**addOrgCustomDomain**](OrganizationsApi.md#addOrgCustomDomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add a custom domain |
| [**createOrganization**](OrganizationsApi.md#createOrganization) | **POST** /api/orgs | ~~Create new organization~~ (disabled) |
| [**deleteOrgCustomDomain**](OrganizationsApi.md#deleteOrgCustomDomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove a custom domain |
| [**deleteOrganization**](OrganizationsApi.md#deleteOrganization) | **DELETE** /api/orgs/{orgId} | Delete organization |
| [**deleteSubOrganization**](OrganizationsApi.md#deleteSubOrganization) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Delete sub-organization~~ (deprecated) |
| [**getOrgCustomDomainDnsInstructions**](OrganizationsApi.md#getOrgCustomDomainDnsInstructions) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/dns-instructions | Get DNS TXT record instructions for one hostname |
| [**getOrganization**](OrganizationsApi.md#getOrganization) | **GET** /api/orgs/{orgId} | Get organization details by ID |
| [**getOrganizationMembers**](OrganizationsApi.md#getOrganizationMembers) | **GET** /api/orgs/{orgId}/members | Get organization members |
| [**getOrganizationUsage**](OrganizationsApi.md#getOrganizationUsage) | **GET** /api/orgs/{orgId}/usage | Get organization usage and billing |
| [**getOrganizationUsers**](OrganizationsApi.md#getOrganizationUsers) | **GET** /api/orgs/{orgId}/users | List organization users with metadata |
| [**getProjectUsers**](OrganizationsApi.md#getProjectUsers) | **GET** /api/orgs/{orgId}/projects/{projectId}/users | List project users with metadata |
| [**getSubOrganizations**](OrganizationsApi.md#getSubOrganizations) | **GET** /api/orgs/{orgId}/suborgs | ~~Get sub-organizations~~ (deprecated) |
| [**getUserOverview**](OrganizationsApi.md#getUserOverview) | **GET** /api/orgs/{orgId}/users/{userId}/overview | Get user overview and data footprint |
| [**internalCustomDomainAddon**](OrganizationsApi.md#internalCustomDomainAddon) | **POST** /internal/org/custom-domain-addon | Enable/disable Growth/Scale custom domain add-on (internal) |
| [**internalCustomDomainSweepStatus**](OrganizationsApi.md#internalCustomDomainSweepStatus) | **GET** /internal/custom-domain/sweep-status | Custom domain background sweep status (internal) |
| [**internalDomainDnsRecheckBatch**](OrganizationsApi.md#internalDomainDnsRecheckBatch) | **POST** /internal/domain-dns/recheck-batch | Batch DNS re-verification for drift (internal) |
| [**internalProvisionEnterprise**](OrganizationsApi.md#internalProvisionEnterprise) | **POST** /internal/provision-enterprise | Provision enterprise dedicated API/DB (internal) |
| [**inviteSubOrganizationMember**](OrganizationsApi.md#inviteSubOrganizationMember) | **POST** /api/orgs/{orgId}/suborgs/{suborgId}/invite | ~~Invite member to sub-organization~~ (deprecated) |
| [**inviteTeamMember**](OrganizationsApi.md#inviteTeamMember) | **POST** /api/orgs/{orgId}/invite | Invite team member to organization |
| [**listOrgCustomDomains**](OrganizationsApi.md#listOrgCustomDomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS verification hints |
| [**listOrganizations**](OrganizationsApi.md#listOrganizations) | **GET** /api/orgs | Get all organizations for user |
| [**orgCustomDomainPlatformReady**](OrganizationsApi.md#orgCustomDomainPlatformReady) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops that hosting or edge work is ready (email) |
| [**orgCustomDomainSubmitCname**](OrganizationsApi.md#orgCustomDomainSubmitCname) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-cname | Custom domain step 2 (optional): org confirms routing CNAME was added |
| [**orgCustomDomainSubmitPlatformDnsVerificationDeprecated**](OrganizationsApi.md#orgCustomDomainSubmitPlatformDnsVerificationDeprecated) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-platform-dns-verification | Deprecated — use POST .../verify-platform-dns |
| [**orgCustomDomainVerifyPlatformDns**](OrganizationsApi.md#orgCustomDomainVerifyPlatformDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-platform-dns | Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness) |
| [**patchOrgCustomDomain**](OrganizationsApi.md#patchOrgCustomDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Update domain status or regenerate verification token |
| [**removeSubOrganizationMember**](OrganizationsApi.md#removeSubOrganizationMember) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId} | ~~Remove member from sub-organization~~ (deprecated) |
| [**removeTeamMember**](OrganizationsApi.md#removeTeamMember) | **DELETE** /api/orgs/{orgId}/members/{userId} | Remove team member from organization |
| [**setOrgPrimaryDomain**](OrganizationsApi.md#setOrgPrimaryDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**updateMemberRole**](OrganizationsApi.md#updateMemberRole) | **PATCH** /api/orgs/{orgId}/members/{userId}/role | Update member role |
| [**updateOrganization**](OrganizationsApi.md#updateOrganization) | **PATCH** /api/orgs/{orgId} | Update organization |
| [**updateOrganizationPlan**](OrganizationsApi.md#updateOrganizationPlan) | **PATCH** /api/orgs/plan/{orgId} | Update organization plan |
| [**updateSubOrganization**](OrganizationsApi.md#updateSubOrganization) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Update sub-organization~~ (deprecated) |
| [**updateSubOrganizationMemberRole**](OrganizationsApi.md#updateSubOrganizationMemberRole) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId}/role | ~~Update sub-organization member role~~ (deprecated) |
| [**updateUserAccountStatus**](OrganizationsApi.md#updateUserAccountStatus) | **PATCH** /api/orgs/{orgId}/users/{userId}/status | Update user account status (activate or suspend) |
| [**verifyOrgCustomDomainDns**](OrganizationsApi.md#verifyOrgCustomDomainDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain ownership via DNS TXT |


<a id="addOrgCustomDomain"></a>
# **addOrgCustomDomain**
> OrgAddDomainResponse addOrgCustomDomain(orgId, projectId, addOrgDomainRequest)

Add a custom domain

Creates a pending domain row; the response **&#x60;domain&#x60;** uses the compact **&#x60;OrgDomainEntryOrgConsole&#x60;** shape (**&#x60;dnsRecords&#x60;** includes the Mudbase ownership TXT). **&#x60;dnsRecords&#x60;** may include Mudbase TXT and routing CNAME only until Mudbase TXT succeeds and Fly ACME (if enabled) provisions a certificate. **&#x60;flyCertificateStatus&#x60;** is typically omitted until Fly ACME runs after first successful **&#x60;verify-dns&#x60;**. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    AddOrgDomainRequest addOrgDomainRequest = new AddOrgDomainRequest(); // AddOrgDomainRequest | 
    try {
      OrgAddDomainResponse result = apiInstance.addOrgCustomDomain(orgId, projectId, addOrgDomainRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#addOrgCustomDomain");
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
| **projectId** | **String**|  | |
| **addOrgDomainRequest** | [**AddOrgDomainRequest**](AddOrgDomainRequest.md)|  | |

### Return type

[**OrgAddDomainResponse**](OrgAddDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Domain created; includes dnsRecords and human-readable instructions (no extra GET required). |  -  |
| **400** | Validation, limit, or hostname_in_use |  -  |
| **429** | domain_rate_limited |  -  |

<a id="createOrganization"></a>
# **createOrganization**
> createOrganization(createOrganizationRequest)

~~Create new organization~~ (disabled)

~~Create a new organization.~~ This endpoint is disabled and kept only for backward compatibility in documentation. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    CreateOrganizationRequest createOrganizationRequest = new CreateOrganizationRequest(); // CreateOrganizationRequest | 
    try {
      apiInstance.createOrganization(createOrganizationRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#createOrganization");
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
| **createOrganizationRequest** | [**CreateOrganizationRequest**](CreateOrganizationRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **403** | Organization creation disabled |  -  |

<a id="deleteOrgCustomDomain"></a>
# **deleteOrgCustomDomain**
> deleteOrgCustomDomain(orgId, projectId, hostname)

Remove a custom domain

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      apiInstance.deleteOrgCustomDomain(orgId, projectId, hostname);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#deleteOrgCustomDomain");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Removed |  -  |

<a id="deleteOrganization"></a>
# **deleteOrganization**
> DeleteOrganization200Response deleteOrganization(orgId)

Delete organization

Delete an organization permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    try {
      DeleteOrganization200Response result = apiInstance.deleteOrganization(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#deleteOrganization");
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

[**DeleteOrganization200Response**](DeleteOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization deleted |  -  |

<a id="deleteSubOrganization"></a>
# **deleteSubOrganization**
> DeleteSubOrganization200Response deleteSubOrganization(orgId, suborgId)

~~Delete sub-organization~~ (deprecated)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String suborgId = "685acbe0e129932fbb7a0fc4"; // String | 
    try {
      DeleteSubOrganization200Response result = apiInstance.deleteSubOrganization(orgId, suborgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#deleteSubOrganization");
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
| **suborgId** | **String**|  | |

### Return type

[**DeleteSubOrganization200Response**](DeleteSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Sub-organization deleted |  -  |

<a id="getOrgCustomDomainDnsInstructions"></a>
# **getOrgCustomDomainDnsInstructions**
> OrgDnsInstructionsResponse getOrgCustomDomainDnsInstructions(orgId, projectId, hostname)

Get DNS TXT record instructions for one hostname

Returns the same shape as list/add for one hostname (URL-encode &#x60;hostname&#x60; in the path), including **&#x60;dnsRecords&#x60;** and **&#x60;flyCertificateStatus&#x60;** when applicable. See **&#x60;listOrgCustomDomains&#x60;** for how Fly ACME and Cloudflare SaaS affect those fields. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      OrgDnsInstructionsResponse result = apiInstance.getOrgCustomDomainDnsInstructions(orgId, projectId, hostname);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getOrgCustomDomainDnsInstructions");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

[**OrgDnsInstructionsResponse**](OrgDnsInstructionsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain row with DNS hints |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **404** | domain_not_found |  -  |

<a id="getOrganization"></a>
# **getOrganization**
> Organization getOrganization(orgId)

Get organization details by ID

Get organization details by ID. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    try {
      Organization result = apiInstance.getOrganization(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getOrganization");
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

[**Organization**](Organization.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization details |  -  |

<a id="getOrganizationMembers"></a>
# **getOrganizationMembers**
> GetOrganizationMembers200Response getOrganizationMembers(orgId)

Get organization members

Get all members of an organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    try {
      GetOrganizationMembers200Response result = apiInstance.getOrganizationMembers(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getOrganizationMembers");
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

[**GetOrganizationMembers200Response**](GetOrganizationMembers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization members |  -  |

<a id="getOrganizationUsage"></a>
# **getOrganizationUsage**
> GetOrganizationUsage200Response getOrganizationUsage(orgId)

Get organization usage and billing

Get usage statistics and billing information for an organization. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    try {
      GetOrganizationUsage200Response result = apiInstance.getOrganizationUsage(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getOrganizationUsage");
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

[**GetOrganizationUsage200Response**](GetOrganizationUsage200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage and billing information |  -  |

<a id="getOrganizationUsers"></a>
# **getOrganizationUsers**
> GetOrganizationUsers200Response getOrganizationUsers(orgId, status)

List organization users with metadata

Get all users in the organization with metadata (email, full name, role, accountStatus, phone, lastLogin, etc.). Optional query &#x60;status&#x60; filters by accountStatus (pending, active, suspended). Requires organization access and owner or admin role. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String status = "pending"; // String | Filter by account status (pending, active, suspended)
    try {
      GetOrganizationUsers200Response result = apiInstance.getOrganizationUsers(orgId, status);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getOrganizationUsers");
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
| **status** | **String**| Filter by account status (pending, active, suspended) | [optional] [enum: pending, active, suspended] |

### Return type

[**GetOrganizationUsers200Response**](GetOrganizationUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization users with metadata |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getProjectUsers"></a>
# **getProjectUsers**
> GetProjectUsers200Response getProjectUsers(orgId, projectId, status)

List project users with metadata

Get all users in a project with metadata (email, full name, role, accountStatus, etc.). Optional query &#x60;status&#x60; filters by accountStatus. Project must belong to the organization. Requires owner or admin role. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String projectId = "685ad30be129932fbb7a1047"; // String | 
    String status = "pending"; // String | Filter by account status (pending, active, suspended)
    try {
      GetProjectUsers200Response result = apiInstance.getProjectUsers(orgId, projectId, status);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getProjectUsers");
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
| **projectId** | **String**|  | |
| **status** | **String**| Filter by account status (pending, active, suspended) | [optional] [enum: pending, active, suspended] |

### Return type

[**GetProjectUsers200Response**](GetProjectUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project users with metadata |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="getSubOrganizations"></a>
# **getSubOrganizations**
> GetSubOrganizations200Response getSubOrganizations(orgId)

~~Get sub-organizations~~ (deprecated)

Get all sub-organizations under a parent organization. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    try {
      GetSubOrganizations200Response result = apiInstance.getSubOrganizations(orgId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getSubOrganizations");
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

[**GetSubOrganizations200Response**](GetSubOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of sub-organizations |  -  |

<a id="getUserOverview"></a>
# **getUserOverview**
> GetUserOverview200Response getUserOverview(orgId, userId)

Get user overview and data footprint

Get a user&#39;s profile plus footprint (files count/size, sessions, API keys, collections in project). Use for dashboard to see everything tied to the user. Requires owner or admin role. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String userId = "userId_example"; // String | 
    try {
      GetUserOverview200Response result = apiInstance.getUserOverview(orgId, userId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#getUserOverview");
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

### Return type

[**GetUserOverview200Response**](GetUserOverview200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User and footprint |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="internalCustomDomainAddon"></a>
# **internalCustomDomainAddon**
> internalCustomDomainAddon(internalCustomDomainAddonRequest)

Enable/disable Growth/Scale custom domain add-on (internal)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: InternalApiKey
    ApiKeyAuth InternalApiKey = (ApiKeyAuth) defaultClient.getAuthentication("InternalApiKey");
    InternalApiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //InternalApiKey.setApiKeyPrefix("Token");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    InternalCustomDomainAddonRequest internalCustomDomainAddonRequest = new InternalCustomDomainAddonRequest(); // InternalCustomDomainAddonRequest | 
    try {
      apiInstance.internalCustomDomainAddon(internalCustomDomainAddonRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#internalCustomDomainAddon");
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
| **internalCustomDomainAddonRequest** | [**InternalCustomDomainAddonRequest**](InternalCustomDomainAddonRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

<a id="internalCustomDomainSweepStatus"></a>
# **internalCustomDomainSweepStatus**
> internalCustomDomainSweepStatus()

Custom domain background sweep status (internal)

Returns the last automated custom-domain sweep (TXT recheck + Fly ACME retry), job env flags, and Fly deploy troubleshooting hints when the proxy reports the app is not listening on 0.0.0.0:PORT. Requires header &#x60;X-Internal-Api-Key&#x60; (same as other /internal routes).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: InternalApiKey
    ApiKeyAuth InternalApiKey = (ApiKeyAuth) defaultClient.getAuthentication("InternalApiKey");
    InternalApiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //InternalApiKey.setApiKeyPrefix("Token");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    try {
      apiInstance.internalCustomDomainSweepStatus();
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#internalCustomDomainSweepStatus");
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

null (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | sweep payload, jobConfig, flyHttpListenTroubleshooting |  -  |
| **401** | Unauthorized |  -  |
| **503** | INTERNAL_API_KEY not configured |  -  |

<a id="internalDomainDnsRecheckBatch"></a>
# **internalDomainDnsRecheckBatch**
> internalDomainDnsRecheckBatch(internalDomainDnsRecheckBatchRequest)

Batch DNS re-verification for drift (internal)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: InternalApiKey
    ApiKeyAuth InternalApiKey = (ApiKeyAuth) defaultClient.getAuthentication("InternalApiKey");
    InternalApiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //InternalApiKey.setApiKeyPrefix("Token");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    InternalDomainDnsRecheckBatchRequest internalDomainDnsRecheckBatchRequest = new InternalDomainDnsRecheckBatchRequest(); // InternalDomainDnsRecheckBatchRequest | 
    try {
      apiInstance.internalDomainDnsRecheckBatch(internalDomainDnsRecheckBatchRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#internalDomainDnsRecheckBatch");
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
| **internalDomainDnsRecheckBatchRequest** | [**InternalDomainDnsRecheckBatchRequest**](InternalDomainDnsRecheckBatchRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Summary counts |  -  |

<a id="internalProvisionEnterprise"></a>
# **internalProvisionEnterprise**
> internalProvisionEnterprise(provisionEnterpriseRequest)

Provision enterprise dedicated API/DB (internal)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure API key authorization: InternalApiKey
    ApiKeyAuth InternalApiKey = (ApiKeyAuth) defaultClient.getAuthentication("InternalApiKey");
    InternalApiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //InternalApiKey.setApiKeyPrefix("Token");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    ProvisionEnterpriseRequest provisionEnterpriseRequest = new ProvisionEnterpriseRequest(); // ProvisionEnterpriseRequest | 
    try {
      apiInstance.internalProvisionEnterprise(provisionEnterpriseRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#internalProvisionEnterprise");
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
| **provisionEnterpriseRequest** | [**ProvisionEnterpriseRequest**](ProvisionEnterpriseRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Applied or idempotent no-op |  -  |
| **403** | not_enterprise_plan |  -  |
| **409** | provision_conflict |  -  |

<a id="inviteSubOrganizationMember"></a>
# **inviteSubOrganizationMember**
> InviteSubOrganizationMember200Response inviteSubOrganizationMember(orgId, suborgId, inviteMemberRequest)

~~Invite member to sub-organization~~ (deprecated)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String suborgId = "685acbe0e129932fbb7a0fc4"; // String | 
    InviteMemberRequest inviteMemberRequest = new InviteMemberRequest(); // InviteMemberRequest | 
    try {
      InviteSubOrganizationMember200Response result = apiInstance.inviteSubOrganizationMember(orgId, suborgId, inviteMemberRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#inviteSubOrganizationMember");
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
| **suborgId** | **String**|  | |
| **inviteMemberRequest** | [**InviteMemberRequest**](InviteMemberRequest.md)|  | |

### Return type

[**InviteSubOrganizationMember200Response**](InviteSubOrganizationMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invitation sent |  -  |

<a id="inviteTeamMember"></a>
# **inviteTeamMember**
> InviteTeamMember200Response inviteTeamMember(orgId, inviteMemberRequest)

Invite team member to organization

Send an invitation to a user to join the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    InviteMemberRequest inviteMemberRequest = new InviteMemberRequest(); // InviteMemberRequest | 
    try {
      InviteTeamMember200Response result = apiInstance.inviteTeamMember(orgId, inviteMemberRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#inviteTeamMember");
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
| **inviteMemberRequest** | [**InviteMemberRequest**](InviteMemberRequest.md)|  | |

### Return type

[**InviteTeamMember200Response**](InviteTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invitation sent |  -  |

<a id="listOrgCustomDomains"></a>
# **listOrgCustomDomains**
> OrgDomainsListResponse listOrgCustomDomains(orgId, projectId)

List custom domains and DNS verification hints

Returns allowed hostnames for **this project**, primary hostname (per project), API base URL, and per-domain DNS guidance.  Each row uses **&#x60;dnsRecords&#x60;** for the Mudbase ownership TXT (purpose **&#x60;mudbase_ownership&#x60;**) and routing **CNAME** from Fly **&#x60;dns_requirements.cname&#x60;** when Fly ACME has provisioned (else fallback **&#x60;CUSTOM_DOMAIN_API_CNAME_TARGET&#x60;**), and—when Fly ACME is enabled (**&#x60;FLY_API_TOKEN&#x60;** + **&#x60;CUSTOM_DOMAIN_FLY_ACME_ENABLED&#x60;**)—Fly rows (&#x60;fly_ownership&#x60;, &#x60;acme_challenge&#x60;, etc.) after the org has passed Mudbase TXT at least once. **&#x60;flyCertificateStatus&#x60;** mirrors Fly’s certificate state when ACME automation is on (e.g. &#x60;pending_validation&#x60;, &#x60;active&#x60;).  **&#x60;edge&#x60;** appears only when edge SSL (SSL-for-SaaS) is configured. Fly ACME and edge SSL are mutually exclusive on the server.  Requires Growth, Scale, or Enterprise plan (custom domains included in plan features). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    try {
      OrgDomainsListResponse result = apiInstance.listOrgCustomDomains(orgId, projectId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#listOrgCustomDomains");
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
| **projectId** | **String**|  | |

### Return type

[**OrgDomainsListResponse**](OrgDomainsListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain list and hints |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |

<a id="listOrganizations"></a>
# **listOrganizations**
> ListOrganizations200Response listOrganizations()

Get all organizations for user

Get all organizations the authenticated user belongs to. Requires: OrgBearerAuth (organization-level authentication only). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    try {
      ListOrganizations200Response result = apiInstance.listOrganizations();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#listOrganizations");
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

[**ListOrganizations200Response**](ListOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of organizations |  -  |

<a id="orgCustomDomainPlatformReady"></a>
# **orgCustomDomainPlatformReady**
> orgCustomDomainPlatformReady(orgId, projectId, hostname, orgCustomDomainPlatformReadyRequest)

Notify platform ops that hosting or edge work is ready (email)

Legacy optional ping: ops are emailed automatically on first successful Mudbase TXT verify. Use this only for an extra nudge. Sends an email to ops while the domain is in platform setup (after Mudbase TXT verification through later pipeline states). Recipients default to &#x60;admin@mudhaxkservices.com&#x60; and &#x60;admin@mudbase.dev&#x60; when &#x60;CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS&#x60; is unset; override with that env (comma/space-separated). Returns **503** &#x60;email_provider_not_configured&#x60; if the platform email provider is not configured. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    OrgCustomDomainPlatformReadyRequest orgCustomDomainPlatformReadyRequest = new OrgCustomDomainPlatformReadyRequest(); // OrgCustomDomainPlatformReadyRequest | 
    try {
      apiInstance.orgCustomDomainPlatformReady(orgId, projectId, hostname, orgCustomDomainPlatformReadyRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#orgCustomDomainPlatformReady");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |
| **orgCustomDomainPlatformReadyRequest** | [**OrgCustomDomainPlatformReadyRequest**](OrgCustomDomainPlatformReadyRequest.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Ops notified |  -  |
| **400** | custom_domain_invalid_state |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **503** | email_provider_not_configured — email provider not configured on the server |  -  |

<a id="orgCustomDomainSubmitCname"></a>
# **orgCustomDomainSubmitCname**
> OrgPatchDomainResponse orgCustomDomainSubmitCname(orgId, projectId, hostname)

Custom domain step 2 (optional): org confirms routing CNAME was added

Usually unnecessary. With Fly ACME default automation, Mudbase TXT verify may already set &#x60;cname_approved&#x60;. Legacy pipelines may queue &#x60;cname_pending_staff&#x60; until staff **&#x60;approve-cname&#x60;**. Use **&#x60;routingCnameTarget&#x60;** from **&#x60;GET .../projects/{projectId}/domains&#x60;** (Fly **&#x60;dns_requirements.cname&#x60;** when provisioned, else **&#x60;CUSTOM_DOMAIN_API_CNAME_TARGET&#x60;**). 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      OrgPatchDomainResponse result = apiInstance.orgCustomDomainSubmitCname(orgId, projectId, hostname);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#orgCustomDomainSubmitCname");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated domain row |  -  |
| **400** | custom_domain_invalid_state |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |

<a id="orgCustomDomainSubmitPlatformDnsVerificationDeprecated"></a>
# **orgCustomDomainSubmitPlatformDnsVerificationDeprecated**
> OrgPatchDomainResponse orgCustomDomainSubmitPlatformDnsVerificationDeprecated(orgId, projectId, hostname)

Deprecated — use POST .../verify-platform-dns

Deprecated alias of **&#x60;orgCustomDomainVerifyPlatformDns&#x60;** (same behavior — manual TXT and/or Fly ACME path per server config).

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      OrgPatchDomainResponse result = apiInstance.orgCustomDomainSubmitPlatformDnsVerificationDeprecated(orgId, projectId, hostname);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#orgCustomDomainSubmitPlatformDnsVerificationDeprecated");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Same as verify-platform-dns |  -  |
| **400** | Error |  -  |
| **503** | dns_lookup_error |  -  |

<a id="orgCustomDomainVerifyPlatformDns"></a>
# **orgCustomDomainVerifyPlatformDns**
> OrgPatchDomainResponse orgCustomDomainVerifyPlatformDns(orgId, projectId, hostname)

Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness)

**Manual path (no Fly ACME):** After staff **&#x60;PATCH .../platform-dns-verification&#x60;**, the org adds the published TXT and calls this endpoint. The API resolves public TXT at **&#x60;platformDnsVerification.recordName&#x60;** and matches **&#x60;recordValue&#x60;**. On success, &#x60;status&#x60; → **&#x60;platform_dns_pending_review&#x60;** until staff **&#x60;POST .../activate&#x60;**.  **Fly ACME path (default):** When Fly ACME is enabled and **&#x60;CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE&#x60;** is **not** set, the org calls this after Mudbase TXT and Fly DNS rows are in place (status typically **&#x60;cname_approved&#x60;** from automated verify-dns). The API triggers Fly **&#x60;POST .../check&#x60;** and **&#x60;GET&#x60;** certificate with bounded retries. On success, &#x60;status&#x60; → **&#x60;active&#x60;** and the org may receive the activation email—**no** staff **&#x60;approve-cname&#x60;** or **&#x60;activate&#x60;** required.  **Fly legacy:** If **&#x60;CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE&#x3D;true&#x60;**, behavior matches the older flow: staff **&#x60;approve-cname&#x60;** may be required first; after a ready Fly cert, **&#x60;status&#x60;** becomes **&#x60;active&#x60;** only when **&#x60;CUSTOM_DOMAIN_FLY_AUTO_ACTIVATE&#x3D;true&#x60;**, else **&#x60;platform_dns_pending_review&#x60;** until staff **&#x60;activate&#x60;**.  **&#x60;platform_dns_verification_failed&#x60;** may include **&#x60;details.flyStatus&#x60;** / **&#x60;details.flyError&#x60;** on the Fly path. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      OrgPatchDomainResponse result = apiInstance.orgCustomDomainVerifyPlatformDns(orgId, projectId, hostname);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#orgCustomDomainVerifyPlatformDns");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain row updated (&#x60;OrgPatchDomainResponse.domain&#x60;). Manual TXT path typically sets &#x60;platform_dns_pending_review&#x60;. Fly ACME default automation: typically &#x60;active&#x60; when the certificate is ready. Fly legacy staff pipeline: may set &#x60;platform_dns_pending_review&#x60; unless &#x60;CUSTOM_DOMAIN_FLY_AUTO_ACTIVATE&#x60; is enabled. Body may include refreshed &#x60;dnsRecords&#x60; and &#x60;flyCertificateStatus&#x60; on the Fly path. |  -  |
| **400** | custom_domain_invalid_state, platform_dns_verification_failed (manual TXT mismatch or Fly cert not active yet; see response details on Fly path) |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **503** | dns_lookup_error |  -  |

<a id="patchOrgCustomDomain"></a>
# **patchOrgCustomDomain**
> OrgPatchDomainResponse patchOrgCustomDomain(orgId, projectId, hostname, patchOrgDomainRequest)

Update domain status or regenerate verification token

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    PatchOrgDomainRequest patchOrgDomainRequest = new PatchOrgDomainRequest(); // PatchOrgDomainRequest | 
    try {
      OrgPatchDomainResponse result = apiInstance.patchOrgCustomDomain(orgId, projectId, hostname, patchOrgDomainRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#patchOrgCustomDomain");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |
| **patchOrgDomainRequest** | [**PatchOrgDomainRequest**](PatchOrgDomainRequest.md)|  | [optional] |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated; domain object includes dnsTxtHost and dnsTxtValue |  -  |

<a id="removeSubOrganizationMember"></a>
# **removeSubOrganizationMember**
> RemoveTeamMember200Response removeSubOrganizationMember(orgId, suborgId, userId)

~~Remove member from sub-organization~~ (deprecated)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String suborgId = "685acbe0e129932fbb7a0fc4"; // String | 
    String userId = "685acbe0e129932fbb7a0fc2"; // String | 
    try {
      RemoveTeamMember200Response result = apiInstance.removeSubOrganizationMember(orgId, suborgId, userId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#removeSubOrganizationMember");
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
| **suborgId** | **String**|  | |
| **userId** | **String**|  | |

### Return type

[**RemoveTeamMember200Response**](RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Member removed |  -  |

<a id="removeTeamMember"></a>
# **removeTeamMember**
> RemoveTeamMember200Response removeTeamMember(orgId, userId)

Remove team member from organization

Remove a user from the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String userId = "685acbe0e129932fbb7a0fc2"; // String | 
    try {
      RemoveTeamMember200Response result = apiInstance.removeTeamMember(orgId, userId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#removeTeamMember");
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

### Return type

[**RemoveTeamMember200Response**](RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Member removed |  -  |

<a id="setOrgPrimaryDomain"></a>
# **setOrgPrimaryDomain**
> setOrgPrimaryDomain(orgId, projectId, setOrgPrimaryDomainRequest)

Set primary custom domain

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    SetOrgPrimaryDomainRequest setOrgPrimaryDomainRequest = new SetOrgPrimaryDomainRequest(); // SetOrgPrimaryDomainRequest | 
    try {
      apiInstance.setOrgPrimaryDomain(orgId, projectId, setOrgPrimaryDomainRequest);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#setOrgPrimaryDomain");
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
| **projectId** | **String**|  | |
| **setOrgPrimaryDomainRequest** | [**SetOrgPrimaryDomainRequest**](SetOrgPrimaryDomainRequest.md)|  | |

### Return type

null (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Primary updated |  -  |

<a id="updateMemberRole"></a>
# **updateMemberRole**
> UpdateMemberRole200Response updateMemberRole(orgId, userId, updateMemberRoleRequest)

Update member role

Update a member&#39;s role in the organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String userId = "685acbe0e129932fbb7a0fc2"; // String | 
    UpdateMemberRoleRequest updateMemberRoleRequest = new UpdateMemberRoleRequest(); // UpdateMemberRoleRequest | 
    try {
      UpdateMemberRole200Response result = apiInstance.updateMemberRole(orgId, userId, updateMemberRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateMemberRole");
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
| **updateMemberRoleRequest** | [**UpdateMemberRoleRequest**](UpdateMemberRoleRequest.md)|  | |

### Return type

[**UpdateMemberRole200Response**](UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

<a id="updateOrganization"></a>
# **updateOrganization**
> UpdateOrganization200Response updateOrganization(orgId, updateOrganizationRequest)

Update organization

Update organization details. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    UpdateOrganizationRequest updateOrganizationRequest = new UpdateOrganizationRequest(); // UpdateOrganizationRequest | 
    try {
      UpdateOrganization200Response result = apiInstance.updateOrganization(orgId, updateOrganizationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateOrganization");
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
| **updateOrganizationRequest** | [**UpdateOrganizationRequest**](UpdateOrganizationRequest.md)|  | |

### Return type

[**UpdateOrganization200Response**](UpdateOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization updated |  -  |

<a id="updateOrganizationPlan"></a>
# **updateOrganizationPlan**
> UpdateOrganizationPlan200Response updateOrganizationPlan(orgId, updateOrganizationPlanRequest)

Update organization plan

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    UpdateOrganizationPlanRequest updateOrganizationPlanRequest = new UpdateOrganizationPlanRequest(); // UpdateOrganizationPlanRequest | 
    try {
      UpdateOrganizationPlan200Response result = apiInstance.updateOrganizationPlan(orgId, updateOrganizationPlanRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateOrganizationPlan");
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
| **updateOrganizationPlanRequest** | [**UpdateOrganizationPlanRequest**](UpdateOrganizationPlanRequest.md)|  | |

### Return type

[**UpdateOrganizationPlan200Response**](UpdateOrganizationPlan200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plan updated (or error if trying to upgrade to paid) |  -  |

<a id="updateSubOrganization"></a>
# **updateSubOrganization**
> UpdateSubOrganization200Response updateSubOrganization(orgId, suborgId, updateOrganizationRequest)

~~Update sub-organization~~ (deprecated)

Update a sub-organization&#39;s configuration. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String suborgId = "685acbe0e129932fbb7a0fc4"; // String | 
    UpdateOrganizationRequest updateOrganizationRequest = new UpdateOrganizationRequest(); // UpdateOrganizationRequest | 
    try {
      UpdateSubOrganization200Response result = apiInstance.updateSubOrganization(orgId, suborgId, updateOrganizationRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateSubOrganization");
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
| **suborgId** | **String**|  | |
| **updateOrganizationRequest** | [**UpdateOrganizationRequest**](UpdateOrganizationRequest.md)|  | |

### Return type

[**UpdateSubOrganization200Response**](UpdateSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Sub-organization updated |  -  |

<a id="updateSubOrganizationMemberRole"></a>
# **updateSubOrganizationMemberRole**
> UpdateMemberRole200Response updateSubOrganizationMemberRole(orgId, suborgId, userId, updateMemberRoleRequest)

~~Update sub-organization member role~~ (deprecated)

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

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

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "685acbe0e129932fbb7a0fc3"; // String | 
    String suborgId = "685acbe0e129932fbb7a0fc4"; // String | 
    String userId = "685acbe0e129932fbb7a0fc2"; // String | 
    UpdateMemberRoleRequest updateMemberRoleRequest = new UpdateMemberRoleRequest(); // UpdateMemberRoleRequest | 
    try {
      UpdateMemberRole200Response result = apiInstance.updateSubOrganizationMemberRole(orgId, suborgId, userId, updateMemberRoleRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateSubOrganizationMemberRole");
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
| **suborgId** | **String**|  | |
| **userId** | **String**|  | |
| **updateMemberRoleRequest** | [**UpdateMemberRoleRequest**](UpdateMemberRoleRequest.md)|  | |

### Return type

[**UpdateMemberRole200Response**](UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

<a id="updateUserAccountStatus"></a>
# **updateUserAccountStatus**
> UpdateUserAccountStatus200Response updateUserAccountStatus(orgId, userId, updateUserAccountStatusRequest)

Update user account status (activate or suspend)

Set a user&#39;s account status to active or suspended. Used to approve pending users or suspend/activate accounts. Cannot change status of an organization owner. Requires owner or admin role. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String userId = "userId_example"; // String | 
    UpdateUserAccountStatusRequest updateUserAccountStatusRequest = new UpdateUserAccountStatusRequest(); // UpdateUserAccountStatusRequest | 
    try {
      UpdateUserAccountStatus200Response result = apiInstance.updateUserAccountStatus(orgId, userId, updateUserAccountStatusRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#updateUserAccountStatus");
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
| **updateUserAccountStatusRequest** | [**UpdateUserAccountStatusRequest**](UpdateUserAccountStatusRequest.md)|  | |

### Return type

[**UpdateUserAccountStatus200Response**](UpdateUserAccountStatus200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User status updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

<a id="verifyOrgCustomDomainDns"></a>
# **verifyOrgCustomDomainDns**
> OrgVerifyCustomDomainDnsSuccessResponse verifyOrgCustomDomainDns(orgId, projectId, hostname)

Verify domain ownership via DNS TXT

Looks up TXT at &#x60;_mudbase-verify.&lt;hostname&gt;&#x60; for value &#x60;mudbase-domain-verification&#x3D;&lt;token&gt;&#x60;.  When the server has **&#x60;CLOUDFLARE_API_TOKEN&#x60;** and **&#x60;CLOUDFLARE_ZONE_ID&#x60;** configured (and Fly ACME is **not** enabled), a successful verify also creates or refreshes a Cloudflare Custom Hostname (SSL for SaaS) and returns **&#x60;cloudflare&#x60;** with DCV hints.  When **Fly ACME** is enabled (**&#x60;FLY_API_TOKEN&#x60;** + **&#x60;CUSTOM_DOMAIN_FLY_ACME_ENABLED&#x3D;true&#x60;** + app slug), a successful verify calls Fly’s Certificates API (&#x60;POST .../certificates/acme&#x60;) and persists DNS requirements. If Fly returns DNS rows and **&#x60;CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE&#x60;** is **not** set, status advances to **&#x60;cname_approved&#x60;** in the same response (no staff **&#x60;approve-cname&#x60;**); **&#x60;org.domain.cname_staff_queued&#x60;** is not logged for that path. Otherwise (legacy Fly or non-Fly), first success from &#x60;pending&#x60;/&#x60;failed&#x60; may move to **&#x60;cname_pending_staff&#x60;** and queue staff as before.  The **200** response may include **&#x60;dnsRecords&#x60;**, **&#x60;flyCertificateStatus&#x60;**, and **&#x60;routingCnameTarget&#x60;** from Fly’s **&#x60;dns_requirements.cname&#x60;** when provisioned.  Cloudflare SaaS and Fly ACME cannot both be enabled; the API process refuses to start if both are configured. 

### Example
```java
// Import classes:
import com.mudbase.sdk.ApiClient;
import com.mudbase.sdk.ApiException;
import com.mudbase.sdk.Configuration;
import com.mudbase.sdk.auth.*;
import com.mudbase.sdk.models.*;
import com.mudbase.sdk.api.OrganizationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://cloud.mudbase.dev");
    
    // Configure HTTP bearer authorization: OrgBearerAuth
    HttpBearerAuth OrgBearerAuth = (HttpBearerAuth) defaultClient.getAuthentication("OrgBearerAuth");
    OrgBearerAuth.setBearerToken("BEARER TOKEN");

    OrganizationsApi apiInstance = new OrganizationsApi(defaultClient);
    String orgId = "orgId_example"; // String | 
    String projectId = "projectId_example"; // String | 
    String hostname = "hostname_example"; // String | 
    try {
      OrgVerifyCustomDomainDnsSuccessResponse result = apiInstance.verifyOrgCustomDomainDns(orgId, projectId, hostname);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling OrganizationsApi#verifyOrgCustomDomainDns");
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
| **projectId** | **String**|  | |
| **hostname** | **String**|  | |

### Return type

[**OrgVerifyCustomDomainDnsSuccessResponse**](OrgVerifyCustomDomainDnsSuccessResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | TXT verified. Fly ACME (default automation): often &#x60;cname_approved&#x60; when Fly returns DNS requirements; legacy Fly or non-Fly may show &#x60;cname_pending_staff&#x60; or &#x60;dns_verified&#x60;. Includes &#x60;dnsTxtHost&#x60;/&#x60;dnsTxtValue&#x60;, optional &#x60;cloudflare&#x60; (Cloudflare SaaS), optional &#x60;dnsRecords&#x60; + &#x60;flyCertificateStatus&#x60; when Fly ACME ran after this verify. |  -  |
| **400** | dns_verification_failed (TXT missing or wrong); body includes dnsTxtHost, dnsTxtValue, challengeHost, expectedTxt |  -  |
| **503** | dns_lookup_error |  -  |

