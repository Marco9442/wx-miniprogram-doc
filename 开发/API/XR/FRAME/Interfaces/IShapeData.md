[xr-frame](./../) / [Exports](./../modules.html) / IShapeData

# [#](#Interface-IShapeData) Interface: IShapeData

## [#](#Hierarchy) Hierarchy

- **`IShapeData`**

  ↳ [`ISphereShapeData`](./ISphereShapeData.html)

  ↳ [`IMeshShapeData`](./IMeshShapeData.html)

  ↳ [`ICapsuleShapeData`](./ICapsuleShapeData.html)

  ↳ [`ICubeShapeData`](./ICubeShapeData.html)

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [autoFit](./IShapeData.html#autoFit)
- [center](./IShapeData.html#center)
- [disabled](./IShapeData.html#disabled)

## [#](#Properties-2) Properties

### [#](#autoFit) autoFit

• `Optional` **autoFit**: `boolean`

轮廓是否自动贴合[Mesh组件](./../classes/Mesh.html)或[GLTF组件](./../classes/GLTF.html)的大小。
如果当前元素下不存在Mesh组件和GLTF组件则不生效。

> [MeshShape](./../classes/MeshShape.html)永远会开启这项。

**`default`** false

---

### [#](#center) center

• `Optional` **center**: [`number`, `number`, `number`]

轮廓中心相对元素[Transform](./../classes/Transform.html)中心的偏移量。

**`default`** [0, 0, 0]

---

### [#](#disabled) disabled

• `Optional` **disabled**: `boolean`

是否禁用shape。

**`default`** false

Incorrect translation.