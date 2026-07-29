[xr-frame](./../) / [Exports](./../modules.html) / ICapsuleShapeData

# [#](#Interface-ICapsuleShapeData) Interface: ICapsuleShapeData

**`see`** [CapsuleShape](./../classes/CapsuleShape.html)

## [#](#Hierarchy) Hierarchy

- [`IShapeData`](./IShapeData.html)

  ↳ **`ICapsuleShapeData`**

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [autoFit](./ICapsuleShapeData.html#autoFit)
- [center](./ICapsuleShapeData.html#center)
- [direction](./ICapsuleShapeData.html#direction)
- [disabled](./ICapsuleShapeData.html#disabled)
- [height](./ICapsuleShapeData.html#height)
- [radius](./ICapsuleShapeData.html#radius)

## [#](#Properties-2) Properties

### [#](#autoFit) autoFit

• `Optional` **autoFit**: `boolean`

轮廓是否自动贴合[Mesh组件](./../classes/Mesh.html)或[GLTF组件](./../classes/GLTF.html)的大小。
如果当前元素下不存在Mesh组件和GLTF组件则不生效。

> [MeshShape](./../classes/MeshShape.html)永远会开启这项。

**`default`** false

#### [#](#Inherited-from) Inherited from

[IShapeData](./IShapeData.html).[autoFit](./IShapeData.html#autoFit)

---

### [#](#center) center

• `Optional` **center**: [`number`, `number`, `number`]

轮廓中心相对元素[Transform](./../classes/Transform.html)中心的偏移量。

**`default`** [0, 0, 0]

#### [#](#Inherited-from-2) Inherited from

[IShapeData](./IShapeData.html).[center](./IShapeData.html#center)

---

### [#](#direction) direction

• `Optional` **direction**: [`ECapsuleShapeDirection`](./../enums/ECapsuleShapeDirection.html)

胶囊体的朝向。

**`default`** ECapsuleShapeDirection["Y-Axis"]

---

### [#](#disabled) disabled

• `Optional` **disabled**: `boolean`

是否禁用shape。

**`default`** false

#### [#](#Inherited-from-3) Inherited from

[IShapeData](./IShapeData.html).[disabled](./IShapeData.html#disabled)

---

### [#](#height) height

• `Optional` **height**: `number`

胶囊体的长度。

**`default`** 2

---

### [#](#radius) radius

• `Optional` **radius**: `number`

胶囊体两端球体的半径。

**`default`** 0.5

Incorrect translation.