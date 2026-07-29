# [#](#wx-onAppRoute-function-listener) wx.onAppRoute(function listener)

> 基础库 3.5.5 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [3.5.5](../../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听路由事件下发后，执行路由逻辑后的事件监听，详见 [页面路由监听](../../../../framework/app-service/route-event-listener.html)。

## [#](#参数) 参数

### [#](#function-listener) function listener

路由事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | path | string | 页面路径 |
|  | query | Object | 路由参数 |
|  | renderer | string | 渲染引擎 |
|  | | 合法值 | 说明 | | --- | --- | | webview | Webview 渲染引擎 | | skyline | Skyline 渲染引擎 | | xr-frame | xr-frame 解决方案 | | | |
|  | openType | string | 路由打开类型 |
|  | webviewId | number | 当前页面 id |
|  | timeStamp | number | 路由下发的时间戳 |
|  | routeEventId | string | 路由事件 id |
|  | pipMode | string |  |
|  | | 合法值 | 说明 | | --- | --- | | min | 视频页面缩小为小窗 | | max | 视频小窗还原为页面 | | | |
|  | notFound | boolean | 是否未找到页面 |
|  | page | Object | 当前打开页面的相关配置 |

> Skyline 渲染引擎相关说明：[详情](../../../../framework/runtime/skyline/introduction.html)
> xr-frame 解决方案相关说明：[详情](errorframework/xr-frame))

## [#](#注意) 注意

在低于 3.5.5 版本的基础库中也存在此接口，但参数可能与当前文档不同，请注意。

## [#](#示例代码) 示例代码

```
const func = function (res) {
  console.log(res)
}
wx.onAppRoute(func)
// 取消监听
wx.offAppRoute(func)
```

Incorrect translation.