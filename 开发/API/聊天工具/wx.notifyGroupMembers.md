# [#](#wx-notifyGroupMembers-Object-object) wx.notifyGroupMembers(Object object)

> 基础库 3.7.8 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：不支持

> 相关文档: [聊天工具模式](../../framework/open-ability/chatTool.html)

## [#](#功能描述) 功能描述

提醒用户完成任务，标题长度不超过 30 个字符，支持中英文和数字，中文算2个字符。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | title | string |  | 是 | 文字链标题，发送的内容将由微信拼接为：@的成员列表+“请完成：”/"请参与："+打开小程序的文字链，如「@alex @cindy 请完成：团建报名统计」。 |
|  | members | Array.<string> |  | 是 | 需要提醒的用户 group\_openid 列表 |
|  | entrancePath | string |  | 是 | 文字链跳转路径 |
|  | type | string | complete | 否 | 展示的动词 |
|  | | 合法值 | 说明 | | --- | --- | | participate | 请参与 | | complete | 请完成 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
  // 最终聊天内显示 @alex @cindy 请完成：团建报名统计
  wx.notifyGroupMembers({
    title: '团建报名统计',
    members: ['alex', 'cindy],
    entrancePath: '/path/to/page',
    type: 'complete',
  })
```

Incorrect translation.