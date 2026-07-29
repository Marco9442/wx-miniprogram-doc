# [#](#FileSystemManager-getSavedFileList-Object-object) FileSystemManager.getSavedFileList(Object object)

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [文件系统](../../framework/ability/file-system.html)

## [#](#功能描述) 功能描述

获取该小程序下已保存的本地缓存文件列表

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | fileList | Array.<Object> | 文件数组 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | filePath | string | 文件路径 (本地路径) | |  | size | number | 本地文件大小，以字节为单位 | |  | createTime | number | 文件保存时的时间戳，从1970/01/01 08:00:00 到当前时间的秒数 | | | |

Incorrect translation.