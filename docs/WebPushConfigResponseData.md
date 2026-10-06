

# WebPushConfigResponseData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** | Whether native Web Push is enabled for this project. |  [optional] |
|**hasKeys** | **Boolean** | Whether a VAPID keypair has been provisioned. |  [optional] |
|**publicKey** | **String** | The VAPID application-server public key clients subscribe with. Null when native Web Push is not enabled.  |  [optional] |
|**vapidSubject** | **String** | RFC 8292 contact subject (a &#x60;mailto:&#x60; address or &#x60;https&#x60; URL). |  [optional] |
|**generatedAt** | **OffsetDateTime** | When the current VAPID keypair was generated. |  [optional] |



