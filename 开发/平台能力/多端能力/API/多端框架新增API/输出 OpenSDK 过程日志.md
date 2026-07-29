# [#](#wx-miniapp-onOpensdkLog) wx.miniapp.onOpensdkLog

> 只支持 iOS

该能力可以输出使用[微信 Open SDK](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_Pay/Vendor_Service_Center) 过程的日志。

## [#](#JSAPI-代码例子) JSAPI 代码例子

```
    const opensdkLog = (e) => {
      console.log('onOpensdkLog', e)
    }
    // 注册
    wx.miniapp.onOpensdkLog(opensdkLog)
    // 取消注册
    wx.miniapp.offOpensdkLog(opensdkLog)
```

Incorrect translation.