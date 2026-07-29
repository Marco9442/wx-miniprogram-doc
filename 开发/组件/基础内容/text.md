# [#](#text) text

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

文本。

1. 内联文本只能用 text 组件，不能用 view，如 <text> foo <text>bar</text> </text>
2. 新增 span 组件用于内联文本和图片，如 <span> <image> </image> <text>bar</text> </span>

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | selectable | boolean | false | 否 | 文本是否可选 (已废弃) | [1.1.0](../framework/compatibility.html) |
|  | user-select | boolean | false | 否 | 文本是否可选，该属性会使文本节点显示为 inline-block | [2.12.1](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | overflow | string | visible | 是 | 文本溢出处理 |
|  | | 合法值 | 说明 | | --- | --- | | clip | 修剪文本 | | fade | 淡出 | | ellipsis | 显示省略号 | | visible | 文本不截断 | | | | | |
|  | max-lines | number |  | 是 | 限制文本最大行数 |
|  | select-on-gesture | boolean | true | 是 | 是否允许通过手势选择文本，关闭后通常可以结合 SelectionContext.selectRange 接口使用 |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | space | string |  | 否 | 显示连续空格 | [1.4.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | ensp | 中文字符空格一半大小 | | emsp | 中文字符空格大小 | | nbsp | 根据字体设置的空格大小 | | | | | | |
|  | decode | boolean | false | 否 | 是否解码 | [1.4.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: decode可以解析的有 `&nbsp;` `&lt;` `&gt;` `&amp;` `&apos;` `&ensp;` `&emsp;`
2. `tip`: 各个操作系统的空格标准并不一致。
3. `tip`:[text](text.html) 组件内只支持 [text](text.html) 嵌套。
4. `tip`: 除了文本节点以外的其他节点都无法长按选中。
5. `bug`: 基础库版本低于 `2.1.0` 时， [text](text.html) 组件内嵌的 [text](text.html) style 设置可能不会生效。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/LQxYkQmm7fJj "在开发者工具中预览效果")

Incorrect translation.