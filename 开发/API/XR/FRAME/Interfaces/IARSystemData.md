[xr-frame](./../) / [Exports](./../modules.html) / IARSystemData

# [#](#Interface-IARSystemData) Interface: IARSystemData

`ARSystem`系统数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [camera](./IARSystemData.html#camera)
- [depthDebug](./IARSystemData.html#depthDebug)
- [depthFar](./IARSystemData.html#depthFar)
- [depthMask](./IARSystemData.html#depthMask)
- [depthNear](./IARSystemData.html#depthNear)
- [modes](./IARSystemData.html#modes)
- [planeMode](./IARSystemData.html#planeMode)
- [pose3d](./IARSystemData.html#pose3d)

## [#](#Properties-2) Properties

### [#](#camera) camera

• `Optional` **camera**: `"Front"` | `"Back"`

使用前置还是后置相机，默认后置`Back`。

---

### [#](#depthDebug) depthDebug

• `Optional` **depthDebug**: `boolean`

开启实时深度遮挡时，显示一个用于Debug的图层。
**目前暂时不可用！**

---

### [#](#depthFar) depthFar

• `Optional` **depthFar**: `number`

开启实时深度遮挡时，遮挡的远处阈值。
值是空间实际尺度（m），默认为`20`。

---

### [#](#depthMask) depthMask

• `Optional` **depthMask**: `boolean`

在支持的情况下，是否开启实时深度遮挡。
**目前暂时不可用！**

---

### [#](#depthNear) depthNear

• `Optional` **depthNear**: `number`

开启实时深度遮挡时，遮挡的近处阈值。
值是空间实际尺度（m），默认为`0.02`。

---

### [#](#modes) modes

• **modes**: [`TTrackMode`](./../modules.html#TTrackMode)[]

系统支持的追踪模式，目前仅支持一个！
`xml`中数据类型为`array`，默认值为`Plane`。

---

### [#](#planeMode) planeMode

• `Optional` **planeMode**: `number`

在`v2`平面模式下，平面检测模式。
`1`为水平面，`2`为垂直平面，`3`为两个都支持。
默认为`3`。

---

### [#](#pose3d) pose3d

• `Optional` **pose3d**: `boolean`

在`Face`/`Body`/`Hand`模式下，使用原生的AI3D推理估计。
默认为`false`。
**目前暂时不可用！**

Incorrect translation.