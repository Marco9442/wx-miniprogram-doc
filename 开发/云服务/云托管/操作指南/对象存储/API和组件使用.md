# [#](#API和组件使用) API和组件使用

此文档主要讲解对象存储API的使用方法和一些简易示例，具体详细参数和API-DEMO，请前往[API文档](../../development/storage/index)

## [#](#COS-SDK方式) COS-SDK方式

微信云托管的对象存储底层使用的是[腾讯云COS](https://cloud.tencent.com/product/cos)，所以你可以通过[开放接口服务](../weixin/open)获取临时秘钥，结合[腾讯云COS-SDK](https://cloud.tencent.com/document/product/436/6474)，实现对象存储的访问处理。

主要操作步骤如下：

1. 安装对应语言的 [COS-SDK](https://cloud.tencent.com/document/product/436/6474)。
2. 使用容器[开放接口服务](../weixin/open)获取临时秘钥，使用该秘钥初始化COSSDK。
3. 使用 COS SDK 操作存储桶，可以进行文件列表读取、文件下载、文件删除等操作。
4. 使用 **文件元数据**，可以进行文件上传、获取文件上传者等操作。

> **注意：** 文件缺少元数据时，小程序端无法访问。

具体的使用请参考[开发指引](../../development/storage/service/cos-sdk)

## [#](#API方式) API方式

#### [#](#_1-上传文件) 1.上传文件

上传成功后会获得文件唯一标识符，即文件 `cloudID`，其可以用于调用下载、临时Url、删除接口

在小程序端可调用 `wx.cloud.uploadFile` 方法进行上传，但需要添加 config 指定微信云托管环境

```
wx.cloud.uploadFile({
  cloudPath: 'test.png', // 对象存储路径，根路径直接填文件名，文件夹例子 test/文件名，不要 / 开头
  filePath: 'wxfile://test.png', // 微信本地文件，通过选择图片，聊天文件等接口获取
  config: {
    env: 'werun-id' // 微信云托管环境ID
  },
  success: console.log,
  fail: console.error
})
```

在公众号或普通网页使用WEB-SDK时，可调用 `cloud.uploadFile` 方法上传，具体使用例子如下：

```
cloud.uploadFile({
  cloudPath: 'example.png', // 对象存储路径，根路径直接填文件名，文件夹例子 test/文件名，不要 / 开头
  file: new File(), // 通过 input 或者 new File 获取
  config: {
    env: 'werun-id' // 需要替换成自己的微信云托管环境ID
  }
  success: res => {
    console.log(res.fileID)
  },
  fail: err => {
    console.error(err)
  }
})
```

> 关于 cloudPath   
> 对象存储路径只需要填写根目录相对位置即可，比如你在根目录放置 `test.jpg` 文件，则只需要填写 `cloudPath: 'test.jpg'`，最终返回的 CloudID 为 `cloud://werun-id/test.jpg`，其中 `cloud://werun-id/` 为示例，每个环境都不同，你可以在控制台上传一个文件看到 CloudID。   
> 无论你是上传层级文件，还是根目录文件，cloudid 前缀都不变，变化的只有后面的文件路径。   
> 如果你要在根目录创建文件夹 `file` ，然后在 `file` 文件夹中创建 `A` 文件夹, 最终在 `A` 文件夹中传入文件 `test.jpg` , 则 `cloudPath` 为 `file/A/test.jpg`，最终返回的 CloudID 为 `cloud://werun-id/file/A/test.jpg`

使用其他客户端，无法使用SDK进行操作时，需要自己组装上传，详情请参见[文档](../../development/storage/service/upload)

#### [#](#_2-下载文件) 2. 下载文件

根据文件 `cloudID` 调用 `wx.cloud.downloadFile` 下载文件，用户仅可下载其有访问权限的文件：

```
wx.cloud.downloadFile({
  fileID: 'cloud://werun-id/test/test.png',
  success: console.log,
  fail: console.error
})
```

在公众号或普通网页使用WEB-SDK时，可调用 `cloud.downloadFile` 方法上传，具体使用例子如下：

```
cloud.downloadFile({
  fileID: 'cloud://test.png', // 对象存储文件ID，从上传文件接口或者控制台获取
  success: res => {
    console.log(res.tempFilePath)
  },
  fail: err => {
    console.error(err)
  }
})
```

使用其他客户端，无法使用SDK进行操作时，详情请参见[文档](../../development/storage/service/download)

#### [#](#_3-删除文件) 3. 删除文件

根据文件 `cloudID` 调用 `wx.cloud.deleteFile` 删除文件：

```
wx.cloud.deleteFile({
  fileList: ['cloud://werun-id/test/test.png'], // 文件唯一标识符 cloudID, 可通过上传文件接口获取
  success: console.log,
  fail: console.error
})
```

在公众号或普通网页使用WEB-SDK时，可调用 `cloud.deleteFile` 方法上传，具体使用例子如下：

```
cloud.deleteFile({
  fileList: ['cloud://test.png'], // 对象存储文件ID列表，最多50个，从上传文件接口或者控制台获取
  success: res => {
    console.log(res.fileList)
  },
  fail: err => {
    console.error(err)
  },
  complete: res => {
    console.log(res)
  }
})
```

使用其他客户端，无法使用SDK进行操作时，详情请参见[文档](../../development/storage/service/delete)

#### [#](#_4-换取临时链接) 4. 换取临时链接

根据文件 `cloudID` 调用 `wx.cloud.getTempFileURL` 换取临时文件网络链接，返回有 fileList 数组

fileList 是一个有如下结构的对象数组

```
{
  "fileID": "cloud://xxx.png", // 文件cloudID
  "tempFileURL": "", // 临时文件网络链接
  "maxAge": 86400, // 有效期，默认86400
}
```

```
wx.cloud.getTempFileURL({
  fileList: ['cloud://werun-id/test/test.png'], // 文件唯一标识符 cloudID, 可通过上传文件接口获取
  success: console.log,
  fail: console.error
})

// 也可以传入对象数组，如下
wx.cloud.getTempFileURL({
  fileList: [{
    fileID: 'cloud://werun-id/test/test.png', // 文件唯一标识符 cloudID, 可通过上传文件接口获取
    maxAge: 3600, // 有效期，不传则86400
  }], 
  success: console.log,
  fail: console.error
})
```

在公众号或普通网页使用WEB-SDK时，可调用 `cloud.getTempFileURL` 方法上传，具体使用例子如下：

```
cloud.getTempFileURL({
  fileList: [{
    fileID: 'cloud://test.png', // 对象存储文件ID列表，最多50个，从上传文件接口或者控制台获取
    maxAge: 86400 , // 有效期时长，单位秒，默认86400
  }],
  success: res => {
    console.log(res.fileList)
  },
  fail: err => {
    console.error(err)
  },
  complete: res => {
    console.log(res)
  }
})
```

使用其他客户端，无法使用SDK进行操作时，详情请参见[文档](../../development/storage/service/delete)

## [#](#组件支持) 组件支持

微信小程序组件支持传入云文件 ID，支持列表如下：

| 组件 | 属性 |
| --- | --- |
| image | src |
| video | src、poster |
| cover-image | src |

| 接口 | 参数 |
| --- | --- |
| getBackgroundAudioManager | src |
| createInnerAudioContext | src |
| previewImage | urls、current |

Incorrect translation.