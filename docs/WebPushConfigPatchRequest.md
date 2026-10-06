

# WebPushConfigPatchRequest

All fields optional. `enabled` toggles native Web Push (and provisions a keypair on first enable); `rotateKeys` regenerates the keypair (invalidating existing subscriptions); `subject` sets the RFC 8292 contact URI. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** |  |  [optional] |
|**rotateKeys** | **Boolean** |  |  [optional] |
|**subject** | **String** | A &#x60;mailto:&#x60; address or an &#x60;https&#x60; URL. |  [optional] |



