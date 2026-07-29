# [#](#LogManager) LogManager

日志管理器实例，可以通过 [wx.getLogManager](wx.getLogManager.html) 获取。

## [#](#方法) 方法

### [#](#LogManager-debug) [LogManager.debug()](LogManager.debug.html)

写 debug 日志

### [#](#LogManager-info) [LogManager.info()](LogManager.info.html)

写 info 日志

### [#](#LogManager-log) [LogManager.log()](LogManager.log.html)

写 log 日志

### [#](#LogManager-warn) [LogManager.warn()](LogManager.warn.html)

写 warn 日志

## [#](#使用说明) 使用说明

最多保存5M的日志内容，超过5M后，旧的日志内容会被删除。  
对于**小程序**，用户可以通过使用 [button](../../../component/button.html) 组件的 `open-type="feedback"` 来上传打印的日志。  
对于**小游戏**，用户可以通过使用 [wx.createFeedbackButton]((wx.createFeedbackButton)) 来创建上传打印的日志的按钮。  
开发者可以通过小程序管理后台左侧菜单“反馈管理”页面查看相关打印日志。  
   
基础库默认会把 `App`、`Page` 的生命周期函数和 `wx` 命名空间下的函数调用写入日志。

Incorrect translation.