# [#](#wx-chooseVideo-Object-object) wx.chooseVideo(Object object)

从基础库 [2.21.0](../../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.chooseMedia](wx.chooseMedia.html) 代替

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

拍摄视频或从手机相册中选视频。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | sourceType | Array.<string> | ['album', 'camera'] | 否 | 视频选择的来源 |  |
|  | | 合法值 | 说明 | | --- | --- | | album | 从相册选择视频 | | camera | 使用相机拍摄视频 | | | | | | |
|  | compressed | boolean | true | 否 | 是否压缩所选择的视频文件 | [1.6.0](../../../framework/compatibility.html) |
|  | maxDuration | number | 60 | 否 | 拍摄视频最长拍摄时间，单位秒 |  |
|  | camera | string | 'back' | 否 | 默认拉起的是前置或者后置摄像头。部分 Android 手机下由于系统 ROM 不支持无法生效 |  |
|  | | 合法值 | 说明 | | --- | --- | | back | 默认拉起后置摄像头 | | front | 默认拉起前置摄像头 | | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | string | 选定视频的临时文件路径 (本地路径) |
| duration | number | 选定视频的时间长度 |
| size | number | 选定视频的数据量大小 |
| height | number | 返回选定视频的高度 |
| width | number | 返回选定视频的宽度 |

## [#](#示例代码) 示例代码

```
wx.chooseVideo({
  sourceType: ['album','camera'],
  maxDuration: 60,
  camera: 'back',
  success(res) {
    console.log(res.tempFilePath)
  }
})
```

Incorrect translation.