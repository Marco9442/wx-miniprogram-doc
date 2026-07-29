# [#](#LivePusherContext-applyEyeShadowMakeup-Object-object) LivePusherContext.applyEyeShadowMakeup(Object object)

> 基础库 2.14.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

添加眼影美妆特效

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| alpha | number |  | 是 | 上色程度 0-1 |
| path | string |  | 是 | 眼影资源路径 |
| blendMode | string |  | 是 |  |
| shimmerPosition | string |  | 否 | 细致效果图片资源路径 |
| shimmerPositionMD5 | string |  | 否 | 细致效果图片资源 md5 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.