# [#](#Worker-onError-function-listener) Worker.onError(function listener)

> **小程序插件**：不支持

> 相关文档: [多线程 Worker](../../framework/workers.html)

## [#](#功能描述) 功能描述

监听 Worker 线程错误事件。当 Worker 线程中发生脚本错误时会触发此事件。

## [#](#参数) 参数

### [#](#function-listener) function listener

Worker 线程错误事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| error | Object | 错误对象 |

## [#](#示例代码) 示例代码

```
const worker = wx.createWorker('workers/request/index.js')

worker.onError(function (error) {
  console.error('Worker 错误:', error)
})
```

Incorrect translation.