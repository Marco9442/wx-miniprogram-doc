# [#](#UploadTask) UploadTask

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

一个可以监听上传进度变化事件，以及取消上传任务的对象

## [#](#方法) 方法

### [#](#UploadTask-abort) [UploadTask.abort()](UploadTask.abort.html)

中断上传任务

### [#](#UploadTask-onProgressUpdate-function-listener) [UploadTask.onProgressUpdate(function listener)](./UploadTask.onProgressUpdate.html)

监听上传进度变化事件

### [#](#UploadTask-offProgressUpdate-function-listener) [UploadTask.offProgressUpdate(function listener)](./UploadTask.offProgressUpdate.html)

移除上传进度变化事件的监听函数

### [#](#UploadTask-onHeadersReceived-function-listener) [UploadTask.onHeadersReceived(function listener)](./UploadTask.onHeadersReceived.html)

监听 HTTP Response Header 事件。会比请求完成事件更早

### [#](#UploadTask-offHeadersReceived-function-listener) [UploadTask.offHeadersReceived(function listener)](./UploadTask.offHeadersReceived.html)

移除 HTTP Response Header 事件的监听函数

## [#](#示例代码) 示例代码

```
const uploadTask = wx.uploadFile({
  url: 'http://example.weixin.qq.com/upload', //仅为示例，非真实的接口地址
  filePath: tempFilePaths[0],
  name: 'file',
  formData:{
    'user': 'test'
  },
  success (res){
    const data = res.data
    //do something
  }
})

uploadTask.onProgressUpdate((res) => {
  console.log('上传进度', res.progress)
  console.log('已经上传的数据长度', res.totalBytesSent)
  console.log('预期需要上传的数据总长度', res.totalBytesExpectedToSend)
})

uploadTask.abort() // 取消上传任务
```

Incorrect translation.