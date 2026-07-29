# [#](#Cloud-CDN-opt-string-ArrrayBuffer-Object) [Cloud](../Cloud).CDN(opt: string|ArrrayBuffer|Object)

> 支持端：[小程序 2.12.0](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version)

小程序端调云函数传递大数据可用的临时 CDN

## [#](#参数) 参数

### [#](#opt-string-ArrrayBuffer-Object) opt: string|ArrrayBuffer|Object

## [#](#使用说明) 使用说明

标记需要上传到 CDN 的文件/大字符串然后转换成 HTTP URL 的数据，必须在 `callFunction` 中使用。

小程序端调用云函数时，如需传递大数据（建议 128k 以上时），可用此 CDN 方法标记需要传递的数据，即可以是字符串，也可以是临时文件路径。标记之后，在调用云函数时，系统会自动上传相应数据到临时 CDN，最终云函数内接收到的该字段将会是一个 CDN 地址，可在云函数内请求下来。

用这个方法可以避免大数据在云函数链路内的传输，提高大数据调用时的性能，同时避免触及调用数据的大小限制。

CDN 方法可以接收三种参数类型：

- String
- ArrayBuffer
- 文件路径定义对象

当使用文件路径定义对象时，将在调用服务 API 时自动将相应文件路径对应的文件内容上传至 CDN 并转换成 CDN URL，对象定义如下：
*入参*\*

接收一个对象，对象下有如下定义的字段：

| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 定义对象的类型，必填 filePath |
| filePath | string | 是 | 文件路径 |

## [#](#示例代码) 示例代码

```
wx.cloud.callFunction({
  name: 'test',
  data: {
    strDemo: wx.cloud.CDN('some large string'),
    filePathDemo: wx.cloud.CDN({
      type: 'filePath',
      filePath: 'xxxxxxxx',
    })
  },
})
.then(console.log)
.catch(console.error)
```

Incorrect translation.