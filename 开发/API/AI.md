# [#](#wx-getInferenceEnvInfo-Object-object) wx.getInferenceEnvInfo(Object object)

> 基础库 2.30.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.30.1](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

获取通用AI推理引擎版本。使用前可参考[AI指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/inference/tutorial.html)

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

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| ver | string | AI推理引擎版本 |

## [#](#示例代码) 示例代码

```
// 获取通用AI推理引擎版本
wx.getInferenceEnvInfo({
      complete: (res) => {
        console.log(res.ver)
        console.log(res.errMsg)
      },
})
```

Incorrect translation.