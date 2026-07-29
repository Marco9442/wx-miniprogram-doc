# [#](#组件数据解析) 组件数据解析

在[组件](./component.html)一章我们知道需要有一个解析器将`xml`中组件对应属性的字符串转换为组件需要的数据类型，对此，框架提供了一套机制来处理。

## [#](#数据解析器) 数据解析器

数据解析器`IDataValueHandler`就是用来将属性字符串转换成特定类型的数据的，其具体定义如下：

```
interface IDataValueHandler<TDataValue> {
  create(value: string, defaultValue: any, scene: Scene): TDataValue;
}
```

可见主要是一个`create`方法，其接受一个字符串的`value`，一个组件`schema`中定义的默认值`defaultValue`和场景引用`scene`，返回解析后的值。一般我们会如此注册一个解析器：

```
registerDataValue('number', {create: (value: string, defaultValue: any, scene: Scene) => {
  return value === undefined ? defaultValue : parseFloat(value));
}});
```

这里注册了`number`类型的解析器，可以看到如果没有传入值则返回默认值，否则用`parseFloat`转换。

除了`registerDataValue`方式注册的数据类型外，还有一类特殊类型的数据，它们就是**资源**。

## [#](#特殊类型-资源) 特殊类型-资源

资源数据和`number`这样的普通数据有些不同，其注册一般不使用`registerDataValue`，而是在`registerAssetLoader`时定义的。如何定义可以参考[资源加载器](./../assets/loader.html)的内容，一般来讲资源数据使用时填写的值都是**资源ID**，比如你要使用纹理资源：

```
<xr-asset-load type="texture" asset-id="waifu" src="/assets/textures/waifu.jpg" />
<xr-asset-material asset-id="simple-mat" uniforms="u_baseColorMap: waifu" />
```

我们先加载了一张id为`waifu`的纹理，然后在下面材质的uniform的`u_baseColorMap`属性使用了它。

> 资源类型的数据在`schema`中描述时，默认值是资源的`id`。
> 注意资源类型的数据还会影响到组件的`onAdd`和`onUpdate`生命周期，**框架会在每一次资源数据更新后，先等待引用的资源加载完成，才会进入这两个生命周期**。

## [#](#内置数据类型) 内置数据类型

框架内置了一些数据类型：

### [#](#非资源数据) 非资源数据

| 类型 | 例子 | 转换 | 说明 |
| --- | --- | --- | --- |
| string | henshin: KuugaAgitoRyuki FaziBladeHibikiKabutoDenOkiva DecadeWOOOFourzeWizardGaim DriveGhostExaidbuildGrandZio | 'KuugaAgitoRyuki FaziBladeHibikiKabutoDenOkiva DecadeWOOOFourzeWizardGaim DriveGhostExaidbuildGrandZio' | 字符串，不作任何处理 |
| number | truth:42 | 42 | 数字，会转成float，支持其他进制如`0xff`、`0b11` |
| boolean | yiyandingzhen:false | false | 布尔，当写'false'时为`false`，否则均为`true`(包括不写值) |
| array | producer:wowaka neru kurogaki | ['wowaka','neru','kurogaki'] | 字符串数组，用空格分割 |
| number-array | idolOffice:7 6 5 | [7,6,5] | 数字数组，用空格分割 |
| color | rem:0.57 0.75 1 1 | [0.57,0.75,1,1] | 颜色，rgba，也可以使用`#fff`这种方式 |
| map | cat:10,dog:8,fox:6 | [['cat',10],['dog',8],['fox',6]] | 映射形式是`key:value`，用`,`分割 |
| dict | camp:瞬光:混乱善良,roam:中立善良,xinyi:绝对中立 | {瞬光:'混乱善良',roam:'中立善良',xinyi:'绝对中立'} | 字典，和`map`类型写起来一样，转换结果不同 |
| transform | target:homo | `nodeId`为homo的Transform组件引用 | 变换，可以用于索引标记过`nodeId`的变换组件 |

### [#](#资源数据) 资源数据

资源数据可见内置的各种资源：[效果](./../render/effect.html)，[图片](./../render/image.html)，[纹理](./../render/texture.html)，[材质](./../render/material.html)，[几何数据](./../render/geometry.html)，[模型](./../gltf/)，[渲染目标](./../render/render-texture.html)，[帧动画](./../animation/keyframe.html)。

Incorrect translation.