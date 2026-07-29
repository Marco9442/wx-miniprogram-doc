# [#](#VKSession) VKSession

> 基础库 2.20.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

vision kit 会话对象。

## [#](#属性) 属性

### [#](#number-state) number state

会话状态

**state 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 0 | 不可用 |  |
| 1 | 运行中 |  |
| 2 | 暂停中 |  |
| 3 | 初始化中 | [2.29.0](../../../framework/compatibility.html) |

### [#](#Object-config) Object config

会话配置

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | version | string | vision kit 版本。 | [2.22.0](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | v1 | v1适用于用户在平面场景下，例如桌面，地面，泛平面场景，放置虚拟物体，不提供真实世界距离。用户放置物体时，手机相机倾斜向下对着目标平面点击即可，具有广泛的机型支持 | | v2 | v2提供真实物理距离的 ar 定位功能，提供平面识别功能，用户在平面范围点击放置虚拟物体的功能，具有[有限的机型支持](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/plane.html#%E9%99%84%E5%BD%95)。iOS 设备在基础库 2.22.0 开始支持v2。安卓设备在基础库 2.25.1 开始支持v2，另外，安卓v2不支持竖直平面。\*\*使用v2算法需要初始化，移动手机进行左右平移初始化效果最佳。\*\* | | | | |
|  | track | Object | 跟踪能力配置，目前不同的跟踪能力之间是互斥的，默认使用平面跟踪能力。需要注意目前 track 中不同的跟踪配置存在互斥关系（比如 marker 跟踪配置和 OSD 跟踪配置不能同时存在），请按需配置。 |  |
|  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | plane | Object | 平面跟踪配置 |  | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 平面跟踪配置模式 |  | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 检测横向平面 |  | | 2 | 检测纵向平面，只有 v2 版本支持 | [2.22.0](../../../framework/compatibility.html) | | 3 | 检测横向和纵向平面，只有 v2 版本支持 | [2.22.0](../../../framework/compatibility.html) | | | | | |  | force | boolean | 是否开启强制使用V2的模式，只有 v2 版本支持 | [3.6.5](../../../framework/compatibility.html) | | | | | |  | marker | boolean | marker 跟踪配置，基础库(3.0.0)开始允许同时支持v2的水平面检测能力 | [2.24.5](../../../framework/compatibility.html) | |  | OSD | boolean | OSD 跟踪配置 | [2.24.5](../../../framework/compatibility.html) | |  | depth | Object | 深度识别配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/depth.html)。 | [3.0.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 深度识别模式 | [3.0.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [3.0.0](../../../framework/compatibility.html) | | 2 | 静态图片检测 | [3.0.0](../../../framework/compatibility.html) | | | | | | | | | |  | face | Object | 人脸检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/face.html)。安卓微信8.0.25开始支持，iOS微信8.0.24开始支持。 | [2.25.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 人脸检测模式 | [2.25.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [2.25.0](../../../framework/compatibility.html) | | 2 | 静态图片检测 | [2.25.0](../../../framework/compatibility.html) | | | | | | | | | |  | OCR | Object | OCR检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/ocr.html)。 | [2.27.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | OCR检测模式 | [2.27.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [2.27.0](../../../framework/compatibility.html) | | 2 | 静态图片检测 | [2.27.0](../../../framework/compatibility.html) | | | | | | | | | |  | IDCard | Object | 身份证检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/idcard.html)。 | [3.3.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 身份证检测模式 | [3.3.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 2 | 静态图片检测 | [3.3.0](../../../framework/compatibility.html) | | | | | | | | | |  | body | Object | 人体检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/body.html)。 | [2.28.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 人体检测模式 | [2.28.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [2.28.0](../../../framework/compatibility.html) | | 2 | 静态图片检测 | [2.28.0](../../../framework/compatibility.html) | | | | | | | | | |  | hand | Object | 手势检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/hand.html)。 | [2.28.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 手势检测模式 | [2.28.0](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [2.28.0](../../../framework/compatibility.html) | | 2 | 静态图片检测 | [2.28.0](../../../framework/compatibility.html) | | | | | | | | | |  | shoe | Object | 鞋部检测配置。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/shoe.html)。 | [3.2.1](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | mode | number | 鞋部检测模式 | [3.2.1](../../../framework/compatibility.html) | |  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | 1 | 通过摄像头实时检测 | [3.2.1](../../../framework/compatibility.html) | | | | | | | | | |  | threeDof | boolean | 提供基础AR功能，输出相机旋转的3个自由度的位姿，利用手机陀螺仪传感器，实现快速稳定的AR定位能力，适用于简单AR场景。 | [2.28.0](../../../framework/compatibility.html) | | | | |
|  | gl | WebGLRenderingContext | 绑定的 WebGLRenderingContext 对象 | [2.23.0](../../../framework/compatibility.html) |

### [#](#Object-cameraSize) Object cameraSize

相机尺寸

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度 |
| height | number | 高度 |

## [#](#方法) 方法

### [#](#VKSession-start-VKSessionStartCallback-callback) [VKSession.start(VKSessionStartCallback callback)](VKSession.start.html)

开启会话。

### [#](#VKSession-stop) [VKSession.stop()](VKSession.stop.html)

停止会话。

### [#](#VKSession-destroy) [VKSession.destroy()](VKSession.destroy.html)

销毁会话。

### [#](#number-VKSession-requestAnimationFrame-function-callback) [number VKSession.requestAnimationFrame(function callback)](VKSession.requestAnimationFrame.html)

在下次进行重绘时执行。

### [#](#VKSession-cancelAnimationFrame-number-requestID) [VKSession.cancelAnimationFrame(number requestID)](VKSession.cancelAnimationFrame.html)

取消由 requestAnimationFrame 添加到计划中的动画帧请求。

### [#](#VKFrame-VKSession-getVKFrame-number-width-number-height) [VKFrame VKSession.getVKFrame(number width, number height)](VKSession.getVKFrame.html)

获取帧对象，每调用一次都会触发一次帧分析过程。目前 VKSession 相机的最大帧数是 30 fps，因此调用 getVKFrame 的频率也可以限制在 30 fps，以减少渲染开销。

### [#](#Array-HitTestRes-VKSession-hitTest-number-x-number-y-Object-reset) [Array.<HitTestRes> VKSession.hitTest(number x, number y, Object reset)](VKSession.hitTest.html)

触摸检测，v1 版本只支持单平面（即 hitTest 生成一次平面后，后续 hitTest 均不会再生成平面，而是以之前生成的平面为基础进行检测）。如果需要重新识别其他平面，可以在调用此方法时将 reset 参数置为 true。

### [#](#number-VKSession-addMarker-string-path) [number VKSession.addMarker(string path)](VKSession.addMarker.html)

添加一个 marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.marker 为 true

### [#](#VKSession-removeMarker-number-markerId) [VKSession.removeMarker(number markerId)](VKSession.removeMarker.html)

删除一个 marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.marker 为 true

### [#](#Array-VKMarker-VKSession-getAllMarker) [Array.<VKMarker> VKSession.getAllMarker()](VKSession.getAllMarker.html)

获取所有 marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.marker 为 true

### [#](#number-VKSession-addOSDMarker-string-path) [number VKSession.addOSDMarker(string path)](VKSession.addOSDMarker.html)

添加一个 OSD marker（one-shot detection marker），要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.OSD 为 true

### [#](#VKSession-removeOSDMarker-number-markerId) [VKSession.removeOSDMarker(number markerId)](VKSession.removeOSDMarker.html)

删除一个 OSD marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.OSD 为 true

### [#](#Array-VKMarker-VKSession-getAllOSDMarker) [Array.<VKMarker> VKSession.getAllOSDMarker()](VKSession.getAllOSDMarker.html)

获取所有 OSD marker，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.OSD 为 true

### [#](#VKSession-update3DMode-Object-object) [VKSession.update3DMode(Object object)](VKSession.update3DMode.html)

更新三维识别相关配置，要求调 [wx.createVKSession](wx.createVKSession.html) 时使用 face / hand / body。

### [#](#VKSession-updateMaskMode-Object-object) [VKSession.updateMaskMode(Object object)](VKSession.updateMaskMode.html)

设置裁剪相关配置，要求调 [wx.createVKSession](wx.createVKSession.html) 时使用 shoe。

### [#](#VKSession-updateOSDThreshold-number-threshold) [VKSession.updateOSDThreshold(number threshold)](VKSession.updateOSDThreshold.html)

更新 OSD 识别精确度，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入的 track.OSD 为 true

### [#](#VKSession-setDepthOccRange-number-threshold) [VKSession.setDepthOccRange(number threshold)](VKSession.setDepthOccRange.html)

更新 深度遮挡 Occ范围，要求调 [wx.createVKSession](wx.createVKSession.html) 时传入 {track: {depth: {mode: 2} } }

### [#](#VKSession-detectFace-Object-object) [VKSession.detectFace(Object object)](VKSession.detectFace.html)

静态图像人脸关键点检测。当 wx.createVKSession 参数传入 {track: {face: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/face.html)。安卓微信8.0.25开始支持，iOS微信8.0.24开始支持。

### [#](#VKSession-detectBody-Object-object) [VKSession.detectBody(Object object)](VKSession.detectBody.html)

静态图像人体关键点检测。当 wx.createVKSession 参数传入 {track: {body: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/body.html)。

### [#](#VKSession-detectHand-Object-object) [VKSession.detectHand(Object object)](VKSession.detectHand.html)

静态图像手势关键点检测。当 wx.createVKSession 参数传入 {track: {hand: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/hand.html)。

### [#](#VKSession-detectDepth-Object-object) [VKSession.detectDepth(Object object)](VKSession.detectDepth.html)

深度识别。当 wx.createVKSession 参数传入 {track: {depth: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/depth.html)。

### [#](#VKSession-runOCR-Object-object) [VKSession.runOCR(Object object)](VKSession.runOCR.html)

静态图像OCR检测。当 wx.createVKSession 参数传入 {track: {OCR: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/ocr.html)。

### [#](#VKSession-on-string-eventName-function-fn) [VKSession.on(string eventName, function fn)](VKSession.on.html)

监听会话事件。

### [#](#VKSession-off-string-eventName-function-fn) [VKSession.off(string eventName, function fn)](VKSession.off.html)

取消监听会话事件。

Incorrect translation.