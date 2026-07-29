# [#](#wx-miniapp-copyNativeFileToWx) wx.miniapp.copyNativeFileToWx

该接口用于将系统中的文件复制进 wx 文件沙箱中；传入参数 nativeFilePath 即文件在手机文件系统中的绝对路径，成功后会返回 tempFilePath

> Android SDK >= 1.3.26；iOS SDK >= 1.3.36

## [#](#接口详情) 接口详情

### [#](#参数) 参数

| **属性** | **类型** | **默认值** | **必填** | **说明** |
| --- | --- | --- | --- | --- |
| nativeFilePath | string |  | 是 | 只支持本地路径 |

### [#](#返回参数) 返回参数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errcode | number | 错误码 |
| errmsg | string | 错误提示 |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.copyNativeFileToWx({
        nativeFilePath: param.data.url,
        success(res) {
          console.log('copyNativeFileToWx success', res)
        },
        fail(e) {
          console.log('copyNativeFileToWx fail', e)
        }
      })
```

### [#](#和-registOpenURL-一起使用的例子) 和 registOpenURL 一起使用的例子

```
wx.miniapp.registOpenURL((param) => {
    console.log('regsitOpenUrl', param)
    if (param.data.isFile) {
      wx.miniapp.copyNativeFileToWx({
        nativeFilePath: param.data.url,
        success(res) {
          console.log('copyNativeFileToWx success', res)
        },
        fail(e) {
          console.log('copyNativeFileToWx fail', e)
        }
      })
    }
})
```

Incorrect translation.