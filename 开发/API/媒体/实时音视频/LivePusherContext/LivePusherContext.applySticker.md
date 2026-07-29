# [#](#LivePusherContext-applySticker-Object-object) LivePusherContext.applySticker(Object object)

> 基础库 2.14.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

添加贴纸特效

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | type | string |  | 是 | 贴纸类型 |
|  | stickers | Array.<Object> |  | 是 | 贴纸类型 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | title | string |  | 是 | 贴纸名称 | |  | path | string |  | 是 | 贴纸资源路径。资源必须为一个资源文件夹路径或一个压缩包路径，文件夹或压缩包内的贴纸资源必须按照 `{title}_{index}.{ext}` 格式命名。其中 `{title}` 为贴纸名称；`{index}` 为帧序号，从0开始；`{ext}` 为拓展名。 | |  | len | number |  | 是 | 贴纸帧数 | |  | id | string |  | 否 | 贴纸ID | |  | pos | Array.<string> |  | 否 | 贴纸位置，格式为 [x1,y1,x2,y2] 。当 `type` 为 `'2D'` 或 `'front'` 时必填。仅 2D 贴纸和前景贴纸有效 | |  | md5 | string |  | 否 | 贴纸资源 md5 | |  | active | number | -1 | 否 | 贴纸触发动作 | |  | | 合法值 | 说明 | | --- | --- | | -1 | 循环播放 | | 10 | 张嘴 | | 11 | 噘嘴/kiss | | 12 | 眨/闭左眼 | | 13 | 眨/闭右眼 | | 14 | 眨/闭眼 | | 15 | 挑眉毛 | | 16 | 左右摇头 | | 17 | 上下点头 | | 100 | 比心 | | 101 | 张开手掌 | | 102 | 剪刀手/比耶/胜利 | | 103 | 握拳 | | 104 | 数字1 | | 105 | 我爱你 | | 106 | 点赞 | | 107 | OK | | 108 | Rock&Roll | | 109 | 数字6 | | 110 | 数字8 | | 111 | 暂不支持（留空） | | 112 | 双手抱拳/恭喜发财 | | | | | | |  | segtype | number | 0 | 否 | 背景贴纸展示位置。仅背景贴纸有效 | |  | | 合法值 | 说明 | | --- | --- | | 0 | 背景贴纸 | | 1 | 只在人像区域显示的贴纸 | | | | | | | | | | |
|  | templateTransSet | Object |  | 否 |  |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.