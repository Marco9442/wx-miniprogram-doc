# [#](#组件) 组件

组件[Component](/miniprogram/dev/api/xr-frame/classes/Component)用于实现`xr-frame`中所有的逻辑，以生命周期拉驱动。它们在`wxml`中对应于每个标签上的属性，比如`<xr-element transform="position: 1 1 1;" />`，就是在`xr-element`标签上挂在了一个`transform`组件。组件的聚合构成了后面章节的[元素](./element.html)，也就是`wxml`中对应的标签。

组件的构成主要分为两部分——数据定义和生命周期。

![](https://res.wx.qq.com/wxdoc/dist/assets/img/1.a57c1e3b.png)

## [#](#让我们定制一个组件) 让我们定制一个组件

通过定制一个简单的组件，我们可以对组件的机制有比较清晰的了解：

```
// 这里只包括类型信息
import XrFrame from 'XrFrame';
// 这里是实例
const xrFrameSystem = wx.getXrFrameSystem();

// 自定义组件的数据接口
export interface IAutoRotateData {
  speed: number[];
}

// 自定义组件的`schema`，详见后面论述
const AutoRotateSchema: XrFrame.IComponentSchema = {
  speed: {type: 'number-array', defaultValue: [1, 1, 1]}
}

// 定义组件
class AutoRotate extends xrFrameSystem.Component<IAutoRotateData> {
  public readonly schema: XrFrame.IComponentSchema = AutoRotateSchema;

  private _speedX: number = 1;
  private _speedY: number = 1;
  private _speedZ: number = 1;

  // 所挂载的`element`被挂载到场景时触发的回调。
  public onAdd(parent: XrFrame.Element, data: IAutoRotateData): void {
    this._processData(data);
  }

  // 数据更新时触发的回调。
  public onUpdate(data: IAutoRotateData, preData: IAutoRotateData): void {
    this._processData(data);
  }

  // 渲染每帧触发的回调。
  public onTick(delta: number, data: IAutoRotateData) {
    const trs = this.el.getComponent(xrFrameSystem.Transform);

    // 如果没有挂载到一个`Node`节点，则不生效。
    if (!trs) {
      return;
    }

    // 其实这里实现有点问题，不过是例子也无伤大雅了（逃
    trs.rotation.x += this._speedX * 0.1;
    trs.rotation.y += this._speedY * 0.1;
    trs.rotation.z += this._speedZ * 0.1;
  }

  // 所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上呗移除时，触发的回调。
  // 一般用于消除功能的运作。
  public onRemove(parent: XrFrame.Element, data: IAutoRotateData): void {

  }

  // 从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
  // 一般用于释放持有的资源。
  public onRelease(data: IAutoRotateData) {

  }

  private _processData(data: IAutoRotateData) {
    this._speedX = data.speed?.[0] !== undefined ? data.speed[0] : 1;
    this._speedY = data.speed?.[1] !== undefined ? data.speed[1] : 1;
    this._speedZ = data.speed?.[2] !== undefined ? data.speed[2] : 1;
  }
}

// 最后将组件注册进框架，名为`auto-rotate`
xrFrameSystem.registerComponent('auto-rotate', AutoRotate);
```

通过以上代码，我们定制了一个为挂载的元素提供**旋转功能**的组件。

首先可以看到的是`IAutoRotateData`和`AutoRotateSchema`，接口是为了通过泛型给定义的组件提供类型推断，而真正作用于运行时逻辑的，则是那个`schema`，其类型定义为：

```
interface IComponentSchema {
  [key: string]: {type: string, defaultValue?: any}
}
```

在`schema`中，我们定义了组件每个数据的类型`type`和默认值`defaultValue`。这是由于所有组件在`xml`中对应的属性的值**都是字符串**，所以需要告诉框架如何将这些字符串转换成最终的值，这一部分详见[组件数据解析](./data-values.html)。

在数据定义后，我们继承了`xrFrameSystem.Component`派生了一个子类，它有一些生命周期，这就是组件具体逻辑实现的载体。我们在`onAdd`和`onUpdate`的时候去更新旋转速度数据，然后在每帧`onTick`的时候去修改挂载元素的`transform`组件中的旋转。注意还有`onRemove`和`onRelease`两个生命周期，但由于本组件没有额外资源需要处理，所以不需要执行任何操作。

完成了逻辑的实现后，我们最后一步调用了`xrFrameSystem.registerComponent`将这个组件注册到了框架中，并给它了一个名字`auto-rotate`，接下来就可以正常使用了。

## [#](#使用这个组件) 使用这个组件

使用组件的方式有两种：

### [#](#在wxml中使用) 在wxml中使用

首先是在`wxml`中使用，我们只需要按照注册的名字和数据类型定义将其写在元素标签上即可：

```
<xr-node auto-rotate="speed: 2 3 1;" />
```

如此这个节点便会自动旋转，速度为`{x: 2, y: 3, z: 1}`。

> 组件还可以通过代理的方式来简化使用，详见[元素](./element.html)中的**数据代理**部分。

### [#](#手动使用) 手动使用

我们也可以在运行时来手动添加组件或设置它的数据，但注意**一定不要和`xml`中冲突**！

要手动使用组件，我们需要先拿到元素的实例引用，详见[场景](./scene.html)中获取元素引用相关的描述，拿到了引用后便可以执行操作：

```
// 添加组件，并给一个可选的初始值
el.addComponent(AutoRotate, {speed: [2, 3, 1]});

// 获取组件并更新数据，注意`setData`包括`getData`都是通用方法，但有些组件有自己的实现，比如`transform.position`。
el.getComponent(AutoRotate).setData({speed: [1, 1, 1]});

// 手动移除组件
el.removeComponent(AutoRotate);
```

Incorrect translation.