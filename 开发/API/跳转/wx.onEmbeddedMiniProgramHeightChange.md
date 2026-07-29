# [#](#wx-onEmbeddedMiniProgramHeightChange-function-listener) wx.onEmbeddedMiniProgramHeightChange(function listener)

> 基础库 2.33.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

监听半屏小程序可视高度变化事件

## [#](#参数) 参数

### [#](#function-listener) function listener

半屏小程序可视高度变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| height | number | 可视高度 |
| initialHeight | number | 半屏小程序初始高度 |

## [#](#示例代码) 示例代码

```
const func = function (res) {
  console.log(res.height)
  console.log(res.initialHeight)
}
wx.onEmbeddedMiniProgramHeightChange(func)
// 取消监听
wx.offEmbeddedMiniProgramHeightChange(func)
```

Incorrect translation.