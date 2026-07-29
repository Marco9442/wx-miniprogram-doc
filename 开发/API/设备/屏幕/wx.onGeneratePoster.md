# [#](#wx-onGeneratePoster-function-listener) wx.onGeneratePoster(function listener)

> 基础库 3.12.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

监听用户截屏之后需要开发者生成自定义海报事件，在点击转发截图按钮时触发。只能注册一个监听函数，重复调用会覆盖上一个监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

用户截屏之后需要开发者生成自定义海报事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| src | string | 开发者生成自定义海报图片的路径，支持网络路径、本地路径 |
| promise | Object | 如果该参数存在，则其它的参数将会以 resolve 结果为准，如果3秒内不 resolve，会使用上面传入的默认参数 |

## [#](#示例代码) 示例代码

```
wx.onGeneratePoster(function () {
  console.log('需要开发者生成自定义海报')
  return {
    src: 'images/a.jpg',
    promise: new Promise((resolve) => { // 通过promise延时传递小程序的query参数
      setTimeout(() => {
        resolve({
          src: 'images/a.jpg',
        })
      }, 1000) // 在1秒内对query进行解析
    })
  }
})
```

Incorrect translation.