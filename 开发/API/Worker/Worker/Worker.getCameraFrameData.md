# [#](#ArrayBuffer-Worker-getCameraFrameData) ArrayBuffer Worker.getCameraFrameData()

> 基础库 2.25.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

获取摄像头当前帧图像，返回ArrayBuffer数据。仅限在 worker 线程中使用。

## [#](#返回值) 返回值

### [#](#ArrayBuffer) ArrayBuffer

摄像头帧数据

## [#](#注意事项) 注意事项

- 接口仅在 iOS 上可用
- 接口仅在 worker 线程中可用
- 接口仅在 useExperimentalWorker 为 true 时可用
- 使用前需要先在主线程调用 CameraFrameListener.start({ worker })
- 该接口的目的是借助 iOS ExperimentalWorker 的JS高运行性能，配合摄像头帧数据实现 AR 等场景
- 由于安卓主线程本身已经支持JIT，因此安卓上可以直接在主线程使用 CameraContext.onCameraFrame 接口实现 AR 等场景

## [#](#示例代码) 示例代码

```
// app.js
const worker = wx.createWorker('workers/index.js', {
  useExperimentalWorker: true
})

const cameraContext = wx.createCameraContext()
const cameraFrameListener = cameraContext.onCameraFrame(function() {})
cameraFrameListener.start({
  worker: worker
})
```

```
// workers/index.js
const data = worker.getCameraFrameData()
console.log(data)
```

Incorrect translation.