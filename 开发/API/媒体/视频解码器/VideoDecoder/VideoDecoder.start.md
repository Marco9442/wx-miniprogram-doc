# [#](#Promise-VideoDecoder-start-Object-object) Promise VideoDecoder.start(Object object)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

## [#](#功能描述) 功能描述

开始解码

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| source | string |  | 是 | 需要解码的视频源文件。基础库 2.13.0 以下的版本只支持本地路径。 2.13.0 开始支持 http:// 和 https:// 协议的远程路径。 |  |
| mode | number | 1 | 否 | 解码模式。0：按 pts 解码；1：以最快速度解码 |  |
| abortAudio | boolean | false | 否 | 是否不需要音频轨道 | [2.15.0](../../../framework/compatibility.html) |
| abortVideo | boolean | false | 否 | 是否不需要视频轨道 | [2.15.0](../../../framework/compatibility.html) |

## [#](#返回值) 返回值

### [#](#Promise) Promise

> 基础库 2.16.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

Incorrect translation.