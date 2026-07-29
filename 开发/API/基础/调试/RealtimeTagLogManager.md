# [#](#RealtimeTagLogManager) RealtimeTagLogManager

> 基础库 2.16.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [实时日志](../../../framework/realtimelog/index.html)

给定标签的实时日志管理器实例，可以通过 [RealtimeLogManager.tag](RealtimeLogManager.tag.html) 接口获取，目前只支持在插件使用。

## [#](#方法) 方法

### [#](#RealtimeTagLogManager-info-string-key-Object-Array-any-number-string-value) [RealtimeTagLogManager.info(string key, Object|Array.<any>|number|string value)](RealtimeTagLogManager.info.html)

写 info 日志

### [#](#RealtimeTagLogManager-warn-string-key-Object-Array-any-number-string-value) [RealtimeTagLogManager.warn(string key, Object|Array.<any>|number|string value)](RealtimeTagLogManager.warn.html)

写 warn 日志

### [#](#RealtimeTagLogManager-error-string-key-Object-Array-any-number-string-value) [RealtimeTagLogManager.error(string key, Object|Array.<any>|number|string value)](RealtimeTagLogManager.error.html)

写 error 日志

### [#](#RealtimeTagLogManager-setFilterMsg-string-msg) [RealtimeTagLogManager.setFilterMsg(string msg)](RealtimeTagLogManager.setFilterMsg.html)

设置过滤关键字

### [#](#RealtimeTagLogManager-addFilterMsg-string-msg) [RealtimeTagLogManager.addFilterMsg(string msg)](RealtimeTagLogManager.addFilterMsg.html)

添加过滤关键字

## [#](#使用说明) 使用说明

[RealtimeTagLogManager](RealtimeTagLogManager.html) 功能和 [RealtimeLogManager](RealtimeLogManager.html) 相似，但是为了让输出的实时日志更易于分析，其具有更严格的格式要求。  
 [RealtimeTagLogManager](RealtimeTagLogManager.html) 使用时需要传入标签，调用该实例所输出的日志均会被汇集到对应标签下，同时该实例的日志只支持 key-value 格式进行输出。

Incorrect translation.