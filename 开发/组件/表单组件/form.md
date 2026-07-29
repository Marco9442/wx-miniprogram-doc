# [#](#form) form

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [聊天工具模式](../framework/open-ability/chatTool.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

表单。将组件内的用户输入的[switch](switch.html) [input](input.html) [checkbox](checkbox.html) [slider](slider.html) [radio](radio.html) [picker](picker.html) 提交。

当点击 [form](form.html) 表单中 form-type 为 submit 的 [button](button.html) 组件时，会将表单组件中的 value 值进行提交，需要在表单组件中加上 name 来作为 key。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| report-submit | boolean | false | 否 | 是否返回 formId 用于发送[模板消息](../framework/open-ability/template-message.html) | [1.0.0](../framework/compatibility.html) |
| report-submit-timeout | number | 0 | 否 | 等待一段时间（毫秒数）以确认 formId 是否生效。如果未指定这个参数，formId 有很小的概率是无效的（如遇到网络失败的情况）。指定这个参数将可以检测 formId 是否有效，以这个参数的时间作为这项检测的超时时间。如果失败，将返回 requestFormId:fail 开头的 formId | [2.6.2](../framework/compatibility.html) |
| bindsubmit | eventhandle |  | 否 | 携带 form 中的数据触发 submit 事件，event.detail = {value : {'name': 'value'} , formId: ''} | [1.0.0](../framework/compatibility.html) |
| bindreset | eventhandle |  | 否 | 表单重置时会触发 reset 事件 | [1.0.0](../framework/compatibility.html) |
| bindsubmitToGroup | eventhandle |  | 否 | 用户发送文本到聊天后触发，但不代表最终发送成功 | [3.7.8](../framework/compatibility.html) |

## [#](#发送文本到群示例代码) 发送文本到群示例代码

需结合 [button](button.html) 和 [textarea](textarea.html) 组件使用。
[button](button.html) 需要设置 `form-type="submitToGroup"`，此时点击按钮将会发送 [textarea](textarea.html) 的内容到聊天。

```
<form bind:submitToGroup="onSubmitToGroup">
	<textarea value="{{shareText}}" />
	<button
    form-type="submitToGroup"
    need-show-entrance="{{true}}"
    entrance-path=""
	></button>
</form>
```

## [#](#示例代码) 示例代码

// [在开发者工具中预览效果](https://developers.weixin.qq.com/s/MUaz7cmy6AYq "在开发者工具中预览效果")

## [#](#使用内置-behaviors) 使用内置 behaviors

对于 form 组件，目前可以自动识别下列内置 behaviors:

wx://form-field

wx://form-field-group

wx://form-field-button

### [#](#wx-form-field) wx://form-field

使自定义组件有类似于表单控件的行为。
form 组件可以识别这些自定义组件，并在 submit 事件中返回组件的字段名及其对应字段值。这将为它添加以下两个属性。

| 属性名 | 类型 | 描述 | 最低版本 |
| --- | --- | --- | --- |
| name | String | 在表单中的字段名 | [1.6.7](../framework/compatibility.html) |
| value | 任意 | 在表单中的字段值 | [1.6.7](../framework/compatibility.html) |

代码示例：
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/3FjTHCmY7ghg "在开发者工具中预览效果")

```
// custom-form-field.js
Component({
 behaviors: ['wx://form-field'],
 data: {
   value: ''
 },
 methods: {
   onChange: function (e) {
     this.setData({
       value: e.detail.value,
     })
   }
 }
})
```

### [#](#wx-form-field-group) wx://form-field-group

从基础库版本 [2.10.2](../framework/compatibility.html) 开始提供支持。

代码示例：
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/G4mBEDms7chC "在开发者工具中预览效果")

使 form 组件可以识别到这个自定义组件内部的所有表单控件。
例如，页面的结构如下：

```
<form bindsubmit="submit">
  <custom-comp></custom-comp>
  <button form-type="submit">submit</button>
</form>
```

组件 `custom-comp` 自身结构如下：

```
<input name="name" />
<switch name="student" />
```

如果组件 `custom-comp` 配置有：

```
Component({
 behaviors: ['wx://form-field-group']
})
```

此时，表单的 `submit` 事件的 `value` 中将包含 `name` 和 `student` 两个字段。

### [#](#wx-form-field-button) wx://form-field-button

从基础库版本 [2.10.3](../framework/compatibility.html) 开始提供支持。

代码示例：
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/HSmT1Dmz7Phx "在开发者工具中预览效果")

使 form 组件可以识别到这个自定义组件内部的 button ，
如果自定义组件内部有设置了 form-type 的 button ，它将被组件外的 form 接受。
例如，页面的结构如下：

```
<form bindsubmit="submit">
  <input name="name" placeholder="请输入名字"></input>
  <custom-comp></custom-comp>
</form>
```

组件 `custom-comp` 自身结构如下：

```
<button form-type="submit">submit</button>
```

如果组件 `custom-comp` 配置有：

```
Component({
 behaviors: ['wx://form-field-button']
})
```

此时点击组件内的 button ，将触发 form 的 submit 事件。

Incorrect translation.