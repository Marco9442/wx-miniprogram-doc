# [#](#wx-getImageInfo-Object-object) wx.getImageInfo(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取图片信息。网络图片需先配置download域名才能生效。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| src | string |  | 是 | 图片的路径，支持网络路径、本地路径、代码包路径 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | width | number | 图片原始宽度，单位px。不考虑旋转。 |  |
|  | height | number | 图片原始高度，单位px。不考虑旋转。 |  |
|  | path | string | 图片的本地路径 |  |
|  | orientation | string | [拍照时设备方向](http://sylvana.net/jpegcrop/exif_orientation.html) | [1.9.90](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | up | 默认方向（手机横持拍照），对应 Exif 中的 1。或无 orientation 信息。 | | up-mirrored | 同 up，但镜像翻转，对应 Exif 中的 2 | | down | 旋转180度，对应 Exif 中的 3 | | down-mirrored | 同 down，但镜像翻转，对应 Exif 中的 4 | | left-mirrored | 同 left，但镜像翻转，对应 Exif 中的 5 | | right | 顺时针旋转90度，对应 Exif 中的 6 | | right-mirrored | 同 right，但镜像翻转，对应 Exif 中的 7 | | left | 逆时针旋转90度，对应 Exif 中的 8 | | | | |
|  | type | string | 图片格式 | [1.9.90](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | unknown | 未知格式 | | jpeg | jpeg压缩格式 | | png | png压缩格式 | | gif | gif压缩格式 | | tiff | tiff压缩格式 | | | | |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/Kd47Sbmr6yYu "在开发者工具中预览效果")

```
wx.getImageInfo({
  src: 'images/a.jpg',
  success (res) {
    console.log(res.width)
    console.log(res.height)
  }
})

wx.chooseImage({
  success (res) {
    wx.getImageInfo({
      src: res.tempFilePaths[0],
      success (res) {
        console.log(res.width)
        console.log(res.height)
      }
    })
  }
})
```

Incorrect translation.