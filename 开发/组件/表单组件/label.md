# [#](#label) label

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

用来改进表单组件的可用性。

使用for属性找到对应的id，或者将控件放在该标签下，当点击时，就会触发对应的控件。
for优先级高于内部控件，内部有多个控件的时候默认触发第一个控件。
目前可以绑定的控件有：[button](button.html), [checkbox](checkbox.html), [radio](radio.html), [switch](switch.html), [input](input.html)。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| for | string |  | 否 | 绑定控件的 id | [1.0.0](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/vt1UCSmQ7MJY "在开发者工具中预览效果")

Incorrect translation.