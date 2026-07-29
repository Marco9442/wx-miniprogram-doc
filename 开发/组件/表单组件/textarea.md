# [#](#textarea) textarea

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

多行输入框。该组件是[原生组件](native-component.html)，使用时请注意相关限制。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | value | string |  | 否 | 输入框的内容 | [1.0.0](../framework/compatibility.html) |
|  | placeholder | string |  | 否 | 输入框为空时占位符 | [1.0.0](../framework/compatibility.html) |
|  | placeholder-style | string |  | 否 | 指定 placeholder 的样式，目前仅支持color,font-size,font-weight,line-height | [1.0.0](../framework/compatibility.html) |
|  | disabled | boolean | false | 否 | 是否禁用 | [1.0.0](../framework/compatibility.html) |
|  | maxlength | number | 140 | 否 | 最大输入长度，设置为 -1 的时候不限制最大长度 | [1.0.0](../framework/compatibility.html) |
|  | auto-focus | boolean | false | 否 | 自动聚焦，拉起键盘。 | [1.0.0](../framework/compatibility.html) |
|  | focus | boolean | false | 否 | 获取焦点 | [1.0.0](../framework/compatibility.html) |
|  | auto-height | boolean | false | 否 | 是否自动增高，设置auto-height时，style.height不生效 | [1.0.0](../framework/compatibility.html) |
|  | cursor-spacing | number | 0 | 否 | 指定光标与键盘的距离。取`textarea`距离底部的距离和`cursor-spacing`指定的距离的最小值作为光标与键盘的距离 | [1.0.0](../framework/compatibility.html) |
|  | cursor | number | -1 | 否 | 指定focus时的光标位置 | [1.5.0](../framework/compatibility.html) |
|  | selection-start | number | -1 | 否 | 光标起始位置，自动聚集时有效，需与`selection-end`搭配使用 | [1.9.0](../framework/compatibility.html) |
|  | selection-end | number | -1 | 否 | 光标结束位置，自动聚集时有效，需与`selection-start`搭配使用 | [1.9.0](../framework/compatibility.html) |
|  | adjust-position | boolean | true | 否 | 键盘弹起时，是否自动上推页面 | [1.9.90](../framework/compatibility.html) |
|  | hold-keyboard | boolean | false | 否 | focus时，点击页面的时候不收起键盘 | [2.8.2](../framework/compatibility.html) |
|  | disable-default-padding | boolean | false | 否 | 是否去掉 iOS 下的默认内边距 | [2.10.0](../framework/compatibility.html) |
|  | confirm-type | string | return | 否 | 设置键盘右下角按钮的文字 | [2.13.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | send | 右下角按钮为“发送” | | search | 右下角按钮为“搜索” | | next | 右下角按钮为“下一个” | | go | 右下角按钮为“前往” | | done | 右下角按钮为“完成” | | return | 右下角按钮为“换行” | | | | | | |
|  | confirm-hold | boolean | false | 否 | 点击键盘右下角按钮时是否保持键盘不收起 | [2.16.0](../framework/compatibility.html) |
|  | adjust-keyboard-to | boolean | cursor | 否 | 键盘对齐位置。 | [2.16.1](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | cursor | 对齐光标位置 | | bottom | 对齐输入框底部 | | | | | | |
|  | bindfocus | eventhandle |  | 否 | 输入框聚焦时触发，event.detail = { value, height }，height 为键盘高度，在基础库 1.9.90 起支持 | [1.0.0](../framework/compatibility.html) |
|  | bindblur | eventhandle |  | 否 | 输入框失去焦点时触发，event.detail = {value, cursor} | [1.0.0](../framework/compatibility.html) |
|  | bindlinechange | eventhandle |  | 否 | 输入框行数变化时调用，event.detail = {height: 0, heightRpx: 0, lineCount: 0} | [1.0.0](../framework/compatibility.html) |
|  | bindinput | eventhandle |  | 否 | 当键盘输入时，触发 input 事件，event.detail = {value, cursor, keyCode}，keyCode 为键值，目前工具还不支持返回keyCode参数。\*\*bindinput 处理函数的返回值并不会反映到 textarea 上\*\* | [1.0.0](../framework/compatibility.html) |
|  | bindconfirm | eventhandle |  | 否 | 点击完成时， 触发 confirm 事件，event.detail = {value: value} | [1.0.0](../framework/compatibility.html) |
|  | bindkeyboardheightchange | eventhandle |  | 否 | 键盘高度发生变化的时候触发此事件，event.detail = {height: height, duration: duration} | [2.7.0](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | placeholder-style | string |  | 否 | 需传入对象，格式为 `{ fontSize: number, fontWeight: string, color: string }` |  |
|  | bind:selectionchange | eventhandle |  | 否 | 选区改变事件, {selectionStart, selectionEnd} | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionstart | eventhandle |  | 否 | 输入法开始新的输入时触发 （仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionupdate | eventhandle |  | 否 | 输入法输入字符时触发（仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |
|  | bind:keyboardcompositionend | eventhandle |  | 否 | 输入法输入结束时触发（仅当输入法支持时触发） | [3.2.0](../framework/compatibility.html) |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | placeholder-class | string | textarea-placeholder | 否 | 指定 placeholder 的样式类，目前仅支持color,font-size和font-weight | [1.0.0](../framework/compatibility.html) |
|  | fixed | boolean | false | 否 | 如果 textarea 是在一个 `position:fixed` 的区域，需要显示指定属性 fixed 为 true | [1.0.0](../framework/compatibility.html) |
|  | show-confirm-bar | boolean | true | 否 | 是否显示键盘上方带有”完成“按钮那一栏 | [1.6.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: `textarea` 的 `blur` 事件会晚于页面上的 `tap` 事件，如果需要在 `button` 的点击事件获取 `textarea`，可以使用 `form` 的 `bindsubmit`。
2. `tip`: 不建议在多行文本上对用户的输入进行修改，所以 `textarea` 的 `bindinput` 处理函数并不会将返回值反映到 `textarea` 上。
3. `tip` : 键盘高度发生变化，keyboardheightchange事件可能会多次触发，开发者对于相同的height值应该忽略掉
4. `bug`: 微信版本 `6.3.30`，`textarea` 在列表渲染时，新增加的 `textarea` 在自动聚焦时的位置计算错误。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/QAwRn6m86tYu "在开发者工具中预览效果")

```
<view class="section">
  <textarea bindblur="bindTextAreaBlur" auto-height placeholder="自动变高" />
</view>
<view class="section">
  <textarea placeholder="placeholder颜色是红色的" placeholder-style="color:red;"  />
</view>
<view class="section">
  <textarea placeholder="这是一个可以自动聚焦的textarea" auto-focus />
</view>
<view class="section">
  <textarea placeholder="这个只有在按钮点击的时候才聚焦" focus="{{focus}}" />
  <view class="btn-area">
    <button bindtap="bindButtonTap">使得输入框获取焦点</button>
  </view>
</view>
<view class="section">
  <form bindsubmit="bindFormSubmit">
    <textarea placeholder="form 中的 textarea" name="textarea"/>
    <button form-type="submit"> 提交 </button>
  </form>
</view>
```

```
//textarea.js
Page({
  data: {
    height: 20,
    focus: false
  },
  bindButtonTap: function() {
    this.setData({
      focus: true
    })
  },
  bindTextAreaBlur: function(e) {
    console.log(e.detail.value)
  },
  bindFormSubmit: function(e) {
    console.log(e.detail.value.textarea)
  }
})
```

Incorrect translation.