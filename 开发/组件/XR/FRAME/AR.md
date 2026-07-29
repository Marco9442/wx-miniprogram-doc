# [#](#AR系统) AR系统

AR系统 [ARSystem](/miniprogram/dev/api/xr-frame/classes/ARSystem) 将 **xr-frame** 和 [小程序AI系统 VisionKit](/miniprogram/dev/api/ai/visionkit/VKSession.html) 关联起来，让AR变得十分简单易用。

AR系统默认是关闭的，开启它需要在场景元素`Scene`上挂载`ARSystem`即可，以下是基础案例

```
<!-- 平面模式下，开启后置摄像头 -->
<xr-scene ar-system="modes:Plane;camera:Back">
</xr-scene>
```

ARSystem 支持以下几个属性，来决定AR系统的具体行为

### [#](#识别模式) 识别模式

`modes` 属性，决定AR系统使用的具体识别模式。大部分情况下只允许同时运行一种模式。

> 目前不支持 modes 模式的动态切换。如果需要切换，可以考虑销毁原AR组件后，新建其他AR模式组件实现

目前支持的单一模式：

1. 平面识别 `Plane`
2. 2DMarker / 3DMarker 识别 `Marker`
3. OSD识别 `OSD`
4. 人脸识别 `Face`
5. 肢体识别 `Body`
6. 手部识别 `Hand`

> 目前由于小程序AI系统限制，除了 Plane + Marker 模式外，**只能同时开启一种模式**！！！

目前支持的混合模式：

1. 平面结合Marker识别 `Plane Marker`

```
<!-- 目前版本 plane + marker 模式下 planeMode 需设置为 1 (只允许水平面识别) -->
<xr-scene ar-system="modes:Plane Marker; planeMode: 1"></xr-scene>
```

### [#](#摄像机朝向-camera) 摄像机朝向 camera

配置使用哪一个相机。

默认为后置`Back`，前置为`Front`。

> 前置相机依赖于客户端版本 **8.0.31**

### [#](#平面识别模式-planeMode) 平面识别模式 planeMode

在 `Plane` 模式，且支持 `v2` 的设备上，设定识别方式。

`1` 为水平面，`2` 为垂直面，`3` 为二者都识别。默认值为 `3` 二者都识别。

```
<!-- 平面模式下，只识别水平面 -->
<xr-scene ar-system="modes:Plane; planeMode: 1">
</xr-scene>
```

### [#](#深度遮挡) 深度遮挡

> Beta 版本特性 依赖基础库版本 **v3.1.0**

> 需要在 `Plane` 模式，且支持 `v2` 的设备上，planeMode 需设定为 `1`(只允许水平面识别)。

通过以下几个属性确定 ARsystem `深度遮挡`的具体表现

1. `depthMask` 在满足使用要求的情况下，是否开启实时深度遮挡。
2. `depthNear` 开启实时深度遮挡时，遮挡的近处阈值。
3. `depthFar` 开启实时深度遮挡时，遮挡的远处阈值。
4. `depthDebug` 开启实时深度遮挡时，显示一个用于Debug的图层。

