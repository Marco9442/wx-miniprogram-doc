# [#](#Android-NativePlugin-通用拓展插件) Android NativePlugin 通用拓展插件

> 大部分拓展能力都可以通过 NativePlugin 通用拓展插件来实现。如自定义新增一个 APP 内小程序页面的 JSAPI 或者注册一些原生事件监听，从此暴露一些 APP 原生功能给小程序进行调用。

## [#](#多端应用与多端插件的调用时序) 多端应用与多端插件的调用时序

在开始 Android 多端插件的开发前，理解多端应用与多端插件的调用时序将更好帮助开发者进行开发。

sequenceDiagram
participant app as 多端应用
participant plugin as 多端插件
app->>app:wx.miniapp.loadNativePlugin 加载插件
app->>plugin: 加载插件
plugin->>plugin: 载入时即实例化插件对象
app->>plugin: 加载插件，进行一系列初始化操作（包括 id 注册、插件方法注册、插件 initPlugin 方法调用）
app->>app: 持有插件实例 pluginInstance
note over app,plugin: 插件加载完成
app->>plugin: pluginInstance.func() 进行插件方法的调用

请注意：

1. Android pluginInstance 的插件实例运行在小程序的**子进程**中。
2. 在此情境下获取的 Activity 是**小程序运行时的 Activity**。

注册加载流程 sdk 会实现，开发者只需要继承NativePluginInterface，实现需要暴露给 js 侧的方法

```
import com.tencent.luggage.wxa.SaaA.plugin.NativePluginInterface
import com.tencent.luggage.wxa.SaaA.plugin.SyncJsApi
import com.tencent.luggage.wxa.SaaA.plugin.AsyncJsApi
import org.json.JSONObject

class TestNativePlugin: NativePluginInterface {
    private val TAG = "TestNativePlugin"

    override fun getPluginID(): String {
        android.util.Log.i(TAG, "getPluginID")
        return BuildConfig.PLUGIN_ID
    }

    // 同步方法
    // js 侧调用 plugin.mySyncFunc 会触发 test 函数
    @SyncJsApi(methodName = "mySyncFunc")
    fun test(data: JSONObject?): String {
        android.util.Log.i(TAG, data.toString())
        return "test"
    }

    // 异步方法
    // js 侧调用 plugin.myAsyncFuncwithCallback 会触发 testAsync 函数
    @AsyncJsApi(methodName = "myAsyncFuncwithCallback")
    fun testAsync(data: JSONObject?, callback: (data: Any) -> Unit) {
        android.util.Log.i(TAG, data.toString())

        callback("async testAsync")
    }

}
```

### [#](#注册同步方法) 注册同步方法

- 使用 `SyncJsApi` 注解

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| methodName | String | 是 | 在 js 层可用获取的 pluginInstance.methodName 进行方法调用 |

- 同步方法的入参与出参

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| 入参 1 | JSONObject? | 否 | 在 js 层调用 pluginInstance.methodName 时传入的 Object 类型参数 |
| 入参 2 | Activity | 否 | 小程序当前运行的 Activity，要正常获取该参数`debugSaaAVersion` 要更新到 `1.0.1`及以上版本 |
| 出参 | 可序列化类型 | 否 | 在 js 层调用 pluginInstance.methodName 的返回 |

- 代码示例

Android 侧的插件同步方法实现

```
    @SyncJsApi(methodName = "mySyncFunc")
    fun test(data: JSONObject?): String {
        android.util.Log.i(TAG, data.toString())
        return "test"
    }
```

如果要获取 activity：

```
    @SyncJsApi(methodName = "mySyncFunc")
    fun test(data: JSONObject?, activity: Activity): String {
        android.util.Log.i(TAG, data.toString())

        val componentName = activity.componentName.toString()
        android.util.Log.i(TAG, componentName)
        
        return "test"
    }
```

JS 侧的方法调用

```
wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        console.log('load plugin success')
        const ret = plugin.mySyncFunc({ a: 'hello', b: [1,2] })
        console.log('mySyncFunc ret:', ret)
    },
    fail: (e) => {
        console.log('load plugin fail', e)
    }
})
```

### [#](#注册异步方法) 注册异步方法

