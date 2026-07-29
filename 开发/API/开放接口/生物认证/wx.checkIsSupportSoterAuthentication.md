# [#](#wx-checkIsSupportSoterAuthentication-Object-object) wx.checkIsSupportSoterAuthentication(Object object)

> 基础库 1.5.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [生物认证](../../../framework/open-ability/bio-auth.html)

## [#](#功能描述) 功能描述

获取本机支持的 SOTER 生物认证方式

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | supportMode | Array.<string> | 该设备支持的可被SOTER识别的生物识别方式 |
|  | | 合法值 | 说明 | | --- | --- | | fingerPrint | 指纹识别 | | facial | 人脸识别 | | speech | 声纹识别（暂未支持） | | | |

## [#](#示例代码) 示例代码

```
wx.checkIsSupportSoterAuthentication({
  success(res) {
    // res.supportMode = [] 不具备任何被SOTER支持的生物识别方式
    // res.supportMode = ['fingerPrint'] 只支持指纹识别
    // res.supportMode = ['fingerPrint', 'facial'] 支持指纹识别和人脸识别
  }
})
```

Incorrect translation.