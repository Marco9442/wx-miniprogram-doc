[xr-frame](./../) / [Exports](./../modules.html) / ITransformData

# [#](#Interface-ITransformData) Interface: ITransformData

[Transform](./../classes/Transform.html)组件数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [layer](./ITransformData.html#layer)
- [nodeId](./ITransformData.html#nodeId)
- [position](./ITransformData.html#position)
- [rotation](./ITransformData.html#rotation)
- [scale](./ITransformData.html#scale)
- [visible](./ITransformData.html#visible)

## [#](#Properties-2) Properties

### [#](#layer) layer

• `Optional` **layer**: `number`

节点的层级，作为控制节点以及子节点是否可见的一部分，配合[Camera.cullMask](./../classes/Camera.html#cullMask)使用。
判定规则为自顶层节点向下，只有全部通过了判定才能显示。
`xml`中的数据类型为`number`，默认为`0`。

---

### [#](#nodeId) nodeId

• **nodeId**: `string`

设置一个唯一的节点Id，区别于`xml`上的那个`id`。
`xml`中的数据类型为`string`。

---

### [#](#position) position

• **position**: `number`[]

节点的位移。
`xml`中的数据类型为`number-array`，默认为`0 0 0`。

---

### [#](#rotation) rotation

• **rotation**: `number`[]

节点的旋转，注意此处为**角度**。
`xml`中的数据类型为`number-array`，默认为`0 0 0`。

---

### [#](#scale) scale

• **scale**: `number`[]

节点的位缩放。
`xml`中的数据类型为`number-array`，默认为`1 1 1`。

---

### [#](#visible) visible

• `Optional` **visible**: `boolean`

节点的可见性，可以控制该节点以及所有子节点是否可见。
`xml`中的数据类型为`boolean`，默认为`true`。

Incorrect translation.