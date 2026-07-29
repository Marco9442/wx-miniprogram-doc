# [#](#Animation) Animation

> 相关文档: [动画](../../../framework/view/animation.html)

动画对象

## [#](#方法) 方法

### [#](#Object-Animation-export) [Object Animation.export()](Animation.export.html)

导出动画队列。**export 方法每次调用后会清掉之前的动画操作。**

### [#](#Animation-Animation-step-Object-object) [Animation Animation.step(Object object)](Animation.step.html)

表示一组动画完成。可以在一组动画中调用任意多个动画方法，一组动画中的所有动画会同时开始，一组动画完成后才会进行下一组动画。

### [#](#Animation-Animation-matrix) [Animation Animation.matrix()](Animation.matrix.html)

同 [transform-function matrix](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/matrix)

### [#](#Animation-Animation-matrix3d) [Animation Animation.matrix3d()](Animation.matrix3d.html)

同 [transform-function matrix3d](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/matrix3d)

### [#](#Animation-Animation-rotate-number-angle) [Animation Animation.rotate(number angle)](Animation.rotate.html)

从原点顺时针旋转一个角度

### [#](#Animation-Animation-rotate3d-number-x-number-y-number-z-number-angle) [Animation Animation.rotate3d(number x, number y, number z, number angle)](Animation.rotate3d.html)

从 固定 轴顺时针旋转一个角度

### [#](#Animation-Animation-rotateX-number-angle) [Animation Animation.rotateX(number angle)](Animation.rotateX.html)

从 X 轴顺时针旋转一个角度

### [#](#Animation-Animation-rotateY-number-angle) [Animation Animation.rotateY(number angle)](Animation.rotateY.html)

从 Y 轴顺时针旋转一个角度

### [#](#Animation-Animation-rotateZ-number-angle) [Animation Animation.rotateZ(number angle)](Animation.rotateZ.html)

从 Z 轴顺时针旋转一个角度

### [#](#Animation-Animation-scale-number-sx-number-sy) [Animation Animation.scale(number sx, number sy)](Animation.scale.html)

缩放

### [#](#Animation-Animation-scale3d-number-sx-number-sy-number-sz) [Animation Animation.scale3d(number sx, number sy, number sz)](Animation.scale3d.html)

缩放

### [#](#Animation-Animation-scaleX-number-scale) [Animation Animation.scaleX(number scale)](Animation.scaleX.html)

缩放 X 轴

### [#](#Animation-Animation-scaleY-number-scale) [Animation Animation.scaleY(number scale)](Animation.scaleY.html)

缩放 Y 轴

### [#](#Animation-Animation-scaleZ-number-scale) [Animation Animation.scaleZ(number scale)](Animation.scaleZ.html)

缩放 Z 轴

### [#](#Animation-Animation-skew-number-ax-number-ay) [Animation Animation.skew(number ax, number ay)](Animation.skew.html)

对 X、Y 轴坐标进行倾斜

### [#](#Animation-Animation-skewX-number-angle) [Animation Animation.skewX(number angle)](Animation.skewX.html)

对 X 轴坐标进行倾斜

### [#](#Animation-Animation-skewY-number-angle) [Animation Animation.skewY(number angle)](Animation.skewY.html)

对 Y 轴坐标进行倾斜

### [#](#Animation-Animation-translate-number-tx-number-ty) [Animation Animation.translate(number tx, number ty)](Animation.translate.html)

平移变换

### [#](#Animation-Animation-translate3d-number-tx-number-ty-number-tz) [Animation Animation.translate3d(number tx, number ty, number tz)](Animation.translate3d.html)

对 xyz 坐标进行平移变换

### [#](#Animation-Animation-translateX-number-translation) [Animation Animation.translateX(number translation)](Animation.translateX.html)

对 X 轴平移

### [#](#Animation-Animation-translateY-number-translation) [Animation Animation.translateY(number translation)](Animation.translateY.html)

对 Y 轴平移

### [#](#Animation-Animation-translateZ-number-translation) [Animation Animation.translateZ(number translation)](Animation.translateZ.html)

对 Z 轴平移

### [#](#Animation-Animation-opacity-number-value) [Animation Animation.opacity(number value)](Animation.opacity.html)

设置透明度

### [#](#Animation-Animation-backgroundColor-string-value) [Animation Animation.backgroundColor(string value)](Animation.backgroundColor.html)

设置背景色

### [#](#Animation-Animation-width-number-string-value) [Animation Animation.width(number|string value)](Animation.width.html)

设置宽度

### [#](#Animation-Animation-height-number-string-value) [Animation Animation.height(number|string value)](Animation.height.html)

设置高度

### [#](#Animation-Animation-left-number-string-value) [Animation Animation.left(number|string value)](Animation.left.html)

设置 left 值

### [#](#Animation-Animation-right-number-string-value) [Animation Animation.right(number|string value)](Animation.right.html)

设置 right 值

### [#](#Animation-Animation-top-number-string-value) [Animation Animation.top(number|string value)](Animation.top.html)

设置 top 值

### [#](#Animation-Animation-bottom-number-string-value) [Animation Animation.bottom(number|string value)](Animation.bottom.html)

设置 bottom 值

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/Swab8kmW7v2V "在开发者工具中预览效果")

```
<view animation="{{animationData}}" style="background:red;height:100rpx;width:100rpx"></view>
```

```
Page({
  data: {
    animationData: {}
  },
  onShow: function(){
    var animation = wx.createAnimation({
      duration: 1000,
      timingFunction: 'ease',
    })

    this.animation = animation

    animation.scale(2,2).rotate(45).step()

    this.setData({
      animationData:animation.export()
    })

    setTimeout(function() {
      animation.translate(30).step()
      this.setData({
        animationData:animation.export()
      })
    }.bind(this), 1000)
  },
  rotateAndScale: function () {
    // 旋转同时放大
    this.animation.rotate(45).scale(2, 2).step()
    this.setData({
      animationData: this.animation.export()
    })
  },
  rotateThenScale: function () {
    // 先旋转后放大
    this.animation.rotate(45).step()
    this.animation.scale(2, 2).step()
    this.setData({
      animationData: this.animation.export()
    })
  },
  rotateAndScaleThenTranslate: function () {
    // 先旋转同时放大，然后平移
    this.animation.rotate(45).scale(2, 2).step()
    this.animation.translate(100, 100).step({ duration: 1000 })
    this.setData({
      animationData: this.animation.export()
    })
  }
})
```

Incorrect translation.