- 使用 `AsyncJsApi` 注解

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| methodName | String | 是 | 在 js 层可用获取的 pluginInstance.methodName 进行方法调用 |

- 异步方法的入参与出参

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| 入参1 | JSONObject? | 是 | 在 js 层调用 pluginInstance.methodName 时传入的第 1 个 Object 类型参数 |
| 入参2 | 函数 | 是 | 该回调方法支持一个可序列化类型的参数。通过该方法回调传回给 js 层 |
| 入参3 | Activity | 否 | 小程序当前运行的 Activity，要正常获取该参数`debugSaaAVersion` 要更新到 `1.0.1`及以上版本 |

- 代码示例
  Android 侧的插件异步方法实现

```
@AsyncJsApi(methodName = "myAsyncFuncwithCallback")
fun testAsync(data: JSONObject?, callback: (data: Any) -> Unit) {
    android.util.Log.i(TAG, data.toString())

    callback("async testAsync")
}
```

如果要获取 activity：

```
@AsyncJsApi(methodName = "myAsyncFuncwithCallback")
fun testAsync(data: JSONObject?, callback: (data: Any) -> Unit, activity: Activity) {
    android.util.Log.i(TAG, data.toString())

    val componentName = activity.componentName.toString()
    android.util.Log.i(TAG, componentName)

    callback("async testAsync")
}
```

JS 侧的方法调用

```
wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        console.log('load plugin success')
        plugin.myAsyncFuncwithCallback({ a: 'hello', b: [1,2] }, (ret) => {
            console.log('myAsyncFuncwithCallback ret:', ret)
        })
    },
    fail: (e) => {
        console.log('load plugin fail', e)
    }
})
```

### [#](#插件事件监听) 插件事件监听

- 在 Native 侧通过调用继承于 NativePluginBase 的方法 `sendMiniPluginEvent` 可向 JS 侧发送事件。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | HashMap | 是 | 在 js 侧的监听方法获得的入参 |

1. `debugSaaAVersion` 要更新到 `1.0.2`及以上版本
2. 继承 `NativePluginBase`
3. 调用 `sendMiniPluginEvent`，入参类型是 `HashMap`

```
import com.tencent.luggage.wxa.SaaA.plugin.NativePluginBase

class TestNativePlugin: NativePluginBase(), NativePluginInterface {
    private val TAG = "TestNativePlugin"

    override fun getPluginID(): String {
        android.util.Log.e(TAG, "getPluginID")
        return BuildConfig.PLUGIN_ID
    }

    @AsyncJsApi(methodName = "myAsyncFuncwithCallback")
    fun testAsync(data: JSONObject?, callback: (data: Any) -> Unit) {
        android.util.Log.i(TAG, data.toString())

        // 有需要的时候向 js 发送消息
        val values1 = HashMap<String, Any>()
        values1["status"] = "testAsync start"
        this.sendMiniPluginEvent(values1)

        callback("async testAsync")

        // 有需要的时候向 js 发送消息
        val values2 = HashMap<String, Any>()
        values2["status"] = "testAsync end"
        this.sendMiniPluginEvent(values2)
    }
}
```

- 在 JS 侧可使用插件实例的 `onMiniPluginEvent` 方法注册监听

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | Native 侧向 JS 侧发送事件时触发的回调，支持注册多个回调 |

- 在 JS 侧可使用插件实例的 `offMiniPluginEvent` 取消监听。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 否 | 取消监听；当未指定需要取消的回调时，取消所有监听回调 |

JS 侧的方法调用

```
const listener1 = (param) => {
  console.log('onMiniPluginEvent listener1', param)
}

const listener2 = (param) => {
  console.log('onMiniPluginEvent listener2', param)
}

wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        plugin.onMiniPluginEvent(listener1)
        plugin.onMiniPluginEvent(listener2)
    }
})
```

### [#](#在主进程执行代码) 在主进程执行代码

> `debugSaaAVersion` 要更新到 `1.0.6`及以上版本

部分 sdk 要求必须在主进程初始化代码，封装了`NativePluginMainProcessTask`用于方便在主进程执行，详细参数见下面代码例子

1. 首先需要继承 NativePluginMainProcessTask

