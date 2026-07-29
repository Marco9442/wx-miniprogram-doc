# [#](#worklet-Easing) worklet.Easing

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

Easing 模块实现了常见的动画缓动函数（动画效果参考 https://easings.net/ ），可从 [wx.worklet](../wx.worklet.html) 对象中读取。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/f94TCOmg7JFH "在开发者工具中预览效果")

### [#](#预置动画函数) 预置动画函数

- [Easing.bounce](#Easing.bounce) 反弹动画
- [Easing.ease](#Easing.ease) 惯性动画
- [Easing.elastic](#Easing.elastic) 弹性动画

### [#](#标准缓动函数) 标准缓动函数

- [Easing.linear](#Easing.linear) 线性
- [Easing.quad](#Easing.quad) 二次方
- [Easing.cubic](#Easing.cubic) 三次方
- [Easing.poly](#Easing.poly) 实现其它幂函数

### [#](#其它数学函数) 其它数学函数

- [Easing.bezier](#Easing.bezier) 三次贝塞尔曲线
- [Easing.circle](#Easing.circle) 圆形曲线
- [Easing.sin](#Easing.sin) 正弦函数
- [Easing.exp](#Easing.exp) 指数函数

### [#](#缓动方式) 缓动方式

以上效果均有三种缓动方式

- [Easing.in](#in) 正向执行缓动函数
- [Easing.out](#out) 反向执行缓动函数
- [Easing.inOut](#inout) 前半程正向，后半程反向
  以 `sin` 函数为例，其中 `Easing.in(Easing.sin)` 和直接使用 `Easing.sin` 效果相同。

1. `Easing.in(Easing.sin)` 动画效果参考 https://easings.net/#easeInSine
2. `Easing.out(Easing.sin)` 动画效果参考 https://easings.net/#easeOutSine
3. `Easing.inOut(Easing.sin)` 动画效果参考 https://easings.net/#easeInOutSine

### [#](#Easing-bounce) Easing.bounce

简单的反弹效果，[动画效果参考](https://easings.net/#easeInBounce)

```
Easing.bounce(t)
```

### [#](#Easing-ease) Easing.ease

简单的惯性动画，[动画效果参考](https://cubic-bezier.com/#.42,0,1,1)

```
Easing.ease(t)
```

### [#](#Easing-elastic) Easing.elastic

简单的弹性动画，类似弹簧来回摆动，高阶函数。默认弹性为 1，会稍微超出一次。弹性为 0 时 不会过冲。[动画效果参考](https://easings.net/#easeInElastic)

```
Easing.elastic(bounciness = 1)
```

### [#](#Easing-linear) Easing.linear

线性函数，f(t) = t，[动画效果参考](https://cubic-bezier.com/#0,0,1,1)

```
Easing.linear(t)
```

### [#](#Easing-quad) Easing.quad

二次方函数，f(t) = t \* t，[动画效果参考](https://easings.net/#easeInQuad)

```
Easing.quad(t)
```

### [#](#Easing-cubic) Easing.cubic

立方函数，f(t) = t \* t \* t，[动画效果参考](https://easings.net/#easeInCubic)

```
Easing.cubic(t)
```

### [#](#Easing-poly) Easing.poly

高阶函数，返回幂函数

poly(4): [动画效果参考](https://easings.net/#easeInQuart)

poly(5): [动画效果参考](https://easings.net/#easeInQuint)

```
Easing.poly(n)
```

### [#](#Easing-bezier) Easing.bezier

三次贝塞尔曲线，效果同 css `transition-timing-function`

调试参数可借助 [可视化工具](https://cubic-bezier.com/)

```
Easing.bezier(x1, y1, x2, y2)
```

### [#](#Easing-circle) Easing.circle

圆形曲线，[动画效果参考](https://easings.net/#easeInCirc)

```
Easing.circle(t)
```

### [#](#Easing-sin) Easing.sin

正弦函数，[动画效果参考](https://easings.net/#easeInSine)

```
Easing.sin(t)
```

### [#](#Easing-exp) Easing.exp

指数函数，[动画效果参考](https://easings.net/#easeInExpo)

```
Easing.exp(t)
```

### [#](#Easing-in) Easing.in

正向运行 `easing function`，高阶函数。

```
Easing.in(easing)
```

### [#](#Easing-out) Easing.out

反向运行 `easing function`，高阶函数。

```
Easing.out(easing)
```

### [#](#Easing-inOut) Easing.inOut

前半程正向，后半程反向，高阶函数。

```
Easing.inOut(easing)
```

Incorrect translation.