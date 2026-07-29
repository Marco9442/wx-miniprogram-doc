# [#](#Android-设置-meta-data) Android 设置 meta-data

为方便开发者构建 Android 的渠道包用于统计不同渠道的投放效果，现已支持开发者设置自定义的 meta-data，开发者可在 meta-data 中设置自定义的渠道 id。

- 注意：开发者工具版本需版本 >= 1.06.2312182，建议使用[最新的 nightly](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)。

## [#](#使用说明) 使用说明

前往 project.miniapp.json，切换到 json 模式，在 `mini-android` 中新增 "channel" 配置，如下：

![](https://res.wx.qq.com/op_res/I_wO7b6xzV4YI2qQGurOCQRms4hKPAR4ao-ZwRTVklzgFWweBcuKh1JFe13t3TB6Ww1MJAApk8TS6luUQGNneA)

- 解释说明：上述配置后，即底层生成的 meta-data 示例如下：

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312191134488.png)
- 配置后，重新构建 APK，构建的 APK 产物会将命名为「包名」字段+`-${channel.value}` 字段。
- 补充，如开发者需构建多个渠道的安装包，需按照上述操作进行多次，后续开发者工具将继续优化支持一次配置多个渠道包。
- 设置的 meta-data 值之后可以通过 [wx.miniapp.getMetaData](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/miniapp/getMetaData.html) 接口获取。

Incorrect translation.