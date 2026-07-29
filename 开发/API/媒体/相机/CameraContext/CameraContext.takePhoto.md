# [#](#CameraContext-takePhoto-Object-object) CameraContext.takePhoto(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [camera 组件介绍](../../../component/camera.html)

## [#](#功能描述) 功能描述

拍摄照片

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | quality | string | normal | 否 | 成像质量 |  |
|  | | 合法值 | 说明 | | --- | --- | | high | 高质量 | | normal | 普通质量 | | low | 低质量 | | original | 原图 | | | | | | |
|  | selfieMirror | boolean | true | 否 | 是否开启镜像 | [2.22.0](../../../framework/compatibility.html) |
|  | captureMetadata | boolean | false | 否 | 是否返回照片的拍摄信息 | [3.15.0](../../../framework/compatibility.html) |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| tempImagePath | string | 照片文件的临时路径 (本地路径)，安卓是jpg图片格式，ios是png |  |
| metadata | Object | 照片的拍摄信息，仅当传入的 captureMetadata 属性值为 true 时返回该字段 | [3.15.0](../../../framework/compatibility.html) |

Incorrect translation.