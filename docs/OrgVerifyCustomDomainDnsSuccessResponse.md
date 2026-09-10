

# OrgVerifyCustomDomainDnsSuccessResponse


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**success** | **Boolean** |  |  |
|**hostname** | **String** |  |  |
|**status** | **String** | Domain row status after check (typically cname_pending_staff after first TXT success from pending/failed; legacy dns_verified possible) |  |
|**verificationToken** | **String** |  |  |
|**challengeHost** | **String** | Same as dnsTxtHost (_mudbase-verify.&lt;hostname&gt;) |  |
|**expectedTxt** | **String** | Same as dnsTxtValue |  |
|**dnsTxtHost** | **String** |  |  |
|**dnsTxtValue** | **String** |  |  |
|**edge** | [**OrgEdgeHints**](OrgEdgeHints.md) |  |  [optional] |
|**dnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) | Same shape as &#x60;OrgDomainEntryWithDns.dnsRecords&#x60; when certificate provisioning ran after this successful verify; omit or empty when provisioning is disabled or not yet run. |  [optional] |
|**flyCertificateStatus** | **String** | Managed certificate status after verify when provisioning is active; null otherwise |  [optional] |
|**flyAcmeEnabled** | **Boolean** | True when automated managed-certificate provisioning is configured for this deployment. |  [optional] |
|**flyAcmeDisabledReason** | **String** | When &#x60;flyAcmeEnabled&#x60; is false, why automated provisioning did not run (ops misconfiguration hint). |  [optional] |
|**flyProvisionError** | **String** | When provisioning is enabled but certificate issuance failed, the provider error message for support; null on success. |  [optional] |
|**flyLegacyStaffPipeline** | **Boolean** | When true, the legacy staff pipeline is on: status may stay &#x60;cname_pending_staff&#x60; and staff approve-cname is required even if certificate provisioning succeeds. |  [optional] |



