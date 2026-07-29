# [#](#wx-postMessageToReferrerMiniProgram-Object-object) wx.postMessageToReferrerMiniProgram(Object object)

> 基础库 3.2.1 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

向跳转的源小程序发送消息，源小程序可在 [wx.onShow]((wx.onShow)) 或 [wx.getEnterOptionsSync](../life-cycle/wx.getEnterOptionsSync.html) 中通过 extraData 接收消息。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| extraData | Object |  | 否 | 需要返回的数据 |

多次调用会覆盖之前传递的消息，通过 [wx.navigateBackMiniProgram](../../../navigate/wx.navigateBackMiniProgram.html) 传递 extraData 也会覆盖消息。

在触发返回后传递的消息不会被收到。

如果没有源小程序能够收到消息，会抛出 no referrer 错误。

Incorrect translation.