> 请注意，下面例子里的`valToSync1`和`valToSync2`只是用于跨进程传输的数据字段，如果不需要传输，可以直接删除

```
import com.tencent.luggage.wxa.SaaA.plugin.NativePluginMainProcessTask
import kotlinx.android.parcel.Parcelize

    @Parcelize
    class TestTask(private var valToSync1: String, private var valToSync2: String) :
        NativePluginMainProcessTask() {

        private var clientCallback: ((Any) -> Unit)? = null

        fun setClientCallback(callback: (data: Any) -> Unit) {
            this.clientCallback = callback
        }

        /**
         * 运行在主进程的逻辑，不建议在主进程进行耗时太长的操作
         */
        override fun runInMainProcess() {
            android.util.Log.e("MainProcess", "runInMainProcess, valToSync1:${valToSync1}, valToSync2:${valToSync2}")
            // 如果需要把主进程的数据回调到小程序进程，就赋值后调用 callback 函数
            valToSync1 = "runInMainProcess"
            this.callback() // callback函数会同步主进程的task数据，并在子进程调用runInClientProcess
        }

        /**
         * 运行在小程序进程的逻辑
         */
        override fun runInClientProcess() {
            android.util.Log.e("ClientProcess", "valToSync1: ${valToSync1}, valToSync2:${valToSync2}")
            this.clientCallback?.let { callback ->
                callback(valToSync1)
            }
        }

        override fun parseFromParcel(mainProcessData: Parcel?) {
            // 如果需要获得主进程数据，需要重写parseFromParcel，手动解析Parcel
            this.valToSync1 = mainProcessData?.readString() ?: ""
            this.valToSync2 = mainProcessData?.readString() ?: ""
        }

    }
```

2. 需要的时候真正执行runInMainProcess

```
@AsyncJsApi(methodName = "registerPush")
fun registerPush(data: JSONObject?, callback: (data: Any) -> Unit, activity: Activity) {
    val testTask = TestTask("test1", "test2")
    testTask.setClientCallback(callback)
    testTask.execAsync() // 真正执行runInMainProcess
}
```

### [#](#requestPermission) requestPermission

> `debugSaaAVersion` 要更新到 `1.0.6`及以上版本

为了减少在插件侧申请权限时的麻烦，包装了一个`requestPermission`方法

```
    @AsyncJsApi(methodName = "registerPush")
    fun registerPush(data: JSONObject?, callback: (data: Any) -> Unit, activity: Activity) {
        android.util.Log.i(TAG, data.toString())

        this.requestPermission(
                activity,
                arrayOf(Manifest.permission.POST_NOTIFICATIONS)
            ) { permissions, grantResults ->
                if (grantResults != null && grantResults.size > 0
                    && grantResults[0] == PackageManager.PERMISSION_GRANTED
                ) {
                    android.util.Log.i(TAG, "PERMISSION_GRANTED, do invoke again");
                    callback("PERMISSION_GRANTED")
                    
                } else {
                    android.util.Log.e(TAG, "reloadQRCode fail, SYS_PERM_DENIED");
                    callback("fail！")
                }

            }

    }
```

### [#](#startactivityForResult) startactivityForResult

新增封装`startactivityForResult`用于在小程序Activity启动另一个Activity并在完成特定操作后返回结果

> `debugSaaAVersion` 要更新到 `1.0.8`及以上版本

```
    @AsyncJsApi(methodName = "openActivity")
    fun openActivity(data: JSONObject?, callback: (data: Any) -> Unit, activity: Activity) {
        android.util.Log.i(TAG, "openActivity")

        // 封装后的startActivityForResult
        this.startActivityForResult(intent) { resultCode, intent ->
            android.util.Log.i(TAG, "resultCode ${resultCode}")

            if (resultCode == RESULT_OK) {
                val data: Intent? = intent
                // 在这里处理结果
                if (data != null) {
                    val resultString = data.getStringExtra("result_key")
                    android.util.Log.i(TAG,"Result: $resultString")

                    callback("openActivity ret: ${resultString}")
                } else {
                    callback("openActivity ret: no data")
                }
            } else {
                android.util.Log.e(TAG, "resultCode ${resultCode}")
                callback("openActivity ret: nothing")
            }
        }

    }
```

Incorrect translation.