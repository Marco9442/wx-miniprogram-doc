[xr-frame](./../) / [Exports](./../modules.html) / IRenderStates

# [#](#Interface-IRenderStates) Interface: IRenderStates

支持定制的渲染状态。

大部分状态会定制的开发者应该看名字就懂，就不详细说明了。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [blendDst](./IRenderStates.html#blendDst)
- [blendDstAlpha](./IRenderStates.html#blendDstAlpha)
- [blendDstRGB](./IRenderStates.html#blendDstRGB)
- [blendFunc](./IRenderStates.html#blendFunc)
- [blendOn](./IRenderStates.html#blendOn)
- [blendSrc](./IRenderStates.html#blendSrc)
- [blendSrcAlpha](./IRenderStates.html#blendSrcAlpha)
- [blendSrcRGB](./IRenderStates.html#blendSrcRGB)
- [colorWrite](./IRenderStates.html#colorWrite)
- [cullFace](./IRenderStates.html#cullFace)
- [cullOn](./IRenderStates.html#cullOn)
- [depthTestComp](./IRenderStates.html#depthTestComp)
- [depthTestOn](./IRenderStates.html#depthTestOn)
- [depthWrite](./IRenderStates.html#depthWrite)
- [primitiveType](./IRenderStates.html#primitiveType)
- [renderQueue](./IRenderStates.html#renderQueue)
- [stencilComp](./IRenderStates.html#stencilComp)
- [stencilFail](./IRenderStates.html#stencilFail)
- [stencilPass](./IRenderStates.html#stencilPass)
- [stencilReadMask](./IRenderStates.html#stencilReadMask)
- [stencilRef](./IRenderStates.html#stencilRef)
- [stencilTestOn](./IRenderStates.html#stencilTestOn)
- [stencilWriteMask](./IRenderStates.html#stencilWriteMask)
- [stencilZFail](./IRenderStates.html#stencilZFail)

## [#](#Properties-2) Properties

### [#](#blendDst) blendDst

• `Optional` **blendDst**: [`EBlendFactor`](./../enums/EBlendFactor.html)

不要使用，使用`blendDstRGB`。

---

### [#](#blendDstAlpha) blendDstAlpha

• `Optional` **blendDstAlpha**: [`EBlendFactor`](./../enums/EBlendFactor.html)

---

### [#](#blendDstRGB) blendDstRGB

• `Optional` **blendDstRGB**: [`EBlendFactor`](./../enums/EBlendFactor.html)

---

### [#](#blendFunc) blendFunc

• `Optional` **blendFunc**: [`EBlendEquation`](./../enums/EBlendEquation.html)

---

### [#](#blendOn) blendOn

• `Optional` **blendOn**: `boolean`

---

### [#](#blendSrc) blendSrc

• `Optional` **blendSrc**: [`EBlendFactor`](./../enums/EBlendFactor.html)

不要使用，使用`blendSrcRGB`。

---

### [#](#blendSrcAlpha) blendSrcAlpha

• `Optional` **blendSrcAlpha**: [`EBlendFactor`](./../enums/EBlendFactor.html)

---

### [#](#blendSrcRGB) blendSrcRGB

• `Optional` **blendSrcRGB**: [`EBlendFactor`](./../enums/EBlendFactor.html)

---

### [#](#colorWrite) colorWrite

• `Optional` **colorWrite**: `number`

在基础库版本`v2.31.1`以上支持。

---

### [#](#cullFace) cullFace

• `Optional` **cullFace**: [`ECullMode`](./../enums/ECullMode.html)

---

### [#](#cullOn) cullOn

• `Optional` **cullOn**: `boolean`

---

### [#](#depthTestComp) depthTestComp

• `Optional` **depthTestComp**: [`ECompareFunc`](./../enums/ECompareFunc.html)

---

### [#](#depthTestOn) depthTestOn

• `Optional` **depthTestOn**: `boolean`

---

### [#](#depthWrite) depthWrite

• `Optional` **depthWrite**: `boolean`

---

### [#](#primitiveType) primitiveType

• `Optional` **primitiveType**: [`EPrimitiveType`](./../enums/EPrimitiveType.html)

---

### [#](#renderQueue) renderQueue

• `Optional` **renderQueue**: `number`

渲染队列，大于等于`2500`为透明物体，否则为非透明物体。

---

### [#](#stencilComp) stencilComp

• `Optional` **stencilComp**: [`ECompareFunc`](./../enums/ECompareFunc.html)

---

### [#](#stencilFail) stencilFail

• `Optional` **stencilFail**: [`EStencilOp`](./../enums/EStencilOp.html)

---

### [#](#stencilPass) stencilPass

• `Optional` **stencilPass**: [`EStencilOp`](./../enums/EStencilOp.html)

---

### [#](#stencilReadMask) stencilReadMask

• `Optional` **stencilReadMask**: `number`

---

### [#](#stencilRef) stencilRef

• `Optional` **stencilRef**: `number`

---

### [#](#stencilTestOn) stencilTestOn

• `Optional` **stencilTestOn**: `boolean`

---

### [#](#stencilWriteMask) stencilWriteMask

• `Optional` **stencilWriteMask**: `number`

---

### [#](#stencilZFail) stencilZFail

• `Optional` **stencilZFail**: [`EStencilOp`](./../enums/EStencilOp.html)

Incorrect translation.