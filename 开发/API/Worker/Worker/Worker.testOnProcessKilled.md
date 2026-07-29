# [#](#Worker-testOnProcessKilled) Worker.testOnProcessKilled()

> 基础库 2.27.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

用于模拟 iOS ExperimentalWorker 线程被系统回收事件，以便于调试。接口仅在 worker 线程内可用。参考 [Worker.onProcessKilled](Worker.onProcessKilled.html)

## [#](#示例代码) 示例代码

```
// game.js
const worker = wx.createWorker('workers/index.js', {
  useExperimentalWorker: true
})

// 监听 ExperimentalWorker 被系统回收事件
worker.onProcessKilled(function () {
  console.log('worker has been killed')
  // 重新创建一个worker
  // wx.createWorker()
})
```

```
// workers/index.js
setTimeout(() => {
  // 模拟 ExperimentalWorker 线程被系统回收事件
  worker.testOnProcessKilled()
}, 2000)
```

Incorrect translation.