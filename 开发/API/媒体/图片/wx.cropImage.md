# [#](#wx-cropImage-Object-object) wx.cropImage(Object object)

> 基础库 2.26.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

裁剪图片接口

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | src | string |  | 是 | 图片路径，图片的路径，支持本地路径、代码包路径 |
|  | cropScale | string |  | 是 | 裁剪比例 |
|  | | 合法值 | 说明 | | --- | --- | | 16:9 | 宽高比为16比9 | | 9:16 | 宽高比为9比16 | | 4:3 | 宽高比为4比3 | | 3:4 | 宽高比为3比4 | | 5:4 | 宽高比为5比4 | | 4:5 | 宽高比为4比5 | | 1:1 | 宽高比为1比1 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | string | 编辑后图片的临时文件路径 (本地路径) |

## [#](#示例代码) 示例代码

```
wx.cropImage({
  src: '', // 图片路径
  cropScale: '16:9', // 裁剪比例
})
```

Incorrect translation.