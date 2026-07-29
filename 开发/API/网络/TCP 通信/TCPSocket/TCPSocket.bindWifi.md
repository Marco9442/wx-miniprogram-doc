# [#](#TCPSocket-bindWifi-Object-options) TCPSocket.bindWifi(Object options)

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

将 TCP Socket 绑定到当前 wifi 网络，成功后会触发 onBindWifi 事件（仅安卓支持）

## [#](#参数) 参数

### [#](#Object-options) Object options

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| BSSID | string |  | 是 | 当前 wifi 网络的 BSSID ，可通过 wx.getConnectedWifi 获取 |

## [#](#示例代码) 示例代码

```
  const tcp = wx.createTCPSocket()
  tcp.bindWifi({ BSSID: 'xxx' })
  tcp.onBindWifi(() => {})
```

Incorrect translation.