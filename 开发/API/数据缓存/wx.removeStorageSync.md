# [#](#wx-removeStorageSync-string-key) wx.removeStorageSync(string key)

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

[wx.removeStorage](wx.removeStorage.html) 的同步版本

## [#](#参数) 参数

### [#](#string-key) string key

本地缓存中指定的 key

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