# [#](#wx-choosePoi-Object-object) wx.choosePoi(Object object)

为确保选择地理位置接口的合理使用，位置接口调整参考 [选择地理位置接口调整公告](https://developers.weixin.qq.com/community/develop/doc/0006e45df2cac030e6edf367c56001)

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **[用户授权](../../framework/open-ability/authorize.html)**：需要 scope.userLocation
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

打开POI列表选择位置，支持模糊定位（精确到市）和精确定位混选。

## [#](#使用方法) 使用方法

自 2022 年 7 月 14 日后发布的小程序，若使用该接口，需要在 app.json 中进行声明，否则将无法正常使用该接口，2022年7月14日前发布的小程序不受影响。[具体规则见公告](https://developers.weixin.qq.com/community/develop/doc/000a02f2c5026891650e7f40351c01)

## [#](#申请开通) 申请开通

暂只针对具备与地理位置强相关的使用场景的小程序开放，在小程序管理后台，「开发」-「开发管理」-「接口设置」中自助开通该接口权限。
接口权限申请入口将于2022年3月11日开始内测，于3月31日全量上线。并从4月18日开始，在代码审核环节将检测该接口是否已完成开通，如未开通，将在代码提审环节进行拦截。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| type | number | 选择城市时，值为 1，选择精确位置时，值为 2 |
| city | number | 城市名称 |
| name | string | 位置名称 |
| address | string | 详细地址 |
| latitude | number | 纬度，浮点数，范围为-90~90，负数表示南纬。使用 gcj02 国测局坐标系（即将废弃） |
| longitude | number | 经度，浮点数，范围为-180~180，负数表示西经。使用 gcj02 国测局坐标系（即将废弃） |

## [#](#示例) 示例

![](https://res.wx.qq.com/op_res/lzDsNyBNifLczyLX0ms7ZpPQysgAgdhrQTGzzTQPiXkAB2HJIf1Slvl4rnN9I1q0AT3xqoGTg98jMsNexDLbbA#width:260px)

Incorrect translation.