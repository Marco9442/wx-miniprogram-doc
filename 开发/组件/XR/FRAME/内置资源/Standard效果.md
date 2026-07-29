# [#](#Standard-标准物理光照渲染) Standard 标准物理光照渲染

`Standard` 材质基于标准的 `PBR` 进行实现。

`PBR(Physically Based Rendering)` 是指使用基于物理原理和微平面理论建模的着色/光照模型，以及使用从现实中测量的表面参数来准确表示真实世界材质的渲染理念。

![end](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-end.2fbbe1a4.jpg)

使用 `PBR` 的优势

- 基于物理模型与数学推演带来的效果的 `真实`。
- 艺术导向性的、标准化的美术参数带来的 `易用` 与 `效果一致`。

xr-frame 使用 `PBR` 有以下两种方式

1. 使用带光照材质的 [glTF](./../gltf/) 资源，目前主流的各类 `DCC工具` (Digital Content Create) 都可以产出这种业界通用的格式。
2. 使用内置的 `standard` 创建材质，并设置所需的不同 `uniform` 来进行对应渲染。

## [#](#创建-standard-材质进行渲染) 创建 standard 材质进行渲染

使用 standard 材质进行渲染时，可以设置以下的 `uniform` 来决定渲染效果。

各系数的美术意义可以参考 [创建PBR纹理实用指南](https://substance3d.adobe.com/tutorials/courses/the-pbr-guide-part2-zh)。

### [#](#基础色-baseColor) 基础色 (baseColor)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_baseColorMap | texture | 颜色贴图，颜色空间为 `SRGB` | 默认未使用 |
| u\_baseColorFactor | vec4 | 颜色因子，颜色空间为 `SRGB` | 1, 1, 1, 1 |

基础色表示物体的 `表面颜色`，`PBR` 中可以认为影响 电介质(非金属)漫反射 与 金属反射率值。

```
vec4 baseColor = vec4(1.0, 1.0, 1.0, 1.0);
// 若设定基础色贴图
baseColor *= SRGBtoLINEAR(u_baseColorMap);
// 若设定基础色因子，glTF情况下，传入LINEAR空间颜色，不进行颜色空间转化
baseColor *= SRGBtoLINEAR(u_baseColorFactor);
// 若设定顶点色
baseColor *= vec4(v_Color, 1.0);
```

`基础色贴图`：左侧为只有基础色效果；右侧为基础色贴图
![baseColor](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-basecolor.bd1aceb7.jpg)

### [#](#金属度粗糙度-metallic-rougness) 金属度粗糙度 (metallic rougness)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_metallicRoughnessMap | texture | 金属粗糙度贴图，g 部分为粗糙度，b 部分为金属度 | 默认未使用 |
| u\_metallicMap | texture | 金属度贴图，未使用金属粗糙度贴图时才生效 | 默认未使用 |
| u\_roughnessMap | texture | 粗糙度度贴图，未使用金属粗糙度贴图时才生效 | 默认未使用 |
| u\_metallicRoughnessValues | vec2 | 金属粗糙度因子，第一位为金属度，第二位为粗糙度 | 0, 1 |
| u\_ior | float | 折射率，默认值可以认为类似塑料折射率 | 1.5 |

`金属度` 表示 哪些区域是粗金属（0=电介质，1=金属），影响 电介质模型 与 金属模型 的 `线性混合`。

`粗糙度` 表示 表面粗糙度，控制 `漫反射和镜面反射`。

`IOR` 表示 折射率，控制材质的 `F0`，即0度角入射的菲涅尔反射值。

```
float metallic = u_metallicRoughnessValues.b; // 默认值 0.0，glTF 为 1.0
float roughness = u_metallicRoughnessValues.g; // 默认值 1.0
// 若设定金属度粗糙度贴图
metallic *= metallicRoughnessMap.b;
roughness *= metallicRoughnessMap.g;
// F0
f0 = min( pow2( ( u_ior - 1.0 ) / ( u_ior + 1.0 ) ) * specularColorFactor;
```

`金属度粗糙度`：左上角为金属度效果图，左下角为粗糙度效果图，数值0为黑色，数值1为白色；右侧为金属粗糙度贴图，g 部分为粗糙度，b 部分为金属度。
![metallic](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-metallicroughness.eea46c37.jpg)

### [#](#法线-Normal) 法线 (Normal)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_normalMap | texture | 法线贴图 | 默认未使用 |
| u\_normalScale | float | 法线贴图缩放，需使用法线贴图才生效 | 1 |

`法线` 可以认为是 `垂直于顶点表面` 的(单位)向量。于顶点数据中传入，用于 `PBR` 中光照相关的各类运算。

`法线贴图` 可以理解为一种高度贴图，用于`模仿表面细节`。贴图中的每个像素，代表切线空间中，将法线处理为真实法线的偏差处理。

使用法线贴图的情况下，需要传入`顶点Tangent`才能生效。

```
float normal = vNormal;
// 如果使用法线贴图，需要保证存在 vNormal 与 vTangent 以算出vTBN
mat3 vTBN = mat3( tangent, bitangent, normal );
normal = normalize( vTBN * normalMap );
```

`法线`：左侧图片为世界空间中法线效果，右侧为法线贴图。
![normal](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-normal.ec9ce4a0.jpg)

### [#](#自发光-Emissive) 自发光 (Emissive)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_emissiveMap | texture | 自发光贴图，颜色空间为 `SRGB` | 默认未使用 |
| u\_emissiveFactor | vec3 | 自发光贴图因子，颜色空间为 `LINEAR` | 0, 0, 0 |

`自发光` 表示了材质作为光源向外发送的颜色信息，颜色空间为 `SRGB`。

```
vec4 emissiveColor = u_emissiveFactor;
// 若设定自发光贴图
vec4 emissiveColor *= SRGBtoLINEAR(u_emissiveMap);
```

`自发光`：左侧图片为只有自发光的效果，右侧图片为自发光贴图。
![emissive](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-emissive.5de27f23.jpg)

### [#](#环境光遮蔽-Ambient-occlusion) 环境光遮蔽 (Ambient occlusion)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_occlusionMap | texture | 环境光遮蔽贴图 | 默认未使用 |
| u\_occlusionStrength | float | 环境光遮蔽贴图强度，需使用遮蔽贴图才生效 | 1 |

`环境光遮蔽` 指表面某点能获得多少环境中的光。该贴图只影响漫反射分配，不影响高光反射分配。

```
// 若设定遮蔽贴图
float ao = u_occlusionMap;
// 若设定遮蔽贴图 与 遮蔽因子
ao *= u_occlusionStrength;
```

`环境光遮蔽`：左侧图片为默认PBR渲染效果，右侧图片为环境光遮挡显示效果，0为完全遮蔽，1为完全不遮蔽。
![ao](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-ao.08d12bb5.jpg)

### [#](#透明剔除-alphaCutoff) 透明剔除 (alphaCutoff)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_alphaCutoff | float | 透明剔除阈值，当 baseColor 的 alpha 小于 u\_alphaCutoff 时，不进行绘制，`alphaMode` 为 `MASK` 的情况下才生效 | 0.5 |

`透明剔除` 用于进行透明度剔除。当`alphaMode` 为 `MASK` 的情况下，会不渲染 baseColor 的 alpha 小于 u\_alphaCutoff 的像素。

如需使用透明剔除，需手动设置宏 `WX_USE_ALPHA_CUTOFF`或设置渲染状态使用。

`透明剔除`：左侧图片为开启alphaCutoff效果，右侧图片为未使用alphaCutoff效果。
![alphacutoff](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-alphacut.4f90ba1b.jpg)

### [#](#清漆效果-clearcoat) 清漆效果 (clearcoat)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_clearcoatFactor | float | 清漆强度 | 0 |
| u\_clearcoatRoughnessFactor | float | 清漆粗糙度 | 0 |

`清漆效果` 可以认为是往物体表面添加透明涂层。

如需使用清漆效果，需手动设置宏 `WX_USE_CLEARCOAT`。

`清漆强度`：左侧图片为使用clearcoat效果，右侧图片为未使用clearcoat效果
![clearcoat](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-clearcoat.e4438f73.jpg)

### [#](#高光反射与光泽度-specularGlossiness) 高光反射与光泽度 (specularGlossiness)

| uniforms | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| u\_specularFactor | vec3 | 高光反射因子 | 1, 1, 1 |
| u\_glossinessFactor | float | 光泽度 | 1.0 |
| u\_specularGlossinessMap | texture | 高光光泽贴图，其中rgb部分是高光反射，a部分为光泽度 | 默认未使用 |

`高光反射与光泽度` 是 `PBR` 的另外一种渲染流程，相对于[金属度粗糙度流程](#%E9%87%91%E5%B1%9E%E5%BA%A6%E7%B2%97%E7%B3%99%E5%BA%A6-metallic-rougness)，该流程可以在高光反射贴图中控制F0。其中 `光泽度` 相当于(1 - 粗糙度)。

`漫反射部分` 的 diffuse 因子与贴图可以直接使用 [基础色 basecolor](#%E5%9F%BA%E7%A1%80%E8%89%B2-basecolor) 相关参数。

如需使用高光反射与光泽度流程，需手动设置宏 `WX_USE_SPECULARGLOSSINESS`。

`高光反射与光泽度`：左侧为使用高光反射与光泽度流程模型的渲染效果；右上为diffuse贴图(baseColorMap)；右下为specularGlossiness贴图，其中rgb部分为高光反射，a部分为光泽度。
![specularGlossiness](https://res.wx.qq.com/wxdoc/dist/assets/img/standard-specularglossiness.7c850d3b.jpg)

## [#](#standard-参数定义) standard 参数定义

- [基础色相关 basecolor](#%E5%9F%BA%E7%A1%80%E8%89%B2-basecolor)
- [金属度粗糙度相关 metallic rougness ior](#%E9%87%91%E5%B1%9E%E5%BA%A6%E7%B2%97%E7%B3%99%E5%BA%A6-metallic-rougness)
- [法线相关 normal](#%E6%B3%95%E7%BA%BF-normal)
- [自发光相关 emissive](#%E8%87%AA%E5%8F%91%E5%85%89-emissive)
- [环境光遮蔽相关 ambient occlusion](#%E7%8E%AF%E5%A2%83%E5%85%89%E9%81%AE%E8%94%BD-ambient-occlusion)
- [透明剔除相关 alphacutoff](#%E9%80%8F%E6%98%8E%E5%89%94%E9%99%A4-alphacutoff)
- [清漆效果相关 clearcoat](#%E6%B8%85%E6%BC%86%E5%BC%BA%E5%BA%A6-clearcoat)
- [高光反射与光泽度相关 specular glossiness](#%E9%AB%98%E5%85%89%E5%8F%8D%E5%B0%84%E4%B8%8E%E5%85%89%E6%B3%BD%E5%BA%A6-specularglossiness)
- 透射 transmission (TODO)
- 体积渲染 volume (TODO)

## [#](#standard-宏定义) standard 宏定义

| 宏 | 说明 | 类型 |
| --- | --- | --- |
| WX\_MANUAL\_LINEAR\_BASECOLORFACTOR | 基础色因子是否使用 `Linear空间` | bool |
| WX\_USE\_BASECOLORMAP | 是否使用基础色贴图，使用u\_baseColorMap后会自动设为true | bool |
| WX\_USE\_METALROUGHNESSMAP | 是否使用金属粗糙度贴图，使用u\_metallicRoughnessMap后会自动设为true | bool |
| WX\_USE\_EMISSIVEMAP | 是否使用自发光贴图，使用u\_emissiveMap后会自动设为true | bool |
| WX\_USE\_OCCLUSIONMAP | 是否使用遮挡贴图，使用u\_occlusionMap后会自动设为true | bool |
| WX\_USE\_COLOR\_0 | 是否使用第一位顶点色 | bool |
| WX\_USE\_ALPHA\_CUTOFF | 是否使用透明剔除 | bool |
| WX\_USE\_CLEARCOAT | 是否使用清漆效果 | bool |
| WX\_USE\_SPECULARGLOSSINESS | 是否使用高光反射与光泽度渲染流程 | bool |
| WX\_USE\_SPECULARGLOSSINESSMAP | 是否使用高光反射与光泽度渲染贴图，使用u\_specularGlossinessMap后会自动设为true | bool |

## [#](#standard-默认渲染状态) standard 默认渲染状态

```
"renderStates": {
  cullOn: true,
  blendOn: false,
  depthWrite: true,
  cullFace: Kanata.ECullMode.BACK
}
```

具体渲染状态细节可以参考 [材质支持渲染状态列表](./../render/material.html#材质支持渲染状态列表)。

## [#](#使用glTF渲染) 使用glTF渲染

参照 [glTF](./../gltf/) 文档使用。

## [#](#使用Mesh渲染) 使用Mesh渲染

```
<xr-assets>
  <!-- 加载外部环境配置 -->
  <xr-asset-load type="env-data" asset-id="env1" src="/assets/env-hdr/data.bin" />

  <!-- 加载外部贴图 -->
  <xr-asset-load type="texture" asset-id="gold-albedo" src="/assets/material/gold/albedo.png" />
  <xr-asset-load type="texture" asset-id="gold-metallic" src="/assets/material/gold/metallic.png" />
  <xr-asset-load type="texture" asset-id="gold-roughness" src="/assets/material/gold/roughness.png" />
  <xr-asset-load type="texture" asset-id="gold-ao" src="/assets/material/gold/ao.png" />

  <!-- 加载standard材质 -->
  <xr-asset-material asset-id="standard-mat" effect="standard" />
</xr-assets>

<!--
  设置环境数据，配置对应的IBL（漫反射与镜面反射）
  使用外部配置
    env1
  使用内置配置 
    xr-frame-team-workspace-day
    xr-frame-team-workspace-day2
    xr-frame-team-workspace-night
-->
<xr-env env-data="env1"/>

<!--
  添加 圆体
  使用 standard-mat 材质
  设置 金属度因子为1，粗糙度因子为1
  设置 不同类型的贴图
  设置 渲染状态 cullOn 为 false
  ...
-->
<xr-mesh
  node-id="mesh-sphere" geometry="sphere"
  material="standard-mat"
  uniforms="
    u_metallicRoughnessValues: 1 1,
    u_baseColorMap: gold-albedo,
    u_metallicMap: gold-metallic,
    u_roughnessMap: gold-roughness
  "
  states="cullOn: false"
></xr-mesh>
```

```
glTF Resource from SketchFab by @re1monsen @theblueturtle_ @Bastien Genbrugge @Willy Decarpentrie @Martin Trafas
```

Incorrect translation.