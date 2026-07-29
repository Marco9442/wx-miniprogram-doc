# [#](#wx-miniapp-jumpToAppStore) wx.miniapp.jumpToAppStore

该接口用于跳至当前 App 的 AppStore 下载页以及打分评论页

> iOS SDK >= 1.3.3

补充：该接口可结合 [wx.getAppBaseInfo](../diffapi/getAppBaseInfo) 获取当前应用的 `appVersion` ，检测到有新版本即可使用 `wx.miniapp.jumpToAppStore` 接口引导用户前往 AppStore 下载页

## [#](#前置条件) 前置条件

1、当前多端应用需已上架 AppStore

2、该多端应用已绑定的移动应用账号需是「审核通过」且已配置为「已上架」，以及该移动应用配置的「AppStore 下载地址」符合规范，详情可查看[获取 AppStore 下载地址指南](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/guideline/getioslink)

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202308152056257.png)

3、该接口不支持在「开发者工具」和「移动应用助手」中调试，开发者需构建 IPA 安装到手机进行调试

## [#](#接口详情) 接口详情

### [#](#参数) 参数

| **属性** | **类型** | **默认值** | **必填** | **说明** |
| --- | --- | --- | --- | --- |
| action | string |  | 否 | 只能填"write-review"，表示前往前往打分评论页；即如果不传 action 值就是前往下载页 |
| success | function |  | 是 | 获取后成功回调 |

### [#](#返回参数) 返回参数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errcode | number | 错误码 |
| errMsg | string | 错误提示 |

### [#](#错误码) 错误码

| **errCode** | **错误信息** | **说明** |
| --- | --- | --- |
| 10002401 | 该多端应用尚未上架 | 请前往开放平台设置应用为已上架 |
| 10002402 | AppStore 下载地址未审核通过 | 请前往开放平台重新提交审核 |
| 10002403 | AppStore 下载地址未校验通过 | AppStore 下载地址与 BundleID 不匹配 |
| 10002404 | 该应用为商务分发应用 | 商务分发应用不支持跳转 AppStore |
| -700100 | 跳转失败，未知错误 | 未知错误，可前往社区反馈 |
| -700101 | 跳转失败，系统版本过低 | iOS 版本过低 |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.jumpToAppStore({
    success: (res) => {
        console.log('jumpToAppStore success:', res);
    },
    fail: (res) => {
        console.log('jumpToAppStore fail:', res);
    }
});
```

### [#](#前往评论打分页) 前往评论打分页

```
wx.miniapp.jumpToAppStore({
      action: "write-review"
    })
```

Incorrect translation.