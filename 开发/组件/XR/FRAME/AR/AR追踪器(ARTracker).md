# [#](#AR追踪器) AR追踪器

AR追踪器[ARTracker](/miniprogram/dev/api/xr-frame/classes/ARTracker)是AR系统的一部分。

提供了一种非常简单的方式，在特定的识别模式下识别出图像或者物体，对其进行跟随。其一版本代理到元素 [XRARTracker](/miniprogram/dev/api/xr-frame/classes/XRARTracker)。

对应在 `xml` 中的标签是 `xr-ar-tracker`。

## [#](#创建AR追踪器) 创建AR追踪器

AR追踪器的典型创建和使用方式如下：

```
<xr-ar-tracker mode="Marker" src="/assets/2d-marker.png">
  <xr-gltf model="gltf-damageHelmet"></xr-gltf>
</xr-ar-tracker>
```

可见我们使用了追踪器元素，为其指定了模式 `mode` 和识别对象地址 `src`，然后在其子级添加了一个 `glTF模型`（可以为任何派生自节点的元素）。

> 在除了`Plane`以外的模式下，理论可以支持多个追踪器。(比如可以存在多个 Marker tracker)

## [#](#AR追踪器的不同模式) AR追踪器的不同模式

使用ARTracker 的 `mode`，必须和 `ARSystem` 的 [识别模式(modes)](./#识别模式) 指定的模式完全一致。

根据 `mode` 的不同，ARTracker 的 `src` 和 子元素的作用和表现 也各不相同：

### [#](#二维Marker) 二维Marker

2D Marker识别模式，会将传入的 `src` (图片的网络地址) 或是 `image`（`image`类型资源`id`，优先使用）作为特征，去识别出三维空间一个平面上的图像部分，继而进行追踪。这个技术现在已经十分成熟可靠。

> 注意需要相机组件开启`isARCamera`。
> 在这种追踪模式下，当AR系统识别到目标时会自动应用3D变换到AR追踪器组件所在的节点元素上，进而影响所有的子节点：

案例代码片段 [链接](https://github.com/dtysky/xr-frame-demo/blob/master/miniprogram/components/xr-ar-2dmarker/index.wxml)

```
<xr-ar-tracker mode="Marker" src="{{markerImg}}">
  <xr-gltf model="gltf" anim-autoplay position="0.2 0 -0.2" scale="0.6 0.6 0.6" rotation="0 -50 0" />
  <xr-gltf model="gltf" anim-autoplay position="0.4 0 0.3" scale="0.5 0.5 0.5" rotation="0 -50 0" />
  <xr-gltf model="gltf" anim-autoplay position="-0.3 0 0.3" scale="0.4 0.4 0.4" rotation="0 -50 0" />
</xr-ar-tracker>
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/2.mp4)

### [#](#三维Marker) 三维Marker

3D Marker识别模式，使用方法与 2D Marker 基本一致，差异是，识别特征用的 `src` 需使用 三维识别特征文件 `map`，该文件可以通过 小程序示例 的 `接口` - `VisionKit视觉能力` - `3DMarkerAR` 页面生成。

三维识别特征文件 `map` 是根据 `VisionKit` 提供的算法能力，通过环绕物体一周的视频生成。流程同时还会产出`三维重建`的产物 `glTF`。具体的生成视频规范、生成流程、以及产物细节可以参考 [VisionKit 3DMarker](/miniprogram/dev/framework/open-ability/visionkit/marker.html)。

该模式下，识别出来的三维坐标系，会自带一个基于生成视频的`旋转`，一般情况下，这个旋转值都是很接近的。可以在业务逻辑上，对这个旋转进行适配。

```
<xr-ar-tracker mode="Marker" src="/assets/3d-marker.map">
  <!-- 一般情况下，可以用140度的旋转进行修正 -->
  <xr-node rotation="140 0 0">
      <xr-gltf model="gltf"></xr-gltf>
  </xr-node>
</xr-ar-tracker>
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/8.mov)

### [#](#OSD) OSD

OSD（One-shot Detection）Marker识别模式，也会将传入的`src`或是`image`（`image`类型资源`id`，优先使用）作为特征去识别。

但不同于2D Marker，这是一个纯屏幕空间算法，只会影响到所有子节点的位置和缩放，不会影响旋转。

其一般以一个现实中物体的照片作为识别源，来识别出这个物体的在屏幕中的 `二维区域`，我们已经做好了到三维空间的转换，但开发者需要自己保证 `tracker` 下模型的比例是符合识别源的。

OSD模式在识别那些 `二维的、特征清晰的物体` 效果最好，比如广告牌。其余情况，识别准度不如 2D Marker。

这种模式一般用于给现实中的物体做标注，在使用这种模式时，开发者需要自己保证了解要识别的物体（的特征图片）的原始尺寸，然后基于这些信息去添加子节点：

案例代码片段 [链接](https://github.com/dtysky/xr-frame-demo/blob/master/miniprogram/components/xr-ar-osdmarker/index.wxml)

```
<xr-ar-tracker mode="OSD" src="{{markerImg}}">
  <xr-mesh geometry="plane" rotation="-90 0 0" scale="1 1 1" uniforms="u_baseColorFactor:0 1 0 0.5" states="alphaMode:BLEND" />
</xr-ar-tracker>
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/3.mp4)

### [#](#Plane) Plane

平面识别模式，不依靠于`src`和`image`。

AR系统会标定出一个平面，相机组件开启 `isARCamera` 之后，相机的三维变换会与AR系统同步。

AR系统每帧会去求和这个平面的交点，之后同步到AR追踪器组件所在元素上，其所有的子节点继而受到影响。

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/1.mp4)

由于这种模式的灵活度比较高，所以我们还给AR系统提供了几个接口供开发者使用：

```
// 传入某个节点的`nodeId`
scene.ar.placeHere(nodeId);

// 也可以传入元素引用，关闭`switchVisible`
scene.ar.placeHere(element, false);

// resetPlane
scene.ar.resetPlane();
```

`placeHere`方法接受一个节点的`node-id`或者元素引用，将当前和平面的焦点（即追踪器的3D变换）同步到这个节点上。第二个参数`switchVisible`则会在执行同步后自动将这个节点的`visible`设置为`true`。

`resetPlane`方法则是重置平面的标定。

### [#](#PlaneMarker) PlaneMarker

> 从基础库 `v2.33.1` 开始支持。

[ARsystem 识别模式](./#识别模式) 需支持 `Plane Marker` 模式，且开启使用。

平面识别模式下，使用 `2D Marker` 识别。

使用方法，在开启对应模式后，直接使用 2d Marker Tracker 的使用方式即可。

ar-tracker识别到目标后，会同步算法侧得到的，marker识别出来的，转化为相对于 `平面模式世界空间的矩阵信息`，到对应的 `Tracker` 节点。

该模式下，允许 `同时识别多个 2D Marker`。

目前版本，该模式仅适用于静态物体，识别物体更新频率相对较慢。每 `3s`，未明显移动会更新一下位置，每 `7s` 会进行重新检测。

案例代码片段 [链接](https://github.com/dtysky/xr-frame-demo/blob/master/miniprogram/components/xr-ar-vio-marker/index.wxml)

```
<xr-ar-tracker mode="Marker" src="https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/marker/2dmarker-test.jpg">
  <xr-gltf model="butterfly" anim-autoplay position="0.2 0 -0.2" scale="0.6 0.6 0.6" rotation="0 -50 0" />
  <xr-gltf model="butterfly" anim-autoplay position="0.4 0 0.3" scale="0.5 0.5 0.5" rotation="0 -50 0" />
  <xr-gltf model="butterfly" anim-autoplay position="-0.3 0 0.3" scale="0.4 0.4 0.4" rotation="0 -50 0" />
</xr-ar-tracker>
```

## [#](#threeDof) threeDof

> 从基础库 `2.30.4` 开始支持。

由于`Plane`模式在一些安卓机下不稳定，针对**不需要用户移动而只需要旋转设备**的应用，我们提供了`threeDof`模式。这种模式下只需要修改`ARSystem`的`modes`即可，不需要添加`ARTracker`。

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/7.mp4)

## [#](#Face) Face

> 从基础库`2.28.1`开始支持。  
>  前置相机依赖于客户端版本**8.0.31**

人脸识别模式，会通过图像算法识别出人面部的特征点，然后变换到3D空间，可用于一些换装应用等场景，比起上面几种模式，它多出了一个参数和一些方法：

```
<xr-ar-tracker mode="Face" auto-sync="-1 105 104 45 98">
  <xr-mesh name="face" geometry="cube" scale="0.7 0.8 0.1" uniforms="u_baseColorFactor:1 1 1 0.5" states="renderQueue:2500,alphaMode:BLEND"/>
  <xr-mesh name="eyeL" geometry="cube" scale="0.1 0.1 0.1" uniforms="u_baseColorFactor:0 1 0 1" />
  <xr-mesh name="eyeR" geometry="cube" scale="0.1 0.1 0.1" uniforms="u_baseColorFactor:0 1 0 1" />
  <xr-mesh name="nose" geometry="cube" scale="0.1 0.1 0.1" uniforms="u_baseColorFactor:0 0 1 1" />
  <xr-mesh name="mouth" geometry="cube" scale="0.1 0.1 0.1" uniforms="u_baseColorFactor:1 0 0 1" />
</xr-ar-tracker>
```

`auto-sync`属性是一个数字数组，用于将**对应顺序的子节点绑定到某个特征点**上，其中`-1`表示忽略该节点，在运行过程中会自动同步变换信息，如示例：

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/4.mp4)

与此同时，开发者还可以按自己的需求更加灵活地控制：

```
const tracker = el.getComponent(xrFrameSystem.ARTracker);

// 视情况需要自己同步`tracker`的`scale`和`rotation`特定节点。
// 第一个参数是特征点编好，第二个是可选的复用结果，第三个是可选的是否相对于`ARTracker`。
// 为`false`为世界空间的位置，需要配合`scale`自己使用
const position = tracker.getPosition(98, new xrSystem.Vector3(), false);
```

特征点定义如下：

![](https://res.wx.qq.com/wxdoc/dist/assets/img/face.3df2e63d.jpg)

## [#](#Body) Body

> 从基础库`2.28.1`开始支持。

肢体识别模式，会通过图像算法识别出人躯干的特征点，然后变换到3D空间，可用于一些换装、游戏等场景，**与`Face`模式用法一致**：

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/5.mp4)

特征点定义如下：

![](https://res.wx.qq.com/wxdoc/dist/assets/img/body.23d64a2e.jpg)

## [#](#Hand) Hand

> 从基础库`2.28.1`开始支持。

手部识别模式，会通过图像算法识别出人手部的特征点，然后变换到3D空间，可用于一些手势等场景。**与`Face`模式用法一致**，但多出了两个参数：

```
// 获取手势姿态
const gesture = tracker.gesture;
// 获取总体置信度
const score = tracker.score;
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/ar/6.mp4)

特征点定义如下：

![](https://res.wx.qq.com/wxdoc/dist/assets/img/hand.d0aa58d9.jpg)

手势姿态（`0~18`，`-1`为无效）：

![](https://res.wx.qq.com/wxdoc/dist/assets/img/gesture.14eef626.jpg)

## [#](#获取追踪状态) 获取追踪状态

在追踪器使用过程中，开发者往往会希望实事监测追踪状态，包括追踪中、追踪到、出错等，并进行相应的处理。我提供了两个事件来实现这个需求，其中`ar-tracker-switch`比较简单，仅仅在追踪到/追踪中切换，而`ar-tracker-state`则提供了更加详尽的信息：

> `ar-tracker-state`事件从基础库`2.29.1`开始支持。

```
<xr-ar-tracker id="ar-tracker" mode="Marker" src="{{markerImg}}" bind:ar-tracker-state="handleARTrackerState">
  <xr-gltf model="gltf" />
</xr-ar-tracker>
```

绑定后编写逻辑：

```
handleARTrackerState({detail}) {
  // 事件的值即为`ARTracker`实例
  const tracker = detail.value;
  // 获取当前状态和错误信息
  const {state, errorMessage} = tracker;
}
```

以上`state`的类型为[EARTrackerState](./../../../api/xr-frame/enums/EARTrackerState.html)，当状态为`EARTrackerState.Error`时，可以从`errorMessage`获取详细错误信息。

但这里也要注意，由于某些使用时序的问题，很多场景下开发者**需要自己去确定`ARTracker`的初始状态**，比如在`ARSystem`的`ar-ready`事件中通过`id`获取`ARTracker`的引用，然后判定初始状态：

```
handleARReady({detail}) {
  const xrFrameSystem = wx.getXrFrameSystem();
  const tracker = this.scene.getElementById('ar-tracker').getComponent(xrFrameSystem.ARTracker);
  // 初始状态
  const {state, errorMessage} = tracker;
  // 绑定事件
  tracker.el.event.add('ar-tracker-state', tracker => {
    const {state, errorMessage} = tracker;
  });
}
```

## [#](#事件) 事件

AR追踪器为元素提供了以下事件：

| 事件 | 参数 | 立即 | wxml | 时机 |
| --- | --- | --- | --- | --- |
| ar-tracker-state | ARTracker实例，识别状态 | 是 | 是 | 要求基础库v2.29.1及以上，追踪器识别状态切换时，详见上一节 |
| ar-tracker-switch | boolean，识别状态 | 是 | 是 | 追踪器识别状态切换时，识别到了为`true`，否则为`false` |

Incorrect translation.