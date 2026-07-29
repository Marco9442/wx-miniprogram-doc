# [#](#string-wx-getApiCategory) string wx.getApiCategory()

> 基础库 2.33.0 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

获取当前 API 类别

## [#](#返回值) 返回值

### [#](#string) string

API 类别

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

Incorrect translation.