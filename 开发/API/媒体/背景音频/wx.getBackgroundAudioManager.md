# [#](#BackgroundAudioManager-wx-getBackgroundAudioManager) [BackgroundAudioManager](BackgroundAudioManager.html) wx.getBackgroundAudioManager()

> 基础库 1.2.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取**全局唯一**的背景音频管理器。
小程序切入后台，如果音频处于播放状态，可以继续播放。但是后台状态不能通过调用API操纵音频的播放状态。

从微信客户端6.7.2版本开始，若需要在小程序切后台后继续播放音频，需要在 [app.json](../../../reference/configuration/app.html) 中配置 `requiredBackgroundModes` 属性。开发版和体验版上可以直接生效，正式版还需通过审核。

## [#](#返回值) 返回值

### [#](#BackgroundAudioManager) [BackgroundAudioManager](BackgroundAudioManager.html)

Incorrect translation.