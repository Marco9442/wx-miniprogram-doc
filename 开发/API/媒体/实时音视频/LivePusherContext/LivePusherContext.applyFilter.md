# [#](#LivePusherContext-applyFilter-Object-object) LivePusherContext.applyFilter(Object object)

> 基础库 2.14.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

添加滤镜效果

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| path | string |  | 是 | 滤镜资源路径 |
| alpha | number |  | 是 | 滤镜效果透明度，范围是 0-1 |
| md5 | string |  | 否 | 滤镜资源 md5 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.