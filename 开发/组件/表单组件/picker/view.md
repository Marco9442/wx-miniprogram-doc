# [#](#picker-view) picker-view

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

嵌入页面的滚动选择器。其中只可放置 [picker-view-column](picker-view-column.html)组件，其它节点不会显示。

目前滚动过程中 bindpickstart、bindpickend 会被触发多次，后续 skyline 升级会修复该问题
skyline支持在 picker-view-column 上设置 indicator-style

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | value | Array.<number> |  | 否 | 数组中的数字依次表示 picker-view 内的 picker-view-column 选择的第几项（下标从 0 开始），数字大于 picker-view-column 可选项长度时，选择最后一项。 | [1.0.0](../framework/compatibility.html) |
|  | mask-class | string |  | 否 | 设置蒙层的类名 | [1.5.0](../framework/compatibility.html) |
|  | indicator-style | string |  | 否 | 设置选择器中间选中框的样式 | [1.0.0](../framework/compatibility.html) |
|  | bindchange | eventhandle |  | 否 | 滚动选择时触发change事件，event.detail = {value}；value为数组，表示 picker-view 内的 picker-view-column 当前选择的是第几项（下标从 0 开始） | [1.0.0](../framework/compatibility.html) |
|  | bindpickstart | eventhandle |  | 否 | 当滚动选择开始时候触发事件 | [2.3.1](../framework/compatibility.html) |
|  | bindpickend | eventhandle |  | 否 | 当滚动选择结束时候触发事件 | [2.3.1](../framework/compatibility.html) |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | indicator-class | string |  | 否 | 设置选择器中间选中框的类名 | [1.1.0](../framework/compatibility.html) |
|  | mask-style | string |  | 否 | 设置蒙层的样式 | [1.5.0](../framework/compatibility.html) |
|  | immediate-change | boolean | false | 否 | 是否在手指松开时立即触发 change 事件。若不开启则会在滚动动画结束后触发 change 事件。 | [2.21.1](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 滚动时在iOS自带振动反馈，可在系统设置 -> 声音与触感 -> 系统触感反馈中关闭
2. `tip`: indicator-style 属性 skyline 从基础库 [3.3.4](../framework/compatibility.html) 开始支持，目前支持 `height`、`border`、`background-color`

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/5H2mhSmb7UJ0 "在开发者工具中预览效果")

Incorrect translation.