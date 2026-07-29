# [#](#channel-live) channel-live

> 基础库 2.29.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

> 相关文档: [视频号直播](../framework/open-ability/channels-live.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

小程序内嵌视频号直播组件，展示视频号直播状态和封面，并无弹窗跳转至视频号。注意：使用该组件打开的视频号视频需要与小程序的主体一致。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| feed-id | string |  | 是 | 视频 feedId |
| finder-user-name | string |  | 是 | 视频号 id，以“sph”开头的id，可在视频号助手获取。视频号必须与当前小程序相同主体。 |

Incorrect translation.