案例代码片段 [链接](https://github.com/dtysky/xr-frame-demo/blob/master/miniprogram/components/xr-ar-vio-depth/index.wxml)

```
<!-- plane + depth 模式下 planeMode 需设置为 1 (只允许水平面识别) -->
<!-- 水平平面识别情况下，开启深度，近处阈值为0.1，远处阈值为1的深度遮挡，并显示调试用图层 -->
<xr-scene ar-system="modes:Plane; planeMode: 1; depthMask: true; depthNear: 0.1; depthFar: 100; depthDebug: true;">
</xr-scene>
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/11.mov)

## [#](#和相机协作) 和相机协作

在[相机](./../render/camera.html)一章中我们提到过其有两个数据需要和`ar-system`协作，下面就让我们详细论述。

### [#](#ARCamera) ARCamera

```
<xr-camera
  background="ar" is-ar-camera
/>
```

首先是`background`，当将其设置为`ar`时，整个场景的背景将显示为当前手机摄像头拍摄的画面。

然后是`isARCamera`，将开启它时，这个相机会被作为AR相机，在AR系统为`Plane`和`Marker`模式时，相机的参数将由AR系统控制，**请不要在脚本中自行修改相机属性**！！！

## [#](#AR场景事件) AR场景事件

```
<xr-scene bind:ready="handleReady" bind:ar-ready="handleARReady">
</xr-scene>
```

AR系统为场景元素提供了以下事件：

| 事件 | 参数 | 立即 | wxml | 时机 |
| --- | --- | --- | --- | --- |
| ar-ready | 无 | 是 | 是 | ar功能启动成功 |
| ar-error | 错误`error` | 是 | 是 | ar功能启动失败 |

## [#](#添加追踪器) 添加追踪器

开启了某种识别模式后，我们还需要使用对应的追踪器模块，才能完成识别和追踪，详见 [AR追踪器(ARTracker)](./tracker.html) 部分。

`ARTracker` 需包含场景中所需要放置的元素，会进行 VKSession 识别事件返回的 `Transform` 矩阵信息、以及 `部分模式特殊识别信息` 的同步。

## [#](#不同AR追踪器的坐标系差异) 不同AR追踪器的坐标系差异

在使用对应的 `识别模式` 与 `ARTracker`后， `xr-camera` 会完全由 VisionKit 的 `VKCamera` 完全接管相机的控制权（使用 VKCamera 的 ViewMatrix 与 ProjectionMatrix）。

此时，xr-frame 的坐标系，将会由 `VisionKit` 对应模式的坐标系决定。

以下，结合案例（红色轴为 x 轴、绿色轴为 y 轴、蓝色轴为 z 轴，都朝向`正方向`，`轴长为 2` ）

简要阐述不同模式的坐标系规则：

### [#](#Plane-模式) Plane 模式

平面模式下，初始化场景后，相机所在的坐标，就是`世界坐标的 (0, 0, 0)`，坐标轴会基于`初始化的手机朝向`，决定`坐标轴的方向`（正上方为+Y，正右方为+X，正后方为+Z）。

手机的移动和旋转，相机都会有对应的响应。

周围的具体坐标信息变化，是存在多种情况。

#### [#](#在支持-Plane-V2-模式下，会使用-Plane-V2-模式) 在支持 Plane V2 模式下，会使用 `Plane V2` 模式:

该模式下，类似现实世界的空间坐标，坐标系的单位距离和`现实中的物理距离有关`，单位1相当于现实中的1m。

该模式下，trakcer同步的识别平面坐标，会完全基于三维空间坐标进行定义。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-plane.f3e72eac.jpg)

#### [#](#在不支持-Plane-V2-模式下，会使用-Plane-V1-模式，) 在不支持 Plane V2 模式下，会使用 `Plane V1` 模式，

该模式下，类似一个可以无限延展的平面空间，可以移动，但坐标系的单位距离和`现实中的物理距离无关`。

具体 VisionKit 细节可以参考 [VisionKit Plane 文档](/miniprogram/dev/framework/open-ability/visionkit/plane.html)。

### [#](#ThreeDof-模式) ThreeDof 模式

初始化场景后，相机所在的坐标下方，就是`世界坐标的 (0, 0, 0)`。

该模式下，类似一个可以无限延展的平面空间，不可以移动，且坐标系的单位距离和`现实中的物理距离无关`。

手机移动过程中，相机在坐标系中的坐标不会发生改变，但会有旋转的响应。。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-threedof.9938f165.jpg)

### [#](#Marker-模式) Marker 模式

该模式下，识别点中心就是 `世界坐标的 (0, 0, 0)`，坐标轴会基于`识别物`，决定`坐标轴的方向`（识别图片往外为+Y，识别图片右方为+X，识别图片下方为+Z），单位1相当于识别物体的大小。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-marker.bd3666a9.jpg)

### [#](#OSD-模式) OSD 模式

该模式下，识别结果为二维。

识别点中心就是 `世界坐标的 (0, 0, 0)`，坐标轴会基于`识别物`，决定`坐标轴的方向`（识别图片往内为+Z，识别图片上方为+Y，识别图片向右为+X），单位1相当于识别物体的大小。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-osd.77760e1a.jpg)

### [#](#Hand-Face-Body-模式) Hand Face Body 模式

该模式下，识别点的关键点就是 `世界坐标的 (0, 0, 0)`，`坐标轴` 也是用于特征点定位，单位1是基于识别物体的比例。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-hand.fa167b66.jpg)

![](https://res.wx.qq.com/wxdoc/dist/assets/img/location-face.e09ce3a3.jpg)

Incorrect translation.