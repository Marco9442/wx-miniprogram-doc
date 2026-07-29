# [#](#灯光) 灯光

灯光组件[Light](/miniprogram/dev/api/xr-frame/classes/Light)用于给场景提供照明，也是阴影的核心。相机组件一般被代理到灯光元素[XRLight](/miniprogram/dev/api/xr-frame/classes/XRLight)中使用，其派生自[XRNode](./../core/node.html)，对应在`xml`中的标签为`xr-light`。

## [#](#创建灯光) 创建灯光

灯光元素的一个典型使用方式如下：

```
<xr-light type="ambient" color="1 1 1" intensity="0.1" />
<xr-light type="directional" rotation="40 170 0" color="1 1 1" intensity="0.2" />
<xr-light type="point" position="0 0 0" color="1 0 0" range="3" intensity="3" />
<xr-light type="spot" position="0.1 0 -0.1" color="0 0 1" range="12" intensity="10" rotation="0 120 0" inner-cone-angle="80" outer-cone-angle="90" />
```

这里写了四个灯光，分别对应于支持的四周灯光类型。框架针对一个场景共支持六个灯光，它们又被分成两类——主光源和追加光源。

### [#](#主光源) 主光源

主光源包含两部分——按照编写顺序第一个写的环境光和平行光：

1. 环境光：类型是`ambient`，支持颜色`color`和亮度`intensity`，直接影响物体的基础颜色和亮度。
2. 平行光：类型是`directional`，支持颜色`color`和亮度`intensity`，以及通过旋转`rotation`决定的方向，为物体表面通过不同光照算法提供明暗。

**主平行光**同时还决定着这个场景的阴影计算，详见[阴影](#%E9%98%B4%E5%BD%B1)一节。

以上信息会在渲染时通过全局宏和uniforms传入着色器，它们是：

| 类型 | uniforms | 宏 | 说明 |
| --- | --- | --- | --- |
| 环境光 | 颜色和亮度`u_ambientLightColorIns` | 是否开启`WX_USE_AMBIENT_LIGHT` | [r, g, b, ins] |
| 平行光 | 颜色和亮度`u_mainLightColorIns`和方向`u_mainLightDir` | 是否开启`WX_USE_MAIN_DIR_LIGHT` | [r, g, b, ins]/vec3 |

### [#](#追加光源) 追加光源

在两个主光源之后，场景还支持四个追加的光源，除了上面说到的平行光之外，还支持点光源和聚光灯：

1. 点光源：支持颜色`color`和亮度`intensity`，以及`position`决定的位置和`range`决定的照亮范围。
2. 聚光灯：支持颜色`color`和亮度`intensity`，以及`position`决定的位置、`rotation`决定的方向、`range`决定的照亮范围，和`inner-cone-angle`与`outer-cone-angle`决定的锥角。

以上信息会在渲染时通过全局宏和uniforms传入着色器，它们是：

| 类型 | 宏 | 说明 |
| --- | --- | --- |
| 开启追加光源 | `WX_USE_ADD_LIGHTS` | bool |
| 灯光数量 | `WX_ADD_LIGHTS_COUNT` | int |

| 类型 | uniforms | 说明 |
| --- | --- | --- |
| 灯光信息 | `u_addLightsInfo` | [type, range, innerConeAngle, outerConeAngle][4] |
| 灯光位置 | `u_addLightsPos` | vec3[4] |
| 灯光方向 | `u_addLightsDir` | vec3[4] |
| 灯光颜色亮度 | `u_addLightsColorIns` | [r, g, b, ins][4] |

## [#](#阴影) 阴影

在前面[网格](./mesh.html)一章中我们提到过阴影，阴影是灯光和这二者的协作结果，只有**主平行光**能够产生阴影，以如下场景为例：

```
<xr-mesh node-id="plane" position="0 -0.4 0" scale="5 0.2 5" geometry="cube"  uniforms="u_baseColorFactor:0.48 0.78 0.64 1" receive-shadow
/>
<xr-gltf model="test-gltf" cast-shadow/>
<xr-camera
  position="3 3 3" target="plane" 
/>
<xr-light type="directional" rotation="60 0 0" color="1 1 1" intensity="2.5" cast-shadow />
```

可见，我们给`plane`这个`xr-mesh`开启了`receive-shadow`去接收阴影，然后开启了`xr-gltf`的`cast-shadow`来产生阴影，最后开启了主光源的`cast-shadow`总开关允许灯光产生阴影。

当然，在实际使用中会有一些需要关注的地方：

1. 支持自己给自己投影，可以同时开启产生和接收阴影。
2. 可能需要视情况调整`shadow-distance`来避免阴影投影过大或者过小。
3. 适当调整`shadow-bias`来防止自阴影。

### [#](#宏和uniforms) 宏和uniforms

以下宏或者uniforms会被传递到着色器中：

| 类型 | 宏 | 说明 |
| --- | --- | --- |
| 开启接受阴影 | `WX_RECEIVE_SHADOW` | bool |

可以直接通过以下方法来获取当前物体阴影：

| 方法 | 说明 |
| --- | --- |
| `float shadowCalculation(vec3 posWorld)` | 传入世界坐标，返回阴影强度 |

Incorrect translation.