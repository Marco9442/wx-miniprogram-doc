# [#](#Element) Element

Element 模块提供了控制小程序页面元素的方法。

## [#](#属性) 属性

### [#](#element-tagName) element.tagName

标签名，小写。

```
element.tagName: string
```

## [#](#方法) 方法

### [#](#element) element.$

在元素范围内获取元素。

```
element.$(selector: string): Promise<Element>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| selector | string | 是 | - | 选择器 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  let element = await page.$('.index-hd')
  element = await element.$('.index-desc')
  console.log(await element.text())
})
```

### [#](#element-2) element.$$

在元素范围内获取元素数组。

```
element.$$(selector: string): Promise<Element[]>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| selector | string | 是 | - | 选择器 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-bd')
  const elements = await element.$$('.kind-list-text')
  console.log(await elements[0].text())
})
```

### [#](#element-size) element.size

获取元素大小。

```
element.size(): Promise<Object>
```

**返回值说明**

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 元素宽度 |
| height | number | 元素高度 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-bd')
  const { width, height } = await element.size()
  console.log(width, height)
})
```

### [#](#element-offset) element.offset

获取元素绝对位置。

```
element.offset(): Promise<Object>
```

**返回值说明**

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| left | number | 左上角 x 坐标，单位：px |
| top | number | 左上角 y 坐标，单位：px |

坐标信息以页面左上角为原点。

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-bd')
  const { left, top } = await element.offset()
  console.log(left, top)
})
```

### [#](#element-text) element.text

获取元素文本。

```
element.text(): Promise<string>
```

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-desc')
  console.log(await element.text())
})
```

### [#](#element-attribute) element.attribute

获取元素特性。

```
element.attribute(name: string): Promise<string>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| name | string | 是 | - | 特性名 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-logo')
  console.log(await element.attribute('src')) // -> 'resources/kind/logo.png'
})
```

### [#](#element-property) element.property

> automator 0.9.0，基础库 2.9.5 开始支持。

获取元素属性。

```
element.property(name: string): Promise<any>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| name | string | 是 | - | 属性名 |

element.property 与 element.attribute 主要区别如下：

- element.attribute 获取的是标签上的值，因此它的返回类型一定是字符串，element.property 则不一定。
- element.attribute 可以获取到 class 和 id 之类的值，element.property 不行。
- element.property 可以获取到文档里对应组件列举的大部分属性值，比如表单 input 等组件的 value 值。

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('input')
  console.log(await element.property('value'))
})
```

### [#](#element-wxml) element.wxml

获取元素 WXML。

```
element.wxml(): Promise<string>
```

### [#](#element-outerWxml) element.outerWxml

同 wxml，只是会获取到元素本身。

```
element.outerWxml(): Promise<string>
```

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-desc')
  console.log(await element.wxml())
  console.log(await element.outerWxml())
})
```

### [#](#element-value) element.value

获取元素值。

```
element.value(): Promise<string>
```

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.weui-input')
  console.log(await element.value())
})
```

### [#](#element-style) element.style

获取元素样式值。

```
element.style(name: string): Promise<string>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| name | string | 是 | - | 样式名 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-desc')
  console.log(await element.style('color')) // -> 'rgb(136, 136, 136)'
})
```

### [#](#element-tap) element.tap

点击元素。

```
element.tap(): Promise<void>
```

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.kind-list-item-hd')
  await element.tap()
})
```

### [#](#element-longpress) element.longpress

长按元素。

```
element.longpress(): Promise<void>
```

### [#](#element-touchstart) element.touchstart

> automator 0.8.0，基础库 2.9.1 开始支持。

手指开始触摸元素。

```
element.touchstart(options: Object): Promise<void>
```

options 字段定义如下：

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| touches | array<Touch> | 是 | - | 触摸事件，当前停留在屏幕中的触摸点信息的数组 |
| changedTouches | array<Touch> | 是 | - | 触摸事件，当前变化的触摸点信息的数组 |

### [#](#element-touchmove) element.touchmove

> automator 0.8.0，基础库 2.9.1 开始支持。

手指触摸元素后移动。

```
element.touchmove(options: Object): Promise<void>
```

options 字段同 touchstart。

### [#](#element-touchend) element.touchend

> automator 0.8.0，基础库 2.9.1 开始支持。

手指结束触摸元素。

```
element.touchend(options: Object): Promise<void>
```

