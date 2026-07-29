# [#](#wx-canvasToTempFilePath-Object-object-Object-this) wx.canvasToTempFilePath(Object object, Object this)

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

把当前画布指定区域的内容导出生成指定大小的图片。在 `draw()` 回调里调用该方法才能保证图片导出成功。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | x | number | 0 | 否 | 指定的画布区域的左上角横坐标 | [1.2.0](../../framework/compatibility.html) |
|  | y | number | 0 | 否 | 指定的画布区域的左上角纵坐标 | [1.2.0](../../framework/compatibility.html) |
|  | width | number | canvas宽度-x | 否 | 指定的画布区域的宽度 | [1.2.0](../../framework/compatibility.html) |
|  | height | number | canvas高度-y | 否 | 指定的画布区域的高度 | [1.2.0](../../framework/compatibility.html) |
|  | destWidth | number | width\*屏幕像素密度 | 否 | 输出的图片的宽度 | [1.2.0](../../framework/compatibility.html) |
|  | destHeight | number | height\*屏幕像素密度 | 否 | 输出的图片的高度 | [1.2.0](../../framework/compatibility.html) |
|  | canvasId | string |  | 否 | 画布标识，传入 [canvas](../../component/canvas.html) 组件的 canvas-id |  |
|  | canvas | Object |  | 否 | 画布标识，传入 [canvas](../../component/canvas.html) 组件实例 （canvas type="2d" 时使用该属性）。 |  |
|  | fileType | string | png | 否 | 目标文件的类型 | [1.7.0](../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | jpg | jpg 图片 | | png | png 图片 | | | | | | |
|  | quality | number |  | 否 | 图片的质量，目前仅对 jpg 有效。取值范围为 (0, 1]，不在范围内时当作 1.0 处理。 | [1.7.0](../../framework/compatibility.html) |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | string | 生成文件的临时路径 (本地路径) |

### [#](#Object-this) Object this

在自定义组件下，当前组件实例的this，以操作组件内 [canvas](../../component/canvas.html) 组件

## [#](#示例代码) 示例代码

```
wx.canvasToTempFilePath({
  x: 100,
  y: 200,
  width: 50,
  height: 50,
  destWidth: 100,
  destHeight: 100,
  canvasId: 'myCanvas',
  success(res) {
    console.log(res.tempFilePath)
  }
})
```

Incorrect translation.