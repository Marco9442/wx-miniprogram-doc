# [#](#input) input

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

输入框。该组件是[原生组件](native-component.html)，使用时请注意相关限制

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | value | string |  | 是 | 输入框的初始内容 | [1.0.0](../framework/compatibility.html) |
|  | type | string | text | 否 | input 的类型 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | text | 文本输入键盘 |  | | number | 数字输入键盘 |  | | idcard | 身份证输入键盘 |  | | digit | 带小数点的数字键盘 |  | | safe-password | 密码安全输入键盘 [指引](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/safe-password.html)。仅 Webview 支持。 | [2.18.0](../framework/compatibility.html) | | nickname | 昵称输入键盘。 | [2.21.2](../framework/compatibility.html) | | | | | | |
|  | password | boolean | false | 否 | 是否是密码类型 | [1.0.0](../framework/compatibility.html) |
|  | placeholder | string |  | 是 | 输入框为空时占位符 | [1.0.0](../framework/compatibility.html) |
|  | placeholder-style | string |  | 是 | 指定 placeholder 的样式 | [1.0.0](../framework/compatibility.html) |
|  | disabled | boolean | false | 否 | 是否禁用 | [1.0.0](../framework/compatibility.html) |
|  | maxlength | number | 140 | 否 | 最大输入长度，设置为 -1 的时候不限制最大长度 | [1.0.0](../framework/compatibility.html) |
|  | cursor-spacing | number | 0 | 否 | 指定光标与键盘的距离，取 input 距离底部的距离和 cursor-spacing 指定的距离的最小值作为光标与键盘的距离 | [1.0.0](../framework/compatibility.html) |
|  | auto-focus | boolean | false | 否 | (即将废弃，请直接使用 focus )自动聚焦，拉起键盘 | [1.0.0](../framework/compatibility.html) |
|  | focus | boolean | false | 否 | 获取焦点 | [1.0.0](../framework/compatibility.html) |
|  | confirm-type | string | done | 否 | 设置键盘右下角按钮的文字，仅在type='text'时生效 | [1.1.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | send | 右下角按钮为“发送” | | search | 右下角按钮为“搜索” | | next | 右下角按钮为“下一个” | | go | 右下角按钮为“前往” | | done | 右下角按钮为“完成” | | | | | | |
|  | always-embed | boolean | false | 否 | 强制 input 处于同层状态，默认 focus 时 input 会切到非同层状态 (仅在 iOS 下生效) | [2.10.4](../framework/compatibility.html) |
|  | confirm-hold | boolean | false | 否 | 点击键盘右下角按钮时是否保持键盘不收起 | [1.1.0](../framework/compatibility.html) |
|  | cursor | number |  | 是 | 指定focus时的光标位置 | [1.5.0](../framework/compatibility.html) |
|  | cursor-color | string |  | 是 | 光标颜色。iOS 下的格式为十六进制颜色值 #000000，安卓下的只支持 default 和 green，Skyline 下无限制 | [3.1.0](../framework/compatibility.html) |
|  | selection-start | number | -1 | 否 | 光标起始位置，自动聚集时有效，需与selection-end搭配使用 | [1.9.0](../framework/compatibility.html) |
|  | selection-end | number | -1 | 否 | 光标结束位置，自动聚集时有效，需与selection-start搭配使用 | [1.9.0](../framework/compatibility.html) |
|  | adjust-position | boolean | true | 否 | 键盘弹起时，是否自动上推页面 | [1.9.90](../framework/compatibility.html) |
|  | hold-keyboard | boolean | false | 否 | focus时，点击页面的时候不收起键盘 | [2.8.2](../framework/compatibility.html) |
|  | safe-password-cert-path | string |  | 否 | 安全键盘加密公钥的路径，只支持包内路径。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | safe-password-length | number |  | 否 | 安全键盘输入密码长度。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | safe-password-time-stamp | number |  | 否 | 安全键盘加密时间戳。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | safe-password-nonce | string |  | 否 | 安全键盘加密盐值。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | safe-password-salt | string |  | 否 | 安全键盘计算hash盐值，若指定custom-hash 则无效。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | safe-password-custom-hash | string |  | 否 | 安全键盘计算hash的算法表达式，如 `md5(sha1('foo' + sha256(sm3(password + 'bar'))))`。鸿蒙 OS 暂不支持 | [2.18.0](../framework/compatibility.html) |
|  | bindinput | eventhandle |  | 是 | 键盘输入时或内容改变时触发。event.detail = { value: string, cursor?: number, keyCode?: number }，cursor 为光标位置，keyCode 为键值。2.1.0 起支持，处理函数可以直接 return 一个字符串，将替换输入框的内容。 | [1.0.0](../framework/compatibility.html) |
|  | bindchange | eventhandle |  | 是 | 键盘非聚焦状态内容改变时触发。event.detail = { value: string } | [1.0.0](../framework/compatibility.html) |
|  | bindfocus | eventhandle |  | 是 | 输入框聚焦时触发，event.detail = { value: string, height: number }，height 为键盘高度，在基础库 1.9.90 起支持 | [1.0.0](../framework/compatibility.html) |
|  | bindblur | eventhandle |  | 是 | 输入框失去焦点时触发，event.detail = { value: string, encryptedValue?: string, encryptError?: string } | [1.0.0](../framework/compatibility.html) |
|  | bindconfirm | eventhandle |  | 是 | 点击完成按钮时触发，event.detail = { value: string, encryptedValue?: string, encryptError?: string } | [1.0.0](../framework/compatibility.html) |
|  | bindkeyboardheightchange | eventhandle |  | 是 | 键盘高度发生变化的时候触发此事件，event.detail = {height: number, duration: number} | [2.7.0](../framework/compatibility.html) |
|  | bindnicknamereview | eventhandle |  | 是 | 用户昵称审核完毕后触发，仅在 type 为 "nickname" 时有效，event.detail = { pass: boolean, timeout: boolean } | [2.29.1](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | bind:selectionchange | eventhandle |  | 否 | 选区改变事件, {selectionStart, selectionEnd} | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionstart | eventhandle |  | 否 | 输入法开始新的输入时触发 （仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionupdate | eventhandle |  | 否 | 输入法输入字符时触发（仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionend | eventhandle |  | 否 | 输入法输入结束时触发（仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |
|  | worklet:onkeyboardheightchange | worklet |  | 否 | 键盘高度变化时触发。event.detail = {height: height, pageBottomPadding: pageBottomPadding}； height: 键盘高度，pageBottomPadding: 页面上推高度 | [3.2.4](../framework/compatibility.html) |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | placeholder-class | string | input-placeholder | 否 | 指定 placeholder 的样式类 | [1.0.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: confirm-type的最终表现与手机输入法本身的实现有关，部分安卓系统输入法和第三方输入法可能不支持或不完全支持
2. `tip` : input 组件是一个原生组件，字体是系统字体，所以无法设置 font-family
3. `tip` : 在 input 聚焦期间，避免使用 css 动画
4. `tip` : 对于将 `input` 封装在自定义组件中、而 `form` 在自定义组件外的情况， `form` 将不能获得这个自定义组件中 `input` 的值。此时需要使用自定义组件的 [内置 behaviors](../framework/custom-component/behaviors.html) `wx://form-field`
5. `tip` : 键盘高度发生变化，keyboardheightchange事件可能会多次触发，开发者对于相同的height值应该忽略掉
6. `bug` : 微信版本 `6.3.30`, focus 属性设置无效
7. `bug` : 微信版本 `6.3.30`, placeholder 在聚焦时出现重影问题

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/Is4OlSm27MJe "在开发者工具中预览效果")

Incorrect translation.