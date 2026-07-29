# [#](#view) view

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

视图容器

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| hover-class | string | none | 否 | 指定按下去的样式类。当 `hover-class="none"` 时，没有点击态效果 | [1.0.0](../framework/compatibility.html) |
| hover-stop-propagation | boolean | false | 否 | 指定是否阻止本节点的祖先节点出现点击态 | [1.5.0](../framework/compatibility.html) |
| hover-start-time | number | 50 | 否 | 按住后多久出现点击态，单位毫秒 | [1.0.0](../framework/compatibility.html) |
| hover-stay-time | number | 400 | 否 | 手指松开后点击态保留时间，单位毫秒 | [1.0.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 如果需要使用滚动视图，请使用 [scroll-view](scroll-view.html)

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/v2BmcQmM7qJa "在开发者工具中预览效果")

Incorrect translation.