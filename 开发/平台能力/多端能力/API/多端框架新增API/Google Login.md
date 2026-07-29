# [#](#wx-miniapp-googleLogin) wx.miniapp.googleLogin

该接口用于实现 Google 登录的功能

## [#](#前置条件) 前置条件

1、SDK 版本：iOS SDK >= 1.4.20；Android >= 1.4.14；即在开发者工具的 `project.miniapp.json` 需将 SDK 选择至符合要求的版本

2、开发者工具版本：需使用版本 >= 1.06.2411052 的 [nightly 开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)

3、开发配置：需前往开发者工具 `project.miniapp.json` 填写下方内容：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202411061956437.png)

## [#](#接口详情) 接口详情

### [#](#返回参数) 返回参数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errcode | number | 错误码 |
| errMsg | string | 错误信息 |
| userID | string | 用户的 userID |
| idToken | string | 用户的 idToken |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
 wx.miniapp.googleLogin({
        success: (res) => {
          console.log('googleLogin success', res.userID)
          console.log('googleLogin success', res.idToken)
        },
        fail:(e) =>{
          console.log('googleLogin fail', e)
        }
      })
```

## [#](#常见问题) 常见问题

### [#](#_1-出现报错：googleLogin-fail-com-google-android-gms-common-api-fbZLw-10) 1. 出现报错：googleLogin:fail:com.google.android.gms.common.api.fbZLw: 10

- 如果调用接口的时候出现 `googleLogin:fail:com.google.android.gms.common.api.fbZLw: 10` 的报错，在 Google 登录的控制台那里勾选「OAuth 2.0 客户端 ID」的时候选择「Web clint」，不要选择「Android clinet」即可。

Incorrect translation.