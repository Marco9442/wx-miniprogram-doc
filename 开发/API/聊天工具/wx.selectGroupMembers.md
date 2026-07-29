# [#](#wx-selectGroupMembers-Object-object) wx.selectGroupMembers(Object object)

> 基础库 3.7.8 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持

> 相关文档: [聊天工具模式](../../framework/open-ability/chatTool.html)

## [#](#功能描述) 功能描述

选择聊天室的成员，并返回选择成员的 group\_openid。若当前为群聊，则会拉起成员选择器；若当前为单聊，则直接返回双方的 group\_openid。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| maxSelectCount | number |  | 否 | 最多可选人数 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| members | Array.<string> | 所选用户在此聊天室下的唯一标识，同一个用户在不同的聊天室下id不同 |

```
  wx.selectGroupMembers({
    maxSelectCount: 3,
    success(res) {
      // res.members
    }
  })
```

Incorrect translation.