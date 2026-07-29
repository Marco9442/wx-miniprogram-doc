# [#](#Performance) Performance

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

Performance 对象，用于获取性能数据及创建性能监听器

## [#](#方法) 方法

### [#](#Array-PerformanceEntry-Performance-getEntries) [Array.<PerformanceEntry> Performance.getEntries()](Performance.getEntries.html)

该方法返回当前缓冲区中的所有性能数据

### [#](#Array-PerformanceEntry-Performance-getEntriesByType-string-entryType) [Array.<PerformanceEntry> Performance.getEntriesByType(string entryType)](Performance.getEntriesByType.html)

获取当前缓冲区中所有类型为 [entryType] 的性能数据

### [#](#Array-PerformanceEntry-Performance-getEntriesByName-string-name-string-entryType) [Array.<PerformanceEntry> Performance.getEntriesByName(string name, string entryType)](Performance.getEntriesByName.html)

获取当前缓冲区中所有名称为 [name] 且类型为 [entryType] 的性能数据

### [#](#PerformanceObserver-Performance-createObserver-function-callback) [PerformanceObserver Performance.createObserver(function callback)](Performance.createObserver.html)

创建全局性能事件监听器

### [#](#Performance-setBufferSize-number-size) [Performance.setBufferSize(number size)](Performance.setBufferSize.html)

设置缓冲区大小，默认缓冲 30 条性能数据

Incorrect translation.