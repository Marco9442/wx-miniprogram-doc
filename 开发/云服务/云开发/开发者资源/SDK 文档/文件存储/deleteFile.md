# [#](#Cloud-deleteFile-fileList-string-Promise-Object) [Cloud](../Cloud).deleteFile(fileList: string[]): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../reference/changelog-server-sdk) , [Web](../../reference/changelog-web-sdk)

从云存储空间删除文件，一次最多 50 个

## [#](#参数) 参数

### [#](#fileList-string) fileList: string[]

云文件 ID 字符串数组

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| fileList | Object | 文件列表 |

**fileList 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云文件 ID |
| status | number | 状态码，0 为成功 |
| errMsg | string | 成功为 ok，失败为失败原因 |

## [#](#小程序端示例) 小程序端示例

Promise 风格

```
wx.cloud.deleteFile({
  fileList: ['a7xzcb']
}).then(res => {
  // handle success
  console.log(res.fileList)
}).catch(error => {
  // handle error
})
```

Callback 风格

```
wx.cloud.deleteFile({
  fileList: ['a7xzcb'],
  success: res => {
    // handle success
    console.log(res.fileList)
  },
  fail: err => {
    // handle error
  },
  complete: res => {
    // ...
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
  const fileIDs = ['xxx', 'xxx']
  const result = await cloud.deleteFile({
    fileList: fileIDs,
  })
  return result.fileList
}
```

Incorrect translation.