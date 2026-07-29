# [#](#image) image

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

图片。支持 JPG、PNG、SVG、WEBP、GIF 等格式，[2.3.0](../framework/compatibility.html) 起支持云文件ID。

1. 使用 svg 格式且 mode=scaleToFill 时，WebView 会居中（除非 svg 里加上 preserveAspectRatio="none"），Skyline 则会撑满
2. svg 格式不支持百分比单位
3. svg 格式不支持 <style> element

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | src | string |  | 否 | 图片资源地址 | [1.0.0](../framework/compatibility.html) |
|  | mode | string | scaleToFill | 否 | 图片裁剪、缩放的模式 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | scaleToFill | 缩放模式，不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素 |  | | aspectFit | 缩放模式，保持纵横比缩放图片，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来。 |  | | aspectFill | 缩放模式，保持纵横比缩放图片，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取。 |  | | widthFix | 缩放模式，宽度不变，高度自动变化，保持原图宽高比不变 |  | | heightFix | 缩放模式，高度不变，宽度自动变化，保持原图宽高比不变 | [2.10.3](../framework/compatibility.html) | | top | 裁剪模式，不缩放图片，只显示图片的顶部区域。仅 Webview 支持。 |  | | bottom | 裁剪模式，不缩放图片，只显示图片的底部区域。仅 Webview 支持。 |  | | center | 裁剪模式，不缩放图片，只显示图片的中间区域。仅 Webview 支持。 |  | | left | 裁剪模式，不缩放图片，只显示图片的左边区域。仅 Webview 支持。 |  | | right | 裁剪模式，不缩放图片，只显示图片的右边区域。仅 Webview 支持。 |  | | top left | 裁剪模式，不缩放图片，只显示图片的左上边区域。仅 Webview 支持。 |  | | top right | 裁剪模式，不缩放图片，只显示图片的右上边区域。仅 Webview 支持。 |  | | bottom left | 裁剪模式，不缩放图片，只显示图片的左下边区域。仅 Webview 支持。 |  | | bottom right | 裁剪模式，不缩放图片，只显示图片的右下边区域。仅 Webview 支持。 |  | | | | | | |
|  | show-menu-by-longpress | boolean | false | 否 | 长按图片显示发送给朋友、收藏、保存图片、搜一搜、打开名片/前往群聊/打开小程序（若图片中包含对应二维码或小程序码）的菜单。 | [2.7.0](../framework/compatibility.html) |
|  | binderror | eventhandle |  | 否 | 当错误发生时触发，event.detail = {errMsg} | [1.0.0](../framework/compatibility.html) |
|  | bindload | eventhandle |  | 否 | 当图片载入完毕时触发，event.detail = {height, width} | [1.0.0](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | fade-in | boolean | false | 否 | 是否渐显 |  |
|  | preload | boolean | false | 否 | 是否预加载图片，即设置图片 src 时就触发图片下载和解码 | [3.15.0](../framework/compatibility.html) |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | webp | boolean | false | 否 | 默认不解析 webP 格式，只支持网络资源 | [2.9.0](../framework/compatibility.html) |
|  | lazy-load | boolean | false | 否 | 图片懒加载，在即将进入一定范围（上下三屏）时才开始加载。Skyline 默认懒加载。 | [1.5.0](../framework/compatibility.html) |
|  | forceHttps | boolean | false | 否 | 自动将 http 链接替换为 https 链接 | [3.9.1](../framework/compatibility.html) |

## [#](#支持长按识别的码) 支持长按识别的码

| 类型 | 说明 | 最低版本 |
| --- | --- | --- |
| 小程序码 |  |  |
| 微信个人码 |  | [2.18.0](../framework/compatibility.html) |
| 企业微信个人码 |  | [2.18.0](../framework/compatibility.html) |
| 普通群码 | 指仅包含微信用户的群 | [2.18.0](../framework/compatibility.html) |
| 互通群码 | 指既有微信用户也有企业微信用户的群 | [2.18.0](../framework/compatibility.html) |
| 公众号二维码 |  | [2.18.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：image组件默认宽度320px、高度240px
2. `tip`：image组件进行缩放时，计算出来的宽高可能带有小数，在不同webview内核下渲染可能会被抹去小数部分

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/NwPpTRmS7AJf "在开发者工具中预览效果")

##### [#](#原图) 原图

![image](https://res.wx.qq.com/wxdoc/dist/assets/img/0.4cb08bb4.jpg)

Incorrect translation.