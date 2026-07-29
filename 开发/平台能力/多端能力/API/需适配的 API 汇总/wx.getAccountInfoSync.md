# [#](#wx-getAccountInfoSync) wx.getAccountInfoSync

获取当前多端应用账号信息，包括其绑定的小程序账号信息

### [#](#变更周知) 变更周知

- 当 SDK >= 1.4.3，新增返回 miniappId 和 moduleId，含义查看文档说明
- 当 SDK >= 1.4.X, miniProgram.appId 返回值为小程序 AppID；而在 SDK < 1.4.X 版本中该字段返回的是多端资源包 id，请开发者注意
- Android SDK >= 1.5.10 以及 iOS SDK >= 1.5.12 新增 miniapp object

### [#](#返回值-object) 返回值 object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| miniProgram | object | 该多端应用所绑定的小程序账号信息 |
| plugin | object | 该多端应用所引用的小程序插件信息 |
| host | object | 多端应用账号信息 |

#### [#](#miniProgram) miniProgram

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| appId | string | 小程序 appId ；该字段在多端应用才会生效且iOS SDK >= 1.4.3，Android SDK >= 1.4.0 |
| envVersion | string | 该字段在多端应用中返回"release"，为无效值 |
| version | string | 该字段在多端应用中返回""，为无效值 |

#### [#](#miniapp) miniapp

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| miniappId | string | 多端应用 appId ；该字段在多端应用才会生效且iOS SDK >= 1.5.12，Android SDK >= 1.5.10 |
| moduleId | string | 资源包 appId ；该字段在多端应用才会生效且iOS SDK >= 1.5.12，Android SDK >= 1.5.10 |
| envVersion | string | 资源包的版本 |

#### [#](#host) host

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| miniappId | string | 多端应用 Id；该字段在多端应用才会生效且iOS SDK >= 1.4.3，Android SDK >= 1.4.0 |
| moduleId | string | 多端应用资源包 Id ；该字段在多端应用才会生效且iOS SDK >= 1.4.3，Android SDK >= 1.4.0 |

#### [#](#plugin) plugin

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| appId | string | 插件 appId，该字段在多端应用中为无效值 |
| version | string | 插件版本号，该字段在多端应用中为无效值 |

## [#](#示例代码) 示例代码

```
const accountInfo = wx.getAccountInfoSync();
console.log(accountInfo.miniProgram.appId) // 小程序 appId
console.log(accountInfo.host.miniappId) // 多端应用 Id
console.log(accountInfo.host.moduleId) // 多端应用资源包 Id
console.log(accountInfo.plugin.appId) // 插件 appId
console.log(accountInfo.plugin.version) // 插件版本号， 'a.b.c' 这样的形式
```

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202502101227063.png)

Incorrect translation.