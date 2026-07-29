# [#](#wx-checkIsSoterEnrolledInDevice-Object-object) wx.checkIsSoterEnrolledInDevice(Object object)

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [生物认证](../../../framework/open-ability/bio-auth.html)

## [#](#功能描述) 功能描述

获取设备内是否录入如指纹等生物信息的接口

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | checkAuthMode | string |  | 是 | 认证方式 |
|  | | 合法值 | 说明 | | --- | --- | | fingerPrint | 指纹识别 | | facial | 人脸识别 | | speech | 声纹识别（暂未支持） | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| isEnrolled | boolean | 是否已录入信息 |
| errMsg | string | 错误信息 |

## [#](#示例代码) 示例代码

```
wx.checkIsSoterEnrolledInDevice({
  checkAuthMode: 'fingerPrint',
  success(res) {
    console.log(res.isEnrolled)
  }
})
```

Incorrect translation.