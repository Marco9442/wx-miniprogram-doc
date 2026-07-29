# [#](#Simple-无光照渲染) Simple 无光照渲染

`Simple` 材质基于最基本的 `无光照` 情况进行实现。

使用该材质渲染的物体，`不受任何光源影响，渲染性能最高`。

![simple](https://res.wx.qq.com/wxdoc/dist/assets/img/simple-basic.d84708ee.jpg)

## [#](#simple-参数定义) simple 参数定义

| 名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_baseColorMap | texture | 颜色贴图，颜色空间为 `SRGB` | 默认未使用 |
| u\_baseColorFactor | vec4 | 颜色因子，颜色空间为 `SRGB` | 1, 1, 1, 1 |

## [#](#simple-宏定义) simple 宏定义

| 宏 | 说明 | 类型 |
| --- | --- | --- |
| WX\_USE\_BASECOLORMAP | 是否使用基础色贴图，使用u\_baseColorMap后会自动设为true | bool |

## [#](#使用glTF渲染) 使用glTF渲染

参照 [glTF](./../gltf/) 文档使用 `Unlit` 材质资源即可。

## [#](#使用Mesh渲染) 使用Mesh渲染

```
<!-- 加载simple材质 -->
<xr-asset-material asset-id="simple-mat" effect="simple" />
<!--
  添加 圆体
  默认使用 simple 材质
  设置 颜色因子为 红色
-->
<xr-mesh
  node-id="mesh-sphere" geometry="sphere"
  material="simple-mat"
  uniforms="
    u_baseColorFactor: 1 0 0 1
  "
></xr-mesh>
```

Incorrect translation.