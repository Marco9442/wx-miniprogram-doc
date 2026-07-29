# [#](#wx-miniapp-login) wx.miniapp.login

跳转微信获取微信登录态

注：

1、该接口需要申请和初始化微信 open 能力，需要客户端进行相关配置

2、该接口不支持在「移动应用助手」中调试，开发者需构建 apk 或者 ipa 安装到手机后才能调试

3、该接口已支持在鸿蒙端使用

## [#](#接入前注意事项) 接入前注意事项

- 该能力依赖[微信 Open SDK](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_Pay/Vendor_Service_Center) ，需按照指引在[微信开放平台](https://open.weixin.qq.com/)创建移动应用账号，以完成相关初始化配置，详情可查看[微信移动应用能力初始化指引](../../new-capability/opensdk)
- 该接口底层的 scope 是 snsapi\_userinfo ，通过该接口获取 code 之后可以调用 [/sns/oauth2/access\_token](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_Login/Development_Guide) 接口获取 access\_token ，可通过 [/sns/userinfo](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_Login/Development_Guide) 接口获取用户信息。
- 注意：生成 access\_token 的 appid 和 secret 是微信开放平台的移动应用账号的 appid 和 secret

#### [#](#参数) 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 是 | 获取后成功回调 |

#### [#](#JSAPI-代码例子) JSAPI 代码例子

```
// login
wx.miniapp.login({
    success: (res) => {
        console.log('login success:', res.code)
    }
})
```

Incorrect translation.