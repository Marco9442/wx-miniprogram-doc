# [#](#Android-NativePrivacyPlugin-隐私授权相关插件) Android NativePrivacyPlugin 隐私授权相关插件

在打开应用前，安卓合规规范要求必须要有隐私弹窗授权的过程。该隐私授权过程需要在用户同意前，才能允许应用获取相关的隐私信息数据。多端场景提供了配置默认隐私弹窗的能力。但对于

1. 需要自定义隐私弹窗的样式和交互
2. 需要设置用户拒绝隐私授权后，`仅浏览模式的兜底页面`

则需要考虑通过 NativePrivacyPlugin 隐私授权相关插件来实现

### [#](#实例代码) 实例代码

具体可以参考这个项目里的
[插件示例privacy-plugin-demo](https://dldir1.qq.com/WechatWebDev/donut/android/android-demo.zip)

## [#](#开发流程) 开发流程

### [#](#_1-继承-NativePrivacyPluginBase) 1.继承 NativePrivacyPluginBase

参考下面代码

```
package com.donut.xxxx
import android.app.Activity
import android.content.Context
import android.content.Intent
import androidx.core.content.ContextCompat.startActivity
import com.tencent.luggage.wxa.SaaA.plugin.NativePrivacyPluginBase

class PrivacyNativePlugin: NativePrivacyPluginBase() {
    private val TAG = "TestNativePrivacyPlugin"
    override fun getPluginID(): String {
        android.util.Log.e(TAG, "getPluginID")
        return BuildConfig.PLUGIN_ID
    }

    companion object {
        private var instance: PrivacyNativePlugin? = null
        fun getInstance(): PrivacyNativePlugin {
            if (instance == null) {
                instance = PrivacyNativePlugin()
            }
            return instance!!
        }

        private var currentActivity: Activity? = null

       fun setCurrentActivity(activity: Activity) {
           currentActivity = activity
       }

        fun finishCurrentActivity() {
            currentActivity?.finish()
        }
    }

    // 展示隐私弹窗，如使用多端默认的，则可以直接调用 super 的
    fun showAppPrivacyPopup(context: Context) {
        // 只能调用
        super.showPrivacyPopup(context)
    }

    // 获取默认隐私弹窗是否同意结果情况
    override fun onPluginPrivacyResult(result: Boolean) {
        // 如果插件触发的隐私弹窗用户同意了，则只需要关闭自己的 activity
        if (result === true) {
            // 关闭当前的 activity
            PrivacyNativePlugin.finishCurrentActivity()
        }
    }

    // 当用户不同意隐私弹窗的时候，展示自己的业务 activity
    override fun launchRejectedActivity(context: Context) {
        val activityIntent = Intent(context, PrivacyRejectedActivity::class.java);
        activityIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
        startActivity(context, activityIntent, null);
    }
}
```

### [#](#_2-配置接口实现类) 2.配置接口实现类

在 `plugin/src/main/resources/META-INF/services/`目录下新建文件`com.tencent.luggage.wxa.SaaA.plugin.NativePrivacyPluginInterface`

文件内容配置`NativePrivacyPluginInterface`接口实现类的路径，如下图所示
![](https://dldir1.qq.com/WechatWebDev/donut/android/privacy-service.png)

### [#](#_3-开始测试) 3.开始测试

- 查看`DemoApplication`文件(`/app/src/main/java/com/tencent/weauth/DemoApplication.kt`)
- 确认 `SaaAApi.Factory.createApi` 函数里 新增 `privacyPopupCancelWithoutKill = true` 的配置，则会设置当用户不同意隐私授权弹窗的时候，打开应用时，会直接打开当前的隐私授权插件，来展示仅浏览模式的兜底页面
  ![](https://dldir1.qq.com/WechatWebDev/donut/android/privacywithoutkill.png)

### [#](#_4-构建插件上传后在云构建时使用) 4.构建插件上传后在云构建时使用

参考 Android 原生插件开发指引的[上传章节](androidPlugin#上传)即可

Incorrect translation.