# [#](#wx-showActionSheet-Object-object) wx.showActionSheet(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

显示操作菜单

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| alertText | string |  | 否 | 警示文案 | [2.14.0](../../../framework/compatibility.html) |
| itemList | Array.<string> |  | 是 | 按钮的文字数组，数组长度最大为 6 |  |
| itemColor | string | #000000 | 否 | 按钮的文字颜色 |  |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tapIndex | number | 用户点击的按钮序号，从上到下的顺序，从0开始 |

## [#](#示例代码) 示例代码

```
wx.showActionSheet({
  itemList: ['A', 'B', 'C'],
  success (res) {
    console.log(res.tapIndex)
  },
  fail (res) {
    console.log(res.errMsg)
  }
})
```

## [#](#注意) 注意

- Android 6.7.2 以下版本，点击取消或蒙层时，回调 fail, errMsg 为 "fail cancel"；
- Android 6.7.2 及以上版本 和 iOS 点击蒙层不会关闭模态弹窗，所以尽量避免使用「取消」分支中实现业务逻辑

Incorrect translation.