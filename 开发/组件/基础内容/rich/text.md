# [#](#rich-text) rich-text

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

富文本。

1. 自基础库 2.33.0 版本开始支持（3.0.0 除外）。
2. 遵循 skyline 的样式和布局规则，html tag 被映射成类似 text/span/view 节点，因此存在 text 嵌套问题。
3. 不支持 td/tr 等表格布局 tag，也不支持 bdo/bdi 等文字排版 tag。建议完全使用 flex 等 skyline 支持的布局方式来创建富文本内容。
4. 提供了可选的兼容布局模式选项 `mode`，但仍不保证与 WebView 表现 100% 一致。
5. 在 2.33.0 基础库下，请尽可能避免为 html tag 使用 wx-rich-text 开头的类名。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | nodes | array/string | [] | 否 | 节点列表/HTML String | [1.4.0](../framework/compatibility.html) |
|  | space | string |  | 否 | 显示连续空格 | [2.4.1](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | ensp | 中文字符空格一半大小 | | emsp | 中文字符空格大小 | | nbsp | 根据字体设置的空格大小 | | | | | | |
|  | user-select | boolean | false | 否 | 文本是否可选，该属性会使节点显示为 block | [2.24.0](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | mode | string | default | 否 | 布局兼容模式 |
|  | | 合法值 | 说明 | | --- | --- | | default | 完全遵循 skyline 的默认行为，不对节点树进行任何更改。 | | compat | 尽可能将 tag 映射为 `<view><span></span></view>` 的形式。通常最接近 webview 的表现。 | | aggressive | 所有 tag 均被映射为形如 `<view><span></span></view>` 的形式。 | | inline-block | 实验性的 inline-block 布局策略，但无法实现折行。 | | web | 使用 webview 渲染富文本，基础库 3.6.0 开始支持。 | | web-static | 使用 webview 截图的方式渲染富文本，基础库 3.7.7 开始支持。 | | | | | |

## [#](#nodes) nodes

现支持两种节点，通过type来区分，分别是元素节点和文本节点，默认是元素节点，在富文本区域里显示的HTML节点

### [#](#元素节点：type-node) 元素节点：type = node

| 属性 | 说明 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| name | 标签名 | string | 是 | 支持部分受信任的 HTML 节点 |
| attrs | 属性 | object | 否 | 支持部分受信任的属性，遵循 Pascal 命名法 |
| children | 子节点列表 | array | 否 | 结构和 nodes 一致 |

### [#](#文本节点：type-text) 文本节点：type = text

| 属性 | 说明 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| text | 文本 | string | 是 | 支持entities |

## [#](#受信任的HTML节点及属性) 受信任的HTML节点及属性

全局支持class和style属性，**不支持id属性**。

| 节点 | 属性 |
| --- | --- |
| a |  |
| abbr |  |
| address |  |
| article |  |
| aside |  |
| b |  |
| bdi |  |
| bdo | dir |
| big |  |
| blockquote |  |
| br |  |
| caption |  |
| center |  |
| cite |  |
| code |  |
| col | span，width |
| colgroup | span，width |
| dd |  |
| del |  |
| div |  |
| dl |  |
| dt |  |
| em |  |
| fieldset |  |
| font |  |
| footer |  |
| h1 |  |
| h2 |  |
| h3 |  |
| h4 |  |
| h5 |  |
| h6 |  |
| header |  |
| hr |  |
| i |  |
| img | alt，src，height，width |
| ins |  |
| label |  |
| legend |  |
| li |  |
| mark |  |
| nav |  |
| ol | start，type |
| p |  |
| pre |  |
| q |  |
| rt |  |
| ruby |  |
| s |  |
| section |  |
| small |  |
| span |  |
| strong |  |
| sub |  |
| sup |  |
| table | width |
| tbody |  |
| td | colspan，height，rowspan，width |
| tfoot |  |
| th | colspan，height，rowspan，width |
| thead |  |
| tr | colspan，height，rowspan，width |
| tt |  |
| u |  |
| ul |  |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: nodes 不推荐使用 String 类型，性能会有所下降。
2. `tip`: `rich-text` 组件内屏蔽所有节点的事件。
3. `tip`: attrs 属性不支持 id ，支持 class 。
4. `tip`: name 属性大小写不敏感。
5. `tip`: 如果使用了不受信任的HTML节点，该节点及其所有子节点将会被移除。
6. `tip`: img 标签仅支持网络图片。
7. `tip`: 如果在自定义组件中使用 `rich-text` 组件，那么仅自定义组件的 wxss 样式对 `rich-text` 中的 class 生效。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/zPVmpim46wYQ "在开发者工具中预览效果")

Incorrect translation.