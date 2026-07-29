# [#](#wx-shareFileMessage-Object-object) wx.shareFileMessage(Object object)

> 基础库 2.16.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

转发文件到聊天

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| filePath | string |  | 是 | 要分享的文件地址，必须为本地路径或临时路径 |
| fileName | string |  | 否 | 自定义文件名，若留空则使用filePath中的文件名 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
  // callback 写法
  wx.downloadFile({
    url: URL, // 下载url
    success (res) {
      // 下载完成后转发
      wx.shareFileMessage({
        filePath: res.tempFilePath,
        success() {},
        fail: console.error,
      })
    },
    fail: console.error,
  })

  // async await 写法
  const { tempFilePath } = await wx.downloadFile({
    url: URL, // 下载url
  })
  // 下载完成后转发
  await wx.shareFileMessage({
    filePath: tempFilePath,
  })
```

Incorrect translation.