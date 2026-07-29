# [#](#store-gift) store-gift

> 基础库 3.8.10 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

小程序送礼物接口支持小程序调用官方组件完成一次微信礼物的赠送，送礼后，用户可通过微信【我】-【订单与卡券】查看礼物订单详情。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| present-order-id | string |  | 是 | 礼物订单id，调用“创建并发送礼物”或通过“查询礼物订单列表”open api拿到，[open api文档链接](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/business-capabilities/cooperation_shop/activity_present_cooperation_shop.html)。 | [3.8.10](../framework/compatibility.html) |
| open-id | string |  | 是 | 用户openid。 | [3.8.10](../framework/compatibility.html) |
| show-gift-card | boolean | true | 否 | 控制是否展示礼物卡片，默认展示礼物卡片。 | [3.8.10](../framework/compatibility.html) |
| bindsuccess | eventhandle |  | 否 | 打开礼物成功的回调，event.detail={code,message}。【新特性支持】微信iOS / Android版本>=8.0.61、鸿蒙版本>=8.0.15，支持在成功打开礼物并回到小程序时，触发成功回调。 | [3.8.10](../framework/compatibility.html) |
| binderror | eventhandle |  | 否 | 打开礼物失败的回调，event.detail={code,message}。 | [3.8.10](../framework/compatibility.html) |

## [#](#组件引用示例代码) 组件引用示例代码

```
<store-gift present-order-id="xxx" open-id="xxx" />

<store-gift present-order-id="xxx" open-id="xxx" show-gift-card="{{false}}" bind:success="xxx" bind:error="xxx" />
```

### [#](#detail-对象) detail 对象

| 属性名 | 类型 | 说明 |
| --- | --- | --- |
| code | Number | 状态码 |
| message | String | 错误信息 |

##### [#](#code-常见错误码) code 常见错误码

| 值 | 含义 | 备注 |
| --- | --- | --- |
| -1001 | 打开礼物失败[参数错误] | 代表调用组件的传参有误 |
| -1003 | 打开礼物失败 | 调用客户端jsapi失败，是因为客户端是测试包不支持jsapi所致 |
| -1004 | 正在loading无法打开礼物 | 正在获取礼物订单信息中，可提醒用户稍后再试 |
| -1005 | 当前客户端版本不支持礼物领取 |  |

注：其他错误码，建议提示“打开失败，请联系小程序/小游戏客服”

## [#](#Bug-Tip) Bug & Tip

1. `tip`：参数 present-order-id、open-id、show-gift-card 请在组件首次加载时传入，暂不支持在组件加载完成后调整参数。
2. `tip`：暂不支持在微信 Windows 版和微信 Mac 版的小程序上使用本组件。
3. `tip`：已于3.14.2版本支持在微信 鸿蒙 OS 版的小程序上使用本组件。
4. `tip`：礼物卡片展示时限制，最大宽度350px，最小宽度312px。
5. `tip`：组件要求微信iOS版本>=8.0.61，微信Android版本>=8.0.61，微信鸿蒙版本>=8.0.15。

Incorrect translation.