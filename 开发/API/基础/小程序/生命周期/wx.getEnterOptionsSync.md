# [#](#Object-wx-getEnterOptionsSync) Object wx.getEnterOptionsSync()

> 基础库 2.9.4 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.4](../../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取本次小程序启动时的参数。如果当前是冷启动，则返回值与 [`App.onLaunch`](../../../../reference/api/App.html#onLaunch-Object-object) 的回调参数一致；如果当前是热启动，则返回值与 [`App.onShow`](../../../../reference/api/App.html#onShow-Object-object) 一致。

## [#](#返回值) 返回值

### [#](#Object) Object

启动参数

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | path | string | 启动小程序的路径 (代码包路径) |  |
|  | scene | number | 启动小程序的[场景值](../../../../framework/app-service/scene.html) |  |
|  | query | Record.<string, string> | 启动小程序的 query 参数 |  |
|  | shareTicket | string | shareTicket，详见[获取更多转发信息](../../../../framework/open-ability/share.html#获取更多转发信息) |  |
|  | referrerInfo | Object | 来源信息。从另一个小程序、公众号或 App 进入小程序时返回。否则返回 `{}`。(参见后文注意) |  |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | appId | string | 来源小程序、公众号或 App 的 appId | |  | extraData | Object | 来源小程序传过来的数据，scene=1037或1038时支持 | | | | |
|  | forwardMaterials | Array.<Object> | 打开的文件信息数组，只有从聊天素材场景打开（scene为1173）才会携带该参数 |  |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | type | string | 文件的mimetype类型 | |  | name | string | 文件名 | |  | path | string | 文件路径（如果是webview则是url） | |  | size | number | 文件大小 | | | | |
|  | chatType | number | 从微信群聊/单聊打开小程序时，chatType 表示具体微信群聊/单聊类型 |  |
|  | | 合法值 | 说明 | | --- | --- | | 1 | 微信联系人单聊 | | 2 | 企业微信联系人单聊 | | 3 | 普通微信群聊 | | 4 | 企业微信互通群聊 | | | | |
|  | hostExtraData | Object | 宿主传递的数据，第三方 app 中运行小程序时返回 |  |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | host\_scene | string | 宿主app对应的场景值 | | | | |
|  | apiCategory | string | API 类别 | [2.20.0](../../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | default | 默认类别 | | nativeFunctionalized | 原生功能化，视频号直播商品、商品橱窗等场景打开的小程序 | | browseOnly | 仅浏览，朋友圈快照页等场景打开的小程序 | | embedded | 内嵌，通过打开半屏小程序能力打开的小程序 | | chatTool | 聊天工具，通过打开聊天工具能力打开的小程序 | | | | |

## [#](#返回有效-referrerInfo-的场景) 返回有效 referrerInfo 的场景

| 场景值 | 场景 | appId含义 |
| --- | --- | --- |
| 1020 | 公众号 profile 页相关小程序列表 | 来源公众号 |
| 1035 | 公众号自定义菜单 | 来源公众号 |
| 1036 | App 分享消息卡片 | 来源App |
| 1037 | 小程序打开小程序 | 来源小程序 |
| 1038 | 从另一个小程序返回 | 来源小程序 |
| 1043 | 公众号模板消息 | 来源公众号 |

## [#](#不同-apiCategory-场景下的-API-限制) 不同 apiCategory 场景下的 API 限制

`X` 表示 API 被限制无法使用；不在表格中的 API 不限制。

|  | default | nativeFunctionalized | browseOnly | embedded | chatTool |
| --- | --- | --- | --- | --- | --- |
| openSetting |  |  | `X` |  |  |
| <button open-type="share"> |  | `X` | `X` | `X` | `X` |
| <button open-type="feedback"> |  |  | `X` |  |  |
| <button open-type="open-setting"> |  |  | `X` |  |  |
| navigateToMiniProgram |  | `X` | `X` |  | `X` |
| openEmbeddedMiniProgram |  | `X` | `X` | `X` | `X` |
| openOfficialAccountArticle |  |  |  |  | `X` |
| openChannelsUserProfile |  |  |  |  | `X` |
| ad |  |  |  |  | `X` |
| ad-custom |  |  |  |  | `X` |
| 小程序菜单分享 |  |  |  |  | `X` |

## [#](#注意) 注意

部分版本在无 `referrerInfo` 的时候会返回 `undefined`，建议使用 `options.referrerInfo && options.referrerInfo.appId` 进行判断。

Incorrect translation.