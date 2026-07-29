# [#](#VKSession-on-string-eventName-function-fn) VKSession.on(string eventName, function fn)

> 基础库 2.20.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.20.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

监听会话事件。

## [#](#参数) 参数

### [#](#string-eventName) string eventName

事件名称

**eventName 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| resize | 相机尺寸变化事件，回调参数为相机尺寸 |  |
| addAnchors | 增加 anchor 事件，回调参数为 [VKPlaneAnchor](VKPlaneAnchor.html)/[VKMarkerAnchor](VKMarkerAnchor.html)/[VKOSDAnchor](VKOSDAnchor.html) 列表（只有v2版本支持） 或 [VKFaceAnchor](VKFaceAnchor.html)/[VKOCRAnchor](VKOCRAnchor.html)/[VKHandAnchor](VKHandAnchor.html)/[VKBodyAnchor](VKBodyAnchor.html)列表（v1、v2都支持） | [2.22.0](../../../framework/compatibility.html) |
| updateAnchors | 更新 anchor 事件，回调参数为 [VKPlaneAnchor](VKPlaneAnchor.html)/[VKMarkerAnchor](VKMarkerAnchor.html)/[VKOSDAnchor](VKOSDAnchor.html) 列表（只有v2版本支持） 或 [VKFaceAnchor](VKFaceAnchor.html)/[VKOCRAnchor](VKOCRAnchor.html)/[VKHandAnchor](VKHandAnchor.html)/[VKBodyAnchor](VKBodyAnchor.html)列表（v1、v2都支持） | [2.22.0](../../../framework/compatibility.html) |
| removeAnchors | 删除 anchor 事件，回调参数为 [VKPlaneAnchor](VKPlaneAnchor.html)/[VKMarkerAnchor](VKMarkerAnchor.html)/[VKOSDAnchor](VKOSDAnchor.html) 列表（只有v2版本支持） 或 [VKFaceAnchor](VKFaceAnchor.html)/[VKOCRAnchor](VKOCRAnchor.html)/[VKHandAnchor](VKHandAnchor.html)/[VKBodyAnchor](VKBodyAnchor.html) 列表（v1、v2都支持） | [2.22.0](../../../framework/compatibility.html) |

### [#](#function-fn) function fn

事件监听函数

Incorrect translation.