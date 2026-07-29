# [#](#wx-batchSetStorage-Object-object) wx.batchSetStorage(Object object)

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

将数据批量存储在本地缓存中指定的 key 中。会覆盖掉原来该 key 对应的内容。除非用户主动删除或因存储空间原因被系统清理，否则数据都一直可用。单个 key 允许存储的最大数据长度为 1MB，所有数据存储上限为 10MB。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| kvList | Array |  | 是 | [{ key, value }] |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.setStorage({
  key:"key",
  data:"value"
})
```

```
// 开启加密存储
wx.batchSetStorage({
  kvList: [{
    key: 'key',
    value: 'value',
  }],
})
```

Incorrect translation.