# [#](#元素) 元素

元素[Element](/miniprogram/dev/api/xr-frame/classes/Element)本身没有逻辑，其主要负责两部分——组件的聚合和属性代理。所以在阅读以下内容之前，请保证先阅读了[组件](./component.html)的相关内容。

元素有两种使用方式，在`xml`中直接对应于标签，也可以在脚本中动态创建，但注意动态创建的时候，必须作为[Shadow元素](./shadow.html)的子孙结点！！！

## [#](#定制一个元素) 定制一个元素

让我们从定制一个元素开始，理解它的功能：

```
import XrFrame from 'XrFrame';
const xrFrameSystem = wx.getXrFrameSystem();

// 指定默认挂载的组件
const AutoRotateTouchableGLTFDefaultComponents: XrFrame.IEntityComponents = Object.assign({
  'mesh-shape': {},
  'auto-rotate': {}
}, xrFrameSystem.GLTFDefaultComponents);

// 指定一个映射，将`xml`上特定的属性，映射为组件的数据
const AutoRotateTouchableGLTFDataMapping: {[key: string]: string[];} = Object.assign({
  speed: ['auto-rotate', 'speed']
}, xrFrameSystem.GLTFDataMapping);

// 定义元素类
class XRAutoRotateTouchableGLTF extends xrFrameSystem.Element {
  // 指定默认组件集
  public readonly defaultComponents: XrFrame.IEntityComponents = AutoRotateTouchableGLTFDefaultComponents;
  // 指定默认数据映射
  public readonly dataMapping: {[key: string]: string[];} = AutoRotateTouchableGLTFDataMapping;
}

// 注册元素实现`XRAutoRotateTouchableGLTF`为名字`auto-rotate-touchable-gltf`
xrFrameSystem.registerElement('auto-rotate-touchable-gltf', XRAutoRotateTouchableGLTF);
```

在这个自定义元素中，我们首先指定了它初始化时就要挂载的组件，这其中有两部分，第一部分是`xrFrameSystem.GLTFDefaultComponents`，这其实就是`xr-gltf`组件默认挂载的组件集合，之后在其上追加了`mesh-shape`和上一节定制的`auto-rotate`组件。

其次我们指定了映射，还是分为了两部分，第一部分是`xrFrameSystem.GLTFDataMapping`，第二部分是追加的`speed`。来看看`speed`的值，数组第一个值为`auto-rotate`，就是挂载在这个元素上的组件名字，第二个值是`speed`，就是说要将写在标签上的`speed`属性直接映射到`auto-rotate`组件的数据`speed`上。

> 注意，所有的内置组件的映射，都是会将如`isARCamera`这样的驼峰，映射为`is-ar-camera`这样的小写加中划线分割的形式。
> 从这里我们可以看出，元素确实是用组合而非继承的方式实现的功能。最后我们继承自`Element`实现了元素，并用`registerElement`将其注册到了框架中。

## [#](#使用这个元素) 使用这个元素

和组件一样，使用元素的方式同样有两种：

### [#](#在wxml使用) 在wxml使用

首先是在`wxml`中使用，只需要按照注册时的名字使用就好：

```
<xr-auto-rotate-touchable-gltf id="artg" position="-2 0 0" model="gltf-damageHelmet" speed="1 0 0" bind:drag-shape="handleDrag" bind:touch-shape="handleTouchStart" bind:untouch-shape="handleTouchEnd" />
```

可以看到，这里确实直接写了`speed`属性。

> 组件的属性写法和数据映射是可以共存的，同时数据映射并不先要求组件存在。

### [#](#手动使用) 手动使用

我们也可以在运行时来代码创建元素和添加到场景，但注意**绝对不能将其添加到Shadow元素以外的元素**！！！

> 为了避免开发者失误，创建和添加详见[Shadow元素](./shadow.html)。

```
const node = scene.createElement(xrFrameSystem.XRNode, {
  position: '1 1 1'
});

node.setAttribute(position, '2 2 2');
```

这段代码通过`createElement`方法创建了一个元素，注意第二个初始化参数传入的是属性，其**完全对应于**标签上的名字，值也是**字符串**，接下来我们还通过`setAttribute`方法更新了其属性。

> 但建议不要使用`setAttribute`去更新属性，而是先获取组件，然后用[组件](./component.html)中的`setData`方法来设置，省去字符串解析！

### [#](#查找) 查找

有时候我们需要获得元素的实例，来进一步进行其他操作，以下几个方法可以帮助我们拿到它：

```
// 通过在`wxml`的元素上设置的`id`索引，比如上面例子中的`artg`，`id`是唯一的
scene.getElementById(id);

// 获取元素的第`i`个子元素
el.getChildAtIndex(i);

// 通过一个`filter`函数，获取第一个子元素或者子元素集
el.getChildByFilter(filter);
el.getChildrenByFilter(filter);

// 通过类获取子元素
el.getChildByClass(clz);

// 通过在`wxml`元素上设置的名字`name`获取子元素，`name`可以不唯一
el.getChildName(name);
el.getChildrenName(name);
```

## [#](#事件) 事件

每个元素上都有一个事件管理器，来管理其下挂载的所有组件的事件派发，这个派发也可以触达到`wxml`的事件绑定，详见[事件](./event.html)。

Incorrect translation.