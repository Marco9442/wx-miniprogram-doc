AI/视觉算法/VKSession/VKSession.addOSDMarker/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#number-VKSession-addOSDMarker-string-path) number VKSession.addOSDMarker(string path)
> 基础库 2.24.5 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：支持，需要小程序基础库版本不低于 [2.24.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
添加一个 OSD marker（one-shot detection marker），要求调 [wx.createVKSession](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/wx.createVKSession.html) 时传入的 track.OSD 为 true
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#string-path) string path
图片路径，目前只支持本地用户图片
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#number) number
marker id
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKSession.addOSDMarker.html\#%E4%BD%BF%E7%94%A8%E6%8F%90%E7%A4%BA) 使用提示
注意事项：
1. 使用 addOSDMarker 接口之前，需要在 createVKSession 的时候声明开启 OSD 跟踪。即 wx.createVKSession({ track: { OSD: true } })
2. 可以添加多个 OSDMarker 图片，但不能重复添加相同的 OSDMarker 图片。
对传入的图片有如下要求：
1. 格式：jpg 格式彩色图片
2. 分辨率：尺寸不低于 240x240
3. 宽高比：在 1:1 ~ 16:9 之间，要求尽量方正，避免狭长的图片
4. 质量：目标物体需要占画面主体，避免大面积留白，避免大面积文字，不能含其他物体。
示例：
![image.png](https://res.wx.qq.com/op\_res/rg0BkiSl-LPBybgJtcQCq\_Mq0ReXEA5nOzDIvnYYPttmwxn0V1e\_yI6UUgkNT6K6aOQj2QRba5IHQglHULkrKg)
![image.png](https://res.wx.qq.com/op\_res/rg0BkiSl-LPBybgJtcQCqwiRcyGk9oenkCpd3vAHWSTSZPPJcgIrPzcpwnSpmk\_9bMiCqUdS8Ds789Rjhy0CtA)
![image.png](https://res.wx.qq.com/op\_res/rg0BkiSl-LPBybgJtcQCqx8fYUYypBmFmB1\_zX-APH06j1oMZDz7K0CE2To\_982NDOB5fmM4Y2Rrr1uQF6J4gg)
建议：
1. 具有丰富的细节，避免纯色且形状特点不鲜明的物体，例如：
![image.png](https://res.wx.qq.com/op\_res/rg0BkiSl-LPBybgJtcQCq-6WwSZKlNbN-if0NCag-Dm6AmNJeBFi5dvR-bRZINlZmuA9G1e4wpngvhlr2z6CXQ)
2. 避免模糊，最好采用高清图片