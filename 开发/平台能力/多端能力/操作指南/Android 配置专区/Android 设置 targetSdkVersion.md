# [#](#Android-设置-targetSdkVersion) Android 设置 targetSdkVersion

targetSdkVersion 是用于指定应用的目标 Android 版本（API 等级），设置 targetSdkVersion 的值即表示 App 适配的 Android 版本（API 等级），如果平台的 API 级别高于应用 targetSdkVersion 所声明的版本，系统便可启用兼容性行为。故设置低版本的 targetSdkVersion 会使 APP 兼容模式运行，也就可能无法用到新系统的特性，甚至在兼容模式下运行可能存在安全漏洞等问题，因此开发者需谨慎设置。

**注意**

1、多端应用在开发者工具中默认的 targetSdkVersion 默认值为 29，且支持可设置的最小值为 29（即开发者可设置 ≥ 29 的值；一些应用市场会要求设置较高的 targetSdkVersion 才可以提交，开发者在提交应用市场审核时按照应用市场要求设置）。

2、App 升级时 targetSdkVersion 只能增加不能降低，也就是说 targetSdkVersion 高的 App 无法被 targetSdkVersion 低的 App 覆盖安装。

3、targetSdkVersion 值为 Number 类型，且必须为正整数，取值范围参考下方的 Android 版本列表中的 API 等级。

## [#](#一、targetSdkVersion-配置指引) 一、targetSdkVersion 配置指引

将开发者工具升级至最新的 [nightly 版](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)，进入到多端模式，点击 `project.miniapp.json`，找到 Android 下的「其他常用设置」，可参考下图进行 targetSdkVersion 配置。

- 配置之后需重新构建 APK 即可生效。
- minSdkVersion 用于配置应用运行所需最低 API 级别的整数。如果系统的 API 级别低于该属性中指定的值，Android 系统将阻止用户安装应用。默认值为 21，请勿填写低于 21 的值。

