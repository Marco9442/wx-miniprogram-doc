# [#](#PluginUpdateManager) PluginUpdateManager

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

PluginUpdateManager 对象，用来管理插件更新，可通过 [wx.getPluginUpdateManager](wx.getPluginUpdateManager.html) 接口获取实例。

## [#](#方法) 方法

### [#](#PluginUpdateManager-onCheckForUpdate-function-listener) [PluginUpdateManager.onCheckForUpdate(function listener)](./PluginUpdateManager.onCheckForUpdate.html)

监听向微信后台请求检查插件更新结果事件。微信在小程序每次启动（包括热启动）时自动检查插件更新，不需由开发者主动触发。

### [#](#PluginUpdateManager-onUpdateReady-function-listener) [PluginUpdateManager.onUpdateReady(function listener)](./PluginUpdateManager.onUpdateReady.html)

监听插件有版本更新事件。客户端主动触发下载（无需开发者触发），下载成功后回调

### [#](#PluginUpdateManager-onUpdateFailed-function-listener) [PluginUpdateManager.onUpdateFailed(function listener)](./PluginUpdateManager.onUpdateFailed.html)

监听插件更新失败事件。插件有新版本，客户端主动触发下载（无需开发者触发），下载失败（可能是网络原因等）后回调

## [#](#示例代码) 示例代码

```
const pluginUpdateManager = wx.getPluginUpdateManager({
  pluginId: 'wx1234567890abcdef'
})

pluginUpdateManager.onCheckForUpdate(function (res) {
  // 请求完插件新版本信息的回调
  console.log(res.hasUpdate)
  if (res.hasUpdate) {
    console.log(res.pluginVersion)
  }
})

pluginUpdateManager.onUpdateReady(function (res) {
  wx.showModal({
    title: '更新提示',
    content: '插件新版本已经准备好，是否重启应用？',
    success: function (modalRes) {
      if (modalRes.confirm) {
        // 插件新版本已经下载好，调用 applyUpdate 应用新版本并重启
        wx.getUpdateManager().applyUpdate()
      }
    }
  })
})

pluginUpdateManager.onUpdateFailed(function (res) {
  // 插件新版本下载失败
  console.log(res.pluginVersion)
})
```

Incorrect translation.