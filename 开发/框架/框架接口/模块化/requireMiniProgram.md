# [#](#any-requireMiniProgram) any requireMiniProgram()

> 基础库 '2.11.1' 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility)。

插件引入当前使用者小程序。返回使用者小程序通过插件配置中 `export` 暴露的接口。参考 [使用插件 - 导出到插件](https://developers.weixin.qq.com/miniprogram/dev/framework/plugin/using#%E5%AF%BC%E5%87%BA%E5%88%B0%E6%8F%92%E4%BB%B6)

**该接口仅在插件中存在。**

## [#](#参数) 参数

> 该接口不需要参数

## [#](#示例代码) 示例代码

```
// in plugin
var mp = requireMiniProgram()
console.log(mp.whoami)  // 'Wechat MiniProgram'
```

Incorrect translation.