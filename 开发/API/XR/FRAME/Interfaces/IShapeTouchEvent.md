[xr-frame](./../) / [Exports](./../modules.html) / IShapeTouchEvent

# [#](#Interface-IShapeTouchEvent) Interface: IShapeTouchEvent

`touch-shape`和`untouch-shape`事件的回调参数。

## [#](#Hierarchy) Hierarchy

- **`IShapeTouchEvent`**

  ↳ [`IShapeDragEvent`](./IShapeDragEvent.html)

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [camera](./IShapeTouchEvent.html#camera)
- [dir](./IShapeTouchEvent.html#dir)
- [force](./IShapeTouchEvent.html#force)
- [origin](./IShapeTouchEvent.html#origin)
- [shape](./IShapeTouchEvent.html#shape)
- [target](./IShapeTouchEvent.html#target)
- [x](./IShapeTouchEvent.html#x)
- [y](./IShapeTouchEvent.html#y)

## [#](#Properties-2) Properties

### [#](#camera) camera

• **camera**: [`Camera`](./../classes/Camera.html)

渲染\*被选中的[轮廓](./../classes/Shape.html)\*的相机。

---

### [#](#dir) dir

• **dir**: [`number`, `number`, `number`]

从[camera](./IShapeTouchEvent.html#camera)投射出的射线的单位向量。

---

### [#](#force) force

• **force**: `number`

**`unimplemented`**

---

### [#](#origin) origin

• **origin**: [`number`, `number`, `number`]

[camera](./IShapeTouchEvent.html#camera)在三维场景中的位置。

---

### [#](#shape) shape

• **shape**: [`Shape`](./../classes/Shape.html)<`any`>

被选中的[轮廓](./../classes/Shape.html)。

---

### [#](#target) target

• **target**: [`Element`](./../classes/Element.html)

\*被选中的[轮廓](./../classes/Shape.html)\*所在的元素。

---

### [#](#x) x

• **x**: `number`

点击位置在二维canvas中的x坐标。

---

### [#](#y) y

• **y**: `number`

点击位置在二维canvas中的y坐标。

Incorrect translation.