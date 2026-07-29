# [#](#wx-miniapp-openSaaAActionSheet) wx.miniapp.openSaaAActionSheet

> iOS >= 1.0.3，Android >= 1.0.1

打开 SDK 操作菜单栏。

#### [#](#SDK-菜单栏功能) SDK 菜单栏功能

- [日志上传](../../handbook/build/upload-log)

#### [#](#参数) 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 是 | 获取后成功回调 |

#### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.openSaaAActionSheet({
    success: (res) => {
        console.log('openSaaAActionSheet success:', res)
    }
})
```

Incorrect translation.