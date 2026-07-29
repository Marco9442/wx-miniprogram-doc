# [#](#wx-removeStorage-Object-object) wx.removeStorage(Object object)

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

从本地缓存中移除指定 key。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| key | string |  | 是 | 本地缓存中指定的 key |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.removeStorage({
  key: 'key',
  success (res) {
    console.log(res)
  }
})
```

```
try {
  wx.removeStorageSync('key')
} catch (e) {
  // Do something when catch error
}
```

Incorrect translation.