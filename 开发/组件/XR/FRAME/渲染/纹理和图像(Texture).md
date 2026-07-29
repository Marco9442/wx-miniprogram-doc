# [#](#纹理) 纹理

纹理[Texture](/miniprogram/dev/api/xr-frame/classes/Texture)是GPU中的图像，供着色器采样使用。在框架中其一般被作为[材质](./material.html)的一部`uniforms`使用。

由于纹理来源的复杂性，有普通纹理、立方体纹理、视频纹理、渲染纹理等，它们均有不同的创建或者加载方式，却往往有相同的用法，所以框架为其特别约定了一套资源引用方式，详见[使用纹理](#%E4%BD%BF%E7%94%A8%E7%BA%B9%E7%90%86)一节。

## [#](#普通纹理) 普通纹理

普通纹理即2D纹理，创建普通纹理一般有以下几种方式：

### [#](#通过加载器) 通过加载器

通过加载器加载是最为通用的方式，我们可以用标签来加载：

```
<xr-asset-load type="texture" asset-id="waifu" src="/assets/waifu.png" options="wrapU:1,wrapV:2" />
```

也可以使用代码加载：

```
scene.assets.loadAsset({type: 'texture', assetId: 'waifu', src: '/assets/waifu.png'});
```

注意这里的`options`我们可以给纹理添加一些配置选项，比如`wrap`、`filter`等，其对应的值都是枚举，详细可见[ITextureLoaderOptions](/miniprogram/dev/api/xr-frame/interfaces/ITextureLoaderOptions)。

### [#](#代码创建) 代码创建

除了加载器，还可以通过代码创建的方式，这里的`options`详见[ITextureOptions](/miniprogram/dev/api/xr-frame/interfaces/ITextureOptions)：

```
function createGreenTexture(scene: XrFrame.Scene) {
  return scene.createTexture({
    source: [new Uint8Array([0, 1, 0, 1])],
    pixelFormat: xrFrameSystem.ETextureFormat.RGBA8,
    width: 1,
    height: 1,
    magFilter: xrFrameSystem.EFilterMode.NEAREST,
    minFilter: xrFrameSystem.EFilterMode.NEAREST,
    wrapU: xrFrameSystem.EWrapMode.CLAMP_TO_EDGE,
    wrapV: xrFrameSystem.EWrapMode.CLAMP_TO_EDGE,
    anisoLevel:1
  });
}

// 可以将其注册到资源系统
xrFrameSystem.registerTexture('green', createGreenTexture);
```

### [#](#更新) 更新

除了一开始就创建完毕，有时候开发者可能需要去动态更新纹理的内容：

```
tex.update({
  buffer: source,
  xoffset: 0, yoffset: 0,
  width: 256, height: 256
});
```

这里面的`buffer`可以是`ArrayBuffer`、`ArrayBufferView`或者`IImage`（图像）。

### [#](#图像) 图像

图像资源在框架中一般用于作为纹理的`source`或者AR识别的来源等，有两种方式来创建图片，首先是`xml`中：

```
<xr-asset-load type="image" asset-id="waifu-img" src="/assets/waifu.png" />
```

也可以用代码加载：

```
scene.createImage({type: 'texture', assetId: 'waifu-img', src: '/assets/waifu.png'})
```

还可以代码创建：

```
const image = scene.createImage();
image.onload = () => {};
image.onerror = error => {};
image.src = '/assets/waifu.png';
```

## [#](#立方体纹理) 立方体纹理

立方体纹理[CubeTexture](/miniprogram/dev/api/xr-frame/classes/CubeTexture)是一种特殊的纹理，一般用于实现天空盒或者环境贴图，虽然在框架中一般使用普通全景纹理，但仍然提供给开发者一个选择。

### [#](#通过加载器-2) 通过加载器

立方体纹理的创建也可以通过加载的方式创建。用`xml`加载：

```
<xr-asset-load
  type="cube-texture" asset-id="sky" src="/assets/sky/"
  options="faces: right.jpg left.jpg top.jpg bottom.jpg front.jpg back.jpg,wrapU:1,wrapV:2"
/>
```

或是使用代码加载：

```
scene.assets.loadAsset({
  type: 'cube-texture', assetId: 'sky', src: '/assets/sky/',
  options: {faces: ['right.jpg', 'left.jpg', 'top.jpg', 'bottom.jpg', 'front.jpg', 'back.jpg']}
});
```

`options`中除了`faces`用于配置每个面的纹理地址，其他参数和`TextureLoader`一致。

### [#](#代码创建-2) 代码创建

也可以代码创建，通过注册加入资源系统：

```
function createGreenCubeTexture(scene: XrFrame.Scene) {
  const buffer = new Uint8Array([0, 1, 0, 1]);
  return scene.createTexture({
    type: xrFrameSystem.ETextureType.Cube,
    slices: 6,
    source: [buffer, buffer, buffer, buffer, buffer, buffer],
    pixelFormat: xrFrameSystem.ETextureFormat.RGBA8,
    width: 1,
    height: 1,
    magFilter: xrFrameSystem.EFilterMode.NEAREST,
    minFilter: xrFrameSystem.EFilterMode.NEAREST,
    wrapU: xrFrameSystem.EWrapMode.CLAMP_TO_EDGE,
    wrapV: xrFrameSystem.EWrapMode.CLAMP_TO_EDGE,
    anisoLevel:1
  });
}

// 可以将其注册到资源系统
xrFrameSystem.registerCubeTexture('green', createGreenCubeTexture);
```

可见其实它也是一种普通的纹理，只不过类型不一样。

立方体纹理也支持更新，和普通纹理基本一致，只不过必须提供`slice`参数。

## [#](#视频纹理) 视频纹理

有时候我们需要将视频放入场景中进行渲染，使用视频纹理[VideoTexture](/miniprogram/dev/api/xr-frame/classes/CubeTexture)资源就可以实现这个需求。视频纹理本质上是创建一个普通纹理，然后定时用视频解码数据对它进行更新。

### [#](#通过加载器-3) 通过加载器

视频纹理的创建也可以通过加载的方式创建。用`xml`加载：

```
<xr-asset-load
  type="video-texture" asset-id="vt" src="/assets/video.mp4"
  options="autoPlay:true,loop:true,abortAudio:false,placeHolder:/assets/video.jpg"
/>
```

或是使用代码加载：

```
scene.assets.loadAsset({
  type: 'video-texture', assetId: 'vt', src: '/assets/video.mp4',
  options: {autoPlay: true}
});
```

注意到视频纹理的几个选项，`autoPlay`开启后视频加载成功时会自动播放，`loop`开启时会循环播放，`abortAudio`用于指定是否要禁止声音（默认禁止），`placeHolder`则是作为视频尚未加载成功时的一个占位图，可选。

> 特别注意，**`placeHolder`的尺寸必须和视频完全一致**！！！

### [#](#代码创建-3) 代码创建

视频纹理也可以手动在代码中创建：

```
const vt = await createVideoTexture({src, autoPlay, loop, placeHolder});
```

注意这是个异步方法，在有`placeHolder`时会在图片加载完毕时返回，否则将在视频准备好时返回。

### [#](#控制) 控制

视频纹理对于开发者而言主要是视频，所以我们提供了一些用于控制视频播放的方法：

```
// 开始播放，异步方法
await vt.play();

// 从`pos`秒开始播放，异步方法
await vt.seek(pos);

// 停止播放
vt.stop();

// 释放视频
vt.release();

// 在播放结束并且非loop的情况下，会执行
vt.onEnd = () => {};

// 在基础库`v2.33.0`及以上，提供了暂停/唤醒方法
// 同时可以配合新暴露的播放状态使用
const xrSystem = wx.getXrFrameSystem();
if (vt.state === xrSystem.EVideoState.Playing) {
  vt.pause();
} else if (vt.state === xrSystem.EVideoState.Paused) {
  vt.resume();
}
```

注意，如果是自己创建的视频资源，请务必**自己调用`release`方法释放**！！！

## [#](#渲染纹理) 渲染纹理

渲染纹理比较特殊，详见[渲染纹理](./render-texture.html)。

## [#](#使用纹理) 使用纹理

加载或者创建了纹理后，便可以在组件或者材质的`uniforms`中使用。但通过以上的章节，我们知道了纹理的种类有许多，虽然组件数据可以通过指定具体的类型，比如`cube-texture`来取得具体的类型的资源，但对于`uniforms`来说是无法判断的，同时也比较繁琐。

为了解决这个问题，我们遵循**约定大于配置**的原则，对于所有这些纹理资源，开发者只需要将组件数据类型指定为`texture`，加上不同的前缀，资源系统会自动匹配获取对应的资源：

1. 不加前缀，取得普通纹理。
2. `cube-`前缀，取得立方体纹理资源。
3. `video-`前缀，取得视频纹理。
4. `render-`前缀，取得渲染纹理。

如果是应用于`uniforms`中，开发者不需要自己去关心它们的区别，只需要`uniforms="u_baseColorMap:video-vt"`这样即可，但如果是自定义组件数据，就需要开发者自己处理一下了：

```
onUpdate(data: {texture: XrFrame.Texture | XrFrame.ITextureWrapper}) {
  const realTex = xrFrameSystem.isTextureWrapper(data.texture)
    ? data.texture.texture
    : data.texture;
}
```

Incorrect translation.