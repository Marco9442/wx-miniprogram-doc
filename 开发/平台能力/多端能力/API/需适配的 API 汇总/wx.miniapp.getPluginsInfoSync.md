API/需适配的 API 汇总/wx.miniapp.getPluginsInfoSync/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/diffapi/getPluginsInfo.html\#wx-miniapp-getPluginsInfoSync) wx.miniapp.getPluginsInfoSync
获取当前多端应用所引用的插件信息
说明：Android SDK >= 1.5.10 以及 iOS SDK >= 1.5.12
### [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/diffapi/getPluginsInfo.html\#%E8%BF%94%E5%9B%9E%E5%80%BC-object) 返回值 object
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| plugins | object | 该多端应用所引用的多端插件信息，注意不是小程序插件 |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/diffapi/getPluginsInfo.html\#plugins) plugins
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| pluginId | string | 插件 appId |
| version | string | 插件版本号 |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/diffapi/getPluginsInfo.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const pluginInfo = wx.getPluginsInfoSync();
console.log(pluginInfo.plugins.pluginId) // 多端插件 appId
console.log(pluginInfo.plugins.version) // 多端插件 版本
```
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202502101231592.png)