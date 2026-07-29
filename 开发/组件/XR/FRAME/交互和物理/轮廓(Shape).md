# [#](#轮廓) 轮廓

如果想要与场景中的物体进行互动，比如说点击、拖拽物体，那么这个物体得先拥有一个*轮廓*才行。

> 轮廓是一个*组件*。与某个物体互动，实际上是在与这个物体的轮廓进行互动，轮廓让这个物体在*物理世界*中拥有了一个分身。

## [#](#创建轮廓) 创建轮廓

创建轮廓非常简单，只要为xml标签添加上xxx-shape的属性即可。  
例如以下代码为一个球体创建了一个球状轮廓：

```
<xr-mesh node-id="mesh-sphere" geometry="sphere" sphere-shape></xr-mesh>
```

实际上，不需要标签是`xr-mesh`，任意一个场景标签都可以创建轮廓：

```
<xr-node node-id="shape-node" sphere-shape></xr-node>
```

## [#](#轮廓种类) 轮廓种类

| 名称 | 标签属性名 | 组件数据 | 备注 |
| --- | --- | --- | --- |
| 球状轮廓 | sphere-shape | center, radius, autoFit |  |
| 胶囊体轮廓 | capsule-shape | center, radius, height, autoFit |  |
| 长方体轮廓 | cube-shape | center, size, autoFit |  |
| 网格模型轮廓 | mesh-shape | - | 自动适配元素下的Mesh和GLTF模型 |

除了网格模型轮廓之外，其他轮廓均拥有autoFit属性（实际上网格模型轮廓的autoFit常开，所以不能设置）。开启autoFit之后，轮廓会自动寻找当前元素下的`Mesh组件`和`GLTF组件`，并使用自身形状去尽量贴合模型。

> 如果将`GLTF组件`和开启了`autoFit`的*轮廓*组合使用，那么会为GLTF内部的每个Mesh都创建一个轮廓。  ⚠️ 使用`MeshShape`的时候，请确保模型顶点数量小于65535个。如果超过了数量限制，推荐使用CubeShape+autoFit来代替。

## [#](#轮廓交互) 轮廓交互

可以通过为标签绑定事件的方式来与轮廓进行互动，如果尚未了解如何绑定事件，可以参考[事件文档](./../core/event.html)。

例如使用以下代码，可以为轮廓绑定一个log事件（需自行完成logFunction函数）：

```
<xr-node node-id="shape-node" cube-shape bind:touch-shape="logFunction"></xr-node>
```

| 事件名 | 描述 | 事件回调参数 | 备注 |
| --- | --- | --- | --- |
| touch-shape | 点击轮廓时触发 | [IShapeTouchEvent](./../../../api/xr-frame/interfaces/IShapeTouchEvent.html) | 如果有多个物体叠在一起，会点中最上层的。 |
| drag-shape | 点击轮廓后，手指不松开的情况下进行拖拽时触发 | [IShapeDragEvent](./../../../api/xr-frame/interfaces/IShapeDragEvent.html) | 只有在先触发touch-shape之后才会触发这个事件，target和touch-shape保持一致。 |
| untouch-shape | 点击轮廓后，手指松开时触发 | [IShapeTouchEvent](./../../../api/xr-frame/interfaces/IShapeTouchEvent.html) | 只有在先触发touch-shape之后才会触发这个事件。 |

> 无论有没有绑定事件，其实都会触发事件，只是没有事件回调函数就什么都没发生。

## [#](#轮廓可视化) 轮廓可视化

为标签加上`shape-gizmo`即可将标签上的轮廓用线框绘制出来：

```
<xr-node node-id="shape-node" cube-shape shape-gizmo></xr-node>
```

> `MeshShape`不会显示轮廓，因为基本上和渲染出来的模型一致。 ![](https://res.wx.qq.com/wxdoc/dist/assets/img/2022-09-21-17-00-41.19f3485c.png)

Incorrect translation.