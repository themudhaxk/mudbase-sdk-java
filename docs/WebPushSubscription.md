

# WebPushSubscription

A browser `PushSubscription` from `pushManager.subscribe()` - the push-service `endpoint` plus the `p256dh` / `auth` keys the server needs to encrypt a payload for that endpoint. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**endpoint** | **String** | The push-service endpoint URL returned by &#x60;pushManager.subscribe()&#x60;. |  |
|**keys** | [**WebPushSubscriptionKeys**](WebPushSubscriptionKeys.md) |  |  |



