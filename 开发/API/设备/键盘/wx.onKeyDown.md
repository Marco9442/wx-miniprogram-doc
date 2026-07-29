# [#](#wx-onKeyDown-function-listener) wx.onKeyDown(function listener)

> 基础库 3.6.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

监听小程序全局键盘按键按下事件。仅适用于 PC 平台

## [#](#参数) 参数

### [#](#function-listener) function listener

小程序全局键盘按键按下事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| key | string | 按键名称，同 Web 规范 KeyEvent key 属性 |
| code | string | 按键 code，同 Web 规范 KeyEvent code 属性 |
| altKey | string | 当前是否同时按下了 altKey，同 Web 规范 KeyEvent altKey 属性 |
| shiftKey | string | 当前是否同时按下了 shiftKey，同 Web 规范 KeyEvent shiftKey 属性 |
| timeStamp | number | 事件触发时的时间戳 |

## [#](#注意事项) 注意事项

1. 必须在小程序窗口处于前台且曾有过用户操作（例如点击等）后才会触发。
2. 如某个快捷键组合已经被系统定义（例如 alt+F4、全屏时按 esc 退出等），则会优先响应系统操作，是否发送此事件取决于系统规则。
3. 如当前焦点正聚焦在 `input`、`textarea`、`editor` 组件，则不会发送此事件。
4. 如当前焦点在 webview 组件中，则不会发送此事件。

Incorrect translation.