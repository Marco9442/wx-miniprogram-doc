# [#](#slider) slider

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

滑动选择器。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| min | number | 0 | 否 | 最小值 | [1.0.0](../framework/compatibility.html) |
| max | number | 100 | 否 | 最大值 | [1.0.0](../framework/compatibility.html) |
| step | number | 1 | 否 | 步长，取值必须大于 0，并且可被(max - min)整除 | [1.0.0](../framework/compatibility.html) |
| disabled | boolean | false | 否 | 是否禁用 | [1.0.0](../framework/compatibility.html) |
| value | number | 0 | 否 | 当前取值 | [1.0.0](../framework/compatibility.html) |
| color | color | #e9e9e9 | 否 | 背景条的颜色（请使用 backgroundColor） | [1.0.0](../framework/compatibility.html) |
| selected-color | color | #1aad19 | 否 | 已选择的颜色（请使用 activeColor） | [1.0.0](../framework/compatibility.html) |
| activeColor | color | #1aad19 | 否 | 已选择的颜色 | [1.0.0](../framework/compatibility.html) |
| backgroundColor | color | #e9e9e9 | 否 | 背景条的颜色 | [1.0.0](../framework/compatibility.html) |
| block-size | number | 28 | 否 | 滑块的大小，取值范围为 12 - 28 | [1.9.0](../framework/compatibility.html) |
| block-color | color | #ffffff | 否 | 滑块的颜色 | [1.9.0](../framework/compatibility.html) |
| show-value | boolean | false | 否 | 是否显示当前 value | [1.0.0](../framework/compatibility.html) |
| bindchange | eventhandle |  | 否 | 完成一次拖动后触发的事件，event.detail = {value} | [1.0.0](../framework/compatibility.html) |
| bindchanging | eventhandle |  | 否 | 拖动过程中触发的事件，event.detail = {value} | [1.7.0](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/3NbqVcm56OYS "在开发者工具中预览效果")

Incorrect translation.