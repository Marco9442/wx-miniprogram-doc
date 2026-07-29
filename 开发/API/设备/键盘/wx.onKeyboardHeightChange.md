# [#](#wx-onKeyboardHeightChange-function-listener) wx.onKeyboardHeightChange(function listener)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听键盘高度变化事件

## [#](#参数) 参数

### [#](#function-listener) function listener

键盘高度变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| height | number | 键盘高度 |

## [#](#示例代码) 示例代码

```
wx.onKeyboardHeightChange(res => {
  console.log(res.height)
})
```

Incorrect translation.