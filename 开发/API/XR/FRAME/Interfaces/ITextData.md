[xr-frame](./../) / [Exports](./../modules.html) / ITextData

# [#](#Interface-ITextData) Interface: ITextData

`Text`数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [anchor](./ITextData.html#anchor)
- [color](./ITextData.html#color)
- [height](./ITextData.html#height)
- [horzAlign](./ITextData.html#horzAlign)
- [lineHeight](./ITextData.html#lineHeight)
- [neverCull](./ITextData.html#neverCull)
- [padding](./ITextData.html#padding)
- [size](./ITextData.html#size)
- [states](./ITextData.html#states)
- [uniforms](./ITextData.html#uniforms)
- [value](./ITextData.html#value)
- [vertAlign](./ITextData.html#vertAlign)
- [width](./ITextData.html#width)

## [#](#Properties-2) Properties

### [#](#anchor) anchor

• `Optional` **anchor**: `number`[]

文本轴点
`xml`中的数据类型为`number-array`，默认为`0 1`。

---

### [#](#color) color

• `Optional` **color**: `number`[]

文本颜色
`xml`中的数据类型为`number-array`，默认为`0 0 0 1`。

---

### [#](#height) height

• `Optional` **height**: `number`

文本框高度
`xml`中的数据类型为`number`

---

### [#](#horzAlign) horzAlign

• `Optional` **horzAlign**: `string`

文本水平定位
`xml`中的数据类型为`string`，默认为`left`。

---

### [#](#lineHeight) lineHeight

• `Optional` **lineHeight**: `number`

文本框行高，为比例
`xml`中的数据类型为`number`

---

### [#](#neverCull) neverCull

• `Optional` **neverCull**: `boolean`

是否不参与剔除，默认false(即参与剔除)。

---

### [#](#padding) padding

• `Optional` **padding**: `number`[]

文本内边距
`xml`中的数据类型为`number-array`，默认为`0 0 0`。

---

### [#](#size) size

• `Optional` **size**: `number`

文本大小
`xml`中的数据类型为`number`

---

### [#](#states) states

• `Optional` **states**: [`string`, `string`][]

覆盖`material`中的默认`states`，如果覆盖了，则会先创建一个材质副本。
`xml`中同{@link IMaterialData.states}。

---

### [#](#uniforms) uniforms

• `Optional` **uniforms**: [`string`, `string`][]

覆盖`material`中的默认`uniforms`，如果覆盖了，则会先创建一个材质副本。
`xml`中同{@link IMaterialData.uniforms}。

---

### [#](#value) value

• `Optional` **value**: `string`

文本内容
`xml`中的数据类型为`string`

---

### [#](#vertAlign) vertAlign

• `Optional` **vertAlign**: `string`

文本垂直定位
`xml`中的数据类型为`string`，默认为`top`。

---

### [#](#width) width

• `Optional` **width**: `number`

文本框宽度
`xml`中的数据类型为`number`

Incorrect translation.