# [#](#wx-enableAlertBeforeUnload-Object-object) wx.enableAlertBeforeUnload(Object object)

> 基础库 2.12.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [取消监听 wx.disableAlertBeforeUnload](wx.disableAlertBeforeUnload.html)

## [#](#功能描述) 功能描述

开启小程序页面返回询问对话框。

## [#](#弹窗条件) 弹窗条件

- 当用户在小程序内非首页页面/最底层页
- 官方导航栏上的的返回
- 全屏模式下自绘返回键
- android 系统 back 键时

## [#](#注意事项) 注意事项

- 手势滑动返回时不做拦截
- 在任何场景下，此功能都不应拦住用户退出小程序的行为

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| message | string |  | 是 | 询问对话框内容 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/MTPm9Cmh7VfT "在开发者工具中预览效果")

Incorrect translation.