![](https://res.wx.qq.com/op_res/7PrSl5jgk_Dg8Xk0LC9vO2PDuMGoG85II_HXeLDbqbze5Sq_nkgDnVzehtByKsArug9XoMxt7NA_UDYdfNoqRg)

## [#](#二、API-等级与-Android-版本对应列表) 二、API 等级与 Android 版本对应列表

更多详情可以查看官网<https://developer.android.com/guide/topics/manifest/uses-sdk-element?hl=zh-cn>

| 平台版本 | API 级别 |
| --- | --- |
| [Android 14](https://developer.android.com/about/versions/14?hl=zh-cn) | [34](https://developer.android.com/sdk/api_diff/34/changes?hl=zh-cn) |
| [Android 13](https://developer.android.com/about/versions/13?hl=zh-cn) | [33](https://developer.android.com/sdk/api_diff/33/changes?hl=zh-cn) |
| [Android 12](https://developer.android.com/about/versions/12?hl=zh-cn) | [32](https://developer.android.com/sdk/api_diff/32/changes?hl=zh-cn) |
| [Android 12](https://developer.android.com/about/versions/12?hl=zh-cn) | [31](https://developer.android.com/sdk/api_diff/31/changes) |
| [Android 11](https://developer.android.com/about/versions/11?hl=zh-cn) | [30](https://developer.android.com/sdk/api_diff/30/changes?hl=zh-cn) |
| [Android 10](https://developer.android.com/about/versions/10?hl=zh-cn) | [29](https://developer.android.com/sdk/api_diff/29/changes?hl=zh-cn) |
| [Android 9](https://developer.android.com/about/versions/pie?hl=zh-cn) | [28](https://developer.android.com/sdk/api_diff/28/changes?hl=zh-cn) |
| [Android 8.1](https://developer.android.com/about/versions/oreo/android-8.1?hl=zh-cn) | [27](https://developer.android.com/sdk/api_diff/27/changes?hl=zh-cn) |
| [Android 8.0](https://developer.android.com/about/versions/oreo?hl=zh-cn) | [26](https://developer.android.com/sdk/api_diff/26/changes?hl=zh-cn) |
| [Android 7.1.1、7.1](https://developer.android.com/about/versions/nougat/android-7.1?hl=zh-cn) | [25](https://developer.android.com/sdk/api_diff/25/changes?hl=zh-cn) |
| [Android 7.0](https://developer.android.com/about/versions/nougat/android-7.0?hl=zh-cn) | [24](https://developer.android.com/sdk/api_diff/24/changes?hl=zh-cn) |
| [Android 6.0](https://developer.android.com/about/versions/marshmallow/android-6.0?hl=zh-cn) | [23](https://developer.android.com/sdk/api_diff/23/changes?hl=zh-cn) |
| [Android 5.1](https://developer.android.com/about/versions/android-5.1?hl=zh-cn) | [22](https://developer.android.com/sdk/api_diff/22/changes?hl=zh-cn) |
| [Android 5.0](https://developer.android.com/about/versions/android-5.0?hl=zh-cn) | [21](https://developer.android.com/sdk/api_diff/21/changes?hl=zh-cn) |
| [Android 4.4](https://developer.android.com/about/versions/android-4.4?hl=zh-cn) | [19](https://developer.android.com/sdk/api_diff/19/changes?hl=zh-cn) |
| [Android 4.3](https://developer.android.com/about/versions/android-4.3?hl=zh-cn) | [18](https://developer.android.com/sdk/api_diff/18/changes?hl=zh-cn) |
| [Android 4.2、4.2.2](https://developer.android.com/about/versions/android-4.2?hl=zh-cn) | [17](https://developer.android.com/sdk/api_diff/17/changes?hl=zh-cn) |
| [Android 4.1、4.1.1](https://developer.android.com/about/versions/android-4.1?hl=zh-cn) | [16](https://developer.android.com/sdk/api_diff/16/changes?hl=zh-cn) |
| [Android 4.0.3、4.0.4](https://developer.android.com/about/versions/android-4.0.3?hl=zh-cn) | [15](https://developer.android.com/sdk/api_diff/15/changes?hl=zh-cn) |
| [Android 4.0、4.0.1、4.0.2](https://developer.android.com/about/versions/android-4.0?hl=zh-cn) | [14](https://developer.android.com/sdk/api_diff/14/changes?hl=zh-cn) |
| [Android 3.2](https://developer.android.com/about/versions/android-3.2?hl=zh-cn) | [13](https://developer.android.com/sdk/api_diff/13/changes?hl=zh-cn) |
| [Android 3.1.x](https://developer.android.com/about/versions/android-3.1?hl=zh-cn) | [12](https://developer.android.com/sdk/api_diff/12/changes?hl=zh-cn) |
| [Android 3.0.x](https://developer.android.com/about/versions/android-3.0?hl=zh-cn) | [11](https://developer.android.com/sdk/api_diff/11/changes?hl=zh-cn) |
| [Android 2.3.4、2.3.3](https://developer.android.com/about/versions/android-2.3.3?hl=zh-cn) | [10](https://developer.android.com/sdk/api_diff/10/changes?hl=zh-cn) |
| [Android 2.3.2、2.3.1、2.3](https://developer.android.com/about/versions/android-2.3?hl=zh-cn) | [9](https://developer.android.com/sdk/api_diff/9/changes?hl=zh-cn) |
| [Android 2.2.x](https://developer.android.com/about/versions/android-2.2?hl=zh-cn) | [8](https://developer.android.com/sdk/api_diff/8/changes?hl=zh-cn) |
| [Android 2.1.x](https://developer.android.com/about/versions/android-2.1?hl=zh-cn) | [7](https://developer.android.com/sdk/api_diff/7/changes?hl=zh-cn) |
| [Android 2.0.1](https://developer.android.com/about/versions/android-2.0.1?hl=zh-cn) | [6](https://developer.android.com/sdk/api_diff/6/changes?hl=zh-cn) |
| [Android 2.0](https://developer.android.com/about/versions/android-2.0?hl=zh-cn) | [5](https://developer.android.com/sdk/api_diff/5/changes?hl=zh-cn) |
| [Android 1.6](https://developer.android.com/about/versions/android-1.6?hl=zh-cn) | [4](https://developer.android.com/sdk/api_diff/4/changes?hl=zh-cn) |
| [Android 1.5](https://developer.android.com/about/versions/android-1.5?hl=zh-cn) | [3](https://developer.android.com/sdk/api_diff/3/changes?hl=zh-cn) |
| [Android 1.1](https://developer.android.com/about/versions/android-1.1?hl=zh-cn) | 2 |
| Android 1.0 | 1 |

Incorrect translation.