# [#](#效果) 效果

[几何数据](./geometry.html) 提供了渲染的原材料，[材质](./material.html) 决定了渲染的方式，但在讨论材质之前，我们要讨论一下其基于的效果 [Effect](/miniprogram/dev/api/xr-frame/classes/Effect)。

效果可以认为是一个**材质模板**，通过**光照模式**`lightMode`和**宏定义**`definition`来对模板的各个功能进行开关。

## [#](#内置效果) 内置效果

详见 [内置效果资源](./../builtin/effect.html)。

## [#](#定制一个效果) 定制一个效果

```
function createSimpleEffect (scene: XRFrame.Scene) {
  return scene.createEffect({
    name: 'simple',
    properties: [
      {
        key: 'u_baseColorFactor',
        type: xrFrameSystem.EUniformType.FLOAT4,
        default: [1, 1, 1, 1]
      }
    ],
    images: [
      {
        key: 'u_baseColorMap',
        default: 'white',
        macro: 'WX_USE_BASECOLORMAP'
      }
    ],
    // 透明物体需要大于`2500`！
    defaultRenderQueue: 2000,
    passes: [
      {
        renderStates: {
          cullOn: true,
          blendOn: false,
          depthWrite: true,
          cullFace: xrFrameSystem.ECullMode.BACK,
        },
        lightMode: 'ForwardBase',
        useMaterialRenderStates: true,
        shaders: [0, 1]
      }
    ],
    shaders: [`#version 100

    attribute vec3 a_position;
    attribute highp vec2 a_texCoord;

    uniform mat4 u_view;
    uniform mat4 u_projection;
    uniform mat4 u_world;
  
    varying highp vec2 v_uv;
    
    void main()
    {
      v_uv = a_texCoord;
      gl_Position = u_projection * u_view * u_world * vec4(a_position, 1.);
    }`,
      `#version 100
    precision mediump float;

    uniform highp vec4 u_baseColorFactor;
    #ifdef WX_USE_BASECOLORMAP
      uniform sampler2D u_baseColorMap;
    #endif

    varying highp vec2 v_uv;

    void main()
    {
  #ifdef WX_USE_BASECOLORMAP
      vec4 baseColor = texture2D(u_baseColorMap, v_Uv) * u_baseColorFactor;
  #else
      vec4 baseColor = u_baseColorFactor;
  #endif

      gl_FragData[0] = baseColor;
    }  
      `],
  });
}
```

在效果的参数中，首先是其名字`name`，然后是其能允许的属性`properties`和`images`。

### [#](#定义属性) 定义属性

属性对应后续生成材质的`uniforms`的定义。每个`property`都需要一个键`key`、类型`type`和对应于类型的默认值，而每个`image`则不需要`type`、默认值也是已经注册到了资源系统的[纹理](./texture.html)的资源`id`。

这里特别要注意在那个`marco`参数，它定义了当用户修改设置（通过材质的接口）了这个属性后，将会开启的宏，这个宏会直接应用到[着色器](#%E7%BC%96%E5%86%99%E7%9D%80%E8%89%B2%E5%99%A8)中。

> 注意，**所有的外部设置的宏都必须以`WX_`开头**！
> 为了让整个渲染正常运作，框架内置了一些属性和宏，可见文章末尾的附录。

### [#](#渲染队列) 渲染队列

由`defaultRenderQueue`定义的渲染队列，决定了渲染顺序，将在下一章[材质](./material.html)中详细论述。

> 透明物体需要大于`2500`！

### [#](#配置Pass) 配置Pass

`Pass`对应的是使用了基于这个效果的材质的网格的一次渲染，这个和[相机](./camera.html)组件相关，使用哪个`pass`渲染取决于相机当次绘制指定的`lightMode`。

`lightMode`是光照模式，目前建议只能使用一个模式`ForwardBase`。当存在多个`pass`都使用了同一个光照模式时，将会按顺序将网格渲染多次。

`renderStates`顾名思义即渲染状态，渲染状态直接对应底层图形API都会提供的一系列概念，比如混合`blend`、深度`depthTest`等，比如示例里就定义了`blendOn: false`，即表明要**关掉混合**。

更多的渲染状态可见API文档[IRenderStates](./../../../api/xr-frame/interfaces/IRenderStates.html)，这里不赘述，这里主要要说明一个规则，即`useMaterialRenderStates`这个参数的作用。

在`xr-frame`框架的设计中，渲染状态是**由效果决定默认值，材质决定最终值**的，而`useMaterialRenderStates`则就是用于决定材质是否能够覆盖效果默认值的，如果为`false`，则总是使用效果提供的默认值，如果为`true`，则由下面会讲到材质的渲染状态的规则来决定。

在配置完这些之后，就是要定制`shaders`了。这是一个有两个数字的数组，分别指定了**顶点着色器**和**片段着色器**在顶层参数中的`shaders`的索引。

### [#](#编写着色器) 编写着色器

效果配置的顶层参数中最后一项是`shaders`，这是一个字符串数组，每个元素都是一个完整的着色器。着色器使用标准的`glsl1`语法，这个不属于教程范畴不再赘述。

我们提供了一些内置可用的着色器的函数，在文章末尾会给出。

## [#](#注册到资源系统) 注册到资源系统

将效果注册到资源系统可用：

```
xrFrameSystem.registerEffect('custom', createSimpleEffect);
```

注册后在`schema`中类型指定为`effect`的数据，便可以使用`custom`这个资源id引用到创建的资源了。

Incorrect translation.