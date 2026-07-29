# [#](#wx-openEmbeddedMiniProgram-Object-object) wx.openEmbeddedMiniProgram(Object object)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.26.2](../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

打开半屏小程序。接入指引请参考 [半屏小程序能力](../../framework/open-ability/openEmbeddedMiniProgram.html)。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | appId | string |  | 是 | 要打开的小程序 appId |  |
|  | path | string |  | 否 | 打开的页面路径，如果为空则打开首页。path 中 ? 后面的部分会成为 query，在小程序的 `App.onLaunch`、`App.onShow` 和 `Page.onLoad` 的回调函数或小游戏的 [wx.onShow](errorwx.onShow)) 回调函数、[wx.getLaunchOptionsSync](../base/app/life-cycle/wx.getLaunchOptionsSync.html) 中可以获取到 query 数据。对于小游戏，可以只传入 query 部分，来实现传参效果，如：传入 "?foo=bar"。 |  |
|  | extraData | object |  | 否 | 需要传递给目标小程序的数据，目标小程序可在 `App.onLaunch`，`App.onShow` 中获取到这份数据。如果跳转的是小游戏，可以在 [wx.onShow](errorwx.onShow))、[wx.getLaunchOptionsSync](../base/app/life-cycle/wx.getLaunchOptionsSync.html) 中可以获取到这份数据数据。 |  |
|  | envVersion | string | release | 否 | 要打开的小程序版本。仅在当前小程序为开发版或体验版时此参数有效。如果当前小程序是正式版，则打开的小程序必定是正式版。 |  |
|  | | 合法值 | 说明 | | --- | --- | | develop | 开发版 | | trial | 体验版 | | release | 正式版 | | | | | | |
|  | shortLink | string |  | 否 | 小程序链接，当传递该参数后，可以不传 appId 和 path。链接可以通过【小程序菜单】->【复制链接】获取。仅 verify=binding 支持。 |  |
|  | verify | string | binding | 否 | 校验方式。 | [2.24.3](../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | binding | 校验小程序管理后台的绑定关系。 | | unionProduct | 校验目标打开链接是否为[小程序联盟](https://developers.weixin.qq.com/doc/ministore/union/brief-introduction.html)商品。 | | | | | | |
|  | noRelaunchIfPathUnchanged | boolean | false | 否 | 不reLaunch目标小程序，直接打开目标跳转的小程序退后台时的页面，需满足以下条件：1. 目标跳转的小程序生命周期未被销毁；2. 且目标当次启动的path、query与上次启动相同，apiCategory以wx.getApiCategory接口的返回结果为准。 | [2.24.0](../../framework/compatibility.html) |
|  | allowFullScreen | boolean | false | 否 | 打开的小程序是否支持全屏。基础库 `3.10.0` 版本起，强制为 true | [2.33.0](../../framework/compatibility.html) |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

Incorrect translation.