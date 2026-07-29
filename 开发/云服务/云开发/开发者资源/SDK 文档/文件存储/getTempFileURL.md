# [#](#Cloud-getTempFileURL-fileList-string-Promise-Object) [Cloud](../Cloud).getTempFileURL(fileList: string[]): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../reference/changelog-server-sdk) , [Web](../../reference/changelog-web-sdk)

用云文件 ID 换取真实链接，公有读的文件获取的链接不会过期，私有的文件获取的链接十分钟有效期。一次最多取 50 个。

## [#](#参数) 参数

### [#](#fileList-string) fileList: string[]

要换取临时链接的云文件 ID 列表

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| fileList | Object | 文件列表 |

**fileList 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云文件 ID |
| tempFileURL | string | 临时文件路径 |
| status | number | 状态码，0 为成功 |
| errMsg | string | 成功为 ok，失败为失败原因 |

## [#](#小程序端示例) 小程序端示例

Promise 风格

```
wx.cloud.getTempFileURL({
  fileList: [{
    fileID: 'a7xzcb',
    maxAge: 60 * 60, // one hour
  }]
}).then(res => {
  // get temp file URL
  console.log(res.fileList)
}).catch(error => {
  // handle error
})
```

Callback 风格

```
wx.cloud.getTempFileURL({
  fileList: ['cloud://xxx', 'cloud://yyy'],
  success: res => {
    // get temp file URL
    console.log(res.fileList)
  },
  fail: err => {
    // handle error
  }
})
```

## [#](#云函数端示例) 云函数端示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const fileList = ['cloud://xxx', 'cloud://yyy']
  const result = await cloud.getTempFileURL({
    fileList: fileList,
  })
  return result.fileList
}
```

Incorrect translation.