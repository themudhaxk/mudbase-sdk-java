

# AuthConfig

Project auth configuration (providers, notifyOnNewSignIn).

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**providers** | [**List&lt;AuthProvider&gt;**](AuthProvider.md) |  |  [optional] |
|**notifyOnNewSignIn** | **Boolean** | When true, a \&quot;new sign-in detected\&quot; email is sent to the user on each app sign-in (local or OAuth). Counts against the org&#39;s messaging/email plan quota. Default false. Organization-based sign-in always sends this email (no quota deduction).  |  [optional] |



