# [#](#wx-loadBuiltInFontFace-Object-object) wx.loadBuiltInFontFace(Object object)

> 基础库 3.7.9 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.7.9](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

加载内置字体。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | global | boolean | false | 否 | <是否全局生效 |
|  | family | string |  | 是 | 定义的字体名称 |
|  | source | string |  | 是 | 要加载的内置字体名字 |
|  | | 合法值 | 说明 | | --- | --- | | WeChatSansSS | WeChatSansSS 字体 | | WeChatSansStd | WeChatSansStd 字体 | | | | | |
|  | scopes | Array |  | 否 | 字体作用范围，可选值为 webview / native / skyline，默认全选，设置 native 可在 Canvas 2D 下使用 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/i4rduVmM7JWZ "在开发者工具中预览效果")

```
wx.loadBuiltInFontFace({
  family: 'WeChatSansSS',
  source: 'WeChatSansSS',
  success: console.log
})
```

Incorrect translation.