# [#](#Object-wx-getExptInfoSync-Array-string-keys) Object wx.getExptInfoSync(Array.<string> keys)

> 基础库 2.17.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

给定实验参数数组，获取对应的实验参数值

## [#](#参数) 参数

### [#](#Array-string-keys) Array.<string> keys

实验参数数组，不填则获取所有实验参数

## [#](#返回值) 返回值

### [#](#Object) Object

结果对象，key 为传入的 keys 中的各项，value 为参数值

## [#](#提示) 提示

假设实验参数有 `color`, `size`
调用 wx.getExptInfoSync() 会返回 `{color:'#fff',size:20}` 类似的结果
而 wx.getExptInfoSync(['color']) 则只会返回 `{color:'#fff'}`

Incorrect translation.