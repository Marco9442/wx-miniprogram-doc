# [#](#any-requirePlugin-string-path) any requirePlugin(string path)

引入插件。返回插件通过 `main` 暴露的接口。参考 [使用插件 - js 接口](https://developers.weixin.qq.com/miniprogram/dev/framework/plugin/using#js-%E6%8E%A5%E5%8F%A3)

## [#](#参数) 参数

| 名称 | 类型 | 说明 |
| --- | --- | --- |
| module | string | 需要引入的插件的 alias。基础库 ['2.14.0'](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility) 起，也可以是插件的 AppID |

## [#](#示例代码) 示例代码

```
var myPluginInterface = requirePlugin('myPlugin');

myPluginInterface.hello();
var myWorld = myPluginInterface.world;
```

```
var myPluginInterface = requirePlugin('wxIDxxxxxxxxxx'); // 2.14.0 起
```

Incorrect translation.