# [#](#设备认证-SDK（安卓）) 设备认证 SDK（安卓）

**注意：License 计费不再支持使用设备认证 SDK 认证的设备，请尽快切换到[使用 WMPF 认证设备](device-register-wmpf)，无需维护 deviceToken，接入更便捷。**

在系统集成 rpmbd 后，开发者需要在 Launcher 应用中接入设备认证 SDK，SDK 主要提供以下能力：

- 注册设备 `registerDevice`：将 model\_id 和 SN 与设备绑定。一旦成功后 **model\_id 和 SN 不可修改**。
- 获取设备凭证 `getDeviceToken`：进行设备认证并从微信后台获取凭证，设备端发起通话时传给 VOIP 通话插件的 [initByCaller](voip-plugin/api/initByCaller) 接口的 voipToken 参数。

## [#](#_1-下载-SDK) 1. 下载 SDK

请在 [此处](https://git.weixin.qq.com/wxa_iot/voipsdk/) 下载 SDK 的 aar 文件。

**建议使用 1.3 及以上版本（物联网卡应使用 1.3.1 及以上版本）。低版本不支持并发调用 `registerVoipDevice`，请务必注意在前一次调用返回前不要重复调用。**

- v1.5.0 及以上版本需集成 `voipsdk-x.x-release.aar` 和 `safeguard-release.aar` 两个 aar 文件
- v1.3.1 及以下版本只需集成 `voipsdk-x.x-release.aar`

**注意：使用设备认证 SDK 前，需先保证 rmpbd 服务正常运行。**

## [#](#_2-接口文档（v1-5-0-及以上版本）) 2. 接口文档（v1.5.0 及以上版本）

### [#](#_2-1-注册设备-registerDevice) 2.1 注册设备 `registerDevice`

将 model\_id 和 SN 与设备绑定，一旦成功后 appid、model\_id、SN 均不能更换。

```
int registerDevice(String appid, String model_id, String sn, String sn_ticket) throws Exception
```

#### [#](#注意事项（调用前必读）) 注意事项（**调用前必读**）

- 注册设备成功后，会将 SN 固化至 EMMC/RPMB 分区中，标定此设备的唯一身份。**SN 和 model\_id 一经写入后续即不可更改。**
- **此处使用的 SN，必须经过 WMPF 的 [addDevice](https://developers.weixin.qq.com/doc/oplatform/Miniprogram_Frame/api/backend/addDevice) 接口作为 deviceId 注册，并与 WMPF [设备激活](https://developers.weixin.qq.com/doc/oplatform/Miniprogram_Frame/api/cli/boot/init) 使用的 deviceId 一致。** 否则后续无法正常发起通话。
- 注册成功后会在本 APK 的存储里存放数字证书，如果 APK 有变动（Android 系统认为应用变更了），则证书失效（会报错`cert fail`），可以清理 APK 的数据再以**相同的 appid、model\_id、SN**调用接口重新申请即可。
- 注册过程会有网络请求，时长根据网络情况会有所不同。高版本 android 不允许在主线程里进行网络请求，可以加处理或在线程里来调用 sdk。

#### [#](#参数说明) 参数说明

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| appid | String | 小程序的 appid |
| model\_id | String | [设备接入](device-access)时从「小程序管理后台」申请获得的 model\_id |
| sn | String | 设备序列号。厂商自己生成，长度不能超过 128 字节。字符只接受数字，大小写字母，下划线（\*）和连字符（-）。  **此处使用的 sn 必须与 WMPF 激活设备使用的 deviceId 一致** |
| sn\_ticket | String | 通过[获取设备票据](https://developers.weixin.qq.com/miniprogram/dev/server/API/hardware-device/api_getsnticket)接口获得 |

#### [#](#返回值) 返回值

其他异常说明请参考[设备验证常见问题](device-register)

| 名称 | 值 | 描述 |
| --- | --- | --- |
| OK | 0 | 成功 |
| ERR\_ARGS | -1 | 参数错误 |
| ERR\_IO | -2 | 通用 IO 错误 |
| ERR\_KEY\_IO | -3 | KEY 不匹配 |
| ERR\_RESPONSE | -4 | 网络请求无回复 |
| ERR\_PEM | -5 | 权限错误 |
| ERR\_INVALID\_KEY | -6 | KEY 不可用 |
| ERR\_SERVICE | -7 | rpmbd 服务没运行 |
| ERR\_EMMC\_UFS\_CONFUSED | -8 | EMMC/UFS 不匹配。里面已经存在 SN |
| ERR\_EMMC\_UFS\_IO | -9 | EMMC/UFS IO 错误 |
| ERR\_REG\_NOPEM | -10 | 密钥不存在 |

### [#](#_2-2-获取设备凭证-getDeviceToken) 2.2 获取设备凭证 `getDeviceToken`

进行设备认证，并从微信后台获取设备凭证。设备发起通话时需要将这一凭证传给 VOIP 通话插件的 [initByCaller](voip-plugin/api/initByCaller) 接口的 voipToken 参数。

```
String getDeviceToken(String appid, String model_id) throws Exception
```

如果设备是使用 v1.5 及以上版本 SDK 进行注册设备的，可以使用无参数的版本。

```
String getDeviceToken() throws Exception
```

#### [#](#参数说明-2) 参数说明

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| appid | String | 小程序的 appid |
| model\_id | String | [设备接入](device-access)时从「小程序管理后台」申请获得的 model\_id |

#### [#](#注意事项) 注意事项

- 接口耗时与网络有关，正常会在 1 秒左右。高版本 android 不允许在主线程里做，可以加处理或在线程里来调用 sdk。
- ticket 有一个小时的有效期，一个小时内可被多次通话复用。建议开发者在用户发起通话前，提前调用 getCallerTicket 并缓存，避免在发起通话时再进行获取，以缩短发起通话时的用户等待时长。

### [#](#_2-3-获取设备-SN-getDeviceSn（仅调试用）) 2.3 获取设备 SN `getDeviceSn`（仅调试用）

获取 `registerDevice` 接口写入的 SN。

```
String getDeviceSn()
```

### [#](#_2-4-获取设备-modelId-getDeviceModelid（仅调试用）) 2.4 获取设备 modelId `getDeviceModelid`（仅调试用）

获取使用 `registerDevice` 接口写入的 modelId。仅在设备是使用 v1.5 及以上版本 SDK 进行注册设备时有效。

```
String getDeviceModelid()
```

## [#](#_3-接口文档（v1-3-1-及以下版本）) 3. 接口文档（v1.3.1 及以下版本）

### [#](#_3-1-初始化-init) 3.1 初始化 `init`

SDK 初始化，其它接口在调用之前需要保证 init 成功。

```
boolean init()
```

### [#](#_3-2-注册设备-registerVoipDevice) 3.2 注册设备 `registerVoipDevice`

参考 2.1 `registerDevice`。

- **1.3 以下版本 SDK，此接口严禁并发执行**，务必在逻辑中保证一次 registerVoipDevice 返回后才能再次调用。

### [#](#_3-3-获取拨打方票据-getCallerTicket) 3.3 获取拨打方票据 `getCallerTicket`

参考 2.2 `getDeviceToken`

### [#](#_3-4-获取设备-SN-GetDeviceSn（仅调试用）) 3.4 获取设备 SN `GetDeviceSn`（仅调试用）

同 2.3 `getDeviceSn`

Incorrect translation.