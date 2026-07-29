# [#](#后处理) 后处理

后处理一般指一次渲染的最后环节，它接受一个相机的渲染结果，用图像处理算法对结果增强来达到一些效果，比如模糊、辉光、渐晕等等。

`xr-frame`内置的后处理系统以[相机](./camera.html)为基础，将[后处理资源](/miniprogram/dev/api/xr-frame/classes/PostProcess)组装起来，实现最终的效果。

> ⚠️ 后处理系统在框架内部涉及到渲染管线，目前暂时不接受定制，未来视情况开放。

## [#](#后处理资源) 后处理资源

单个后处理资源对应后处理中的一个步骤，我们可以用以下几种方式来创建它：

### [#](#在xml中创建) 在xml中创建

在XML中创建是最常用的使用方式

```
<xr-asset-post-process asset-id="blur" type="blur" is-hdr data="radius:10" />
```

可见我们指定了资源的`asset-id`、后处理类型`type`、是否为`is-hdr`和参数`data`。如此一来在资源系统中将会创建一个类型为`blur`、开启HDR、参数为`{radius:10}`的后处理资源`blur`。

### [#](#在代码中创建) 在代码中创建

当然，如果有需要我们也可以使用代码创建：

```
const xrFrameSystem = wx.getXrFrameSystem();

scene.assets.addAsset('post-process', 'vignette', scene.createPostProcess({
  type: 'vignette',
  isHDR: false,
  data: {
    intensity: 0,
    smoothness: 2,
    color: [0 0 0 1]
  }
}));
```

这里创建了一个类型为`vignette`的后处理资源。

## [#](#在相机中配置) 在相机中配置

有了资源，只需要将它们配置给相机便可以开启后处理效果了：

```
<xr-camera
  ......
  post-process="blur vignette"
/>
```

相机元素的`post-process`属性接受一个字符串数组，数组的每个元素都是后处理资源的`id`，它们会按照步骤顺序执行。

## [#](#修改参数) 修改参数

有时候我们想修改后处理资源的参数来调整效果，有两种方式可以实现：

### [#](#在代码中修改) 在代码中修改

一个最常用的方法就是在代码中拿到资源引用后修改：

```
const blur = scene.assets.getAssets('post-process', 'blur');
blur.data.radius = 20;
```

### [#](#使用帧动画) 使用帧动画

另一种方法是使用帧动画，指定某帧的属性为后处理资源：

```
{
  "keyframe": {
    "blur": {
      "0": {
        "asset-post-process.assetData.radius": 10
      },
      "100": {
        "asset-post-process.assetData.radius": 64
      }
    }
  },
  "animation": {
    "parent": {
      "keyframe": "blur",
      "duration": 4,
      "ease": "linear",
      "loop": -1
    }
  }
}
```

## [#](#内置后处理资源) 内置后处理资源

目前框架内置支持的后处理资源类型和对应效果可见：[内置后处理资源](./../builtin/post-process.html)。

Incorrect translation.