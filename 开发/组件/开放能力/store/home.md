# [#](#store-home) store-home

> 基础库 3.5.5 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 鸿蒙 OS 版**：支持

> 相关文档: [微信小店指引](https://developers.weixin.qq.com/doc/store/API/basics/component.html)

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

小程序内嵌微信小店首页，展示小店首页，并进行跳转交易。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| appid | string |  | 是 | 小店appid。获取方式：[小店后台](https://store.weixin.qq.com/shop/setting/home) - 店铺管理 - 基础信息 - 账号信息 - 微信小店ID。 |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：平台规则限制，请保持组件内容完整展示且透明度、组件内部样式等未做修改，若不符合要求则会导致组件不可用，并可能导致使用本组件的能力被封禁。
2. `tip`：暂不支持在微信 Windows 版和微信 Mac 版的小程序上使用本组件。

Incorrect translation.