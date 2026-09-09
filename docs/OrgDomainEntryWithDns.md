

# OrgDomainEntryWithDns

Full allowed-domain row (admin and legacy): includes **`dnsTxtHost`** / **`dnsTxtValue`**, optional managed edge TLS hints, staff-published step-3 TXT (`platformDnsVerification` on the manual path), and unified **`dnsRecords`** when the API builds a checklist. **`routingCnameTarget`** is the managed routing CNAME target when the certificate has provisioned, else the platform default. Org-facing routes return the compact **`OrgDomainEntryOrgConsole`** shape instead (no raw `verificationToken` or duplicate TXT keys).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** | Subdocument id when present (MongoDB) |  [optional] |
|**hostname** | **String** |  |  [optional] |
|**hostnameNormalized** | **String** |  |  [optional] |
|**status** | **String** |  |  [optional] |
|**isPrimary** | **Boolean** |  |  [optional] |
|**source** | [**SourceEnum**](#SourceEnum) |  |  [optional] |
|**verificationToken** | **String** |  |  [optional] |
|**createdAt** | **OffsetDateTime** |  |  [optional] |
|**verifiedAt** | **OffsetDateTime** |  |  [optional] |
|**lastVerifiedAt** | **OffsetDateTime** |  |  [optional] |
|**dnsTxtHost** | **String** | FQDN for the TXT record (e.g. _mudbase-verify.example.com) |  [optional] |
|**dnsTxtValue** | **String** | Exact TXT string value (mudbase-domain-verification&#x3D;&lt;token&gt;) |  [optional] |
|**edge** | [**OrgEdgeHints**](OrgEdgeHints.md) |  |  [optional] |
|**platformActivationPending** | **Boolean** | True while Mudbase TXT passed but custom host not yet active (includes CNAME and platform DNS pipeline). |  [optional] |
|**customDomainLiveForApiTraffic** | **Boolean** |  |  [optional] |
|**customDomainVerificationStep** | **Integer** | Console wizard step 1–3; null when active/verified. |  [optional] |
|**routingCnameTarget** | **String** | Routing CNAME target: the managed certificate&#39;s provisioned CNAME target when requirements have been stored; otherwise the platform default target. |  [optional] |
|**dnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) | Unified checklist: Mudbase ownership TXT, routing CNAME (purpose &#x60;routing&#x60;) when provisioned else the platform default, and the managed certificate-provisioning rows once the managed certificate has been provisioned after the Mudbase TXT. Empty or absent when the certificate is not yet provisioned. Prefer this over &#x60;platformDnsVerification&#x60; alone for org-facing DNS UI. |  [optional] |
|**flyCertificateStatus** | **String** | Managed certificate &#x60;status&#x60; during provisioning (e.g. &#x60;pending_validation&#x60;, &#x60;active&#x60;). Null when managed certificate provisioning is not in use for this deployment. |  [optional] |
|**platformDnsVerification** | [**OrgPlatformDnsVerificationCustomer**](OrgPlatformDnsVerificationCustomer.md) |  |  [optional] |
|**cnameSubmittedAt** | **OffsetDateTime** |  |  [optional] |
|**cnameApprovedAt** | **OffsetDateTime** |  |  [optional] |
|**platformDnsVerificationSubmittedAt** | **OffsetDateTime** |  |  [optional] |



## Enum: SourceEnum

| Name | Value |
|---- | -----|
| MANUAL | &quot;manual&quot; |
| API | &quot;api&quot; |
| IMPORTED | &quot;imported&quot; |



