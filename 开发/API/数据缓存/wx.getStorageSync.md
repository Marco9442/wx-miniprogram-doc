# [#](#any-wx-getStorageSync-string-key) any wx.getStorageSync(string key)

> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

从本地缓存中同步获取指定 key 的内容。

## [#](#参数) 参数

### [#](#string-key) string key

本地缓存中指定的 key

## [#](#返回值) 返回值

### [#](#any) any

key对应的内容

## [#](#注意) 注意

storage 应只用来进行数据的持久化存储，不应用于运行时的数据传递或全局状态管理。启动过程中过多的同步读写存储，会显著影响启动耗时。

## [#](#示例代码) 示例代码

```
try {
  var value = wx.getStorageSync('key')
  if (value) {
    // Do something with return value
  }
} catch (e) {
  // Do something when catch error
}
```

Incorrect translation.