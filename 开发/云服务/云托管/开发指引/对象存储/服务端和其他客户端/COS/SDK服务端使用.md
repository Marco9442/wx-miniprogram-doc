# [#](#COS-SDK服务端使用) COS-SDK服务端使用

COS-SDK主要使用步骤如下：

1. 使用[开放接口服务](../../../guide/weixin/open)获取临时密钥。
2. 使用临时密钥初始化[COS-SDK](https://cloud.tencent.com/document/product/436/6474)
3. 使用COS-SDK做增删改查等操作。
4. 上传文件时，需要使用[开放接口服务](../../../guide/weixin/open)获取文件元数据，保证小程序端可以访问。

### [#](#使用限制) 使用限制

1. 文件缺少元数据时，小程序端 **无法访问**，请务必参考本文档获取文件元数据并正确写入。
2. 云托管域名请求体大小二进制限制 20MiB，如果超大文件上传，请参考文档[从客户端上传](upload)。

> **注意：**

## [#](#一、获取临时秘钥) 一、获取临时秘钥

对象存储提供的临时秘钥角色可以访问当前环境下的存储桶。

```
http://api.weixin.qq.com/_/cos/getauth
```

返回信息格式如下：

```
{
  "TmpSecretId": "",  // 临时密钥的 tmpSecretId
  "TmpSecretKey": "", // 临时密钥的 tmpSecretKey
  "Token": "", // 临时密钥的 sessionToken
  "ExpiredTime": ""  // 临时密钥失效时间戳，是申请临时密钥时，时间戳加 durationSeconds
}
```

#### [#](#代码示例) 代码示例

以下为 NodeJS 使用 COS SDK 访问对象存储的示例代码，其他语言可以参考 COS SDK 的文档进行初始化。

异步获取临时密钥，通过 `getAuthorization` 传入 COS SDK 即可。

```
// 在服务启动时或者页面加载时初始化，注意这是异步的，需要等待完成，可以通过 this.cos 是否存在来判断是否完成。
initcos()

/**
 * 封装的COS-SDK初始化函数，建议在服务启动时挂载全局，通过this.cos使用对象
 */
async function initcos() {
  const COS = require('cos-nodejs-sdk-v5')
  try {
    this.cos = new COS({
      getAuthorization: async function (options, callback) {
        const res = await call({
          url: 'http://api.weixin.qq.com/_/cos/getauth',
          method: 'GET',
        })
        const info = JSON.parse(res)
        const auth = {
          TmpSecretId: info.TmpSecretId,
          TmpSecretKey: info.TmpSecretKey,
          SecurityToken: info.Token,
          ExpiredTime: info.ExpiredTime,
        }
        callback(auth)
      },
    })
    console.log('COS初始化成功')
  } catch (e) {
    console.log('COS初始化失败', res)
  }
}

/**
 * 封装的网络请求方法
 */
function call (obj) {
  return new Promise((resolve, reject) => {
    request({
      url: obj.url,
      method: obj.method || 'POST',
      headers: {
        'content-type': 'application/json'
      },
      body: JSON.stringify(obj.data || {})
    }, function (err, response) {
      if (err) reject(err)
      resolve(response.body)
    })
  })
}
```

## [#](#二、访问存储桶和文件下载) 二、访问存储桶和文件下载

访问存储桶，以及做对象存储操作时，均需要指定`bucket`和`region`，可以在[微信云托管控制台-对象存储-存储配置](https://cloud.weixin.qq.com/cloudrun/storage)中获取。

以下是封装的一些使用方法，可以参考用于其他的API方法。

```
// 需要先参考一开始的初始化COSSDK，初始化完成后再操作下面的。

const path = require('path')
const cosConfig = {
  Bucket: '', // 填写云托管对象存储桶名称
  Region: 'ap-shanghai' // 存储桶地域，默认是上海，其他地域环境对应填写
}
/**
 * 封装的文件下载函数
 * @param {*} cloudpath 文件路径
 * @param {*} filepath 保存本地路径
 */
async function getFile (cloudpath, filepath) {
  try {
    const res = await this.cos.getObject({
      Bucket: cosConfig.Bucket,
      Region: cosConfig.Region,
      Key: cloudpath,
      Output: path.join('./', filepath)
    })
    if (res.statusCode === 200) {
      return {
        code: 0,
        file: path.join('./', filepath)
      }
    } else {
      return {
        code: 1,
        msg: JSON.stringify(res)
      }
    }
  } catch (e) {
    console.log('下载文件失败', e.toString())
    return {
      code: -1,
      msg: e.toString()
    }
  }
}
```

## [#](#三、文件元数据) 三、文件元数据

在服务端上传文件时，需要对文件增加元数据，以区分上传者 OpenID 和控制文件权限。**若文件无元数据，则该文件将不可被小程序侧访问。**

通过如下的接口，可以获取文件元数据，或对元数据进行解析得到 OpenID。

### [#](#_1-获取元数据) 1. 获取元数据

输入用户`openid`，`bucket`名称和上传目录，获取文件的加密元数据。

```
POST https://api.weixin.qq.com/_/cos/metaid/encode
```

body信息：

```
{
  "openid": "exampleopenid",
  "bucket": "bucket", // 在「微信云托管控制台-对象存储-存储配置」获取
  "paths": [
    "/aaa", // 文件路径
    "/bbb"
  ]
}
```

返回结果如下，返回的 `x_cos_meta_field_strs` 的顺序与输入的顺序相同。

```
{
  "errcode": 0,
  "errmsg": "ok",
  "respdata": {
    "x_cos_meta_field_strs": [
      "xxx-xxx-xxxxxx",
      "xxx-xxx-xxxxxx"
    ]
  }
}
```

接口 `/_/cos/metaid/encode`，理论上可以生成任意存在或者不存在的文件、存储桶、openid为入参的元数据，本质上是对这些入参做了一次签名，在之后的客户端（小程序/h5）使用时，可以根据元数据推断出所属用户，并根据权限管理的设定做出读写拦截或放通。

所以你可以根据业务的自身情况，灵活的使用元数据达到期待效果。比如预先生成，重写文件的元数据改变所属人等。如果你生成的元数据跟真实的不符，无法解析或者信息不对应，统一按照未知处理；若权限在创建者可读写的情况下，只有管理端（SDK或者服务端API）可以对文件进行修改，小程序端无法操作读写。

### [#](#_2-解析元数据) 2. 解析元数据

输入加密元数据，返回用户`openid`，上传目录和`bucket`名称。暂仅支持解析单个 metaid，批量解析时需要注意访问频率。

```
POST https://api.weixin.qq.com/_/cos/metaid/decode
```

```
{
  "metaid": "xxx-xxx-xxxxxx"
}
```

返回结果

```
{
  "errcode": 0,
  "errmsg": "ok",
  "respdata": {
    "raw_data": {
      "openid": "exampleopenid",
      "bucket": "bucket",
      "appid": "exampleappid",
      "path": "/aaa",
      "mpAppId": "exampleappid"
    },
    "x_cos_meta_field_strs": []
  }
}
```

### [#](#_3-使用元数据上传文件) 3. 使用元数据上传文件

以 NodeJS SDK 为例，需要在文件的 Headers 中增加 `x-cos-meta-fileid`

以下是封装的上传文件方法，可参考后自行调整：

```
const fs = require('fs')
const cosConfig = {
  Bucket: '', // 填写云托管对象存储桶名称
  Region: 'ap-shanghai' // 存储桶地域，默认是上海，其他地域环境对应填写
}

/**
 * 封装的上传文件函数
 * @param {*} cloudpath 上传的云上路径
 * @param {*} filepath 本地文件路径
 */
async function uploadFile (cloudpath, filepath) {
  const authres = await call({
    url: 'http://api.weixin.qq.com/_/cos/metaid/encode',
    method: 'POST',
    data: {
      openid: '', // 填写用户openid，管理端为空字符串
      bucket: cosConfig.Bucket,
      paths: [cloudpath]
    }
  })
  try {
    const auth = JSON.parse(authres)
    const res = await this.cos.putObject({
      Bucket: cosConfig.Bucket,
      Region: cosConfig.Region,
      Key: cloudpath,
      StorageClass: 'STANDARD',
      Body: fs.createReadStream(filepath),
      ContentLength: fs.statSync(filepath).size,
      Headers: {
        'x-cos-meta-fileid': auth.respdata.x_cos_meta_field_strs[0]
      }
    })
    if (res.statusCode === 200) {
      return {
        code: 0,
        file: JSON.stringify(res)
      }
    } else {
      return {
        code: 1,
        msg: JSON.stringify(res)
      }
    }
  } catch (e) {
    console.log('上传文件失败', e.toString())
    return {
      code: -1,
      msg: e.toString()
    }
  }
}

function call (obj) {
  return new Promise((resolve, reject) => {
    request({
      url: obj.url,
      method: obj.method || 'POST',
      headers: {
        'content-type': 'application/json'
      },
      body: JSON.stringify(obj.data || {})
    }, function (err, response) {
      if (err) reject(err)
      resolve(response.body)
    })
  })
}
```

## [#](#四、权限问题) 四、权限问题

微信云托管对象存储的底层是COS，而COS的存储桶是默认私有读写的，如果你使用COS SDK内获取对象URL方法获取的 `cos.ap-shanghai.myqcloud.com` 结尾的对象路径，在无 `sign` 参数时会显示权限拒绝的提示。

而在微信云托管控制台-对象存储里的文件路径时 `tcb.qcloud.la` 结尾的，这个是文件访问的另一个途径，权限是受微信云托管控制台权限管控的。

如果你想使COS SDK获取的，`cos.ap-shanghai.myqcloud.com` 链接公有读，可以使用[权限修改接口](https://cloud.tencent.com/document/product/436/41898)修改COS存储桶的权限。（在这里列举的PHP链接，其他语言请自行查找）

微信云托管内对象存储底层的COS存储桶，没有暴露任何控制台界面，所以想对COS桶进行设置，需要通过SDK或API完成。

## [#](#五、使用案例) 五、使用案例

我们写了一个DEMO，使用 [sharp](https://sharp.pixelplumbing.com/) 将上传的图片全部转成webp格式，并返回webp格式的链接。

服务的上传下载直接使用的为COS-SDK，可以做有价值的参考。

项目仓库：[github](https://github.com/WeixinCloud/wxcloud-img-sharp)

Incorrect translation.