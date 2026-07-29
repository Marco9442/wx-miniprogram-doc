# [#](#wx-onAfterPageUnload-function-listener) wx.onAfterPageUnload(function listener)

> 基础库 3.5.5 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [3.5.5](../../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听路由事件引起现有页面实例销毁时，页面实例销毁后的事件监听，详见 [页面路由监听](../../../../framework/app-service/route-event-listener.html)。

## [#](#参数) 参数

### [#](#function-listener) function listener

路由事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| path | string | 页面路径 |
| routeEventId | string | 路由事件 id |

## [#](#示例代码) 示例代码

```
const func = function (res) {
  console.log(res)
}
wx.onAfterPageUnload(func)
// 取消监听
wx.offAfterPageUnload(func)
```

Incorrect translation.