[xr-frame](./../) / [Exports](./../modules.html) / IViewAction

# [#](#Interface-IViewAction) Interface: IViewAction

对一个View进行清屏的操作。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [clearColor](./IViewAction.html#clearColor)
- [clearDepth](./IViewAction.html#clearDepth)
- [clearStencil](./IViewAction.html#clearStencil)
- [colorAction](./IViewAction.html#colorAction)
- [depthAction](./IViewAction.html#depthAction)
- [stencilAction](./IViewAction.html#stencilAction)

## [#](#Properties-2) Properties

### [#](#clearColor) clearColor

• `Optional` **clearColor**: [`number`, `number`, `number`, `number`]

用于清屏的颜色值。

**`default`** [0,0,0,0]

---

### [#](#clearDepth) clearDepth

• `Optional` **clearDepth**: `number`

用于清屏的深度值。

**`default`** 1

---

### [#](#clearStencil) clearStencil

• `Optional` **clearStencil**: `number`

用于清屏的模板值。

**`default`** 0

---

### [#](#colorAction) colorAction

• `Optional` **colorAction**: [`ELoadAction`](./../enums/ELoadAction.html)

颜色操作。

---

### [#](#depthAction) depthAction

• `Optional` **depthAction**: [`ELoadAction`](./../enums/ELoadAction.html)

深度操作。

---

### [#](#stencilAction) stencilAction

• `Optional` **stencilAction**: [`ELoadAction`](./../enums/ELoadAction.html)

模板操作。

Incorrect translation.