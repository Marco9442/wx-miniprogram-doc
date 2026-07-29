# [#](#Android-NativePluginApplication-应用-lifecrycle-插件) Android NativePluginApplication 应用 lifecrycle 插件

前面讲到大部分拓展能力可以通过 [NativePlugin 通用拓展插件](androidPluginBase) 来实现，但 `NativePlugin` 其插件实例是运行在小程序的子进程中，其获取的 Activity 是小程序运行时的 Activity。

对于需要`初始化必须在Application.onCreate函数中主线程内调用`、或者`需要通过registerActivityLifecycleCallbacks监听应用前后台切换`的场景，我们则使用通过`NativePluginApplication`类型插件来解决该问题

### [#](#配置准备) 配置准备

- `debugSaaAVersion` 要更新到 `1.0.7`及以上版本 （对应最小Android Sdk Version 为 `1.3.28`）

> 请注意，当前创建多端插件项目的默认`debugSaaAVersion`版本为`1.0.10`，如果您的`debugSaaAVersion`过低，建议新建一个多端插件项目

## [#](#开发流程) 开发流程

### [#](#_1-继承NativePluginApplicationInterface) 1.继承NativePluginApplicationInterface

参考下面代码

```
package com.donut.xxx

import android.app.Activity
import android.app.Application
import android.os.Bundle
import com.tencent.luggage.wxa.SaaA.plugin.NativePluginApplicationInterface

class TestNativePluginApplication: NativePluginApplicationInterface {
    private val TAG = "TestNativePluginApplication"

    override fun getPluginID(): String {
        android.util.Log.e(TAG, "getPluginID")
        return BuildConfig.PLUGIN_ID
    }

    override fun onCreate(application: Application) {
        android.util.Log.e(TAG, "oncreate!")
        application.registerActivityLifecycleCallbacks(object: Application.ActivityLifecycleCallbacks {
            override fun onActivityCreated(p0: Activity, p1: Bundle?) {
                android.util.Log.e(TAG, "onActivityCreated")
            }

            override fun onActivityStarted(p0: Activity) {
                android.util.Log.e(TAG, "onActivityStarted")
            }

            override fun onActivityResumed(p0: Activity) {
                android.util.Log.e(TAG, "onActivityResumed")
            }

            override fun onActivityPaused(p0: Activity) {
                android.util.Log.e(TAG, "onActivityPaused")
            }

            override fun onActivityStopped(p0: Activity) {
                android.util.Log.e(TAG, "onActivityStopped")
            }

            override fun onActivitySaveInstanceState(p0: Activity, p1: Bundle) {
                android.util.Log.e(TAG, "onActivitySaveInstanceState")
            }

            override fun onActivityDestroyed(p0: Activity) {
                android.util.Log.e(TAG, "onActivityDestroyed")
            }
        })
    }

}
```

### [#](#_2-配置接口实现类) 2.配置接口实现类

在 `plugin/src/main/resources/META-INF/services/`目录下新建文件`com.tencent.luggage.wxa.SaaA.plugin.NativePluginApplicationInterface`

文件内容配置`NativePluginApplicationInterface`接口实现类的路径，如下图所示
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202408301045183.png)

### [#](#_3-开始测试) 3.开始测试

- 查看`DemoApplication`文件(`/app/src/main/java/com/tencent/weauth/DemoApplication.kt`)
- 确认 `onCreate` 函数里 是否执行`api.runWhenApplicationOnCreate` ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202408301109050.png)
- 如果没有这段代码，建议重新生成插件项目

```
    override fun onCreate() {
        super.onCreate()
        try {
            val api = SaaAApi.Factory.getApi()
            if (api != null) {
                // 如果您的插件需要使用 application 生命周期钩子，请保证项目里存在以下这段逻辑
                api.runWhenApplicationOnCreate(this)
            }
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
```

### [#](#_4-构建插件上传后在云构建时使用) 4.构建插件上传后在云构建时使用

参考 Android 原生插件开发指引的[上传章节](androidPlugin#上传)即可

Incorrect translation.