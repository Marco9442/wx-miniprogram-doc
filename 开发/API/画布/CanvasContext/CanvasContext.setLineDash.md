# [#](#CanvasContext-setLineDash-Array-number-pattern-number-offset) CanvasContext.setLineDash(Array.<number> pattern, number offset)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [1.9.90](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [CanvasContext.lineDashOffset](CanvasContext.html) 代替

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

设置虚线样式。

## [#](#参数) 参数

### [#](#Array-number-pattern) Array.<number> pattern

一组描述交替绘制线段和间距（坐标空间单位）长度的数字

### [#](#number-offset) number offset

虚线偏移量

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')

ctx.setLineDash([10, 20], 5);

ctx.beginPath();
ctx.moveTo(0,100);
ctx.lineTo(400, 100);
ctx.stroke();

ctx.draw()
```

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUcAAACoCAYAAABzLCyIAAAC/ElEQVR4nO3YMWrbYACGYdl41imag5Ts7dI1kFwj4BpnyDVa6Nql3UMP4pzCF3CjsfTNECw7CTzPKIO+3x5eLC0OTwYA/rF87QMAvEXiCBDEESCII0BY1cWHhz/Dt+8/hv1+f+7zALzIOI7DzfXVcHn5cdb7ZhynMG6+3g4XFx9mHQOY2273OGzv7mePYz5WT/8YhRF4D6ZWneIp1ztHgCCOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQBBHgCCOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQBBHgCCOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQBBHgCCOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQBBHgLB67oPtdvvftc1mM+t4bRS7du0et7tcLof1en323clr/c7HejaOh8Ph5OPn2LBr1+5pzvaWv+8cFodY+vT5y/D718+zHADgWKdolneOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQBBHgCCOAEEcAYI4AgRxBAjiCBDEESCII0AQR4AgjgBBHAGCOAIEcQQI4ggQxBEgiCNAEEeAII4AQRwBgjgCBHEECOIIEMQRIIgjQMg4juM47HaP5z4LwItNrZqaNbdVXby5vhq2d/fDfr+ffRBgTlMYp2bNbXF4MvtdAd457xwBgjgCBHEECOIIEMQRIIgjQBBHgCCOAEEcAYI4AoS/9Pt7GTb0EWgAAAAASUVORK5CYII=)

Incorrect translation.