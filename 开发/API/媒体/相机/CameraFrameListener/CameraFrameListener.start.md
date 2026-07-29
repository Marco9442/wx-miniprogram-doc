# [#](#CameraFrameListener-start-Object-object) CameraFrameListener.start(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

> 相关文档: [camera 组件介绍](../../../component/camera.html)

## [#](#功能描述) 功能描述

开始监听帧数据

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| worker | [Worker](../../worker/Worker.html) |  | 否 | 可选参数。如果需要在 iOS ExperimentalWorker 内监听摄像头帧数据，则需要传入对应 Worker 对象。详情 [Worker.getCameraFrameData](../../worker/Worker.getCameraFrameData.html) | [2.25.1](../../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

Incorrect translation.