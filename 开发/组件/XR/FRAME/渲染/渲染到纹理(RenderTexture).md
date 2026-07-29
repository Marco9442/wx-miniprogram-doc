# [#](#渲染纹理) 渲染纹理

[相机](./camera.html)一章中提到了渲染目标`renderTarget`可以指定为渲染纹理，[纹理](./texture.html)也提到了渲染纹理可以作为纹理使用。可见，渲染纹理[RenderTexture](/miniprogram/dev/api/xr-frame/classes/RenderTexture)就是连接多个相机渲染之间的桥梁。

一个典型场景就是用渲染纹理来做镜子之类的效果。

## [#](#创建渲染纹理) 创建渲染纹理

创建渲染纹理有两种方式，一般我们会优先在`wxml`中进行创建。

### [#](#在wxml中创建) 在wxml中创建

在`xml`中创建需要用到`xr-asset-render-texture`标签：

```
<xr-asset-render-texture asset-id="rt" width="2048" height="1024" />
```

其中`rt`是资源id，`width`和`height`是渲染纹理的宽高。

### [#](#手动代码创建) 手动代码创建

手动代码创建直接使用`scene.createRenderTexture`即可：

```
const rt = scene.createRenderTexture({width: 2048, height: 2048});

// 当然，也可以添加到资源系统中
scene.assets.addAsset('render-texture', 'rt', rt);
```

## [#](#使用渲染纹理) 使用渲染纹理

创建完渲染纹理后便可以使用它，下面是一个在`xml`中的简单使用实例，用代码使用也是类似的：

```
<xr-node layer="1">
  <xr-mesh id="cube" node-id="mesh-cube" position="-1 0.5 1.5" scale="1 1 1" rotation="0 45 0" geometry="cube" uniforms="u_baseColorFactor:0.298 0.764 0.85 1" />
  <xr-mesh node-id="mesh-sphere" position="0 1.25 0" scale="1.25 1.25 1.25" geometry="sphere" uniforms="u_baseColorFactor:0.937 0.176 0.368 1" />
  <xr-mesh node-id="mesh-cylinder" position="1 0.7 1.5" scale="1 0.7 1" geometry="cylinder" uniforms="u_baseColorFactor:1 0.776 0.364 1" />
</xr-node>

<xr-node layer="2">
  <xr-mesh node-id="mesh-plane" position="0 0 -6" rotation="-90 0 0" scale="16 1 12" geometry="plane" uniforms="u_baseColorMap:render-rt" />
</xr-node>

<xr-node node-id="rt-camera-target" position="0 1 0"></xr-node>
<xr-camera
  position="0 1 4" clear-color="0.925 0.925 0.925 1" target="rt-camera-target" render-target="rt" cull-mask="0b011"
/>

<xr-camera
 position="0 4 6" clear-color="0.925 0.925 0.925 1" target="mesh-plane" cull-mask="0b111" camera-orbit-control=""
></xr-camera>
```

第一个相机的`render-target`设置为了`rt`，然后`mesh-plane`的`uniforms`中的一张纹理也设置为了`rt`。在绘制中就会用第一个相机先绘制到渲染纹理上，然后第二个相机绘制的物体中的那个平面在使用渲染纹理渲染。

注意这里我们用到了`layer`和`cullMask`，这个在前面的章节提到过。因为我们不想让第一个相机绘制那个平面，第二个相机则会绘制所有东西。

Incorrect translation.