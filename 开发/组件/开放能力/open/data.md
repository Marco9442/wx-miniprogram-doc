# [#](#open-data) open-data

用户信息相关功能已进行调整，详见 [小程序用户信息相关接口调整公告](https://developers.weixin.qq.com/community/develop/doc/000e881c7046a8fa1f4d464105b001)

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

用于展示微信开放的数据。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | type | string |  | 否 | 开放数据类型 | [1.4.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | groupName | 拉取群名称 | [1.4.0](../framework/compatibility.html) | | userNickName | 用户昵称。不再返回，展示“微信用户” | [1.9.90](../framework/compatibility.html) | | userAvatarUrl | 用户头像。不再返回，展示 [灰色头像](https://mmbiz.qpic.cn/mmbiz/icTdbqWNOwNRna42FI242Lcia07jQodd2FJGIYQfG0LAJGFxM4FbnQP6yfMxBgJ0F3YRqJCJ1aPAK2dQagdusBZg/0) | [1.9.90](../framework/compatibility.html) | | userGender | 用户性别。不再返回，将展示为空（“”） | [1.9.90](../framework/compatibility.html) | | userCity | 用户所在城市。不再返回，将展示为空（“”） | [1.9.90](../framework/compatibility.html) | | userProvince | 用户所在省份。不再返回，将展示为空（“”） | [1.9.90](../framework/compatibility.html) | | userCountry | 用户所在国家。不再返回，将展示为空（“”） | [1.9.90](../framework/compatibility.html) | | userLanguage | 用户的语言。不再返回，将展示为空（“”） | [1.9.90](../framework/compatibility.html) | | | | | | |
|  | open-gid | string |  | 否 | 当 type="groupName" 时生效, 群id | [1.4.0](../framework/compatibility.html) |
|  | lang | string | en | 否 | 当 type="user\*" 时生效，以哪种语言展示 userInfo | [1.4.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | en | 英文 | | zh\_CN | 简体中文 | | zh\_TW | 繁体中文 | | | | | | |
|  | default-text | string |  | 否 | 数据为空时的默认文案 | [2.8.1](../framework/compatibility.html) |
|  | default-avatar | string |  | 否 | 用户头像为空时的默认图片，支持相对路径和网络图片路径 | [2.8.1](../framework/compatibility.html) |
|  | binderror | eventhandle |  | 否 | 群名称或用户信息为空时触发 | [2.8.1](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | type | string |  | 否 | 开放数据类型 | [3.7.11](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | groupName | 拉取群名称 | [3.7.11](../framework/compatibility.html) | | | | | | |
|  | default-text | string |  | 否 | 数据为空时的默认文案 | [3.7.11](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：只有当前用户在此群内才能拉取到群名称
2. `tip`：关于open-gid的获取请使用 [wx.getShareInfo](../api/share/wx.getShareInfo.html)

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/vbdmRcmV67YB "在开发者工具中预览效果")

```
<open-data type="groupName" open-gid="xxxxxx"></open-data>
<open-data type="userAvatarUrl"></open-data>
<open-data type="userGender" lang="zh_CN"></open-data>
```

Incorrect translation.