# [#](#「CloudID开放数据获取服务」示例) 「CloudID开放数据获取服务」示例

在从传统服务迁移到云托管时，获取用户信息会返回CloudID，如何通过这个CloudID获取对应的信息，而不是传统的加解密处理。

云开发云函数迁移到云托管时，event中的CloudID不会自动解析，应该如何手动解析一下？

本文档以NodeJS express 搭建一个获取信息的服务。

## [#](#原理) 原理

1. 小程序或者公众号中发起获取信息操作，可以拿到CloudID
2. 小程序或者公众号需要和服务所在的云托管环境建立联系，本身或者资源复用。
3. 使用[wxa/getopendata接口](https://developers.weixin.qq.com/miniprogram/dev/server/API/cloudbase/others/api_getopendata)，传入CloudID置换。

## [#](#NodeJS代码示例) NodeJS代码示例

#### [#](#一、服务搭建) 一、服务搭建

建立一个目录，放置3个文件

`index.js` 文件

```
const express = require('express')
const request = require('request')
const app = express()

app.use(express.json())

app.all('/getInfo', async function (req, res) {
  const { info } = req.method === 'GET' ? req.query : req.body
  console.log('请求头', req.headers)
  const appid = req.headers['x-wx-from-appid'] || ''
  const openid = req.headers['x-wx-from-openid'] || req.headers['x-wx-openid']
  console.log('原始数据', appid, info, openid)
  const infores = await getOpenData(appid, openid, info)
  console.log('接口数据', infores)
  res.send(infores)
})

app.listen(80, function () {
  console.log('服务启动成功！')
})

function getOpenData (appid, openid, cloudid) {
  return new Promise((resolve, reject) => {
    request({
      url: `http://api.weixin.qq.com/wxa/getopendata?from_appid=${appid}&openid=${openid}`,
      method: 'POST',
      body: JSON.stringify({
        cloudid_list: [cloudid]
      })
    }, function (error, res) {
      if (error) reject(error)
      resolve(res.body)
    })
  })
}
```

`package.json` 文件

```
{
  "name": "server",
  "version": "1.0.0",
  "description": "for get opendata",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "weixin",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.3",
    "request": "^2.88.2"
  }
}
```

`Dockerfile` 文件

```
FROM node:12-slim

WORKDIR /app

COPY package*.json .

RUN npm i

COPY . .

CMD ["node","index.js"]
```

将上述目录部署到云托管服务中，可以参考[自定义部署](../../quickstart/custom/node)

#### [#](#二、调用) 二、调用

小程序中调用

```
const res = await wx.cloud.callContainer({
  config: {
    env: '填入云环境ID',               // 微信云托管的环境ID
  },
  path: '/getInfo',                  // 填入业务自定义路径和参数，根目录，就是 / 
  method: 'POST',                    // 按照自己的业务开发，选择对应的方法
  header: {
    'X-WX-SERVICE': '替换成自己的服务', // xxx中填入服务名称（微信云托管 - 服务管理 - 服务列表 - 服务名称）
  },
  data:{
    info:wx.cloud.CloudID('获取的CloudID')
  }
});

console.log(res);
```

公众号中调用

```
 const res = await cloud.callContainer({
  path: '/getInfo',                   // 填入业务自定义路径和参数，根目录，就是 / 
  method: 'POST',                     // 按照自己的业务开发，选择对应的方法
  header: {
    'X-WX-SERVICE': '替换成自己的服务',  // xxx中填入服务名称（微信云托管 - 服务管理 - 服务列表 - 服务名称）
  },
  data:{
    info:cloud.CloudID('获取的CloudID')
  }
  })
  console.log(res.data)
```

## [#](#其他语言框架) 其他语言框架

待补充

Incorrect translation.