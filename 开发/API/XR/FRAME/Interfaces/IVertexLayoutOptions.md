[xr-frame](./../) / [Exports](./../modules.html) / IVertexLayoutOptions

# [#](#Interface-IVertexLayoutOptions) Interface: IVertexLayoutOptions

顶点布局解构初始化参数。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [attributes](./IVertexLayoutOptions.html#attributes)
- [step](./IVertexLayoutOptions.html#step)
- [stepRate](./IVertexLayoutOptions.html#stepRate)
- [stride](./IVertexLayoutOptions.html#stride)

## [#](#Properties-2) Properties

### [#](#attributes) attributes

• **attributes**: { `format`: [`EVertexFormat`](./../enums/EVertexFormat.html) ; `name`: `string` ; `offset`: `number` ; `usage`: [`EVertexLayoutUsage`](./../enums/EVertexLayoutUsage.html) }[]

顶点属性列表。

---

### [#](#step) step

• `Optional` **step**: [`EVertexStep`](./../enums/EVertexStep.html)

步进类型。

**`default`** EVertexStep.PER\_VERTEX

---

### [#](#stepRate) stepRate

• `Optional` **stepRate**: `number`

步进单位。

**`default`** 1

---

### [#](#stride) stride

• `Optional` **stride**: `number`

步长，不设定会自动计算。

Incorrect translation.