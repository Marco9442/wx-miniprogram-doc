# [#](#Snapshot-takeSnapshot-Object-object) Snapshot.takeSnapshot(Object object)

> 基础库 3.0.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [snapshot](../../component/snapshot.html)

## [#](#功能描述) 功能描述

对 snapshot 组件子树进行截图

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| type | String |  | 是 | 截图导出类型，'file' 保存到临时文件目录或 'arraybuffer' 返回图片二进制数据，默认值为 'file' |
| format | String |  | 是 | 截图文件格式，'rgba' 或 'png'，默认值为 'png' |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | String | 截图保存的临时文件路径，当 type 为 file 该字段生效 |
| data | ArrayBuffer | 截图对应的二进制数据，当 type 为 arraybuffer 该字段生效 |

Incorrect translation.