# [#](#CanvasContext-drawImage-string-imageResource-number-sx-number-sy-number-sWidth-number-sHeight-number-dx-number-dy-number-dWidth-number-dHeight) CanvasContext.drawImage(string imageResource, number sx, number sy, number sWidth, number sHeight, number dx, number dy, number dWidth, number dHeight)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [2.9.0](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](RenderingContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

绘制图像到画布

## [#](#参数) 参数

### [#](#string-imageResource) string imageResource

所要绘制的图片资源（网络图片要通过 getImageInfo / downloadFile 先下载）

### [#](#number-sx) number sx

需要绘制到画布中的，imageResource的矩形（裁剪）选择框的左上角 x 坐标

### [#](#number-sy) number sy

需要绘制到画布中的，imageResource的矩形（裁剪）选择框的左上角 y 坐标

### [#](#number-sWidth) number sWidth

需要绘制到画布中的，imageResource的矩形（裁剪）选择框的宽度

### [#](#number-sHeight) number sHeight

需要绘制到画布中的，imageResource的矩形（裁剪）选择框的高度

### [#](#number-dx) number dx

imageResource的左上角在目标 canvas 上 x 轴的位置

### [#](#number-dy) number dy

imageResource的左上角在目标 canvas 上 y 轴的位置

### [#](#number-dWidth) number dWidth

在目标画布上绘制imageResource的宽度，允许对绘制的imageResource进行缩放

### [#](#number-dHeight) number dHeight

在目标画布上绘制imageResource的高度，允许对绘制的imageResource进行缩放

## [#](#示例代码) 示例代码

有三个版本的写法：

- drawImage(imageResource, dx, dy)
- drawImage(imageResource, dx, dy, dWidth, dHeight)
- drawImage(imageResource, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight) 从 1.9.0 起支持

```
const ctx = wx.createCanvasContext('myCanvas')

wx.chooseImage({
  success: function(res){
    ctx.drawImage(res.tempFilePaths[0], 0, 0, 150, 100)
    ctx.draw()
  }
})
```

![](https://res.wx.qq.com/wxdoc/dist/assets/img/draw-image.22401fa6.png)

Incorrect translation.