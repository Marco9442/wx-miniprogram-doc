# [#](#Object-wx-getStorageInfoSync) Object wx.getStorageInfoSync()

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

[wx.getStorageInfo](wx.getStorageInfo.html) 的同步版本

## [#](#返回值) 返回值

### [#](#Object-object) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keys | Array.<string> | 当前 storage 中所有的 key |
| currentSize | number | 当前占用的空间大小, 单位 KB |
| limitSize | number | 限制的空间大小，单位 KB |

## [#](#示例代码) 示例代码

```
wx.getStorageInfo({
  success (res) {
    console.log(res.keys)
    console.log(res.currentSize)
    console.log(res.limitSize)
  }
})
```

```
try {
  const res = wx.getStorageInfoSync()
  console.log(res.keys)
  console.log(res.currentSize)
  console.log(res.limitSize)
} catch (e) {
  // Do something when catch error
}
```

Incorrect translation.