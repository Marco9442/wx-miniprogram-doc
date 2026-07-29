# [#](#环境) 环境

环境[Env](/miniprogram/dev/api/xr-frame/classes/Env)是一种特殊的组件，其一般被代理到元素[XREnv](/miniprogram/dev/api/xr-frame/classes/XREnv)上使用。环境用于描述当前场景的环境贴图和光照信息，其一般和[相机](./camera.html)与[材质](./material.html)协作，实现丰富真实的渲染效果。

环境数据可以使用[xr-frame-toolkit](./../tools/toolkit.html)来生成。

## [#](#创建环境组件) 创建环境组件

环境组件一般由`xml`创建，不建议使用代码创建：

```
<xr-env env-data="env1" sky-map="video-vt" is-sky2d="false" rotation="30" diffuse-exp="1" specular-exp="1" />
```

以上几个参数中，`env-data`指定的是[环境数据](#%E7%8E%AF%E5%A2%83%E6%95%B0%E6%8D%AE)资源，下面会说到；`sky-map`和`is-sky-2d`均和[天空盒](#%E5%A4%A9%E7%A9%BA%E7%9B%92)相关，后面会说道；剩下这几个均和环境数据相关，统一在那个章节说道。

> 多个环境组件，后面的会覆盖前面的。

## [#](#环境数据) 环境数据

环境数据[EnvData](/miniprogram/dev/api/xr-frame/classes/EnvData)是一种资源，对其加载使用标准的加载流程：

```
<xr-asset-load type="env-data" asset-id="env1" src="/assets/env1.json" />
<xr-asset-load type="env-data" asset-id="env1-bin" src="/assets/env1.bin" />
```

可见其是一个`json`文件或者一个二进制`bin`文件，其实它们都是一样的，只不过出于优化考虑，我们提供了将所有一个环境数据以来的所有资源大包围单二进制文件的形式。

环境数据一般由`xr-frame-toolkit`生成，详见[环境数据生成](./../tools/toolkit.html#环境数据生成)，这里只描述一下它的数据构成，让我们来看看一个典型的环境数据资源的内容：

```
{
  "skybox": {
    "type": "2D",
    "map": "skybox.jpg"
  },
  "specular": {
    "type": "2D",
    "rgbd": true,
    "mipmaps": true,
    "mipmapCount": 8,
    "map": "specular.png"
  },
  "diffuse": {
    "coefficients": [
      [0.8094857154560582, 1.072061074418383, 1.381670726058194],
      [0.4531993330022066, 0.6206639008366144, 0.8139572443587766],
      [-0.004551401381201801, -0.0042687508887899826, -0.0036411318023787],
      [-0.020985594814968922, -0.01687724945396023, -0.021128338350731538],
      [0.1256484901729441, 0.18119453030438287, 0.24183004841815578],
      [-0.0023734980925293335, -0.005654419816258108, -0.008260709190512553],
      [0.032220320622268775, 0.01634986420924315, -0.002981050574747357],
      [-0.010824356719832657, -0.004307541280643478, 0.003995962041610451],
      [-0.019970535027080884, -0.025649669665237452, -0.03417036444009303]
    ]
  }
}
```

可见其主要指定了三个部分：

1. `skybox`：天空盒部分，主要是一张天空盒纹理，目前全部为**2D全景纹理**。
2. `specualr`：高光反射部分，通过一张`1:1`的烘焙好的、包括所有`mipmaps`的高光贴图实现，目前全部采用`rgbd`编码来控制体积。
3. `diffuse`：漫反射部分，通过球谐系数SH9实现。

## [#](#天空盒) 天空盒

在相机的章节里我们提到过天空盒，当`camera.background`设置为`skybox`，将使用环境组件所定义的天空盒纹理，其由两个属性定义：

1. `sky-map`：天空盒纹理，默认由环境数据提供，但也可以接受用户使用此属性覆盖。可以使用任何纹理，包括视频纹理。
2. `is-sky2d`：天空盒渲染模式是否为2D，开启时会渲染一个平铺自适应的2D背景，此时纹理应当是一张2D图。

### [#](#uniforms和宏) uniforms和宏

和渲染相关的环境数据均已全局uniform和全局宏的方式传入着色器，它们是：

| 类型 | 宏 | 说明 |
| --- | --- | --- |
| 开启环境漫反射 | `WX_USE_IBL_DIFFUSE` | bool |
| 开启环境高光反射 | `WX_USE_IBL_SPECULAR` | bool |
| 高光反射mipmaps数量 | `WX_USE_SPECULAR_MIPMAPS` | int |
| 高光反射使用RGBD | `WX_USE_SPECULAR_RGBD` | bool |

| 类型 | uniforms | 说明 |
| --- | --- | --- |
| 漫反射系数 | `u_diffuseSH` | vec3[9] |
| 漫反射曝光值 | `u_diffuseExp` | texture2d |
| 高光反射纹理 | `u_specularEnvMap` | texture2d |
| 高光反射曝光值 | `u_specularExp` | v |
| 环境和天空盒旋转 | `u_envRotation` | float |

Incorrect translation.