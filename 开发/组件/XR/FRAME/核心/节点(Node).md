# [#](#节点) 节点

元素虽然有很多派生，但本质上可以分为两类——3D节点和非3D节点（简称节点）。节点`Node`对应的标签是`xr-node`，它是场景中用于渲染的元素的基础，本质上是在基础元素的基础上默认添加了[`Transform`变换组件](/miniprogram/dev/api/xr-frame/classes/Transform)。

## [#](#变换组件) 变换组件

变换组件提供了渲染最基础的位置`position`、旋转`rotation`和缩放`scale`能力，原理上来讲，整个3D场景的渲染就是由很多个变换组件的级联实现的，最终构成一颗场景节点树。

要使用变换组件，我们有两种方式，一种是直接作为组件使用：

```
<xr-element transform="position: 1 1 1;nodeId=node1">
  <xr-element transform="position: 1 2 1"></xr-element>
</xr-element>
```

这个例子中，我们创建了两个带有变换组件的元素，并将它们级联了起来。而通过使用节点元素，我们可以将其等价地写成：

```
<xr-node node-id="node1" position="1 1 1">
  <xr-node position="1 2 1"></xr-node>
</xr-node>
```

可见，节点元素其实就是将变换组件的属性做了一下映射。我们还可以注意到`nodeId`这个数据，它和元素的`id`不同，是专门给变换组件用的一个索引。在[组件数据解析](./data-values.html)一章最后，有一种`transform`类型的内置数据类型的值，就是这个`nodeId`。此外，我们还可用以下方法来手动获取变换组件的引用：

```
const trs = scene.getNodeById(nodeId);

// 修改位置
trs.position.x = 10;
trs.position.setValue(10, 10, 10);
trs.position.setFromArray([1, 1, 1]);
trs.position.set(new xrFrameSystem.Vector3());

// 欧拉角、缩放、四元素也是类似的
trs.rotation.y = 10;
trs.scale.z = 2;
trs.quaternion.w = 1;
```

更多属性请看API文档。

## [#](#派生) 派生

节点作为一类特殊的元素的基础，很多元素都是派生自它的，比如灯光、相机等等，所以它的默认组件集和数据映射表非常常见，一般来讲要派生自节点，我们需要这么做：

```
import XrFrame from 'XrFrame';
const xrFrameSystem = wx.getXrFrameSystem();

const CustomDefaultComponents: XrFrame.IEntityComponents = Object.assign({
  'custom-component': {
    customData: value
  }
}, xrFrameSystem.NodeDefaultComponents);

const CustomStarDataMapping: {[key: string]: string[];} = Object.assign({
  'custom-data': ['custom-component', 'customData']
}, xrFrameSystem.NodeDataMapping);

xrFrameSystem.registerElement('custom', class XRCustom extends xrFrameSystem.Element {
  public readonly defaultComponents: XrFrame.IEntityComponents = CustomStarDefaultComponents;
  public readonly dataMapping: {[key: string]: string[];} = CustomStarDataMapping;
});
```

关键在于对`xrFrameSystem.NodeDefaultComponents`和`xrFrameSystem.NodeDataMapping`的合并。

## [#](#可见性与图层) 可见性与图层

对于节点和派生自节点的元素（也就是挂载了`Transform`组件的元素），都有`visible`和`layer`两个属性可选。这两个属性用于控制节点自身以及其子孙结点的**可见性**。

当我们需要需要一个开关直截了当得让某个节点之下的所有模型或者灯光都显示或者不显示，最方便的方法就是使用`visible`：

```
<xr-node visible="false">
  <xr-mesh visible geometry="cube" />
</xr-node>
```

比如这个例子，所有节点的`visible`默认都是`true`，但当父节点设置为`false`时，即便子节点显式定义了`true`，也会被隐藏。

除了这种场景，在另外一些场景我们还会有更复杂的需求，比如只是想针对性得剔除掉某一类模型或是灯光，而非按照层级结构，这时候图层`layer`就派上用场了，让我么来看个例子：

```
<xr-node layer="1">
  <xr-mesh geometry="sphere" uniforms="u_baseColorFactor:0.937 0.176 0.368 1" />
  <xr-node layer="2">
    <xr-mesh geometry="cylinder" uniforms="u_baseColorFactor:1 0.776 0.364 1" />
  </xr-node>
</xr-node>
<xr-camera
  position="0 1.6 0" clear-color="0.925 0.925 0.925 1"
  cull-mask="0b01"
/>
```

对于两个`xr-node`节点，我们给第一层指定了`layer=1`，第二层指定了`layer=2`，然后将`xr-camere`节点的`cull-mask`属性（对应于`Camera`组件的`cullMask`数据）设置为`0b01`。如此设置的效果应该是第一个`mesh`被渲染，第二个不被渲染。

开发者看到这里应该不难发现图层的规则：`layer`可以设置`1~32`共32个值，而相机的`cullMask`是一个**32位无符号整数**，每一位都代表一个`layer`。只有当一个节点从顶层到自身路径中的所有节点都通过了这个`mask`的测试，才会被显示出来。这也适用于灯光`Light`组件。

Incorrect translation.