options 字段同 touchstart。

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.touch')
  await element.touchstart({
    touches: [
      {
        identifier: 1,
        pageX: 500,
        pageY: 500
      }
    ],
    changedTouches: [
      {
        identifier: 1,
        pageX: 500,
        pageY: 500
      }
    ]
  })
  await element.touchend({
    touches: [],
    changedTouches: [
      {
        identifier: 1,
        pageX: 500,
        pageY: 500
      }
    ]
  })
})
```

### [#](#element-trigger) element.trigger

触发元素事件。

```
element.trigger(type: string, detail?: Object): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| type | string | 是 | - | 触发事件类型 |
| detail | Object | 否 | - | 触发事件时传递的 detail 值 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('picker')
  await element.trigger('change', { value: 1 })
})
```

> 该方法无法改变组件状态，仅触发响应方法，也无法触发用户操作事件，即 tap，longpress 等事件，请使用对应的其它方法调用。

### [#](#element-input) element.input

> automator 0.9.0，基础库 2.9.5 开始支持。

输入文本，仅 input、textarea 组件可以使用。

```
element.input(value: string): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| value | string | 是 | - | 需要输入的文本 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('input')
  await element.input('test')
})
```

### [#](#element-callMethod) element.callMethod

> automator 0.6.0，基础库 2.9.0 开始支持。

调用组件实例指定方法，仅自定义组件可以使用。

```
element.callMethod(method: string, ...args: any[]): Promise<any>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| method | string | 是 | - | 需要调用的方法名 |
| ...args | array<any> | 否 | - | 方法参数 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('set-tab-bar')
  await element.callMethod('navigateBack')
})
```

### [#](#element-data) element.data

> automator 0.6.0，基础库 2.9.0 开始支持。

获取组件实例渲染数据，仅自定义组件可以使用。

```
element.data(path?: string): Promise<Object>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| path | string | 否 | - | 数据路径 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('set-tab-bar')
  console.log(await element.data('hasSetTabBarBadge'))
})
```

### [#](#element-setData) element.setData

> automator 0.6.0，基础库 2.9.0 开始支持。

设置组件实例渲染数据，仅自定义组件可以使用。

```
element.setData(data: Object): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object | 是 | - | 要改变的数据 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('set-tab-bar')
  await element.setData({
    hasSetTabBarBadge: true
  })
})
```

### [#](#element-callContextMethod) element.callContextMethod

> automator 0.9.0，基础库 2.9.5 开始支持。

调用上下文 Context 对象方法，仅 video 组件可以使用。

```
element.callContextMethod(method: string, ...args: any[]): Promise<any>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| method | string | 是 | - | 需要调用的方法名 |
| ...args | array<any> | 否 | - | 方法参数 |

> video 组件必须设置了 id 才能使用。

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('video')
  await element.callContextMethod('play')
})
```

### [#](#element-scrollWidth) element.scrollWidth

> automator 0.9.0，基础库 2.9.5 开始支持。

获取滚动宽度，仅 scroll-view 组件可以使用。

```
element.scrollWidth(): Promise<number>
```

### [#](#element-scrollHeight) element.scrollHeight

> automator 0.9.0，基础库 2.9.5 开始支持。

获取滚动高度，仅 scroll-view 组件可以使用。

```
element.scrollHeight(): Promise<number>
```

### [#](#element-scrollTo) element.scrollTo

> automator 0.9.0，基础库 2.9.5 开始支持。

滚动到指定位置，仅 scroll-view 组件可以使用。

```
element.scrollTo(x: number, y: number): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| x | number | 是 | - | 横向滚动位置 |
| y | number | 是 | - | 纵向滚动位置 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('scroll-view')
  const y = (await element.scrollHeight()) - 50
  await element.scrollTo(0, y)
})
```

### [#](#element-swipeTo) element.swipeTo

> automator 0.9.0，基础库 2.9.5 开始支持。

滑动到指定滑块，仅 swiper 组件可以使用。

```
element.swipeTo(index: number): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| index | number | 是 | - | 目标滑块的 index |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('swiper')
  await element.swipeTo(2)
})
```

### [#](#element-moveTo) element.moveTo

> automator 0.9.0，基础库 2.9.5 开始支持。

移动视图容器，仅 movable-view 组件可以使用。

```
element.moveTo(x: number, y: number): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| x | number | 是 | - | x 轴方向的偏移 |
| y | number | 是 | - | y 轴方向的偏移 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('movable-view')
  await element.moveTo(40, 40)
})
```

### [#](#element-slideTo) element.slideTo

> automator 0.9.0，基础库 2.9.5 开始支持。

滑动到指定数值，仅 slider 组件可以使用。

```
element.slideTo(value: number): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| value | number | 是 | - | 要设置的值 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('slider')
  await element.slideTo(10)
})
```

Incorrect translation.