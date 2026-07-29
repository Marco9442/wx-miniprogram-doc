# [#](#wx-offCopyUrl) wx.offCopyUrl()

> 基础库 2.14.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

移除用户点击右上角菜单的「复制链接」按钮时触发的事件的全部监听函数

## [#](#示例代码) 示例代码

```
  // 绑定分享参数
  wx.onCopyUrl(() => {
    return { query: 'a=1&b=2' }
  })

  // 取消绑定分享参数
  wx.offCopyUrl()
```

Incorrect translation.