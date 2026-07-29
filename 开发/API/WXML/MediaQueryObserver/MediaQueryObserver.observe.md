# [#](#MediaQueryObserver-observe-Object-descriptor-function-callback) MediaQueryObserver.observe(Object descriptor, function callback)

> **小程序插件**：支持

## [#](#功能描述) 功能描述

开始监听页面 media query 变化情况

## [#](#参数) 参数

### [#](#Object-descriptor) Object descriptor

media query 描述符

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| minWidth | number |  | 否 | 页面最小宽度（ px 为单位） |
| maxWidth | number |  | 否 | 页面最大宽度（ px 为单位） |
| width | number |  | 否 | 页面宽度（ px 为单位） |
| minHeight | number |  | 否 | 页面最小高度（ px 为单位） |
| maxHeight | number |  | 否 | 页面最大高度（ px 为单位） |
| height | number |  | 否 | 页面高度（ px 为单位） |
| orientation | string |  | 否 | 屏幕方向（ `landscape` 或 `portrait` ） |

### [#](#function-callback) function callback

监听 media query 状态变化的回调函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| matches | boolean | 页面的当前状态是否满足所指定的 media query |

Incorrect translation.