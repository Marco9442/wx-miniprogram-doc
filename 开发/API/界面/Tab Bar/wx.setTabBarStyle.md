# [#](#wx-setTabBarStyle-Object-object) wx.setTabBarStyle(Object object)

> 基础库 1.9.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

动态设置 tabBar 的整体样式

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| color | string |  | 否 | tab 上的文字默认颜色，HexColor |
| selectedColor | string |  | 否 | tab 上的文字选中时的颜色，HexColor |
| backgroundColor | string |  | 否 | tab 的背景色，HexColor |
| borderStyle | string |  | 否 | tabBar上边框的颜色， 仅支持 black/white |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.setTabBarStyle({
  color: '#FF0000',
  selectedColor: '#00FF00',
  backgroundColor: '#0000FF',
  borderStyle: 'white'
})
```

Incorrect translation.