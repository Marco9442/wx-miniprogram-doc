# [#](#wx-canvasPutImageData-Object-object-Object-this) wx.canvasPutImageData(Object object, Object this)

> 基础库 1.9.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

将像素数据绘制到画布。在自定义组件下，第二个参数传入自定义组件实例 this，以操作组件内 <canvas> 组件

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| canvasId | string |  | 是 | 画布标识，传入 [canvas](../../component/canvas.html) 组件的 canvas-id 属性。 |
| data | Uint8ClampedArray |  | 是 | 图像像素点数据，一维数组，每四项表示一个像素点的 rgba |
| x | number |  | 是 | 源图像数据在目标画布中的位置偏移量（x 轴方向的偏移量） |
| y | number |  | 是 | 源图像数据在目标画布中的位置偏移量（y 轴方向的偏移量） |
| width | number |  | 是 | 源图像数据矩形区域的宽度 |
| height | number |  | 是 | 源图像数据矩形区域的高度 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

### [#](#Object-this) Object this

在自定义组件下，当前组件实例的this，以操作组件内 [canvas](../../component/canvas.html) 组件

## [#](#示例代码) 示例代码

```
const data = new Uint8ClampedArray([255, 0, 0, 1])
wx.canvasPutImageData({
  canvasId: 'myCanvas',
  x: 0,
  y: 0,
  width: 1,
  height: 1,
  data: data,
  success (res) {}
})
```

Incorrect translation.