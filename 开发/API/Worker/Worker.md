# [#](#Worker) Worker

> 相关文档: [多线程 Worker](../../framework/workers.html)

Worker 实例，主线程中可通过 [wx.createWorker](wx.createWorker.html) 接口获取，worker 线程中可通过全局变量 `worker` 获取。

## [#](#属性) 属性

### [#](#Object-env) Object env

worker内的环境变量

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| USER\_DATA\_PATH | string | 文件系统中的用户目录路径 (本地路径) |

## [#](#方法) 方法

### [#](#Worker-postMessage-Object-message) [Worker.postMessage(Object message)](Worker.postMessage.html)

向主线程/Worker 线程发送的消息。

### [#](#Worker-terminate) [Worker.terminate()](Worker.terminate.html)

结束当前 Worker 线程。仅限在主线程 worker 对象上调用。

### [#](#Worker-testOnProcessKilled) [Worker.testOnProcessKilled()](Worker.testOnProcessKilled.html)

用于模拟 iOS ExperimentalWorker 线程被系统回收事件，以便于调试。接口仅在 worker 线程内可用。参考 [Worker.onProcessKilled](Worker.onProcessKilled.html)

### [#](#Worker-onMessage-function-listener) [Worker.onMessage(function listener)](./Worker.onMessage.html)

监听主线程/Worker 线程向当前线程发送的消息的事件。

### [#](#Worker-onError-function-listener) [Worker.onError(function listener)](./Worker.onError.html)

监听 Worker 线程错误事件。当 Worker 线程中发生脚本错误时会触发此事件。

### [#](#Worker-onProcessKilled-function-listener) [Worker.onProcessKilled(function listener)](./Worker.onProcessKilled.html)

监听 worker线程被系统回收事件（开启 useExperimentalWorker 后，当iOS系统资源紧张时，ExperimentalWorker 线程存在被系统回收的可能，开发者可监听此事件并重新创建一个worker）。仅限在主线程 worker 对象上调用。

## [#](#示例代码) 示例代码

运行以下代码需先进行基础配置，详细请查阅 [多线程 Worker](../../framework/workers.html) 文档了解基础知识和配置方法。

```
const worker = wx.createWorker('workers/request/index.js') // 文件名指定 worker 的入口文件路径，绝对路径

worker.onMessage(function (res) {
  console.log(res)
})
// 监听worker被系统回收事件
worker.onProcessKilled(function () {
  console.log('worker has been killed')
  // 重新创建一个worker
  // wx.createWorker()
})

worker.postMessage({
  msg: 'hello worker'
})

worker.terminate()
```

Incorrect translation.