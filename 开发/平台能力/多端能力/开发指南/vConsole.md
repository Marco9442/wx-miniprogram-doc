# [#](#开启-vConsole) 开启 vConsole

## [#](#一、移动应用助手中开启) 一、移动应用助手中开启

在移动应用助手中打开 vConsole 的方法如下：

- 在 app.js 中新增如下内容，然后重新编译代码。

```
wx.setEnableDebug({
  enableDebug: true
})
```

## [#](#二、在-App-中开启) 二、在 App 中开启

将 App 打包生成 APK 或 IPA，如需在 App 中打开 vConsole，操作步骤如下：

步骤 1. 鼠标点击 project.miniapp.json，右侧即出现可视化配置面板。

步骤 2. 找到 Android/iOS 对应的「调试模式配置」并设置为「开启 open」。

步骤 3. 重新构建新的 APK 或 IPA，重新安装即可生效。

![](https://res.wx.qq.com/op_res/7RsndlF3ubX7fAOybcOhLckA8yXVQeildLKD9TvJ7U5TCMJ5FD3hR-fWLdKi9vcAebSflDeCi6YeAvN9F8kq1Q) ![](https://res.wx.qq.com/op_res/7RsndlF3ubX7fAOybcOhLRwRcFzZXDzFgmbzWVjDVJd40xahS-sAxWIK45iv877ulrVs01jjHZKZkbDvFOMNjA)

- 如果是鸿蒙，则需手动切换至 json 模式，手动添加 `enableVConsole` 如下截图，（true 表示开启，false 表示关闭）

![](https://res8.wxqcloud.qq.com.cn/wxdoc/7ae1a0c8-58b2-4cf7-bb37-27154ae03db2.png)

调试模式配置的说明：

该模式下有三个值，分别为 `open`、`close` 以及 `undefined`。

如果是 `undefined`，仍希望将 vConsole 打开，则可以在 `app.js` 中新增如下内容。

```
wx.setEnableDebug({
  enableDebug: true
})
```

但在 `close` 的情况下，代码中是将 `enableDebug` 设置为 `true` 也不会开启 vConsole 模式，但是会在 App 启动的时候出现「调试模式已启用，请重启生效」的水印。所以在构建正式版上架前开发者需将此模式关闭并且将 `enableDebug` 设置为 `false`。

## [#](#三、其他说明) 三、其他说明

如果 project.miniapp.json 文件中没有出现可视化面板，而是源码形式，可通过右上角的图标进行切换；如果右上角没有切换的图标，则是开发者工具的版本过低，请将开发者工具升级为最新版本。

![](https://res.wx.qq.com/op_res/Z9QAbDB-ijY3l7nJdAnAOuEXopqhwkcF-ccV4NJtTOWqnjn_liKbPuqARYTHA9vcFghgbQng3JvmAoJ41UIp7A)

Incorrect translation.