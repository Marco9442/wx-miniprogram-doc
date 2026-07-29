# [#](#场景) 场景

场景[Scene](/miniprogram/dev/api/xr-frame/classes/Scene)是一种特殊的[元素](./element.html)，对于所有的`xr-frame`小程序组件，其最外层必须有一个`xr-scene`标签**作为根元素，并且组件内只能有一个**，以此作为整个组件的基础。

和一般仅用于组合的元素不同，场景有以下几个特别之处：

1. 其下挂载的组件都是名为**系统**`System`的特殊组件，来驱动逻辑和渲染。
2. 增加了一些方法，用于创建资源、查询等等。
3. 每个元素、组件、资源都是属于当前被包在的`xr-scene`标签对应的元素中的。

在我们编写组件时，常常用到的那个`this.scene`，其实就是这个元素。

## [#](#用途) 用途

一般我们需要用到的是场景的创建和查询能力。

创建资源可以使用类似：

```
// 脱离于资源加载工作流，创建属于这个场景的纹理资源
const texture = scene.createTexture(options);

// 直接创建一个元素，但注意要和`Shadow元素`一起使用
const el = scene.createElement(xrFrameSystem.XRNode);
```

的方式，更多的创建可见[API文档](/miniprogram/dev/api/xr-frame/classes/Scene)。

同样在API文档中我们还可以看到有一些查询接口，比如上一节提到的`scene.getElementById`，以及`scene.width`这种获取画布信息的，`scene.assets`这种获取系统实例引用的，开发者可以按需使用。

## [#](#获取场景实例) 获取场景实例

要使用场景需要先获取实例，在组件、加载器等中，我们可以直接用`this.scene`获取，而在用户小程序脚本中，则需要通过事件：

```
<xr-scene bind:ready="handleReady">
......
</xr-scene>
```

```
// 小程序脚本中绑定的事件
handleReady({detail}) {
  const scene = detail.value;
}
```

## [#](#事件) 事件

场景元素提供了以下事件：

| 事件 | 参数 | 立即 | wxml | 时机 |
| --- | --- | --- | --- | --- |
| ready | 无 | 是 | 是 | 场景第一次解析完毕 |
| tick | 数字，`delta`(ms) | 是 | 是 | 一帧驱动开始 |
| pause | 无 | 是 | 是 | 场景暂停，一般是是压后台 |
| resume | 无 | 是 | 是 | 场景恢复，一般是从后台唤醒 |

Incorrect translation.