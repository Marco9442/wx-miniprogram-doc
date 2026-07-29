# [#](#wx-canvasGetImageData-Object-object-Object-this) wx.canvasGetImageData(Object object, Object this)

> 基础库 1.9.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

获取 canvas 区域隐含的像素数据。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| canvasId | string |  | 是 | 画布标识，传入 [canvas](../../component/canvas.html) 组件的 `canvas-id` 属性。 |
| x | number |  | 是 | 将要被提取的图像数据矩形区域的左上角横坐标 |
| y | number |  | 是 | 将要被提取的图像数据矩形区域的左上角纵坐标 |
| width | number |  | 是 | 将要被提取的图像数据矩形区域的宽度 |
| height | number |  | 是 | 将要被提取的图像数据矩形区域的高度 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 图像数据矩形的宽度 |
| height | number | 图像数据矩形的高度 |
| data | Uint8ClampedArray | 图像像素点数据，一维数组，每四项表示一个像素点的 rgba |

### [#](#Object-this) Object this

在自定义组件下，当前组件实例的this，以操作组件内 [canvas](../../component/canvas.html) 组件

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/yufmRjmZ7W8f "在开发者工具中预览效果")

```
wx.canvasGetImageData({
  canvasId: 'myCanvas',
  x: 0,
  y: 0,
  width: 100,
  height: 100,
  success(res) {
    console.log(res.width) // 100
    console.log(res.height) // 100
    console.log(res.data instanceof Uint8ClampedArray) // true
    console.log(res.data.length) // 100 * 100 * 4
  }
})
```

Incorrect translation.