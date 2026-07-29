# [#](#wx-miniapp-googleLogout) wx.miniapp.googleLogout

该接口用于实现退出 Google 登录的功能

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
| errmsg | string | 错误信息 |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
 wx.miniapp.googleLogout({
   success(res) {
     console.log('googleLogout success', res)
   },
   fail(e) {
     console.log('googleLogout fail', e)
   }
 })
```

Incorrect translation.