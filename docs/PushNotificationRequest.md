

# PushNotificationRequest

Provide at least one target: `tokens` (registered device tokens), `endpoints` (registered Web Push subscription endpoints), `userIds` (Web Push subscriptions associated to those user ids), or `webPushBroadcast: true` (every enabled Web Push subscription in the project). A single send can target both the device-token channel and the native Web Push channel at once. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**tokens** | **List&lt;String&gt;** | Registered device push tokens to deliver to (device-token channel). |  [optional] |
|**endpoints** | **List&lt;String&gt;** | Registered Web Push subscription endpoints to deliver to (native Web Push channel).  |  [optional] |
|**userIds** | **List&lt;String&gt;** | Deliver to every Web Push subscription registered under these user ids (native Web Push channel).  |  [optional] |
|**webPushBroadcast** | **Boolean** | When true, deliver to every enabled Web Push subscription registered to the project (native Web Push channel). Ignored when the project has not enabled native Web Push.  |  [optional] |
|**title** | **String** |  |  |
|**body** | **String** |  |  |
|**data** | **Object** |  |  [optional] |
|**imageUrl** | **String** |  |  [optional] |



