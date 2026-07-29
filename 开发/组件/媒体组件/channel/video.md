# [#](#channel-video) channel-video

> 基础库 2.25.1 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

> 相关文档: [视频号视频](../framework/open-ability/channels-activity.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

小程序内嵌视频号视频组件，支持在小程序中播放视频号视频，并无弹窗跳转至视频号。注意：

1. 若小程序与内嵌视频号视频为同主体，则内嵌视频号视频可支持自动播放；
2. 基础库 2.31.1 起，对于非个人主体小程序，若小程序于内嵌视频号视频非同主体，则内嵌视频号视频不可自动播放，即强制 autoplay=false。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | feed-id | string |  | 是 | 仅视频号视频与小程序同主体时生效。若内嵌非同主体视频，请使用 feed-token。 |  |
|  | finder-user-name | string |  | 是 | 视频号 id，以“sph”开头的id，可在视频号助手获取。视频号必须与当前小程序相同主体。 |  |
|  | feed-token | string |  | 是 | 仅内嵌小程序非同主体视频号视频时使用，获取方式参考[本指引](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/channels-activity#feed-token)。 | [2.31.1](../framework/compatibility.html) |
|  | autoplay | string |  | 是 | 是否自动播放。仅视频号视频与小程序同主体时支持设置为 true。 | [2.31.1](../framework/compatibility.html) |
|  | loop | boolean | false | 否 | 是否循环播放 |  |
|  | muted | boolean | false | 否 | 是否静音播放 |  |
|  | object-fit | boolean | contain | 否 | 当视频大小与 video 容器大小不一致时，视频的表现形式 |  |
|  | | 合法值 | 说明 | | --- | --- | | contain | 包含 | | fill | 填充 | | cover | 覆盖 | | | | | | |
|  | binderror | eventhandle |  | 否 | 视频播放出错时触发 |  |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：暂不支持纯图片视频号内容。

Incorrect translation.