# [#](#switch) switch

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

开关选择器。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| checked | boolean | false | 否 | 是否选中 | [1.0.0](../framework/compatibility.html) |
| disabled | boolean | false | 否 | 是否禁用 | [1.0.0](../framework/compatibility.html) |
| type | string | switch | 否 | 样式，有效值：switch, checkbox | [1.0.0](../framework/compatibility.html) |
| color | string | #04BE02 | 否 | switch 的颜色，同 css 的 color | [1.0.0](../framework/compatibility.html) |
| bindchange | eventhandle |  | 否 | 点击导致 checked 改变时会触发 change 事件，event.detail={ value} | [1.0.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: switch类型切换时在iOS自带振动反馈，可在系统设置 -> 声音与触感 -> 系统触感反馈中关闭

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/6db9lcmu6VYt "在开发者工具中预览效果")

Incorrect translation.