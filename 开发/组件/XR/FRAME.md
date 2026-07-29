# [#](#概述) 概述

本文适合有初步了解的开发者阅读，入门请参见[**指南**](./../../../framework/xr-frame/)。

> ⚠️ `xr-frame`在基础库`v2.32.0`开始基本稳定，发布为正式版，但仍有一些功能还在开发，请见[限制和展望](#%E9%99%90%E5%88%B6%E5%92%8C%E5%B1%95%E6%9C%9B)。

**xr-frame**是一套小程序官方提供的XR/3D应用解决方案，基于混合方案实现，性能逼近原生、效果好、易用、强扩展、渐进式、遵循小程序开发标准：

```
<xr-scene>
  <xr-assets>
    <!-- 加载一个GLTF模型 -->
    <xr-asset-load type="gltf" asset-id="gltf-model" src="..." />
  </xr-assets>
  <xr-env env-data="..." />

  <xr-node>
    <!-- 将一个GLTF模型渲染在AR场景中 -->
    <xr-ar-tracker ...>
      <xr-gltf model="gltf-model" ...></xr-gltf>
    </xr-ar-tracker>
    <xr-camera is-ar-camera ...></xr-camera>
  </xr-node>
  
  <xr-node>
    <!-- 场景光照 -->
    <xr-light type="ambient" ... />
    <xr-light type="directional" ... />
  </xr-node>
</xr-scene>
```

[](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/demo.mp4)

## [#](#特性) 特性

比起目前的`Canvas`组件，**xr-frame**有以下显著的优势：

### [#](#🍰-高度整合，上手简单) 🍰 高度整合，上手简单

提供`xml`的方式来描述3D场景，并集成了AR、物理、动画、粒子、后处理等等系统，上手简单，符合小程序开发规范。

### [#](#🌈-渲染效果好) 🌈 渲染效果好

内置完整的PBR效果、环境光照、阴影，原生支持glTF资源，提供的[xr-frame-toolkit](https://github.com/wechat-miniprogram/xr-frame-toolkit)可以快速通过全景图生成环境数据。

### [#](#⚡️-高性能) ⚡️ 高性能

混合方案，渲染性能逼近原生，[xr-frame-toolkit](https://github.com/wechat-miniprogram/xr-frame-toolkit)可以对外部glTF文件进行优化，来提高加载性能，还有完善的缓存机制保证二次进入的加载性能。

### [#](#🧱-易扩展) 🧱 易扩展

扩展性强，从资源到组件元素，皆可以由高阶用户自己定制，未来还可以暴露内部的渲染管线定制能力。

## [#](#示例) 示例

上面的例子只是一部分简略代码，我们提供了丰富的示例并开源在[xr-frame-demo](https://github.com/dtysky/xr-frame-demo)，可以直接扫码体验：

![demo](https://res.wx.qq.com/wxdoc/dist/assets/img/1.697d997f.png)

以下是部分示例需要用到的扫描资源：

![](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/xr-frame-team/2dmarker/hikari-o.jpg)

典型案例 -> 扫描图片视频

![](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/portalImage.jpg)

典型案例 -> 扫描透视模型

![](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/wxball.jpg)

典型案例 -> 扫描微信球

![](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/marker/2dmarker-test.jpg)

AR案例 -> 2DMarker

![](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/demo/marker/osdmarker-test.jpg)

AR案例 -> OSD Marker

## [#](#限制和展望) 限制和展望

限制：

1. 最低要求客户端iOS**8.0.29**、安卓**8.0.30**及以上，推荐稳定版在iOS**8.0.36**、安卓**8.0.35**及以上。
2. 基础库最低**2.27.1**及以上，推荐**2.32.0**及以上。
3. 开发工具需要最新版本，建议[Nightly版本](https://developers.weixin.qq.com/miniprogram/dev/devtools/nightly.html)。
4. 小程序**全局同一时刻只能存在一个**`xr-frame`组件，否则可能会发生异常。
5. 同一个`xr-frame`组件只能存在一个`xr-scene`，并且必须为顶层。
6. 目前不支持和小程序传统标签比如`<view>`混写。
7. 目前不支持`wxml`自动补全，真机调试需要特别注意，见[真机调试文档](./../tools/debug.html#真机调试)。

同时未来还会追加更多的能力，在未来的规划中，我们还会着重致力于：

1. **XR-FRAME**内置特色的UI组件，让开发者可以在**XR-FRAME**组件中写UI，来实现一套酷炫的UI系统。
2. AR/VR能力持续增强，支持眼睛设备。
3. 交互手段进一步强化，物理碰撞、触发等功能（已完成，待发布）。
4. 工具能力强化，包括标签属性自动补全等。

想要进一步了解整个框架的架构，请看[架构](./../core/)一节。

Incorrect translation.