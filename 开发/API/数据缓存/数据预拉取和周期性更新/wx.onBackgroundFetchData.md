# [#](#wx-onBackgroundFetchData-function-listener) wx.onBackgroundFetchData(function listener)

> 基础库 2.8.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [周期性更新](../../../framework/ability/background-fetch.html)、[数据预拉取](../../../framework/ability/pre-fetch.html)

## [#](#功能描述) 功能描述

监听收到 backgroundFetch 数据事件。如果监听时请求已经完成，则事件不会触发。建议和 [wx.getBackgroundFetchData](wx.getBackgroundFetchData.html) 配合使用

## [#](#参数) 参数

### [#](#function-listener) function listener

收到 backgroundFetch 数据事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| fetchType | string | 缓存数据类别，取值为 periodic 或 pre |
| fetchedData | string | 缓存数据 |
| timeStamp | number | 客户端拿到缓存数据的时间戳 |
| path | String | 小程序页面路径 |
| query | String | 传给页面的 query 参数 |
| scene | Number | 进入小程序的场景值 |

Incorrect translation.