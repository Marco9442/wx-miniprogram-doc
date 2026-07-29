# [#](#wx-openOfficialAccountArticle-Object-object) wx.openOfficialAccountArticle(Object object)

> 基础库 3.4.8 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.15.1](../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

通过小程序打开任意公众号文章（不包括临时链接等异常状态下的公众号文章），必须有点击行为才能调用成功。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string |  | 是 | 需要打开的公众号地址 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| cancel | boolean | 为 true 时，表示用户点击了取消（用于 Android 系统区分点击蒙层关闭还是点击取消按钮关闭） |
| confirm | boolean | 为 true 时，表示用户点击了确定按钮 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-err) Object err

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| errCode | number | 错误码 |

## [#](#示例代码) 示例代码

```
  wx.openOfficialAccountArticle({
         url:'', // 此处填写公众号文章连接
         success: res => {
         },
         fail: res => {
         }
     })
```

Incorrect translation.