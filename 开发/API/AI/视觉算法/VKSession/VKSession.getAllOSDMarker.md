# [#](#Array-Object-VKSession-getAllOSDMarker) Array.<Object> VKSession.getAllOSDMarker()

> 基础库 2.24.5 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.24.5](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

获取所有 OSD marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.OSD 为 true

## [#](#返回值) 返回值

### [#](#Array-Object) Array.<Object>

OSD marker 列表

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| markerId | number | marker id |
| path | string | 图片路径 |

Incorrect translation.