# [#](#Worker-postMessage-Object-message) Worker.postMessage(Object message)

> **小程序插件**：不支持

> 相关文档: [多线程 Worker](../../framework/workers.html)

## [#](#功能描述) 功能描述

向主线程/Worker 线程发送的消息。

## [#](#参数) 参数

### [#](#Object-message) Object message

需要发送的消息。

## [#](#示例代码) 示例代码

worker 线程中

```
worker.postMessage({
  msg: 'hello from worker'
})
```

主线程中

```
const worker = wx.createWorker('workers/request/index.js')

worker.postMessage({
  msg: 'hello from main'
})
```

## [#](#提醒) 提醒

在基础库版本2.20.2之前，postMessage仅支持传递可序列化的key-value对象。
在基础库2.20.2之后，postMessage支持传递任意类型的数据。

Incorrect translation.