# [#](#相机) 相机

相机[Camera](/miniprogram/dev/api/xr-frame/classes/Camera)是渲染系统最核心的组件之一，和几乎所有的渲染引擎一样，它真正驱动着整个渲染管线的运作。相机组件一般被代理到相机元素[XRCamera](/miniprogram/dev/api/xr-frame/classes/XRCamera)中使用，其派生自[XRNode](./../core/node.html)，对应在`xml`中的标签为`xr-camera`。

相机组件也承载了一部分[AR系统](./../ar/)相关的能力，同时我们还提供了配套的相机控制器组件[CameraOrbitControl](/miniprogram/dev/api/xr-frame/classes/CameraOrbitControl)来方便开发者进行相机控制。

## [#](#相机元素) 相机元素

相机元素的一个典型使用方式如下：

```
<xr-node node-id="target" position="1 1 1" />
<xr-camera
  position="0 1 4" clear-color="0.4 0.6 0.7 1"
  background="skybox" target="target"
  camera-orbit-control=""
/>
```

这里面只列出了部分属性，实际上属性要多得多，下面就给大家一一举例。

> 以下属性均已**组件数据驼峰命名**给出，在元素中按照框架约定均转成\*\*小写加`-`\*\*的形式。

### [#](#投影方式) 投影方式

首先是投影方式以及其相关的参数，投影方式由`isPerspective`决定，声明是否使用透视投影，目前默认即为透视投影，关于这两者的区分开发者可以自行查阅。

无论是对于哪种投影类型，以下参数都是通用的：

1. near：近裁剪平面，决定相机最近能看到多远的物体。
2. far：远裁剪平面，决定相机最远能看到多远的物体。

在选择了透视投影的模式下，有以下参数可供调整：

1. fov：视场角，角度，默认为60。

在选择了正交投影的情况下则有以下参数：

1. orthSize：相机可视范围大小，是**横向**的尺寸，纵向会根据`aspect`换算。

#### [#](#自定义矩阵) 自定义矩阵

本质上来讲，投影方式和参数方式决定了投影矩阵，而相机所在元素挂载的`transform`组件则决定了视图矩阵，这里不再赘述这种基本概念，一般来讲都是框架自动计算的。但在某些高级需求，比如水面折射投影的渲染需求中，确实有可能要自己定制投影方式、甚至是定制视图矩阵的计算。为了解决这种需求，框架提供了方案。

```
// 修改投影矩阵
camera.changeProjectMatrix(manual, matrix);

// 修改视图矩阵
camera.changeViewMatrix(manual, matrix);
```

这两个方法可以用于修改投影或者视图矩阵，第一个参数`manual`用于控制开启或者关闭手动模式，第二个参数即为要设置的矩阵值。

### [#](#渲染目标和视图) 渲染目标和视图

知道了要花那些物体、以及如何讲这些物体投影到平面上，还需要知道将这些东西最终画在什么上面，这就是**渲染目标**`renderTarget`。

`renderTarget`可选值为空或者[渲染纹理](./render-texture.html)资源，如果为空则会渲染到主屏上，渲染纹理详见对应的章节。

在渲染目标渲染前，我们需要先视情况将其清空，这主要由几个参数决定：

1. isClearColor/clearColor：设置是否要在绘制前清除渲染目标的颜色，以及要清除为怎样的颜色。
2. isClearDepth/clearDepth：设置是否要在绘制前清除渲染目标的深度，以及要清除为怎样的深度。
3. isClearStencil/clearStencil：设置是否要在绘制前清除渲染目标的模板值，以及要清除为怎样的模板值。

### [#](#背景) 背景

在清屏后我们可能需要为整个场景绘制一个背景，这时候便可以使用`background`数据，其可选以下几种类型：

1. `default`：默认行为，只清屏，不绘制背景。
2. `skybox`：绘制天空盒，依赖于环境数据[Env](./env.html)。
3. `ar`：当开启了AR系统后，将会绘制设备摄像头的内容，详见[AR相关](#ar%E7%9B%B8%E5%85%B3)。

### [#](#跟随目标) 跟随目标

框架默认集成了基本的了相机跟随控制能力，只需要设置`target`即可，在`xml`中这是一个节点的`node-id`，本质上就是一个`transform`组件。

指定了它之后，相机在移动时，的前向将始终朝向`target`。

### [#](#深度和掩码) 深度和掩码

除了通过平截体剔除确定哪些物体要被渲染之外，还需要一种直接精确的剔除方案，这就是**掩码（cullMask）**。这个实际上已经在[可见性与图层](./../core/node.html#可见性与图层)中论述过。

除了单相机的渲染，很多时候会有很多个相机，它们之间也可能会有一定的顺序，这时候就可以使用`depth`来调整这个顺序，越大渲染顺序越靠后。在同一`depth`下，以标签编写的前后顺序为准。

### [#](#AR相关) AR相关

在开启了[AR系统](./../ar/)后，相机便可以使用AR相关的能力。

其一就是`background`指定为`ar`后，场景背景会绘制当前设备摄像机的画面。

第二是`isARCamera`数据，将其开启后在某些AR系统的模式下将会自动设置视图和透视矩阵，来匹配现实中设备摄像机的位置和视角。

> 非常需要注意，当开启`isARCamera`并且AR系统为`Plane`或者`Marker`模式时，**不能同时设置`target`数据**！！！

### [#](#后处理) 后处理

数据`postProcess`用于指定相机需要用到的后处理资源数组，详见[后处理](./post-process.html)。

## [#](#相机控制器) 相机控制器

相机控制器组件提供了一个简单的绕着相机`target`旋转的控制方式，一般而言只需要在元素上添加`camera-orbit-control`属性即可。当然相机控制器也提供了丰富的配置参数，如果想要调节可见API文档[CameraOrbitControl](/miniprogram/dev/api/xr-frame/classes/CameraOrbitControl)。

Incorrect translation.