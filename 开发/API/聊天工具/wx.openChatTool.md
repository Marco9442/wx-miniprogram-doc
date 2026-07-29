# [#](#wx-openChatTool-Object-object) wx.openChatTool(Object object)

> 基础库 3.7.8 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：不支持

> 相关文档: [聊天工具模式](../../framework/open-ability/chatTool.html)

## [#](#功能描述) 功能描述

进入聊天工具模式。

1. 不传入聊天室id时，微信会拉起聊天列表让用户选择，用户选择后绑定聊天室进入聊天工具模式。
2. 传入聊天室id时（群聊为opengid，单聊为open\_single\_roomid），会直接绑定该聊天室进入，此时必须传入对应的 chatType。
3. 聊天室类型可从 [[getGroupEnterInfo]](../open-api/group/wx.getGroupEnterInfo.html) 返回值中获取。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | url | string |  | 是 | 聊天工具分包内的页面路径 |
|  | roomid | string |  | 否 | 聊天室 id，不传则拉起群选择框，可以传入多聊群的 opengid 值，或者单聊群的 open\_single\_roomid 值 |
|  | chatType | number |  | 否 | 群聊类型 |
|  | | 合法值 | 说明 | | --- | --- | | 1 | 微信联系人单聊 | | 2 | 企业微信联系人单聊 | | 3 | 普通微信群聊 | | 4 | 企业微信互通群聊 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
  wx.openChatTool({
    roomid: 'open_single_roomid',
    chatType: 1
  })
```

```
  wx.openChatTool({
    roomid: 'opengid',
    chatType: 3
  })
```

Incorrect translation.