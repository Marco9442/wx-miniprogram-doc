# [#](#LivePlayerContext-snapshot-Object-object) LivePlayerContext.snapshot(Object object)

> 基础库 2.7.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：支持

> 相关文档: [live-player 组件](../../../component/live-player.html)

## [#](#功能描述) 功能描述

截图

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | quality | string | raw | 否 | 图片的质量 | [2.10.0](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | raw | 原图 | | compressed | 压缩图 | | | | | | |
|  | sourceType | string | stream | 否 | 截取的源类型 | [2.25.0](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | stream | 截取视频源 | | view | 截取渲染后的画面 | | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempImagePath | string | 图片文件的临时路径 (本地路径) |
| width | string | 图片的宽度 |
| height | string | 图片的高度 |

Incorrect translation.