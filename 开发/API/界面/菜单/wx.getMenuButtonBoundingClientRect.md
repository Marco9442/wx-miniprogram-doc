界面/菜单/wx.getMenuButtonBoundingClientRect/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html\#Object-wx-getMenuButtonBoundingClientRect) Object wx.getMenuButtonBoundingClientRect()
> 基础库 2.1.0 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：支持，需要小程序基础库版本不低于 [2.15.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)
>
> \*\*微信 Windows 版\*\*：支持
>
> \*\*微信 Mac 版\*\*：支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
获取菜单按钮（右上角胶囊按钮）的布局位置信息。坐标信息以屏幕左上角为原点。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html\#Object) Object
菜单按钮的布局位置信息
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度，单位：px |
| height | number | 高度，单位：px |
| top | number | 上边界坐标，单位：px |
| right | number | 右边界坐标，单位：px |
| bottom | number | 下边界坐标，单位：px |
| left | number | 左边界坐标，单位：px |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const res = wx.getMenuButtonBoundingClientRect()
console.log(res.width)
console.log(res.height)
console.log(res.top)
console.log(res.right)
console.log(res.bottom)
console.log(res.left)
```