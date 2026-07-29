# [#](#wx-getChatToolInfo-Object-object) wx.getChatToolInfo(Object object)

> 基础库 3.7.8 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持

> 相关文档: [聊天工具模式](../../framework/open-ability/chatTool.html)

## [#](#功能描述) 功能描述

获取聊天工具模式下的群聊信息。

需要注意的是，单聊群和多聊群下返回的群唯一标识是不同的。

1. 多聊群下返回 opengid
2. 单聊群下返回 open\_single\_roomid

同时将返回用户在群(含单聊)下的唯一标识 group\_openid。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| encryptedData | string | 包括敏感数据在内的完整转发信息的加密数据，详细见[加密数据解密算法](../../framework/open-ability/signature.html) |
| iv | string | 加密算法的初始向量，详细见[加密数据解密算法](../../framework/open-ability/signature.html) |
| cloudID | string | 敏感数据对应的云 ID，开通[云开发](../../wxcloudservice/wxcloud/basis/getting-started.html)的小程序才会返回，可通过云调用直接获取开放数据，详细见[云调用直接获取开放数据](../../framework/open-ability/signature.html#method-cloud) |

## [#](#示例代码) 示例代码

```
wx.getChatToolInfo({
  success(res) {
    // res
    {
      errMsg: 'getChatToolInfo:ok',
      encryptedData: '',
      iv: ''
    }
  },
  fail() {

  }
})
```

敏感数据有两种获取方式，一是使用 [加密数据解密算法](../../framework/open-ability/signature.html#%E5%8A%A0%E5%AF%86%E6%95%B0%E6%8D%AE%E8%A7%A3%E5%AF%86%E7%AE%97%E6%B3%95) 。
获取得到的开放数据为以下 json 结构（其中 opengid 为当前群的唯一标识）：

```
{
 "opengid": "OPENGID",       // 多聊群下返回的群唯一标识
 "open_single_roomid": "",   // 单聊群下返回的群唯一标识
 "group_openid": "",         // 用户在当前群的唯一标识
 "chat_type": 3,             // 聊天室类型
}
```

Incorrect translation.