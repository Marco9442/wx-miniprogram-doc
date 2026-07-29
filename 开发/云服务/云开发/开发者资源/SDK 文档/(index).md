# [#](#Cloud) Cloud

云开发 SDK 实例

## [#](#属性) 属性

### [#](#Symbol-DYNAMIC-CURRENT-ENV) Symbol DYNAMIC\_CURRENT\_ENV

仅在云函数 SDK。标志当前所在环境。[常量文档](constant/constant)。

### [#](#openapi-openapi) openapi openapi

仅在云函数 SDK。云调用 API 对象。[云调用文档](../guide/openapi/openapi)

### [#](#CloudPay-cloudPay) CloudPay cloudPay

仅在云函数 SDK。云调用 API 对象。[云调用文档](../guide/openapi/openapi)

## [#](#方法) 方法

### [#](#Cloud-init) <Cloud.init>()

初始化 SDK 实例

### [#](#Cloud-callContainer-options-Object-Promise-Object) [Cloud.callContainer](container/Cloud.callContainer)(options: Object): Promise<Object>

调用云托管服务

### [#](#Cloud-callFunction-object-Object-Promise-Object) [Cloud.callFunction](functions/Cloud.callFunction)(object: Object): Promise<Object>

调用云函数

### [#](#Cloud-database-options-Object-Database) <Cloud.database>(options: Object): [Database](database/Database)

获取数据库实例

### [#](#Cloud-CloudID-cloudID-string) [Cloud.CloudID](open/Cloud.CloudID)(cloudID: string)

声明字符串为 CloudID（开放数据 ID），该接口传入一个字符串，返回一个 `CloudID` 特殊对象，将该对象传至云函数可以获取其对应的开放数据。详见[通过云调用获取开放数据](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/signature)

### [#](#Cloud-getCloudCallSign-options-Object-Object) [Cloud.getCloudCallSign](open/Cloud.getCloudCallSign)(options: Object): Object

获取签名

### [#](#Cloud-getOpenData-list-string-Object) [Cloud.getOpenData](open/Cloud.getOpenData)(list: string[]): Object

获取 CloudID 对应的开放数据

### [#](#Cloud-getVoIPSign-options-Object-Promise-Object) [Cloud.getVoIPSign](open/Cloud.getVoIPSign)(options: Object): Promise<Object>

获取实时语音签名

### [#](#Cloud-deleteFile-fileList-string-Promise-Object) [Cloud.deleteFile](storage/Cloud.deleteFile)(fileList: string[]): Promise<Object>

从云存储空间删除文件，一次最多 50 个

### [#](#Cloud-downloadFile) [Cloud.downloadFile](storage/Cloud.downloadFile)()

从云存储空间下载文件

### [#](#Cloud-getTempFileURL-fileList-string-Promise-Object) [Cloud.getTempFileURL](storage/Cloud.getTempFileURL)(fileList: string[]): Promise<Object>

用云文件 ID 换取真实链接，公有读的文件获取的链接不会过期，私有的文件获取的链接十分钟有效期。一次最多取 50 个。

### [#](#Cloud-uploadFile) [Cloud.uploadFile](storage/Cloud.uploadFile)()

将本地资源上传至云存储空间，如果上传至同一路径则是覆盖

### [#](#Cloud-CDN-opt-string-ArrrayBuffer-Object) [Cloud.CDN](utils/Cloud.CDN)(opt: string|ArrrayBuffer|Object)

小程序端调云函数传递大数据可用的临时 CDN

### [#](#Cloud-Cloud-options-Object-Cloud) [Cloud.Cloud](utils/Cloud.Cloud)(options: Object): <Cloud>

新建云开发操作实例

### [#](#Cloud-getJSSDKSignature-options-Object-Promise-Object) [Cloud.getJSSDKSignature](web/Cloud.getJSSDKSignature)(options: Object): Promise<Object>

web 中使用 SDK 登录之后可用此方法获取用于 wx.config 的 JSSDK 签名

### [#](#Cloud-getWXContext-Object) [Cloud.getWXContext](utils/Cloud.getWXContext)(): Object

在云函数中获取微信调用上下文

### [#](#Cloud-logger-Object) [Cloud.logger](utils/Cloud.logger)(): Object

云函数中使用[高级日志](../guide/functions/logservice)能力

### [#](#Cloud-refreshAuth-Promise-Object) [Cloud.refreshAuth](web/Cloud.refreshAuth)(): Promise<Object>

web 中检查登录状态

### [#](#Cloud-signature-opt-Object) [Cloud.signature](utils/Cloud.signature)(opt: Object)

计算签名的辅助方法，可用于小游戏虚拟支付云调用

### [#](#Cloud-checkLogin-options-Object-Promise-Object) [Cloud.checkLogin](web/Cloud.checkLogin)(options: Object): Promise<Object>

web 中检查登录状态

### [#](#Cloud-startLogin-options-Object) [Cloud.startLogin](web/Cloud.startLogin)(options: Object)

web 中发起网页授权登录

Incorrect translation.