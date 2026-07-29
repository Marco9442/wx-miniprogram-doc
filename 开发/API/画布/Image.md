# [#](#Image) Image

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

图片对象

## [#](#属性) 属性

### [#](#string-src) string src

图片的 URL。v2.11.0 起支持传递 base64 Data URI

### [#](#number-width) number width

图片的真实宽度

### [#](#number-height) number height

图片的真实高度

### [#](#string-referrerPolicy) string referrerPolicy

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

`origin`: 发送完整的referrer; `no-referrer`: 不发送。格式固定为 `https://servicewechat.com/{appid}/{version}/page-frame.html`，其中 {appid} 为小程序的 appid，{version} 为小程序的版本号，版本号为 0 表示为开发版、体验版以及审核版本，版本号为 devtools 表示为开发者工具，其余为正式版本；

### [#](#function-onload) function onload

图片加载完成后触发的回调函数

### [#](#function-onerror) function onerror

图片加载发生错误后触发的回调函数

Incorrect translation.