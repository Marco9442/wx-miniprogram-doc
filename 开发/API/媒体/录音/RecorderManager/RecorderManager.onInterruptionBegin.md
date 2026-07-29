# [#](#RecorderManager-onInterruptionBegin-function-listener) RecorderManager.onInterruptionBegin(function listener)

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听录音因为受到系统占用而被中断开始事件。以下场景会触发此事件：微信语音聊天、微信视频聊天。此事件触发后，录音会被暂停。pause 事件在此事件后触发

## [#](#参数) 参数

### [#](#function-listener) function listener

录音因为受到系统占用而被中断开始事件的监听函数

Incorrect translation.