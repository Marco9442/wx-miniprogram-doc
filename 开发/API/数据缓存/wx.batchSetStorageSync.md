# [#](#wx-batchSetStorageSync-Array-Object-kvList) wx.batchSetStorageSync(Array.<Object> kvList)

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [存储策略](../../framework/ability/storage.html)

## [#](#功能描述) 功能描述

将数据批量存储在本地缓存中指定的 key 中。会覆盖掉原来该 key 对应的内容。除非用户主动删除或因存储空间原因被系统清理，否则数据都一直可用。单个 key 允许存储的最大数据长度为 1MB，所有数据存储上限为 10MB。

## [#](#参数) 参数

### [#](#Array-Object-kvList) Array.<Object> kvList

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| key | string |  | 是 | key 本地缓存中指定的 key |
| value | any |  | 是 | data 需要存储的内容。只支持原生类型、Date、及能够通过`JSON.stringify`序列化的对象。 |

## [#](#示例代码) 示例代码

```
try {
  wx.batchSetStorageSync([{key: 'key', value: 'value'}])
} catch (e) { }
```

Incorrect translation.