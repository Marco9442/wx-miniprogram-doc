# [#](#editor) editor

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

富文本编辑器，可以对图片、文字进行编辑。

编辑器导出内容支持带标签的 `html`和纯文本的 `text`，编辑器内部采用 `delta` 格式进行存储。

通过`setContents`接口设置内容时，解析插入的 `html` 可能会由于一些非法标签导致解析错误，建议开发者在小程序内使用时通过 delta 进行插入。

富文本组件内部引入了一些基本的样式使得内容可以正确的展示，开发时可以进行覆盖。需要注意的是，在其它组件或环境中使用富文本组件导出的html时，需要额外引入 [这段样式](data:application/zip;base64,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)，并维护`<ql-container><ql-editor></ql-editor></ql-container>`的结构。

图片控件仅初始化时设置有效。

相关 api：[EditorContext](../api/media/editor/EditorContext.html)

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| read-only | boolean | false | 否 | 设置编辑器为只读 | [2.7.0](../framework/compatibility.html) |
| placeholder | string |  | 否 | 提示信息 | [2.7.0](../framework/compatibility.html) |
| show-img-size | boolean | false | 否 | 点击图片时显示图片大小控件 | [2.7.0](../framework/compatibility.html) |
| show-img-toolbar | boolean | false | 否 | 点击图片时显示工具栏控件 | [2.7.0](../framework/compatibility.html) |
| show-img-resize | boolean | false | 否 | 点击图片时显示修改尺寸控件 | [2.7.0](../framework/compatibility.html) |
| enable-formats | Array.<string> | 所有格式 | 否 | 编辑器允许的名单内的格式 | [3.2.2](../framework/compatibility.html) |
| enterkeyhint | string | enter | 否 | 定义虚拟键盘回车键的[操作标签](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes/enterkeyhint) | [3.7.11](../framework/compatibility.html) |
| confirm-hold | boolean | true | 否 | 点击键盘回车键时是否保持键盘不收起 | [3.7.11](../framework/compatibility.html) |
| bindready | eventhandle |  | 否 | 编辑器初始化完成时触发 | [2.7.0](../framework/compatibility.html) |
| bindfocus | eventhandle |  | 否 | 编辑器聚焦时触发，event.detail = {html, text, delta} | [2.7.0](../framework/compatibility.html) |
| bindblur | eventhandle |  | 否 | 编辑器失去焦点时触发，detail = {html, text, delta} | [2.7.0](../framework/compatibility.html) |
| bindinput | eventhandle |  | 否 | 编辑器内容改变时触发，detail = {html, text, delta} | [2.7.0](../framework/compatibility.html) |
| bindstatuschange | eventhandle |  | 否 | 通过 Context 方法改变编辑器内样式时触发，返回选区已设置的样式 | [2.7.0](../framework/compatibility.html) |

编辑器内支持部分 HTML 标签和内联样式，不支持**class**和**id**

## [#](#支持的标签) 支持的标签

不满足的标签会被忽略，`<div>`会被转行为`<p>`储存。

| 类型 | 节点 |
| --- | --- |
| 行内元素 | `<span> <strong> <b> <ins> <em> <i> <u> <a> <del> <s> <sub> <sup> <img>` |
| 块级元素 | `<p> <h1> <h2> <h3> <h4> <h5> <h6> <hr> <ol> <ul> <li>` |

## [#](#支持的内联样式) 支持的内联样式

内联样式仅能设置在行内元素或块级元素上，不能同时设置。例如 `font-size` 归类为行内元素属性，在 p 标签上设置是无效的。

| 类型 | 样式 |
| --- | --- |
| 块级样式 | `text-align` `direction` `margin` `margin-top` `margin-left` `margin-right` `margin-bottom`   `padding` `padding-top` `padding-left` `padding-right` `padding-bottom` `line-height` `text-indent` |
| 行内样式 | `font` `font-size` `font-style` `font-variant` `font-weight` `font-family`   `letter-spacing` `text-decoration` `color` `background-color` |

## [#](#enable-formats-属性列表) enable-formats 属性列表

可以通过该参数控制以下属性是否被禁用。请注意，不在以下名单内的格式将固定开启。

| name | version |
| --- | --- |
| bold | 3.2.2 |
| italic | 3.2.2 |
| underline | 3.2.2 |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 使用 catchtouchend 绑定事件则不会使编辑器失去焦点(2.8.3)
2. `tip`: 插入的 html 中事件绑定会被移除
3. `tip`: formats 中的 color 属性会统一以 hex 格式返回
4. `tip`: 粘贴时仅纯文本内容会被拷贝进编辑器
5. `tip`: 插入 html 到编辑器内时，编辑器会删除一些不必要的标签，以保证内容的统一。例如`<p><span>xxx</span></p>`会改写为`<p>xxx</p>`
6. `tip`: 编辑器聚焦时页面会被上推，系统行为以保证编辑区可见

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/W7uZ3EmU7jbl "在开发者工具中预览效果")

Incorrect translation.