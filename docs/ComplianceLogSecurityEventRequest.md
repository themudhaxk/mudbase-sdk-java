

# ComplianceLogSecurityEventRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**eventType** | [**EventTypeEnum**](#EventTypeEnum) |  |  |
|**severity** | [**SeverityEnum**](#SeverityEnum) |  |  |
|**details** | [**ComplianceLogSecurityEventRequestDetails**](ComplianceLogSecurityEventRequestDetails.md) |  |  [optional] |



## Enum: EventTypeEnum

| Name | Value |
|---- | -----|
| UNAUTHORIZED_ACCESS_ATTEMPT | &quot;unauthorized_access_attempt&quot; |
| BRUTE_FORCE_ATTEMPT | &quot;brute_force_attempt&quot; |
| SUSPICIOUS_API_ACTIVITY | &quot;suspicious_api_activity&quot; |
| PRIVATE_KEY_EXPORT | &quot;private_key_export&quot; |
| BULK_DATA_EXPORT | &quot;bulk_data_export&quot; |
| ADMIN_PRIVILEGE_ESCALATION | &quot;admin_privilege_escalation&quot; |
| DATA_BREACH_DETECTED | &quot;data_breach_detected&quot; |
| MFA_BYPASS_ATTEMPT | &quot;mfa_bypass_attempt&quot; |



## Enum: SeverityEnum

| Name | Value |
|---- | -----|
| LOW | &quot;low&quot; |
| MEDIUM | &quot;medium&quot; |
| HIGH | &quot;high&quot; |
| CRITICAL | &quot;critical&quot; |



