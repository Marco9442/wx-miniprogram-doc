# [#](#wx-previewMedia) wx.previewMedia

预览图片和视频

## [#](#注意事项) 注意事项

- wx.previewMedia：iOS SDK >= 1.5.2 ；Android SDK >= 1.5.9
- 使用该接口能力之前，需在微信开发者工具 `project.miniapp.json` 中勾选 iOS 的「Video SDK」以及 Android 的「Media SDK」
- 与小程序端的 `wx.previewMedia` 参数有所区别，详情查看下方文档

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | sources | Array.<Object> |  | 是 | 需要预览的资源列表 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | url | String |  | 是 | 图片或视频的地址 | |  | type | String | image | 否 | 资源的类型，默认为图片 | |  | | 合法值 | 说明 | | --- | --- | | image | 图片 | | video | 视频 | | | | | | |  | poster | string |  | 否 | 视频的封面图片 | | | | | | |
|  | current | number | 0 | 否 | 当前显示的资源序号 |
|  | showmenu | boolean | true | 否 | 是否显示操作菜单。不支持长按识别 |
|  | referrerPolicy | string | no-referrer | 否 | 该参数在App端不支持 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.