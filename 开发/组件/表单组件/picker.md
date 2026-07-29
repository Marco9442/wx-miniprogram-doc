# [#](#picker) picker

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

从底部弹起的滚动选择器。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | header-text | string |  | 否 | 选择器的标题，仅安卓可用 | [2.11.0](../framework/compatibility.html) |
|  | mode | string | selector | 否 | 选择器类型 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | selector | 普通选择器 | | multiSelector | 多列选择器 | | time | 时间选择器 | | date | 日期选择器 | | region | 省市区选择器 | | | | | | |
|  | disabled | boolean | false | 否 | 是否禁用 | [1.0.0](../framework/compatibility.html) |
|  | bindcancel | eventhandle |  | 否 | 取消选择时触发 | [1.9.90](../framework/compatibility.html) |

除了上述通用的属性，对于不同的mode，`picker`拥有不同的属性。

## [#](#普通选择器：mode-selector) 普通选择器：mode = selector

| 属性名 | 类型 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
| range | array/object array | [] | mode 为 selector 或 multiSelector 时，range 有效 |  |
| range-key | string |  | 当 range 是一个 Object Array 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容 |  |
| value | number | 0 | 表示选择了 range 中的第几个（下标从 0 开始） |  |
| bindchange | eventhandle |  | value 改变时触发 change 事件，event.detail = {value} |  |

## [#](#多列选择器：mode-multiSelector) 多列选择器：mode = multiSelector

| 属性名 | 类型 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
| range | array/object array | [] | mode 为 selector 或 multiSelector 时，range 有效 |  |
| range-key | string |  | 当 range 是一个 Object Array 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容 |  |
| value | array | [] | 表示选择了 range 中的第几个（下标从 0 开始） |  |
| bindchange | eventhandle |  | value 改变时触发 change 事件，event.detail = {value} |  |
| bindcolumnchange | eventhandle |  | 列改变时触发 |  |

## [#](#时间选择器：mode-time) 时间选择器：mode = time

| 属性名 | 类型 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
| value | string |  | 表示选中的时间，格式为"hh:mm" |  |
| start | string |  | 表示有效时间范围的开始，字符串格式为"hh:mm" |  |
| end | string |  | 表示有效时间范围的结束，字符串格式为"hh:mm" |  |
| bindchange | eventhandle |  | value 改变时触发 change 事件，event.detail = {value} |  |

## [#](#日期选择器：mode-date) 日期选择器：mode = date

| 属性名 | 类型 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
| value | string | 当天 | 表示选中的日期，格式为"YYYY-MM-DD" |  |
| start | string |  | 表示有效日期范围的开始，字符串格式为"YYYY-MM-DD" |  |
| end | string |  | 表示有效日期范围的结束，字符串格式为"YYYY-MM-DD" |  |
| fields | string | day | 有效值 year,month,day，表示选择器的粒度 |  |
| bindchange | eventhandle |  | value 改变时触发 change 事件，event.detail = {value} |  |

**fields 有效值：**

| 值 | 说明 |
| --- | --- |
| year | 选择器粒度为年 |
| month | 选择器粒度为月份 |
| day | 选择器粒度为天 |

## [#](#省市区选择器：mode-region-1-4-0) 省市区选择器：mode = region [1.4.0](../framework/compatibility.html)

| 属性名 | 类型 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
| value | array | [] | 表示选中的省市区，默认选中每一列的第一个值 |  |
| custom-item | string |  | 可为每一列的顶部添加一个自定义的项 | [1.5.0](../framework/compatibility.html) |
| level | string | region | 选择器层级 | [2.21.1](../framework/compatibility.html) |
| bindchange | eventhandle |  | value 改变时触发 change 事件，event.detail = {value, code, postcode}，其中字段 code 是统计用区划代码，postcode 是邮政编码 |  |

level 的有效值

| 值 | 说明 |
| --- | --- |
| province | 省级选择器 |
| city | 市级选择器 |
| region | 区级选择器 |
| sub-district | 街道选择器 |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/D22Y9SmR7fJK "在开发者工具中预览效果")

