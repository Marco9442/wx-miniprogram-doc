# [#](#wx-miniapp-getMetaData) wx.miniapp.getMetaData

> Android >= 1.3.23

获取 meta-data 的值；设置 meta-data 的方法可以查看[Android 设置 meta-data](../../handbook/devtools/meta-data)

### [#](#返回参数) 返回参数

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| 开发者在 project.miniapp.json 自定义的 name（app\_channel） | string | meta-data 的值 |
| errMsg | string | 错误提示 |

#### [#](#示例说明) 示例说明

```
wx.miniapp.getMetaData({
  success (res) {
    console.log('getMetaData success', res)
  }
})
```

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202407111148907.png)

Incorrect translation.