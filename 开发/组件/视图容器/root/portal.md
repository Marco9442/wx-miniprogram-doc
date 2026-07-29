# [#](#root-portal) root-portal

> 基础库 2.25.2 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

使整个子树从页面中脱离出来，类似于在 CSS 中使用 fixed position 的效果。主要用于制作弹窗、弹出层等。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| enable | boolean | true | 否 | 是否从页面中脱离出来 | [2.26.1](../framework/compatibility.html) |
| externalClass | string |  | 否 | 外部样式类 | [3.9.2](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/1XCYEQmb7UJy "在开发者工具中预览效果")

Incorrect translation.