# [#](#Array-any-wx-batchGetStorageSync-Array-string-keyList) Array.<any> wx.batchGetStorageSync(Array.<string> keyList)

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

从本地缓存中同步批量获取指定 key 的内容。

## [#](#参数) 参数

### [#](#Array-string-keyList) Array.<string> keyList

本地缓存中指定的 key 数组

## [#](#返回值) 返回值

### [#](#Array-any) Array.<any>

key对应的内容

## [#](#示例代码) 示例代码

```
try {
  var valueList = wx.batchGetStorageSync(['key'])
  if (valueList) {
    // Do something with return value
  }
} catch (e) {
  // Do something when catch error
}
```

对于多个key的读取, 批量读取在性能上优于多次getStorageSync读取

Incorrect translation.