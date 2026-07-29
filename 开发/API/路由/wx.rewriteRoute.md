# [#](#wx-rewriteRoute-Object-object) wx.rewriteRoute(Object object)

> 基础库 3.8.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> 在小程序插件中使用时，只能重写目标为当前插件的页面的路由事件

## [#](#功能描述) 功能描述

重写正在进行中的路由事件，详见 [路由重写](../../framework/app-service/route-rewrite.html)

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string |  | 是 | 重写目标页面的路径 (代码包路径), 路径后可以带参数。参数与路径之间使用 `?` 分隔，参数键与参数值用 `=` 相连，不同参数用 `&` 分隔；如 `'path?key=value&key2=value2'` |
| preserveQuery | boolean | false | 否 | 是否直接保留当前路由事件的参数，默认为 `false`；开启时，`url` 里面传入的参数会被丢弃 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.onBeforeAppRoute(res => {
  if (res.path === '/pages/do/not/access/me') {
    wx.rewriteRoute({
      url: '/pages/index/index'
    })
  }
})
```

Incorrect translation.