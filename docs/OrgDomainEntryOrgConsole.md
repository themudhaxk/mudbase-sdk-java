

# OrgDomainEntryOrgConsole

Org API compact domain row: use **`dnsRecords`** for the Mudbase ownership TXT (purpose `mudbase_ownership`) and routing CNAME. Omits `hostnameNormalized`, `verificationToken`, `dnsTxtHost`, and `dnsTxtValue`. Omits `cloudflareEdge` when Cloudflare SaaS is not configured. Optional keys with no value are omitted from JSON responses.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  [optional] |
|**hostname** | **String** |  |  [optional] |
|**status** | **String** |  |  [optional] |
|**isPrimary** | **Boolean** |  |  [optional] |
|**source** | [**SourceEnum**](#SourceEnum) |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**verifiedAt** | **OffsetDateTime** |  |  [optional] |
|**lastVerifiedAt** | **OffsetDateTime** |  |  [optional] |
|**cnameSubmittedAt** | **OffsetDateTime** |  |  [optional] |
|**cnameApprovedAt** | **OffsetDateTime** |  |  [optional] |
|**customDomainVerificationStep** | **Integer** |  |  [optional] |
|**routingCnameTarget** | **String** |  |  [optional] |
|**dnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) |  |  [optional] |
|**platformActivationPending** | **Boolean** |  |  [optional] |
|**customDomainLiveForApiTraffic** | **Boolean** |  |  [optional] |
|**cloudflareEdge** | [**OrgCloudflareEdgeHints**](OrgCloudflareEdgeHints.md) |  |  [optional] |
|**flyCertificateStatus** | **String** |  |  [optional] |
|**platformDnsVerification** | [**OrgPlatformDnsVerificationCustomer**](OrgPlatformDnsVerificationCustomer.md) |  |  [optional] |
|**platformDnsVerificationSubmittedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: SourceEnum

| Name | Value |
|---- | -----|
| MANUAL | &quot;manual&quot; |
| API | &quot;api&quot; |
| IMPORTED | &quot;imported&quot; |



