# [#](#wx-onAudioInterruptionBegin-function-listener) wx.onAudioInterruptionBegin(function listener)

> 基础库 2.6.2 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

监听音频因为受到系统占用而被中断开始事件。以下场景会触发此事件：闹钟、电话、FaceTime 通话、微信语音聊天、微信视频聊天、有声广告开始播放、实名认证页面弹出等。此事件触发后，小程序内所有音频会暂停。

## [#](#参数) 参数

### [#](#function-listener) function listener

音频因为受到系统占用而被中断开始事件的监听函数

Incorrect translation.