[xr-frame](./../) / [Exports](./../modules.html) / IMeshShapeData

# [#](#Interface-IMeshShapeData) Interface: IMeshShapeData

**`see`** [MeshShape](./../classes/MeshShape.html)

## [#](#Hierarchy) Hierarchy

- [`IShapeData`](./IShapeData.html)

  ↳ **`IMeshShapeData`**

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [autoFit](./IMeshShapeData.html#autoFit)
- [center](./IMeshShapeData.html#center)
- [convex](./IMeshShapeData.html#convex)
- [disabled](./IMeshShapeData.html#disabled)

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

### [#](#convex) convex

• `Optional` **convex**: `boolean`

是否使用凸多边形来包围Mesh。
*如果元素有`shape-interact`属性，则会强制开启。*

**`default`** false

---

### [#](#disabled) disabled

• `Optional` **disabled**: `boolean`

是否禁用shape。

**`default`** false

#### [#](#Inherited-from-3) Inherited from

[IShapeData](./IShapeData.html).[disabled](./IShapeData.html#disabled)

Incorrect translation.