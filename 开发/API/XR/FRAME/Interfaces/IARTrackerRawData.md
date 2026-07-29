[xr-frame](./../) / [Exports](./../modules.html) / IARTrackerRawData

# [#](#Interface-IARTrackerRawData) Interface: IARTrackerRawData

`Face`/`Body`/`Hand`模式下，[ARTracker](./../classes/ARTracker.html)存储的原始数据类型。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [angle](./IARTrackerRawData.html#angle)
- [confidence](./IARTrackerRawData.html#confidence)
- [gesture](./IARTrackerRawData.html#gesture)
- [origin](./IARTrackerRawData.html#origin)
- [points](./IARTrackerRawData.html#points)
- [points3d](./IARTrackerRawData.html#points3d)
- [score](./IARTrackerRawData.html#score)
- [size](./IARTrackerRawData.html#size)

## [#](#Properties-2) Properties

### [#](#angle) angle

• `Optional` **angle**: `Object`

在`Face`模式下，人脸旋转角度。

#### [#](#Type-declaration) Type declaration

| Name | Type |
| --- | --- |
| `pitch` | `number` |
| `roll` | `number` |
| `yaw` | `number` |
| `z_score` | `number` |

---

### [#](#confidence) confidence

• **confidence**: `number`[]

关键点置信度。

---

### [#](#gesture) gesture

• `Optional` **gesture**: `number`

在`Hand`模式下，手势分类，正常`0~18`，无效为`-1`。

---

### [#](#origin) origin

• **origin**: `Object`

原点，屏幕空间。

#### [#](#Type-declaration-2) Type declaration

| Name | Type |
| --- | --- |
| `x` | `number` |
| `y` | `number` |

---

### [#](#points) points

• **points**: { `x`: `number` ; `y`: `number` }[]

关键点，屏幕空间。

---

### [#](#points3d) points3d

• **points3d**: { `x`: `number` ; `y`: `number` ; `z`: `number` }[]

支持3D时，3D关键点，世界空间。

---

### [#](#score) score

• **score**: `number`

置信度。

---

### [#](#size) size

• **size**: `Object`

尺寸，屏幕空间。

#### [#](#Type-declaration-3) Type declaration

| Name | Type |
| --- | --- |
| `height` | `number` |
| `width` | `number` |

Incorrect translation.