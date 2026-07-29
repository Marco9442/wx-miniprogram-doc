# [#](#wx-getWeRunData-Object-object) wx.getWeRunData(Object object)

> 基础库 1.2.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.werun
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取用户过去三十一天微信运动步数。需要先调用 [wx.login](../login/wx.login.html) 接口。步数信息会在用户主动进入小程序时更新。

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

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| encryptedData | string | 包括敏感数据在内的完整用户信息的加密数据，详细见[加密数据解密算法](../../../framework/open-ability/signature.html)。解密后得到的数据结构见后文 |  |
| iv | string | 加密算法的初始向量，详细见[加密数据解密算法](../../../framework/open-ability/signature.html) |  |
| cloudID | string | 敏感数据对应的云 ID，开通云开发的小程序才会返回，可通过云调用直接获取开放数据，详细见[云调用直接获取开放数据](../../../framework/open-ability/signature.html#method-cloud) | [2.7.0](../../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
wx.getWeRunData({
  success (res) {
    // 拿 encryptedData 到开发者后台解密开放数据
    const encryptedData = res.encryptedData
    // 或拿 cloudID 通过云调用直接获取开放数据
    const cloudID = res.cloudID
  }
})
```

## [#](#开放数据-JSON-结构) 开放数据 JSON 结构

敏感数据有两种获取方式，一是使用 [加密数据解密算法](../../../framework/open-ability/signature.html#%E5%8A%A0%E5%AF%86%E6%95%B0%E6%8D%AE%E8%A7%A3%E5%AF%86%E7%AE%97%E6%B3%95) 。
获取得到的开放数据为以下 json 结构：

```
{
  "stepInfoList": [
    {
      "timestamp": 1445866601,
      "step": 100
    },
    {
      "timestamp": 1445876601,
      "step": 120
    }
  ]
}
```

stepInfoList 中，每一项结构如下：

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| timestamp | number | 时间戳，表示数据对应的时间 |
| step | number | 微信运动步数 |

Incorrect translation.