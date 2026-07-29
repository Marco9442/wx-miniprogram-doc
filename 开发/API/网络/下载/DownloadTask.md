# [#](#DownloadTask) DownloadTask

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

一个可以监听下载进度变化事件，以及取消下载任务的对象

## [#](#方法) 方法

### [#](#DownloadTask-abort) [DownloadTask.abort()](DownloadTask.abort.html)

中断下载任务

### [#](#DownloadTask-onProgressUpdate-function-listener) [DownloadTask.onProgressUpdate(function listener)](./DownloadTask.onProgressUpdate.html)

监听下载进度变化事件

### [#](#DownloadTask-offProgressUpdate-function-listener) [DownloadTask.offProgressUpdate(function listener)](./DownloadTask.offProgressUpdate.html)

移除下载进度变化事件的监听函数

### [#](#DownloadTask-onHeadersReceived-function-listener) [DownloadTask.onHeadersReceived(function listener)](./DownloadTask.onHeadersReceived.html)

监听 HTTP Response Header 事件。会比请求完成事件更早

### [#](#DownloadTask-offHeadersReceived-function-listener) [DownloadTask.offHeadersReceived(function listener)](./DownloadTask.offHeadersReceived.html)

移除 HTTP Response Header 事件的监听函数

## [#](#示例代码) 示例代码

```
const downloadTask = wx.downloadFile({
  url: 'http://example.com/audio/123', //仅为示例，并非真实的资源
  success (res) {
    wx.playVoice({
      filePath: res.tempFilePath
    })
  }
})

downloadTask.onProgressUpdate((res) => {
  console.log('下载进度', res.progress)
  console.log('已经下载的数据长度', res.totalBytesWritten)
  console.log('预期需要下载的数据总长度', res.totalBytesExpectedToWrite)
})

downloadTask.abort() // 取消下载任务
```

Incorrect translation.