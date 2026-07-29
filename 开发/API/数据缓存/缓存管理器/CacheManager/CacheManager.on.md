# [#](#CacheManager-on-string-eventName-function-handler) CacheManager.on(string eventName, function handler)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [弱网体验优化](../../../framework/performance/weak-network.html)

## [#](#功能描述) 功能描述

监听事件。

## [#](#参数) 参数

### [#](#string-eventName) string eventName

事件名

**eventName 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| request | 发生 wx.request 请求，只在缓存管理器开启阶段会触发 |  |
| enterWeakNetwork | 进入弱网/离线状态 |  |
| exitWeakNetwork | 离开弱网/离线状态 |  |

### [#](#function-handler) function handler

事件句柄

这里 request 事件会提供 request 事件对象，用于做后续的处理；在 request 事件中需要返回一个 promise，用来生成 wx.request 请求的返回内容。
这次 request 所返回的请求结果默认不会写入缓存中。如需写入缓存，可以传入参数 `request({ needUpdateCache: true })`

#### [#](#示例代码) 示例代码

```
async function handler(evt) {
  // evt.url - 请求 url
  // evt.data - 请求参数
  // evt.method - 请求方法
  // evt.request - 原始 request 方法，返回一个 promise

  // if (evt.url === '/xxx') {
  //   // 如果有些请求仍然希望走到网络，则可以如下处理
  //   const res = await evt.request()
  //   // res 即为网络请求返回
  // }

  return new Promsie((resolve, reject) => {
    // do sth
    if (data) {
      // 这里 resolve 的 data 就会作为 wx.request 的 success 回调结果返回
      resolve(data)
    } else {
      // 这里 reject 的错误信息就会作为 wx.request 的 fail 回调结果返回
      reject('no data')
    }
  })
}
cacheManager.on('request', handler)
```

Incorrect translation.