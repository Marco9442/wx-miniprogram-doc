[xr-frame](./../) / [Exports](./../modules.html) / ICameraData

# [#](#Interface-ICameraData) Interface: ICameraData

[Camera](./../classes/Camera.html)组件数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [allowFeatures](./ICameraData.html#allowFeatures)
- [background](./ICameraData.html#background)
- [clearColor](./ICameraData.html#clearColor)
- [clearDepth](./ICameraData.html#clearDepth)
- [clearStencil](./ICameraData.html#clearStencil)
- [cullMask](./ICameraData.html#cullMask)
- [depth](./ICameraData.html#depth)
- [far](./ICameraData.html#far)
- [fov](./ICameraData.html#fov)
- [isARCamera](./ICameraData.html#isARCamera)
- [isClearColor](./ICameraData.html#isClearColor)
- [isClearDepth](./ICameraData.html#isClearDepth)
- [isClearStencil](./ICameraData.html#isClearStencil)
- [isPerspective](./ICameraData.html#isPerspective)
- [near](./ICameraData.html#near)
- [orthSize](./ICameraData.html#orthSize)
- [postProcess](./ICameraData.html#postProcess)
- [renderTarget](./ICameraData.html#renderTarget)
- [target](./ICameraData.html#target)

## [#](#Properties-2) Properties

### [#](#allowFeatures) allowFeatures

• **allowFeatures**: `string`[]

允许的渲染标记，配合[RenderSystem](./../classes/RenderSystem.html)的`changeFeatures`一起使用。
`xml`中的数据类型为`array`，默认为空。

---

### [#](#background) background

• **background**: [`TCameraBackground`](./../modules.html#TCameraBackground)

背景清屏模式。
`xml`中的数据类型为`string`，默认为`default`。

---

### [#](#clearColor) clearColor

• **clearColor**: `number`[]

清屏颜色。
`xml`中的数据类型为`color`，默认为`0 0 0 1`。

---

### [#](#clearDepth) clearDepth

• **clearDepth**: `number`

清屏深度。
`xml`中的数据类型为`number`，默认为`1`。

---

### [#](#clearStencil) clearStencil

• **clearStencil**: `number`

清屏模板值。
`xml`中的数据类型为`number`，默认为`0`。

---

### [#](#cullMask) cullMask

• **cullMask**: `number`

掩码，一般和[Transform.layer](./../classes/Transform.html#layer)一起使用，决定那些节点要被渲染。
`xml`中的数据类型为`number`。

---

### [#](#depth) depth

• **depth**: `number`

深度，决定在多相机时的渲染顺序。
`xml`中的数据类型为`number`。

---

### [#](#far) far

• **far**: `number`

远平面。
`xml`中的数据类型为`number`，默认为`100`。

---

### [#](#fov) fov

• **fov**: `number`

视场角。
`xml`中的数据类型为`number`，默认为`60`。

---

### [#](#isARCamera) isARCamera

• **isARCamera**: `boolean`

是否为AR相机，配合[ARSystem](./../classes/ARSystem.html)使用。
`xml`中的数据类型为`boolean`，默认为`false`。
**非常需要注意当设置为`true`时不能同时设置`target`数据！**

---

### [#](#isClearColor) isClearColor

• **isClearColor**: `boolean`

清屏是否要清颜色。
`xml`中的数据类型为`boolean`，默认为`true`。

---

### [#](#isClearDepth) isClearDepth

• **isClearDepth**: `boolean`

清屏是否要清深度。
`xml`中的数据类型为`boolean`，默认为`true`。

---

### [#](#isClearStencil) isClearStencil

• **isClearStencil**: `boolean`

清屏是否要清模板值。
`xml`中的数据类型为`boolean`，默认为`true`。

---

### [#](#isPerspective) isPerspective

• **isPerspective**: `boolean`

是否为透视相机。
`xml`中的数据类型为`boolean`，默认为`true`。

---

### [#](#near) near

• **near**: `number`

近平面。
`xml`中的数据类型为`number`，默认为`0.1`。

---

### [#](#orthSize) orthSize

• **orthSize**: `number`

非透视模式，即正交模式时，可视范围大小。
`xml`中的数据类型为`number`，默认为`4`。

---

### [#](#postProcess) postProcess

• **postProcess**: `string`[]

后处理，一个后处理资源id的数组。
`xml`中的数据类型为`array`，默认为空。

---

### [#](#renderTarget) renderTarget

• `Optional` **renderTarget**: [`RenderTexture`](./../classes/RenderTexture.html)

相机的渲染目标，如果不设置则渲染到屏幕。
`xml`中的数据类型为`render-texture`资源。

---

### [#](#target) target

• `Optional` **target**: [`Transform`](./../classes/Transform.html)

相机对准的目标节点，如果不设置则为自由模式。
`xml`中的数据类型为节点对应的`nodeId`。

Incorrect translation.