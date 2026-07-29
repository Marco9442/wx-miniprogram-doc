[xr-frame](./../) / [Exports](./../modules.html) / ILightData

# [#](#Interface-ILightData) Interface: ILightData

[Light](./../classes/Light.html)组件数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [castShadow](./ILightData.html#castShadow)
- [color](./ILightData.html#color)
- [innerConeAngle](./ILightData.html#innerConeAngle)
- [intensity](./ILightData.html#intensity)
- [outerConeAngle](./ILightData.html#outerConeAngle)
- [range](./ILightData.html#range)
- [shadowBias](./ILightData.html#shadowBias)
- [shadowDistance](./ILightData.html#shadowDistance)
- [type](./ILightData.html#type)

## [#](#Properties-2) Properties

### [#](#castShadow) castShadow

• `Optional` **castShadow**: `boolean`

是否要产生阴影，仅对平行光有效。
`xml`中的数据类型`boolean`，默认为`false`。

---

### [#](#color) color

• **color**: `number`[]

颜色。
`xml`中的数据类型`color`，默认为`[1, 1, 1, 1]`。

---

### [#](#innerConeAngle) innerConeAngle

• **innerConeAngle**: `number`

仅在聚光有效。
`xml`中的数据类型`number`，默认为`1`。

---

### [#](#intensity) intensity

• **intensity**: `number`

强度。
`xml`中的数据类型`number`，默认为`1`。

---

### [#](#outerConeAngle) outerConeAngle

• **outerConeAngle**: `number`

仅在聚光有效。
`xml`中的数据类型`number`，默认为`1`。

---

### [#](#range) range

• **range**: `number`

范围，仅在点光和聚光有效。
`xml`中的数据类型`number`，默认为`1`。

---

### [#](#shadowBias) shadowBias

• `Optional` **shadowBias**: `number`

阴影采样时的容许偏移，仅对平行光有效。
`xml`中的数据类型`number`，默认为`0.002`。

---

### [#](#shadowDistance) shadowDistance

• `Optional` **shadowDistance**: `number`

产生阴影的最大距离，仅对平行光有效。
`xml`中的数据类型`number`，默认为`10`。

---

### [#](#type) type

• **type**: `ELightType`

类型。
`xml`中的数据类型`string`，默认为`directional`。

Incorrect translation.