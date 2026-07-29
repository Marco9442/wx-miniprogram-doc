# [#](#Skyline-WXSS-样式支持与差异) Skyline WXSS 样式支持与差异

## [#](#模块支持) 模块支持

| 模块 | 支持情况 | 备注 |
| --- | --- | --- |
| CSS Animation | ✓ | 安卓 8.0.37，iOS 8.0.39，支持情况见下表 |
| 背景与边框 | ✓ | 常用的基本支持，详见[属性支持](#属性支持) |
| 盒子模型 | ✓ | 支持 border-box 和 content-box，没有 BFC |
| Inline 布局 | × | 开发中 |
| Inline-Block 布局 | × | 仅支持在 text 组件里的嵌套结构使用，完整版本开发中 |
| Block 布局 | ✓ | 详见[开启默认 Block 布局](#开启默认Block布局) |
| Flex 布局 | ✓ | 包括 inline-flex 布局 |
| 字体 | ✓ | 基本支持，也支持自定义字体 |
| Positioned 布局 | ✓ | 支持情况见下表。sticky 可使用 [sticky-header](https://developers.weixin.qq.com/miniprogram/dev/component/sticky-header.html)/[sticky-section](https://developers.weixin.qq.com/miniprogram/dev/component/list-view.html) 替代 |
| CSS Transition | ✓ |  |
| CSS Variable（CSS 变量） | ✓ | 安卓 8.0.35，iOS 8.0.38 |
| Media queries | ✓ | 只支持 DarkMode |
| Font-face | ✓ | 只支持 ttf 格式 |

## [#](#选择器支持) 选择器支持

| 类别 | 示例 | 支持度 | 备注 |
| --- | --- | --- | --- |
| 通配选择器 | \* {} | × |  |
| 元素选择器 | tag {} | ✓ |  |
| 类选择器 | .class {} | ✓ |  |
| ID 选择器 | #id {} | ✓ |  |
| 分组选择器 | a, b {} | ✓ |  |
| 直接子代选择器 | a > b {} | ✓ |  |
| 后代选择器 | a b {} | ✓ |  |
| 属性选择器 | [attr] {} | × |  |
| 一般兄弟选择器 | a ~ b {} | ✓ | 8.0.49 |
| 紧邻兄弟选择器 | a + b {} | ✓ | 8.0.49 |
| 伪类选择器 | :active {} | ✓ | 支持 :first-child / :last-child；微信 8.0.49 起（对应 Skyline 1.3.0）支持 :not / :only-child / :empty；微信 8.0.50 起（对应 Skyline 1.3.3）支持 :nth-child |
| 伪元素选择器 | ::before {} | ✓ | 只支持 ::before 和 ::after |

## [#](#属性支持) 属性支持

| 样式属性 | 支持格式 | 默认值 | 备注 |
| --- | --- | --- | --- |
| display | none / flex / block | flex | 默认值可通过[配置](#开启默认Block布局)改成 block |
| position | relative / absolute / fixed | relative | fixed 在微信客户端 8.0.43 版本开始支持，只支持相对于窗口 viewport 定位，不支持 top / left / bottom / right 默认值 auto 解析，z-index 只作用在兄弟节点；sticky 可使用 [sticky-header](https://developers.weixin.qq.com/miniprogram/dev/component/sticky-header.html)/[sticky-section](https://developers.weixin.qq.com/miniprogram/dev/component/list-view.html) 替代 |
| overflow | hidden / visible | visible | scroll 不支持，只能通过 scroll-view 实现；不支持单独设置 overflow-x/y |
| pointer-events | auto / none | auto |  |
| box-sizing | border-box / content-box | border-box |  |
| transform | none / `<transform-function>` | none |  |
| transform-origin | left / center / right / top / bottom / [`<length>{1, 2}`](#wxss-length) | 50% 50% |  |
| z-index | `<float>` | 0 | 不支持层叠上下文，只对兄弟节点生效；不支持在 scroll-view 下的直接子节点上应用 |
| visibility | visible / hidden | visible |  |
| color | [`<color>`](#wxss-color) | black |  |
| opacity | `<float>` | 1 |  |
| align-items | stretch / center / flex-start / flex-end / baseline | stretch |  |
| align-self | auto / stretch / center / flex-start / flex-end / baseline | auto |  |
| align-content | stretch / center / flex-start / flex-end / space-between / space-around | auto |  |
| justify-content | center / flex-start / flex-end / space-between / space-around / space-evenly | flex-start |  |
| flex-direction | row / row-reverse / column / column-reverse | column |  |
| flex-wrap | nowrap / wrap / wrap-reverse | nowrap |  |
| flex-grow | `<float>` | 0 |  |
| flex-shrink | `<float>` | 1 |  |
| flex-basis | [`<length>`](#wxss-length) | auto |  |
| order | `<float>` | 0 |  |
| gap | `<length>` | 0 |  |
| flex |  |  | 简写属性，支持解析但以展开属性为准 |
| background-color | [`<color>`](#wxss-color) | transparent |  |
| background-image | none / [`<image>`](#wxss-image) | none | 不支持多张图片 |
| background-size | contain / cover / [`[<length> | auto]{1, 2}`](#wxss-length) | auto |  |
| background-position | left / center / right / top / bottom / [`<length>`](#wxss-length) | 0 0 | 完全支持 `<bg-position>`#，请参考 MDN |
| background-repeat | repeat-x / repeat-y / repeat / no-repeat | repeat |  |
| background |  |  | 简写属性，支持解析但以展开属性为准 |
| width | [`<length>`](#wxss-length) | auto |  |
| height | [`<length>`](#wxss-length) | auto |  |
| min-width | [`<length>`](#wxss-length) | auto |  |
| min-height | [`<length>`](#wxss-length) | none |  |
| max-width | [`<length>`](#wxss-length) | auto |  |
| max-height | [`<length>`](#wxss-length) | none |  |
| left | [`<length>`](#wxss-length) | auto |  |
| right | [`<length>`](#wxss-length) | auto |  |
| top | [`<length>`](#wxss-length) | auto |  |
| bottom | [`<length>`](#wxss-length) | auto |  |
| padding | [`<length>{1,4}`](#wxss-length) | 0 0 0 0 |  |
| padding-left | [`<length>`](#wxss-length) | 0 |  |
| padding-top | [`<length>`](#wxss-length) | 0 |  |
| padding-right | [`<length>`](#wxss-length) | 0 |  |
| padding-bottom | [`<length>`](#wxss-length) | 0 |  |
| margin | [`<length>{1,4}`](#wxss-length) | 0 0 0 0 |  |
| margin-left | [`<length>`](#wxss-length) | 0 |  |
| margin-top | [`<length>`](#wxss-length) | 0 |  |
| margin-right | [`<length>`](#wxss-length) | 0 |  |
| margin-bottom | [`<length>`](#wxss-length) | 0 |  |
| border-left-width | [`<length>`](#wxss-length) | 3 |  |
| border-left-style | [`<border-style>`](#wxss-border-style) | none |  |
| border-left-color | [`<color>`](#wxss-color) | black | 默认值与 web 不同， web 默认值是 currentcolor |
| border-top-width | [`<length>`](#wxss-length) | 3 |  |
| border-top-style | [`<border-style>`](#wxss-border-style) | none |  |
| border-top-color | [`<color>`](#wxss-color) | black | 默认值与 web 不同， web 默认值是 currentcolor |
| border-right-width | [`<length>`](#wxss-length) | 3 |  |
| border-right-style | [`<border-style>`](#wxss-border-style) | none |  |
| border-right-color | [`<color>`](#wxss-color) | black | 默认值与 web 不同， web 默认值是 currentcolor |
| border-bottom-width | [`<length>`](#wxss-length) | 3 |  |
| border-bottom-style | [`<border-style>`](#wxss-border-style) | none |  |
| border-bottom-color | [`<color>`](#wxss-color) | black | 默认值与 web 不同， web 默认值是 currentcolor |
| border-width |  |  | 简写属性，支持解析但以展开属性为准 |
| border-style |  |  | 简写属性，支持解析但以展开属性为准 |
| border-color |  |  | 简写属性，支持解析但以展开属性为准 |
| border-left |  |  | 简写属性，支持解析但以展开属性为准 |
| border-right |  |  | 简写属性，支持解析但以展开属性为准 |
| border-top |  |  | 简写属性，支持解析但以展开属性为准 |
| border-bottom |  |  | 简写属性，支持解析但以展开属性为准 |
| border |  |  | 简写属性，支持解析但以展开属性为准 |
| box-shadow | none / inset? && [`<length>{2,4}`](#wxss-length) && [`<color>`](#wxss-color)? | none | 不支持多个叠加 |
| border-top-left-radius | [`<length>{1, 2}`](#wxss-length) | 0 | border-radius 非 0 时，四边的 border-width 可不一致，四边的 border-color 和 border-style 需一致 |
| border-top-right-radius | [`<length>{1, 2}`](#wxss-length) | 0 | border-radius 非 0 时，四边的 border-width 可不一致，四边的 border-color 和 border-style 需一致 |
| border-bottom-left-radius | [`<length>{1, 2}`](#wxss-length) | 0 | border-radius 非 0 时，四边的 border-width 可不一致，四边的 border-color 和 border-style 需一致 |
| border-bottom-right-radius | [`<length>{1, 2}`](#wxss-length) | 0 | border-radius 非 0 时，四边的 border-width 可不一致，四边的 border-color 和 border-style 需一致 |
| border-radius |  |  | 简写属性，支持解析但以展开属性为准 |
| transition-property | none / all / transform / opacity 等 | all | 基本都支持，暂不一一列举 |
| transition-duration | `<time>` | 0 |  |
| transition-timing-function | [`<timing-function>`](#wxss-timing-function) | [`<timing-function>`](#wxss-timing-function) |  |
| transition-delay | `<time>` | 0 |  |
| transition |  |  | 简写属性，支持解析但以展开属性为准 |
| font |  |  | 简写属性，支持解析但以展开属性为准；不支持 caption / icon 等系统字体; |
| font-size | [`<length>`](#wxss-length) | 16px | 不支持百分比；不支持 keyword (smaller..) |
| line-height | normal / `<number>` / [`<length>`](#wxss-length) / `<percent>` | normal |  |
| text-align | left / center / right / justify / start / end | start |  |
| font-weight | normal / bold / `<float>` | normal |  |
| white-space | normal / nowrap / normal |  |  |
| text-overflow | clip / ellipsis | clip | 仅作用于 text 节点 |
| word-break | normal / break-all | normal |  |
| word-spacing | normal / [`<length>`](#wxss-length) | normal |  |
| letter-spacing | normal / [`<length>`](#wxss-length) | normal |  |
| font-family | serif / sans-serif / monospace / cursive / fantasy / `<string>` |  |  |
| font-style | normal / italic | normal |  |
| text-decoration-line | none / underline / overline / line-through | none | 仅作用于 text 节点 |
| text-decoration-style | solid / double / dotted / dashed / wavy | solid | 仅作用于 text 节点 |
| text-decoration-color | [`<color>`](#wxss-color) | black | 仅作用于 text 节点；默认值和 web 不同，web 默认值是 currentcolor |
| text-decoration |  |  | 简写属性，支持解析但以展开属性为准；当前仅支持设置一种类型；暂不支持复合使用 text-decoration |
| text-shadow | none / [`<color>`](#wxss-color)? && [`<length>{2,3}`](#wxss-length) | none |  |
| backdrop-filter | none / [`[<filter-function>]`](#wxss-filter-function) | none | 不支持 multi function；不支持 drop-shadow；不支持 url；与 opacity 混合有问题；blur 某些情况表现不一致； |
| filter | none / [`[<filter-function>]`](#wxss-filter-function) | none | 不支持 multi function；不支持 drop-shadow；不支持 url； |
| mask-image | none / [`<image>`](#wxss-image) | none | 不支持多张图片 |
| animation-delay | `<time>` | 0 |  |
| animation-direction | normal / reverse / alternate / alternate-reverse | normal |  |
| animation-duration | `<time>` | 0 |  |
| animation-fill-mode | forwards / both | none | none 与 backwards 暂未支持，表现均为 forwards |
| animation-iteration-count | infinite / `<number>` | 1 |  |
| animation-name | none / `<custom-ident>` | none |  |
| animation-timing-function | [`<timing-function>`](#wxss-timing-function) | [`<timing-function>`](#wxss-timing-function) |  |
| animation |  |  | 简写属性，支持解析但以展开属性为准 |
| will-change | auto / contents | auto | 声明绘制边界，优化渲染性能 |

## [#](#类型支持列表) 类型支持列表

类别 | 格式 | 支持度 | 备注 |

```
  <tr>
    <td id="wxss-length" valign=center rowspan=12>&lt;length&gt;</td>
    <td valign=center>auto</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>px</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>   
    <td valign=center>rem</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>   
    <td valign=center>em</td>
    <td valign=center>×</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>rpx</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>vw</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>vh</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>vmin</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>vmax</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>ratio</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>env()</td>
    <td valign=center>✓</td>
    <td valign=center>只支持 safe-area-inset-* 系列</td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>calc()</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td id="wxss-color" valign=center rowspan=7>&lt;color&gt;</td>
    <td valign=center>color keywords</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>transparent</td>
    <td valign=center>✓</td>
    <td valign=center></td> 
  </tr>
  <tr>
    <td valign=center>currentColor</td>
    <td valign=center>×</td>
    <td valign=center>考虑支持</td>
  </tr>
  <tr>
    <td valign=center>rgb[a]</td>
    <td valign=center>✓</td>
    <td valign=center></td> 
  </tr>
  <tr>
    <td valign=center>#RRGGBB / #RGB</td>
    <td valign=center>✓</td>
    <td valign=center></td> 
  </tr>
  <tr>
    <td valign=center>hsl</td>
    <td valign=center>✓</td>
    <td valign=center></td>    
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>hsla</td>
    <td valign=center>✓</td>
    <td valign=center></td>    
  </tr>
  
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td id="wxss-url" valign=center>&lt;url&gt;</td>
    <td valign=center>url()</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td valign=center rowspan=3>&lt;gradient&gt;</td>
    <td valign=center>linear-gradient()</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>radial-gradient()</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>conic-gradient()</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td id="wxss-image" valign=center rowspan=2>&lt;image&gt;</td>
    <td valign=center>&lt;url&gt;</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>&lt;gradient&gt;</td>
    <td valign=center>✓</td>
    <td valign=center></td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td id="wxss-border-style" width=149 valign=center rowspan=5>&lt;border-style&gt;</td>
    <td valign=center>none</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>hidden</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>solid</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>dashed</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>dotted</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td id="wxss-filter-function" valign=center rowspan=9>&lt;filter-function&gt;</td>
    <td valign=center>brightness()</td>
    <td valign=center>✓</td>
    <td valign=center rowspan=9>多个 function 暂不支持</td>
  </tr>
  <tr>
    <td valign=center>contrast()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>saturate()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>huerotate()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>invert()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>opacity()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>grayscale()</td>
    <td valign=center>✓</td>
  </tr>
  <tr>
    <td valign=center>specia()</td>
    <td valign=center>✓</td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>drop-shadow</td>
    <td valign=center>×</td>
  </tr>
  
  <tr>
    <td valign=center rowspan=4>&lt;angle&gt;</td>
    <td valign=center>deg</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>grad</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>rad</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr style="border-bottom: 0.5px solid #DDD;">
    <td valign=center>turn</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  
  <tr>
    <td id="wxss-timing-function" valign=center rowspan=9>&lt;timing-function&gt;</td>
    <td valign=center>ease</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>ease-in</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>ease-out</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>ease-in-out</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>linear</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>cubic-bezier</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>steps</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>step-start</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
  <tr>
    <td valign=center>step-end</td>
    <td valign=center>✓</td>
    <td valign=center></td>
  </tr>
</tbody>
```

## [#](#开启默认Block布局) 开启默认Block布局

Skyline 下节点默认为 flex 布局，可通过以下配置切换为默认 block 布局。

| 平台 | 最低版本 |
| --- | --- |
| Android | 8.0.34 |
| iOS | 8.0.36 |
| 开发者工具 | Nightly Build (1.06.2304262) |
| 基础库 | 2.31.1 |

在 `app.json` 或 `page.json` 中配置：

```
rendererOptions: {
  "skyline": {
    "defaultDisplayBlock": true,
  }
}
```

## [#](#开启默认-ContentBox-盒模型) 开启默认 ContentBox 盒模型

Skyline 下节点默认为 border-box 盒模型，可通过以下配置切换为默认 content-box 盒模型。

| 平台 | 最低版本 |
| --- | --- |
| Android | 8.0.42 |
| iOS | 8.0.42 |
| 开发者工具 | Nightly Build (1.06.2310092) |
| 基础库 | 3.1.0 |

在 `app.json` 或 `page.json` 中配置：

```
rendererOptions: {
  "skyline": {
    "defaultContentBox": true,
  }
}
```

## [#](#开启-tag-选择器全局匹配) 开启 tag 选择器全局匹配

Skyline 下 tag 选择器遵循样式隔离机制，而 WebView 下不受样式隔离约束，可通过 `tagNameStyleIsolation: legacy` 配置对齐 WebView 表现，若指定 `tagNameStyleIsolation: isolated` 则遵循样式隔离机制。

| 平台 | 最低版本 |
| --- | --- |
| Android | 8.0.51 |
| iOS | 8.0.51 |
| 开发者工具 | Nightly Build (1.06.2409032) |
| 基础库 | 3.6.0 |

在 `app.json` 或 `page.json` 中配置：

```
rendererOptions: {
  "skyline": {
    "tagNameStyleIsolation": "legacy",
  }
}
```

## [#](#开启-scroll-view-自动撑开) 开启 scroll-view 自动撑开

Skyline 下 scroll-view 默认需要指定宽高撑开，可通过以下配置切换为自动根据内容撑开。

| 平台 | 最低版本 |
| --- | --- |
| Android | 8.0.54 |
| iOS | 8.0.54 |
| 基础库 | 3.7.2 |

在 `app.json` 或 `page.json` 中配置：

```
rendererOptions: {
  "skyline": {
    "enableScrollViewAutoSize": true,
  }
}
```

## [#](#开启-keyframe-样式全局共享) 开启 keyframe 样式全局共享

Skyline 下 @keyframe 规则遵循样式隔离机制，而 WebView 下不受样式隔离约束，可通过 `tagNameStyleIsolation: legacy` 配置对齐 WebView 表现，若指定 `tagNameStyleIsolation: isolated` 则遵循样式隔离机制。

| 平台 | 最低版本 |
| --- | --- |
| Android | 8.0.57 |
| iOS | 8.0.57 |
| 基础库 | 3.8.0 |

在 `app.json` 或 `page.json` 中配置：

```
rendererOptions: {
  "skyline": {
    "keyframeStyleIsolation": "legacy",
  }
}
```

Incorrect translation.