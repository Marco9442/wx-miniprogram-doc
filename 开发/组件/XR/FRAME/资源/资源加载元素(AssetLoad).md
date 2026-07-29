# [#](#资源加载元素) 资源加载元素

在[资源系统](./)一章中我们简略提到了几个`xml`中和资源相关的标签`xr-assets`、`xr-asset-load`等，这一章就来详细介绍一下它们。

## [#](#xr-asset-load) xr-asset-load

`xr-asset-load`是元素[XRAssetLoad](/miniprogram/dev/api/xr-frame/classes/XRAssetLoad)在`xml`中的对应，而这个元素则是组件[AssetLoad](/miniprogram/dev/api/xr-frame/classes/AssetLoad)的一个简单代理。

> 注意`xr-asset-load`标签一旦初始化，后续**不可动态修改**，并且即使移除后再次添加相同`asset-id`的资源，原先已经使用了此`id`的组件也不会更新。如果真的有高级需求，请使用脚本的方式。

若要在`xml`中使用时将其所有的参数写出，大概如下：

```
<xr-asset-load type="texture" asset-id="waifu" src="/assets/waifu.png" weight="2" options="anisoLevel:2" defer />
```

其他的属性不用多说，但大家可能会对`weight`和`defer`比较好奇。`defer`是指延迟加载，只有框架发现这个资源被组件应用了才会去真的加载它，而`weight`，则涉及到下一个要介绍的元素了。

> 在**2.28.1**版本后，内置资源同样可以使用`xr-asset-load`配合下面的`xr-assets`元素获取加载进度，只需要写好类型和资源ID即可：

```
<xr-asset-load type="env-data" asset-id="xr-frame-team-workspace-day" />
```

## [#](#xr-assets) xr-assets

`xr-assets`对应于元素[XRAssets](/miniprogram/dev/api/xr-frame/classes/XRAssets)，其是作为组件[Assets](/miniprogram/dev/api/xr-frame/classes/Assets)的一个代理。

这个元素的功能非常简单，一般使用时我们会让它将`xr-asset-load`元素包裹起来：

```
<xr-assets bind:progress="handleAssetsProgress" bind:loaded="handleAssetsLoaded">
  <xr-asset-load type="texture" asset-id="waifu" src="/assets/waifu.png" weight="2" />
  <xr-asset-load type="texture" asset-id="waifu2" src="/assets/waifu2.png" weight="1" />
</xr-assets>
```

可见，其实它本质上就是**资源组**，是为了在其下资源的加载过程中提供给开发者一些事件，来通知加载进度的。

### [#](#事件) 事件

资源组组件为元素提供了以下事件：

| 事件 | 参数 | 立即 | wxml | 时机 |
| --- | --- | --- | --- | --- |
| progress | 对象，进度`progress`，和当前资源描述`asset` | 是 | 是 | 场景第一次解析完毕 |
| loaded | 对象，成功的资源`assets`，和出的错误`errors` | 是 | 是 | 场景销毁之前 |

Incorrect translation.