# [#](#初始化-SDK) 初始化 SDK

在创建数据模型中，自动会生成多端的操作 SDK，例如 小程序/云函数/Web 等，可以参考如下文档进行初始化和使用。

## [#](#在小程序中调用) 在小程序中调用

### [#](#安装依赖) 安装依赖

#### [#](#方式一：下载-SDK) 方式一：下载 SDK

可以直接把下方的 SDK 链接文件下载到小程序代码的目录（一般是 `miniprogram` 目录）中，保存为 `wxCloudClientSDK.umd.js`

<https://tcb.cloud.tencent.com/wx-cloud-client-sdk/1.2.1/wxCloudClientSDK.umd.js>

#### [#](#方式二：通过-npm-引入) 方式二：通过 npm 引入

> [微信开发者工具使用 npm 指引](https://developers.weixin.qq.com/miniprogram/dev/devtools/npm)

在小程序 `package.json` 所在的目录（一般是 `miniprogram` 目录）执行命令安装 npm 包：

```
npm install @cloudbase/wx-cloud-client-sdk --save
```

然后点击微信开发者工具工具栏上的「工具 - 构建 npm」。

### [#](#初始化和使用-SDK) 初始化和使用 SDK

在 app.js 中加入如下代码：

```
// 如果是下载 SDK 的方式，改成 const { init } = require('./wxCloudClientSDK.umd.js')
const { init } = require("@cloudbase/wx-cloud-client-sdk");

// 指定云开发环境 ID
wx.cloud.init({
  env: "some-env-id", // 当前的云开发环境 ID
});

const client = init(wx.cloud);
const models = client.models; // 或者也可以直接从 wx.cloud.models 上获取，这种方式的类型提示会弱一些

// 接下来就可以调用 models 上的数据模型增删改查等方法了
// models.post.create({
//  data: {
//    body: "你好，世界\n\nfrom china",
//    title: "你好，世界",
//    slug: "hello-world-cn",
//  },
// }).then(({ data } => { console.log(data)}))
```

## [#](#在云函数中调用) 在云函数中调用

云函数中使用需在对应云函数目录下安装 `@cloudbase/wx-cloud-client-sdk` 和 云开发 SDK（`wx-server-sdk` ）依赖。

### [#](#安装依赖-2) 安装依赖

在创建云函数时会在云函数目录下默认新建一个 `package.json` 并提示用户是否立即本地安装依赖。请注意云函数的运行环境是 Node.js，因此在本地安装依赖时务必保证已安装 Node.js，同时 `node` 和 `npm` 都在环境变量中。如不本地安装依赖，可以用命令行在该目录下运行：

```
npm install --save @cloudbase/wx-cloud-client-sdk wx-server-sdk
```

### [#](#初始化和使用-SDK-2) 初始化和使用 SDK

在云函数中调用数据模型 SDK 之前，需要执行一次初始化方法：

```
const cloud = require('wx-server-sdk')
const { init } = require('@cloudbase/wx-cloud-client-sdk')

// 指定云开发环境 ID
cloud.init({
  env: 'some-env-id'，
  // env: cloud.DYNAMIC_CURRENT_ENV
  // 或者给定 DYNAMIC_CURRENT_ENV 常量：接下来的 API 调用都将请求到与该云函数当前所在环境相同的环境
})

const client = init(cloud)
const models = client.models // 或者也可以直接从 wx.cloud.models 上获取，这种方式的类型提示会弱一些

// 接下来就可以调用 models 上的数据模型增删改查等方法了
// models.post.create({
//  data: {
//    body: "你好，世界\n\nfrom china",
//    title: "你好，世界",
//    slug: "hello-world-cn",
//  },
// }).then(({ data } => { console.log(data)}))
```

Incorrect translation.