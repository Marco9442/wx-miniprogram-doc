# [#](#wx-openVideoEditor-Object-object) wx.openVideoEditor(Object object)

> 基础库 2.12.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

打开视频编辑器

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| filePath | string |  | 是 | 视频源的路径，只支持本地路径 |  |
| minDuration | string |  | 是 | 视频裁剪的最小长度 | [2.16.1](../../../framework/compatibility.html) |
| maxDuration | string |  | 是 | 视频裁剪的最大长度 | [2.16.1](../../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| duration | number | 剪辑后生成的视频文件的时长，单位毫秒（ms） |
| size | number | 剪辑后生成的视频文件大小，单位字节数（byte） |
| tempFilePath | string | 编辑后生成的视频文件的临时路径 |
| tempThumbPath | string | 编辑后生成的缩略图文件的临时路径 |

Incorrect translation.