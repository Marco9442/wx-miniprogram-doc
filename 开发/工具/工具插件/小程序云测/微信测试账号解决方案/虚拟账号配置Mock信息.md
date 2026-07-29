云测服务可配置虚拟账号信息，例如定位信息、请求Request

## [#](#虚拟账号配置) 虚拟账号配置

虚拟账号的配置在 `项目管理`，`虚拟账号配置` 中配置

![](https://res8.wxqcloud.qq.com.cn/wxdoc/ff020501-d1ff-474d-b949-37a2e96403dd.png)

## [#](#虚拟账号mock示例) 虚拟账号mock示例

目前支持配置虚拟账号的 **定位**`wx.getLocation(Object object)`的回调信息 及 **请求Request** 信息

![](https://res8.wxqcloud.qq.com.cn/wxdoc/4662e1f3-a323-4f68-afd4-9ca6edb33ad9.png)

例如，配置请求Request规则及回调信息

```
{
    "rule": ".*/SendMsg\\?.*", 
    "success": {"data": "mock result1", "statusCode": 200}
}
```

若需Mock虚拟账号的手机号，可参考 [虚拟账号手机号Mock方案](phone_mock)

## [#](#需要帮助) 需要帮助

如果你任何建议或需求，欢迎前往 [需要帮助](help) 页面，扫码加入云测官方企微群，联系群主反馈。

Incorrect translation.