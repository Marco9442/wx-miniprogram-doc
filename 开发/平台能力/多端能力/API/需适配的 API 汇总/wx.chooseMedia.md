# [#](#wx-chooseMedia) wx.chooseMedia

拍摄或从手机相册中选择图片或视频。

## [#](#注意事项) 注意事项

- iOS SDK 版本需要 ≥ 1.0.18
- Android SDK 版本需要 ≥ 1.0.10
- 使用该接口能力之前，需在微信开发者工具 `project.miniapp.json` 中勾选「Media SDK」，若为 iOS 且 iOS SDK >= 1.3.11 则需同时勾选「Media SDK」中的「Video SDK」与「Image SDK」。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202409031112530.png)

- 使用该接口能力之前，需在微信开发者工具 `project.miniapp.json` 中配置「Android 权限描述配置」或 iOS「隐私信息访问许可描述」的相册读取、摄像头以及麦克风的许可描述。即，该接口需获得相册读取、摄像头以及麦克风权限才可以调用。
  ![](https://res.wx.qq.com/op_res/iWKxAkX6DmXvKx_Z9gVonCo7CfeqKkYK13wL-qTfxvsvlnHs5ba0MIGwwSUQZ2W8ZJXGhrjTS5npE9SLU2I7EA)
- 补充：如果 Android 的 `targetSdkVersion` 配置为 33 及以上，则需在 `project.miniapp.json` 中新增下方这三个权限描述（如果你的开发者工具打开后没有下方三个配置，请将开发者工具升级到[最新的 nightly 版](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)）
  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202402231741545.png)

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | count | number | 9 | 否 | 最多可以选择的文件个数，基础库 2.25.0 前，最多可支持 9 个文件，2.25.0 及以后最多可支持 20 个文件 |
|  | mediaType | Array.<string> | ['image', 'video'] | 否 | 文件类型 |
|  | | 合法值 | 说明 | | --- | --- | | image | 只能拍摄图片或从相册选择图片 | | video | 只能拍摄视频或从相册选择视频 | | mix | 可以出现视频和图片，但是不可以同时选视频和图片 | | | | | |
|  | sourceType | Array.<string> | ['album', 'camera'] | 否 | 图片和视频选择的来源 |
|  | | 合法值 | 说明 | | --- | --- | | album | 从相册选择 | | camera | 使用相机拍摄 | | | | | |
|  | maxDuration | number | 10 | 否 | 拍摄视频最长拍摄时间，单位秒。时间范围为 3s 至 60s 之间。不限制相册。 |
|  | sizeType | Array.<string> | ['original', 'compressed'] | 否 | 是否压缩所选文件，仅对 mediaType 为 image 时有效 |
|  | camera | string | 'back' | 否 | 仅在 sourceType 为 camera 时生效，使用前置或后置摄像头 |
|  | | 合法值 | 说明 | | --- | --- | | back | 使用后置摄像头 | | front | 使用前置摄像头 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | tempFiles | Array.<Object> | 本地临时文件列表 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | tempFilePath | string | 本地临时文件路径 (本地路径) | |  | size | number | 本地临时文件大小，单位 B | |  | duration | number | 视频的时间长度 | |  | height | number | 视频的高度 | |  | width | number | 视频的宽度 | |  | thumbTempFilePath | string | 视频缩略图临时文件路径 | |  | fileType | string | 文件类型 | |  | | 合法值 | 说明 | | --- | --- | | image | 图片 | | video | 视频 | | | | | | |
|  | type | string | 文件类型，有效值有 image、video、mix |

## [#](#示例代码) 示例代码

```
wx.chooseMedia({
  count: 9,
  mediaType: ['image','video'],
  sourceType: ['album', 'camera'],
  maxDuration: 30,
  camera: 'back',
  success(res) {
    console.log(res.tempFiles[0].tempFilePath)
    console.log(res.tempFiles[0].size)
  }
})
```

Incorrect translation.