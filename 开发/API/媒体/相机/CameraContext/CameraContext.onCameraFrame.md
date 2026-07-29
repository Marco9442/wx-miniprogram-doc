# [#](#CameraFrameListener-CameraContext-onCameraFrame-function-callback) [CameraFrameListener](CameraFrameListener.html) CameraContext.onCameraFrame(function callback)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [camera 组件介绍](../../../component/camera.html)

## [#](#功能描述) 功能描述

获取 Camera 实时帧数据

## [#](#参数) 参数

### [#](#function-callback) function callback

回调函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 图像数据矩形的宽度 |
| height | number | 图像数据矩形的高度 |
| data | ArrayBuffer | 图像像素点数据，一维数组，每四项表示一个像素点的 rgba |

## [#](#返回值) 返回值

### [#](#CameraFrameListener) [CameraFrameListener](CameraFrameListener.html)

注： 使用该接口需同时在 [camera](../../../component/camera.html) 组件属性中指定 frame-size。

## [#](#示例代码) 示例代码

```
const context = wx.createCameraContext()
const listener = context.onCameraFrame((frame) => {
  console.log(frame.data instanceof ArrayBuffer, frame.width, frame.height)
})
listener.start()
```

Incorrect translation.