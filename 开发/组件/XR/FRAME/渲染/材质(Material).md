# [#](#材质) 材质

材质 [Material](/miniprogram/dev/api/xr-frame/classes/Material) 基于 [效果 Effect](./effect.html)，提供了修改渲染状态、Uniforms的接口，真正决定了物体最后的渲染方式，体现为物体表面的外观。

## [#](#创建一个材质) 创建一个材质

创建材质有两种方式，一般我们会优先在`wxml`中进行创建。

### [#](#在wxml中创建) 在wxml中创建

在`xml`中创建需要用到`xr-asset-material`标签：

```
<xr-asset-material asset-id="mat" effect="standard" uniforms:"u_baseColorMap: waifu" states="alphaMode:BLEND" renderQueue="2500" />
```

其中`asset-id`是会添加到资源系统中的`id`，`effect`是已经注册过的效果，这两个参数是必填的。`uniforms`类型是`dict`，用于覆盖效果中定义的那些属性，会根据那些属性的`type`来进行解析，比如`Vector2`对应`1 1`这样的数组；`states`类型也是`dict`，用于覆盖效果中定义的那些渲染状态（需要效果中开启`useMaterialStates`）；最后的`renderQueue`用于覆盖效果中的默认渲染顺序，大于等于`2500`为透明物体。

### [#](#用代码创建) 用代码创建

有时候我们需要用代码创建材质，也很简单：

```
// 第一个参数是效果实例的引用，第二个参数是默认`uniforms`
const mat = scene.createMaterial(
  // 使用内置的 Standard 效果
  scene.assets.getAsset('effect', 'standard'),
  {u_baseColorMap: scene.assets.getAsset('texture', 'waifu')}
);

// 可以将其添加到资源系统中备用
scene.assets.addAsset('material', 'test-mat', mat);
```

创建完，接下来就是使用了。

## [#](#使用材质) 使用材质

材质和其他资源一样，可以通过在组件`schema`中设定数据类型为`material`，然后在`xml`中通过资源id索引，或者用`setData`直接使用。目前使用了材质的组件只有[网格](./mesh.html)，详见对应章节。

除了被引用外，材质也提供了一些方法来对其进行修改：

```
// 一系列修改Uniforms的接口
material.setFloat(key, value);
material.setVector(key, vec);
material.setMaterial(key, mat);
material.setTexture(key, texture);

// 修改渲染状态
material.setRenderState(key, value);

// 修改宏
material.setMacros({key: value});

// 重置图片，同时关闭对应的宏
material.resetTexture(key);

// 重置状态
materia.clearRenderState(key);
```

## [#](#材质支持渲染状态列表) 材质支持渲染状态列表

| 状态名称 | 说明 | 类型 |
| --- | --- | --- |
| renderQueue | 渲染顺序 | number |
| cullOn | 是否开启剔除 | bool |
| depthTestOn | 是否开启深度测试 | bool |
| depthTestWrite | 是否开启深度写入 | bool |
| alphaMode | 透明模式 | 'OPAQUE' 'BLEND' 'MASK' |
| alphaCutOff | 是否开启透明剔除 | bool |
| depthTestComp | 深度测试方法 | number, [ECompareFunc](./../../../api/xr-frame/enums/ECompareFunc.html)对应的值 |
| stencilTestOn | 是否开启模板测试 | boolean |
| stencilComp | 模板测试相关 | number, [ECompareFunc](./../../../api/xr-frame/enums/ECompareFunc.html)对应的值 |
| stencilRef | 模板测试相关 | number |
| stencilReadMask | 模板测试相关 | number |
| stencilWriteMask | 模板测试相关 | number |
| stencilPass | 模板测试相关 | number, [EStencilOp](./../../../api/xr-frame/enums/EStencilOp.html)对应的值 |
| stencilFail | 模板测试相关 | number, [EStencilOp](./../../../api/xr-frame/enums/EStencilOp.html)对应的值 |
| stencilZFail | 模板测试相关 | number, [EStencilOp](./../../../api/xr-frame/enums/EStencilOp.html)对应的值 |
| colorWrite | 颜色通道写入掩码，基础库`v2.31.1开始支持` | number, 一个4bits的mask，由高到低为`ABGR`四个通道，比如`0b1001`表示只开启`R`和`A`通道写入 |

Incorrect translation.