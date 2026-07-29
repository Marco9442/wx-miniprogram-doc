# [#](#wx-miniapp-copyWxFileToNative) wx.miniapp.copyWxFileToNative

该接口用于将 wxfile:// 文件复制到系统中，成功会返回 nativeFilePath

> iOS SDK >= 1.4.18；Android SDK >= 1.5.2

## [#](#接口详情) 接口详情

### [#](#参数) 参数

| **属性** | **类型** | **默认值** | **必填** | **说明** |
| --- | --- | --- | --- | --- |
| wxFilePath | string |  | 是 | 形如 wxfile:// 的路径 |

### [#](#返回参数) 返回参数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errcode | number | 错误码 |
| errmsg | string | 错误提示 |
| nativeFilePath | string | 系统文件路径 |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.copyWxFileToNative({
wxFilePath: param.url,
success(res) {
console.log('copyWxFileToNative success', res)
},
fail(e) {
console.log('copyWxFileToNative fail', e)
}
})
```

Incorrect translation.