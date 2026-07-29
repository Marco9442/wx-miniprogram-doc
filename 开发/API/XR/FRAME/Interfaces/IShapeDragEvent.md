[xr-frame](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/) / [Exports](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/modules.html) / IShapeDragEvent
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Interface-IShapeDragEvent) Interface: IShapeDragEvent
`drag-shape`事件的回调参数。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Hierarchy) Hierarchy
- [`IShapeTouchEvent`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html)
↳ \*\*`IShapeDragEvent`\*\*
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Table-of-contents) Table of contents
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Properties) Properties
- [camera](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#camera)
- [deltaX](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#deltaX)
- [deltaY](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#deltaY)
- [dir](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#dir)
- [force](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#force)
- [origin](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#origin)
- [shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#shape)
- [target](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#target)
- [x](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#x)
- [y](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#y)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Properties-2) Properties
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#camera) camera
• \*\*camera\*\*: [`Camera`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Camera.html)
渲染\\*被选中的 [轮廓](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html)\\*的相机。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [camera](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#camera)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#deltaX) deltaX
• \*\*deltaX\*\*: `number`
点击位置在二维canvas中的x坐标的变化量。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#deltaY) deltaY
• \*\*deltaY\*\*: `number`
点击位置在二维canvas中的y坐标的变化量。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#dir) dir
• \*\*dir\*\*: \[`number`, `number`, `number`\]
从 [camera](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#camera) 投射出的射线的单位向量。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-2) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [dir](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#dir)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#force) force
• \*\*force\*\*: `number`
\*\*`unimplemented`\*\*
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-3) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [force](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#force)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#origin) origin
• \*\*origin\*\*: \[`number`, `number`, `number`\]
[camera](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html#camera) 在三维场景中的位置。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-4) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [origin](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#origin)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#shape) shape
• \*\*shape\*\*: [`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) <`any`>
被选中的 [轮廓](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html)。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-5) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#shape)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#target) target
• \*\*target\*\*: [`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html)
\\*被选中的 [轮廓](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html)\\*所在的元素。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-6) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [target](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#target)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#x) x
• \*\*x\*\*: `number`
点击位置在二维canvas中的x坐标。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-7) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [x](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#x)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#y) y
• \*\*y\*\*: `number`
点击位置在二维canvas中的y坐标。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeDragEvent.html\#Inherited-from-8) Inherited from
[IShapeTouchEvent](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html). [y](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeTouchEvent.html#y)