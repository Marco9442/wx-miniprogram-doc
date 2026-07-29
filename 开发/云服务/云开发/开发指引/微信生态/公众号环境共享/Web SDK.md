## [#](#Web-SDK) Web SDK

Web SDK 在 Web 中使用，可以访问云开发资源，既支持公众号登录态、也支持未登录模式。

### [#](#API-异同) API 异同

Web SDK 除了增加公众号登录相关的 API 外，资源访问的 API 与小程序端 API 基本一样，主要有以下不同点：

**全局变量 cloud**

引入云开发 Web SDK 时，会在 `window` 上挂载 `cloud` 对象，所有 API 均在此对象下，但如果在引入云开发 Web SDK 之前引入了公众号 JSSDK，则会在 `wx` 变量下挂载 `cloud` 对象。

**使用 `new cloud.Cloud` 新建实例**

在 Web SDK 中不使用 `cloud.init`，而是使用 `new cloud.Cloud` 来声明已获得授权的小程序的云环境的操作实例然后使用，如：

```
// 声明新的 cloud 实例
var c1 = new cloud.Cloud({
  // 必填，表示是未登录模式
  identityless: true,
  // 资源方 AppID
  resourceAppid: 'wxe0e2656d74f0bff3',
  // 资源方环境 ID
  resourceEnv: 'test-f96b31',
})

// 跨账号调用，必须等待 init 完成
// init 过程中，资源方小程序对应环境下的 cloudbase_auth 函数会被调用，并需返回协议字段（见下）来确认允许访问、访问时长以及可自定义安全规则
await c1.init()

// 完成后正常使用资源方的已授权的云资源
c1.callFunction({
  name: '',
  data: {},
  complete: console.warn,
})
```

**`uploadFile`**

小程序端是传入临时文件地址作为上传的源文件，Web 端要求传入 file 参数，类型为 [File](https://developer.mozilla.org/en-US/docs/Web/API/File)。

**`downloadFile`**

小程序端是将下载的文件存为本地临时文件，Web 端是将内容以 arraybuffer 形式在字段 data 中返回。

**文档**

API 文档都在 SDK API 文档中，支持 Web 端使用的 API 都有标注。

[更新日志](../../reference/changelog-web-sdk)

### [#](#未登录模式使用注意事项) 未登录模式使用注意事项

1）出于安全考虑，云环境默认不支持未登录下访问，需首先在「云开发控制台 - 设置 - 全局设置/权限设置」中开启（需开发者工具 `1.03.2006042` 或以上）

2）未登录模式必须搭配安全规则使用，若数据库、存储的权限设置为简易权限配置而不是安全规则配置，未登录用户将无法访问云资源

3）在未登录模式访问时，安全规则的 `auth` 变量将为空，可以以此判断未登录请求

### [#](#CDN-地址列表) CDN 地址列表

- 1.4.0: <https://web-9gikcbug35bad3a8-1304825656.tcloudbaseapp.com/sdk/1.4.0/cloud.js>
- 1.3.0: <https://web-9gikcbug35bad3a8-1304825656.tcloudbaseapp.com/sdk/1.3.0/cloud.js>
- 1.1.0: <https://res.wx.qq.com/open/js/cloudbase/1.1.0/cloud.js>

### [#](#NPM) NPM

[@wxcloud/cloud-sdk](https://www.npmjs.com/package/@wxcloud/cloud-sdk)

Incorrect translation.