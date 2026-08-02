

# AdminOrgLimitsPatchRequest

Partial org limit overrides for platform admins. At least one property required. Keys match `PLANS[*].limits` in the backend; integers are non-negative or null for unlimited. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**projects** | **Integer** |  |  [optional] |
|**storage** | **Integer** |  |  [optional] |
|**bandwidth** | **Integer** |  |  [optional] |
|**apiCalls** | **Integer** |  |  [optional] |
|**buckets** | **Integer** |  |  [optional] |
|**collections** | **Integer** |  |  [optional] |
|**realtimeConnections** | **Integer** |  |  [optional] |
|**realtimeMessages** | **Integer** |  |  [optional] |
|**chatMessagesPerMonth** | **Integer** |  |  [optional] |
|**monitoredWallets** | **Integer** |  |  [optional] |
|**walletWebhooksPerOrg** | **Integer** |  |  [optional] |
|**apiKeysPerProject** | **Integer** |  |  [optional] |
|**webhooksPerProject** | **Integer** |  |  [optional] |
|**functionsPerProject** | **Integer** |  |  [optional] |
|**functionInvocationsPerMonth** | **Integer** |  |  [optional] |
|**messagingMessagesPerMonth** | **Integer** |  |  [optional] |
|**smsPerMonth** | **Integer** |  |  [optional] |
|**chatChannelsPerProject** | **Integer** |  |  [optional] |
|**backupsPerProject** | **Integer** |  |  [optional] |
|**restoresPerMonth** | **Integer** |  |  [optional] |
|**integrationsPerProject** | **Integer** |  |  [optional] |
|**rolesPerOrg** | **Integer** |  |  [optional] |
|**alertsPerProject** | **Integer** |  |  [optional] |
|**blockchainChains** | **Integer** |  |  [optional] |
|**teamUsers** | **Integer** |  |  [optional] |
|**bugAnalysis** | [**AdminOrgLimitsPatchRequestBugAnalysis**](AdminOrgLimitsPatchRequestBugAnalysis.md) |  |  [optional] |