```
<view class="section">
  <view class="section__title">普通选择器</view>
  <picker bindchange="bindPickerChange" value="{{index}}" range="{{array}}">
    <view class="picker">
      当前选择：{{array[index]}}
    </view>
  </picker>
</view>
<view class="section">
  <view class="section__title">多列选择器</view>
  <picker mode="multiSelector" bindchange="bindMultiPickerChange" bindcolumnchange="bindMultiPickerColumnChange" value="{{multiIndex}}" range="{{multiArray}}">
    <view class="picker">
      当前选择：{{multiArray[0][multiIndex[0]]}}，{{multiArray[1][multiIndex[1]]}}，{{multiArray[2][multiIndex[2]]}}
    </view>
  </picker>
</view>
<view class="section">
  <view class="section__title">时间选择器</view>
  <picker mode="time" value="{{time}}" start="09:01" end="21:01" bindchange="bindTimeChange">
    <view class="picker">
      当前选择: {{time}}
    </view>
  </picker>
</view>

<view class="section">
  <view class="section__title">日期选择器</view>
  <picker mode="date" value="{{date}}" start="2015-09-01" end="2017-09-01" bindchange="bindDateChange">
    <view class="picker">
      当前选择: {{date}}
    </view>
  </picker>
</view>
<view class="section">
  <view class="section__title">省市区选择器</view>
  <picker mode="region" bindchange="bindRegionChange" value="{{region}}" custom-item="{{customItem}}">
    <view class="picker">
      当前选择：{{region[0]}}，{{region[1]}}，{{region[2]}}
    </view>
  </picker>
</view>
```

```
Page({
  data: {
    array: ['美国', '中国', '巴西', '日本'],
    objectArray: [
      {
        id: 0,
        name: '美国'
      },
      {
        id: 1,
        name: '中国'
      },
      {
        id: 2,
        name: '巴西'
      },
      {
        id: 3,
        name: '日本'
      }
    ],
    index: 0,
    multiArray: [['无脊柱动物', '脊柱动物'], ['扁性动物', '线形动物', '环节动物', '软体动物', '节肢动物'], ['猪肉绦虫', '吸血虫']],
    objectMultiArray: [
      [
        {
          id: 0,
          name: '无脊柱动物'
        },
        {
          id: 1,
          name: '脊柱动物'
        }
      ], [
        {
          id: 0,
          name: '扁性动物'
        },
        {
          id: 1,
          name: '线形动物'
        },
        {
          id: 2,
          name: '环节动物'
        },
        {
          id: 3,
          name: '软体动物'
        },
        {
          id: 4,
          name: '节肢动物'
        }
      ], [
        {
          id: 0,
          name: '猪肉绦虫'
        },
        {
          id: 1,
          name: '吸血虫'
        }
      ]
    ],
    multiIndex: [0, 0, 0],
    date: '2016-09-01',
    time: '12:01',
    region: ['广东省', '广州市', '海珠区'],
    customItem: '全部'
  },
  bindPickerChange: function(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      index: e.detail.value
    })
  },
  bindMultiPickerChange: function (e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      multiIndex: e.detail.value
    })
  },
  bindMultiPickerColumnChange: function (e) {
    console.log('修改的列为', e.detail.column, '，值为', e.detail.value);
    var data = {
      multiArray: this.data.multiArray,
      multiIndex: this.data.multiIndex
    };
    data.multiIndex[e.detail.column] = e.detail.value;
    switch (e.detail.column) {
      case 0:
        switch (data.multiIndex[0]) {
          case 0:
            data.multiArray[1] = ['扁性动物', '线形动物', '环节动物', '软体动物', '节肢动物'];
            data.multiArray[2] = ['猪肉绦虫', '吸血虫'];
            break;
          case 1:
            data.multiArray[1] = ['鱼', '两栖动物', '爬行动物'];
            data.multiArray[2] = ['鲫鱼', '带鱼'];
            break;
        }
        data.multiIndex[1] = 0;
        data.multiIndex[2] = 0;
        break;
      case 1:
        switch (data.multiIndex[0]) {
          case 0:
            switch (data.multiIndex[1]) {
              case 0:
                data.multiArray[2] = ['猪肉绦虫', '吸血虫'];
                break;
              case 1:
                data.multiArray[2] = ['蛔虫'];
                break;
              case 2:
                data.multiArray[2] = ['蚂蚁', '蚂蟥'];
                break;
              case 3:
                data.multiArray[2] = ['河蚌', '蜗牛', '蛞蝓'];
                break;
              case 4:
                data.multiArray[2] = ['昆虫', '甲壳动物', '蛛形动物', '多足动物'];
                break;
            }
            break;
          case 1:
            switch (data.multiIndex[1]) {
              case 0:
                data.multiArray[2] = ['鲫鱼', '带鱼'];
                break;
              case 1:
                data.multiArray[2] = ['青蛙', '娃娃鱼'];
                break;
              case 2:
                data.multiArray[2] = ['蜥蜴', '龟', '壁虎'];
                break;
            }
            break;
        }
        data.multiIndex[2] = 0;
        break;
    }
    console.log(data.multiIndex);
    this.setData(data);
  },
  bindDateChange: function(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      date: e.detail.value
    })
  },
  bindTimeChange: function(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      time: e.detail.value
    })
  },
  bindRegionChange: function (e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      region: e.detail.value
    })
  }
})
```

![](https://res.wx.qq.com/wxdoc/dist/assets/img/picker.d20573a8.png)

Incorrect translation.