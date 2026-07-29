# [#](#Shadow元素) Shadow元素

有时候我们需要用代码动态创建元素之后添加到场景中，这个需求和`wxml`写标签这种静态的模板编译方式是冲突的，为了保证DOM树不混乱，我们提供了类似于HTML中的`ShadowRoot`的[XRShadow](/miniprogram/dev/api/xr-frame/classes/XRShadow)元素，对应于`xml`中的`xr-shadow`标签，来解决这个问题。

## [#](#一个例子) 一个例子

让我们以一个例子来说明如何使用Shadow元素，首先在`xml`中定义：

```
<xr-shadow id="shadow" position="0 1 0" />
```

之后便可以在代码中使用：

```
const shadow = scene.getElementById('shadow');
const node = scene.createElement(xrFrameSystem.XRNode);

// 添加创建的节点到`shadow`节点下
shadow.addChild(node);

// 移除创建的节点
shadow.removeChild(node);
```

## [#](#特别注意) 特别注意

在实际使用中我们有一些特别要注意的地方：

1. Shadow元素派生自节点元素，拥有3D变换的能力。
2. 在`wxml`中，Shadow元素下**绝对不能有子元素**！！！当然如果这么做了框架会报错。
3. 动态创建的元素**仅能**添加为Shadow元素的子/孙元素，这个**框架不会检查**，出了问题后果自负。
4. Shadow元素以及子元素的`release`需要自己处理，`remove`后能够继续复用重新`add`！

Incorrect translation.