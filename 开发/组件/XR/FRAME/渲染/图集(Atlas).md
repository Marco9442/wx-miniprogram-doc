# [#](#图集) 图集

图集[Atlas](/miniprogram/dev/api/xr-frame/classes/Atlas)是一种资源，可以优化渲染流程和资源，在业界中用于精灵动画和UI比较多。它将一些散碎的小图拼接为一张大图，加之偏移数据`uvMatrix`或者`uvST`，能有效减少渲染时的纹理数量和切换次数。

目前图集在框架中主要配合[粒子系统](./particle.html)使用。

## [#](#创建图集) 创建图集

`xr-frame`使用的图集是 标准，提供了以下几种方式来创建：

### [#](#工具离线生成，加载器创建) 工具离线生成，加载器创建

最推荐的方式是使用工具去离线生成图集，比如[Shoebox](https://www.renderhjs.net/shoebox/)，输出后将描述文件`js`后缀改为`json`即可。生成后的图像和描述文件大致为：

![](https://res.wx.qq.com/wxdoc/dist/assets/img/atlas-1.a582bcae.jpg)

之后可以通过加载器加载，我们可以用标签来加载：

```
<xr-asset-load type="atlas" asset-id="numbers" src="/assets/numbers.json" />
```

也可以使用代码加载：

```
scene.assets.loadAsset({type: 'atlas', assetId: 'numbers', src: '/assets/numbers.png'});
```

### [#](#代码创建) 代码创建

### [#](#代码创建-2) 代码创建

除了加载器，还可以通过代码创建的方式，这里的`options`详见[IAtlasCreationOptions](/miniprogram/dev/api/xr-frame/interfaces/IAtlasCreationOptions)：

```
// 通过配置创建
const atlas = xrFrameSystem.Atlas.CREATE_FROM_TEXTURE(scene, texture, options);
```

当然也有完全通过格子创建空图集的方式，详见[CREATE\_FROM\_TEXTURE](/miniprogram/dev/api/xr-frame/interfaces/AtlasC#CREATE_FROM_TEXTURE)。

## [#](#使用图集) 使用图集

加载完的图集提供了几个方法来供开发者在不同场景使用：

```
// 获取纹理
const texture = atlas.texture;

// 获取UV矩阵，matrix3
const uvMatrix = atlas.getUVMatrix(frameName);

// 获取UV缩放和偏移，[sx, sy, tx, ty]。
const uvST = atlas.getUVST(frameName);
```

Incorrect translation.