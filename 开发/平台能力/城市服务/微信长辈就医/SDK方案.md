# [#](#微信长辈就医适老化-SDK-方案) 微信长辈就医适老化 SDK 方案

## [#](#一、接入方案) 一、接入方案

微信提供一套前端的 SDK，接入方只需要类似于接入 VUE 一样提供一个 div 的选择器进行初始化后，在不同的页面步骤中传入对应的协议字段 SDK 就会在对应 div 中渲染出对应状态的适老化后的页面。

页面的样式以及交互全部由 SDK 进行处理，接入方只需要处理页面的逻辑部分（数据接口拉取、事件钩子回调逻辑等）。

## [#](#二、接入代码示例) 二、接入代码示例

```
<!doctype html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
  <meta name="apple-mobile-web-app-capable" content="no">
  <meta name="format-detection" content="telephone=no">
  <link rel="icon" href="//res.wx.qq.com/a/wx_fed/assets/res/NTI4MWU5.ico">
  <link rel="dns-prefetch" href="//res.wx.qq.com">
  <title></title>
  <!-- 【必须】业务方代码，调用长辈就医SDK begin -->
  <script>
  // 开发者必须要完善下面的代码
  window.onElderMedicalSDKReady = function() {
    var elderMedicalSDK = window.elderMedicalSDK
    // 初始化SDK的回调函数
    elderMedicalSDK.init({
      onIndexPageMount: function() {
        // TODO: 从后台获取并设置院区的数据
        var branchList = []
        // 封装Promise给医院使用，可以组合一些异步的请求
        // https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise
        function getBranchList() {
            return new elderMedicalSDK.Promise(function(resolve, reject) {
              setTimeout(function() {
                resolve(branchList)
              }, 500)
        }
        getBranchList().then(function(branchList) {
          elderMedicalSDK.setBranchList({
            branchList: branchList,
            errcode: 0,
            errmsg: ''
          })
        })
      },
      // 选择院区点击
      onNoticePageMount: function(branch) {
        // 从后台获取就医须知的通知，并通过下面的函数设置
        elderMedicalSDK.setNotice({
          notice: '',
          errmsg: '',
          errcode: 0
        })
      },
      // 就医须知确认点击
      onDepartmentPageMount: function() {
        // TODO: 从后台获取就医科室，并通过下面的函数设置
        var regDept = []
        elderMedicalSDK.setDepartmentList({
          departmentList: regDept,
          errcode: 0,
          errmsg: ''
        })
      },
      // 选择科室点击
      onDoctorPageMount: function(dept) {
        // TODO: 从后台获取就医科室，并通过下面的函数设置
        var dateList = []
        elderMedicalSDK.setDoctorDateList({          dateList: dateList,
          errmsg: '',
          errcode: 0
        })
      },
      // 选择医生点击
      onPeriodPageMount: function(doctor) {
        // TODO: 从后台获取到该医生的某天的挂号的时间点，并通过下面的函数设置
        elderMedicalSDK.setDoctorTimePointInfo({
          doctorInfo: {},
          amList: [],
          pmList: [],
          errcode: 0,
          errmsg: ''
        })
      },
      onPayPageMount: function(payPageObj) {
        // TODO: 获取挂号的详情信息，比如就诊人等
      },
      onPayOrder: function(payOrder) {
        // TODO: 下单挂号并且跳转到支付的页面
      },
      onCertPayOrder: function(payOrder) {
        // TODO: 点击医保支付选项
      },
      onCancelOrder: function(payOrder) {
        // TODO: 点击退号按钮触发
      },
      // ...
    })
    // 判断下sdk是否是新版
    if (elderMedicalSDK.setOptions) {
      elderMedicalSDK.setOptions({
        showCancelOrder: false, // 挂号详情页面，是否显示取消挂号，默认是true表示显示
        notice: {
          checkedBgColor: 'red', // 就医须知-勾选框颜色
          btnBgColor: 'red' // 就医须知-按钮背景色
        },
        chooseDoctor: {
          chooseDateBgColor: 'red', // 选择医生-当前日期背景色
          recentTagColor: 'blue', // 选择医生-最近就诊字体颜色
          chooseDateColor: 'red', // 选择医生-日期有号文字颜色
          canRegColor: 'green', // 选择医生-剩余号数量颜色
          chooseDateColor: 'blue', // 选择医生-已满颜色
        },
        choosePeriod: {
          color: 'red', // 选择就诊时段-文字颜色
        },
        payDetail: {
          btnBgColor: 'red' // 确认挂号-按钮背景色
        }
      })
    }

  }
  </script>
  <!-- 【必须】业务方代码，调用长辈就医SDK end -->

  <!-- 【必须】引用长辈就医的SDK begin -->
  <script defer="defer" src="https://wximg.qq.com/cityservices/insuranceres/eldermedical/js/0.2.4/elder-medical-sdk-0.2.4.js"></script>
    <!-- 【必须】引用长辈就医的SDK end -->
</head>

<body>
  <!-- 【必须】长辈就医的SDK 会注入到此DOM结构 begin -->
  <div id="app"></div>
  <!-- 【必须】长辈就医的SDK 会注入到此DOM结构 end -->
</body>
</html>
```

## [#](#三、流程-SDK-协议介绍) 三、流程 & SDK 协议介绍

### [#](#_3-1-挂号流程) 3.1 挂号流程

#### [#](#_3-1-1-选择院区) 3.1.1 选择院区

页面预览

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrsrMFI2lOGshN7VCoB7K6NegMHTeZ233zGLMTjGBr9LQsZmIRGkY7zsHNXnP9WLYyQ)

该页面的数据通过 `elderMedicalSDK.setBranchList(param)` 设置（在 onMount 里面调用），参数 `param` 是 `Object` 对象，其定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| branchList | 所有的院区列表 | Array[BranchItem] | 是 | BranchItem 见下表 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

BranchItem 定义：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| name | 院区名称 | String | 是 |  |
| address | 院区地址 | String | 是 |  |
| ybCode | 院区代码 | String | 是 | 院区的唯一标识，后面的科室需要根据此字段获取 |
| phone | 院区电话 | String | 否 |  |

选择院区触发 **onNoticePageMount({ybCode})回调函数，会自动进入就医须知页面，BranchItem 的定义参数如上。onNoticePageMount 的实现里面，需要获取就医须知的内容，并通过 elderMedicalSDK.setNotice(param)** 接口来设置显示在页面

#### [#](#_3-1-2-就医须知) 3.1.2 就医须知

页面预览

![](https://res.wx.qq.com/op_res/VqkJnzDutXCMcLjHRG5G62gnlW1OGM1SbmL2fbqHiLBYZPatD5aPTE4qpPO7SR-QIdVYaepcjckLa9I-8DcLPw)

`elderMedicalSDK.setNotice(param)` 函数 param 的定义如下：

| 参数名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| notice | 就医须知内容 | String | 是 |  |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

`onDepartmentPageMount` 回调里面，需要通过后台获取下一步需要的科室信息，然后通过 `elderMedicalSDK.setDepartmentList(deptList)` 设置科室信息

#### [#](#_3-1-3-选择科室) 3.1.3 选择科室

页面预览：

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrsFZnCLXc4JQk5Rj0Qeq2_e9u2-cLI5Bjc_r4ui4AbK8HQX5H_nZq868m1BhsRIa-Q)

`elderMedicalSDK.setDepartmentList(param)` 入参 param 是 Object，其定义：

| 字段名 | 描述 | 参数类型 | 是否必填 | 备注 |
| --- | --- | --- | --- | --- |
| departmentList | 科室信息 | Array[DepartmentItem] | DepartmentItem 定义见下面 |  |
| showRecent | 是否支持最近就诊的医生 | Boolean | 否 | 默认 true |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

DepartmentItem 定义钩子：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| deptId | 科室唯一 ID | String | 是 |  |
| deptName | 科室名称 | String | 是 |  |
| deptList | 二级科室的列表 | Array[DepartmentItem] | 否 | 如果科室结构是二级的，则通过此字段传入 |

选择科室会触发回调 `onDoctorPageMount(item)`，item 是 Object 对象，包含 `deptId` 和 `deptName` 两个字段。`onDoctorPageMount` 函数内通过后台后去到医生的可挂号的日期列表，然后通过 `elderMedicalSDK.setDoctorDateList(param)` 设置下一步的数据 （进入下面的 3.1.4）

如果是**选择了最近就诊的医生**，则触发回调 `onRecentDoctorPageMount()`，`onRecentDoctorPageMount` 函数内通过后台获取最近就诊的医生列表，然后通过 `elderMedicalSDK.setRecentDoctorList(param)` 设置下一步的数据 （进入下面的步骤1.5）

#### [#](#_3-1-4-选择医生) 3.1.4 选择医生

页面预览

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvriBj5USuP6d7O9vkG_TgE0dmkfv2K8rprEKkt8ujGnYT-d5NZw2jwhE2rdwHyUTuQg)

`elderMedicalSDK.setDoctorDateList(param)` 的入参 param 是 Object 类型，定义如下：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| dateList | 挂号的医生列表 | Array[DateDoctorItem] | 是 | DateDoctorItem 定义如下 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

DateDoctorItem 定义如下

| 参数名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| date | 可挂号的日期 | String | 是 | 格式示例“2022-10-10” |
| doctorList | 该日期下的可挂号医生 | Array[DoctorItem] | 是 | DoctorItem 定义如下 |

DoctorItem 定义如下

| 参数名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorId | 医生唯一 ID | String | 是 |  |
| deptId | 医生所属科室 ID | String | 是 |  |
| deptName | 医生所属科室名字 | String | 是 |  |
| hospSubname | 所属院区的名字 | String | 否 |  |
| ybCode | 所属院区的院区码 | String | 否 |  |
| doctorName | 医生名字 | String | 是 |  |
| gender | 医生性别 | String | 是 | 取值 F 表示女性，M 表示男性 |
| titleId | 医生职称 ID | String | 是 |  |
| titleName | 医生职称 | String | 是 | 示例“主任医师” |
| doctorDesc | 医生描述 | String | 是 |  |
| doctorPhoto | 医生的照片 URL | String | 是 | 是 http 协议的照片链接 |
| regProj | 挂号项目代码 | String | 是 |  |
| regFee | 挂号费用 | String | 是 | 示例“30.00”，单位元 |
| count | 余号数量 | number | 是 | 可挂号的余号数量 |

选择日期会触发 `elderMedicalSDK.onDateClick(param)` 事件，param 参数是 Object，包含 date 字段，格式是 `2022-10-22`，如果有需要拉一些其他数据，比如挂号费，可以在此接口重新拉取并通过 `updateDoctorDateList` 更新某一天的数据，传进来的参数和 `setDoctorDateList` 的参数一样，`updateDoctorDateList` 会和 `setDoctorDateList` 合并。

选择了医生会触发 `elderMedicalSDK.onPeriodPageMount(periodPage)`，参数 `periodPage` 的定义如下：

| 参数名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorId | 医生唯一 ID | String | 是 |  |
| ybCode | 院区唯一 ID | String | 是 |  |
| deptId | 医生所属科室 ID | String | 是 |  |
| regDate | 选中的挂号的日期 | String | 是 | 示例“2022-10-22” |
| regProj | 挂号项目代码 | String | 是 |  |
| titleId | 医生职称 ID | String | 是 |  |

在 `onPeriodPageMount` 该函数内需要后台获取该医生的对应日期的就诊时段，并通过接口 `elderMedicalSDK.setDoctorTimePointInfo(timePointInfo)` 来显示下面的内容

#### [#](#_3-1-5-选择最近就诊的医生) 3.1.5 选择最近就诊的医生

页面预览

![](https://res.wx.qq.com/op_res/UhwTHK44oSpVoY7gO5Ajo4itZ8UTVCV4Gl6j2Ni4o9Tk2mdThm29uOYnDAs-s92VOgZu9rNNeXsBLBgZfieFDw)

选择最近就诊的医生是先选择医生，再选择日期，所以触发的事件和选择医生的流程会有所区别，此页面通过 `elderMedicalSDK.setRecentDoctorList(param)` 设置医生数据，param 的定义如下

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorList | 挂号的医生列表 | Array[DoctorItem] | 是 | DoctorItem 定义在选择医生章节 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

点击医生会弹起选择日期的半屏弹窗，同时会触发事件 `onRecentDoctorClick(param)`, `param` 是 `DoctorItem` 对象，在该事件获取该医生的就诊的日期，然后通过 `elderMedicalSDK.setRecentDoctorDateList(param)` 设置排班日期，`param` 是 `Object`，定义如下：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| dateList | 日期列表 | Array[DateItem] | 是 | 只需要传 date、count 两个字段 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

半屏弹窗选择了日期之后，并进入选择时间的页面，同时会触发 `onPeriodPageMount(param)` 函数，param 是 Object，其定义如下：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorId | 医生唯一 ID | String | 是 |  |
| ybCode | 院区唯一 ID | String | 是 |  |
| deptId | 医生所属科室 ID | String | 是 |  |
| regDate | 选中的挂号的日期 | String | 是 |  |
| regProj | 挂号项目代码 | String | 是 |  |
| titleId | 医生职称 ID | String | 是 |  |

#### [#](#_3-1-6-选择时间) 3.1.6 选择时间

页面预览如下，通过接口 `elderMedicalSDK.setDoctorTimePointInfo(timePointInfo)` 来设置下面的显示的内容

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrmJDhERI7_svPVGuxjxuh0lGHMeoLRAD07CXzsnOQKCpj3CTyDxc3jnQFhct_Vltrg)

`elderMedicalSDK.setDoctorTimePointInfo(param)` 的入参 `param` 是 `Object` 类型，定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorInfo | 医生的详细信息 | DoctorItem | 是 | DoctorItem 定义见上面 |
| list | 各个时间段可挂号的时段列表 | Array[TimePointInfo] | 是 | TimePointInfo 定义如下 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

`TimePointInfo` 定义如下：

| 参数名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| pointId | 该时段的唯一 ID | String | 否 |  |
| beginTime | 该时段开始时间 | String | 是 | 示例“08:00” |
| endTime | 该时段结束时间 | String | 是 | 示例“08:30” |
| timeType | 时段的类型 | String | 是 | 在挂号的回调会带回去，例如 am、pm 之类的，由医院定义 |
| timeTypeWording | 该时段的显示文案 | String | 是 | 显示在页面的文案，例如上午、下午、全天之类的，由医院定义 |
| leaveCount | 该时段余号数量 | number | 是 |  |

选择之后会自动跳转到下面的页面，触发事件**onPayPageMount(param)**，param 是 Object，其定义如下

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| pointId | 该时段的唯一 ID | String | 否 | 在点击某挂号时段的时候带过来 |
| doctorId | 医生唯一 ID | String | 是 |  |
| ybCode | 院区唯一 ID | String | 是 |  |
| deptId | 医生所属科室 ID | String | 是 |  |
| regDate | 选中的挂号的日期 | String | 是 |  |
| regProj | 挂号项目代码 | String | 是 |  |
| titleId | 医生职称 ID | String | 是 |  |
| timePointBegin | 就诊的开始时段 | String | 是 | 示例“08:30” |
| timePointEnd | 就诊的结束时段 | String | 是 | 示例“09:00” |
| timeType | 就诊时段的类型 | String | 是 | 在挂号的回调 onPayOrder 会带回去，例如 am、pm 之类的，由医院定义 |

在 `onPayPageMount` 需要通过接口 `setOrderPayInfo` 设置下面的挂号信息确认页面的信息

#### [#](#_3-1-7-挂号信息确认) 3.1.7 挂号信息确认

页面示例

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrpK6DmmSehLytO41XMj2rnE-0hldpI3U0UQX5IslYSwDaqZITmXK_1yak5hbi29wQg)

页面的信息需要通过 `elderMedicalSDK.setOrderPayInfo(param)` 接口的参数 param 是 Object 对象，其定义如下

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| orderInfo | 订单详情 | OrderPayInfo | 是 | OrderPayInfo 定义如下 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

OrderPayInfo 类型定义：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| deptId | 科室 ID | String | 否 | 用于上报 |
| deptName | 科室名称 | String | 是 |  |
| doctorId | 医生 ID | String | 否 | 用于上报 |
| doctorName | 医生名称 | String | 是 |  |
| fee | 支付金额 | String | 是 | 例如“0.1” |
| ybCode | 院区 ID | String | 否 | 用于上报 |
| hospSubname | 就诊分院区名称 | String | 是 |  |
| orderId | 订单 ID | String | 否 |  |
| orderStatus | 订单状态 | Number | 是 | 取值如下：10 - 挂号待支付，11 - 挂号失败有退款，12 - 挂号异常，13 - 挂号处理中，20 / 30 - 挂号成功 |
| orderNoPay | 是否支持挂号无需支付 | Boolean | 否 | 为 true 时点击确认不会拉起支付选择弹窗，会直接触发 `onPayOrder` 事件，此时再将 orderStatus 设置为 20/30 即可挂号成功 |
| rollbackStatus | 取消订单状态 | Number | 否 | 默认为 0 取值如下：0 - 未取消，10 - 已取消订单，退款中，20 - 已取消订单，退款成功，30 - 已取消订单，退款失败 |
| rollbackErrMsg | 退款失败的原因 | String | 否 | rollbackStatus 为 30，此字段返回退款失败的原因 |
| rollbackTime | 取消订单的时间 | String | 否 | 退款时间，取消订单状态下必填，unix 时间戳 |
| rollbackFee | 退款金额 | String | 否 | 退款金额，取消订单状态下必填，例如“0.1” |
| payType | 支付类型 | Number | 是 | 1 表示自费、2 表示医保 |
| patName | 就诊人姓名 | String | 是 |  |
| regDate | 就诊日期 | String | 是 | 例如"2022-10-19" |
| cardNumber | 就诊凭条卡号 | String | 是 | 在支付成功之后再设置 |
| timePointBegin | 就诊时段开始时间 | String | 是 | 示例“08:30” |
| timePointEnd | 就诊时段结束时间 | String | 是 | 示例“09:30” |
| visitingSeq | 就诊序号 | String | 是 |  |
| visitingRoomLoc | 诊室位置 | String | 是 |  |
| outpatientNum | 门诊流水号 | String | 是 |  |
| supportCertPay | 是否支持医保支付 | Boolean | 否 | 默认是 true |
| identityTypeList | 身份类型 | Array | 否 | IdentityType 是包含 text 和 value 的对象 |

点击“支付”-“自费支付”触发 `elderMedicalSDK.onPayOrder(orderReq)`，orderReq 的定义如下（和上面的 `onPayPageMount` 事件的参数一样）：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| doctorId | 医生唯一 ID | String | 是 |  |
| ybCode | 院区唯一 ID | String | 是 |  |
| deptId | 医生所属科室 ID | String | 是 |  |
| regDate | 选中的挂号的日期 | String | 是 |  |
| regProj | 挂号项目代码 | String | 是 |  |
| titleId | 医生职称 ID | String | 是 |  |
| timePointBegin | 就诊的开始时段 | String | 是 | 示例“08:30” |
| timePointEnd | 就诊的结束时段 | String | 是 | 示例“09:00” |
| timeType | 就诊时段的类型 | String | 是 | 在挂号的回调 onPayOrder 会带回去，例如 am、pm 之类的，由医院定义 |
| identityType | 选中的身份类型 | IdentityType | 否 | IdentityType 是包含 text 和 value 的对象 |

开发者在此回调调起微信支付，用户支付完之后，开发者通过**setOrderPayInfo**设置支付的结果。如果报错了，则调用 `elderMedicalSDK.setOrderErrorInfo(res)` 来设置报错的信息，res 包含 type、errcode 和 errmsg 三个字段。

`elderMedicalSDK.setOrderErrorInfo(res)` 的参数 res 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| type | 错误的类型 | String | 是 | 取值为"pay"、"certpay"、"cancel"，分别表示挂号、医保支付、取消挂号三个场景 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

`elderMedicalSDK.setOrderPayInfo(param)` 接口的参数 param 是 Object 对象，其定义见上面的介绍。

点击“支付”-“医保支付”触发 `elderMedicalSDK.onCertPayOrder(payOrder)`，此回调里面生成医保支付的订单，并跳转到医保支付的 H5 页面去支付。如果报错了，则调用 `elderMedicalSDK.setOrderErrorInfo(res)` 来设置报错的信息，res 包含 errcode 和 errmsg 两个字段。

#### [#](#_3-1-8-退号) 3.1.8 退号

交互示例

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrp49hTWjv3kZ7ZLvPdTfIxrO_pMvI7-B6i730UmTtWy_doTTnOUIqPeMU7F6aD-pKw)

点击底部的取消挂号，会触发事件 `onCancelOrder(payOrder)`，成功后开发者通过 `setOrderPayInfo` 设置支付的结果。如果报错了，则调用 `elderMedicalSDK.setOrderErrorInfo(res)` 来设置报错的信息，res 包含 type、errcode 和 errmsg 三个字段。注意，这个号是已支付的号，必须要给用户退款，退款后 rollbackStatus 应该设置为 30。

#### [#](#_3-1-9-挂号记录) 3.1.9 挂号记录

交互示例

![](https://res.wx.qq.com/op_res/U3kal7FClvMCcrW_glp4c924fdQzei58rwgc7KxomrZ06XGGW8SCkQofKihEn_SYBBg4nPbmfGOVn6szyD8bUA)

页面的链接是 `https://hostname/path?query#/record-list`

进入页面触发事件 `onRecordListPageMount({orderType})`，`orderType` 的值 0 表示挂号记录页面，1 表示缴费记录页面，由于挂号记录和缴费记录页面 UI 类似，所以用了同一套事件，通过 `orderType` 参数区分。

在该事件获取到数据后，通过接口 `setRecordList(param)` 设置数据，参数是 `Object` 对象，具体定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| list | 订单详情 | Array[Record] | 是 | Record 定义如下 |
| hasNext | 是否有下一页 | boolean | 否 | 为 true 表示有下一页数据，滚到底部会触发分页事件 onRecordListNextPage，没有分页可忽略此字段 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

`Record` 定义：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| orderId | 订单 id | string | 是 | 挂号记录和缴费记录页面均需要 |
| patName | 就诊人 | string | 是 | 挂号记录和缴费记录页面均需要 |
| doctorName | 医生名称 | string | 是 |  |
| deptName | 科室名称 | string | 是 |  |
| appointpmentTime | 预约时间 | string | 是 |  |
| orderStatus | 订单状态 | number | 是 | orderType 为 0 时「10-挂号待支付；11-挂号失败·有退款；12-挂号异常；13-挂号处理中；20 或 30-支付成功」orderType 为 1 时「10-待缴费；11-缴费失败·有退款；12-缴费异常；20 或 30-缴费成功」 |
| rollbackStatus | 取消状态 | number | 否 | 默认为 0 表示挂号成功 |
| rollbackFee | 取消金额 | string | 否 | rollbackStatus 非 0 有效 |
| payTime | 缴费时间 | string | 否 | 缴费时间，缴费记录页面有效 |
| payFee | 缴费金额 | number | 否 | 缴费的总金额，缴费记录页面有效，单位是分 |

如果 hasNext 为 true，用户滚到底部会触发事件 `onRecordListNextPage`，参数和 `onRecordListPageMount` 一样，在该事件通过 `concatRecordList(param)` 设置下一页的数据，参数和 `setRecordList` 一样。

用户点击某一项会进入挂号详情页面（如果是缴费页面进入缴费详情），即触发事件 `onPayPageMount`（缴费详情触发 `onPayFeePageMount`），该事件只会带 orderId 参数，请参考该事件用法。另外，如果需要跳转到医院原有的挂号详情页面，可以在该事件里面直接跳转即可。

### [#](#_3-2-缴费流程) 3.2 缴费流程

#### [#](#_3-2-1-待缴费订单) 3.2.1 待缴费订单

![](https://res.wx.qq.com/op_res/U3kal7FClvMCcrW_glp4c5lBlN7b7FNM2s9WX0r14jW1oMd-4GkhoKEWVIeUVYK3lgr6hwCWJybzkeNhFfXOkQ)

页面的链接是 `https://hostname/path?query#/pay-fee-list`

进入页面会触发 `onPayFeeListPageMount()` 事件，进入页面之后，通过 `setPayFeeList(params)` 接口来设置页面数据，params 的数据格式定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| list | 订单详情 | Array[PayFee] | 是 | PayFee 定义如下 |
| hasNext | 是否有下一页 | boolean | 否 | 为 true 表示有下一页数据，滚到底部会触发分页事件 onPayFeeListNextPage，没有分页可忽略此字段 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

PayFee 的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| treatmentType | 门诊类型 | String | 是 |  |
| deptName | 就诊科室 | String | 是 |  |
| doctorName | 医生 | String | 是 |  |
| time | 开单时间 | String | 是 |  |
| orderId | 门诊流水号 | String | 是 | 唯一 ID，点击“去支付”会带到缴费详情页面 |
| unpaidFee | 费用合计 | number | 是 | 单位是元 |

进入页面点击「去支付」，会进入缴费详情页面。

#### [#](#_3-2-2-缴费详情) 3.2.2 缴费详情

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrkdq6FQnnR-M8aHbW7MiBHj1I2LnypjNwG0VBLwu92zHMYQs58ts_xDcFmaAS_muMQ)

从待缴费列表或者缴费记录页面点击缴费项，会进入此页面，如果已缴费完成，则不展示自费支付和医保支付的按钮。

进入页面会触发 `onPayFeeDetailPageMount({orderId})`，`orderId` 是待缴费页面传入的门诊流水号。该页面通过 `setPayFeeDetail(params)` 设置数据，`params` 的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| detail | 订单详情 | PayFeeOrderInfo | 是 | PayFeeOrderInfo 定义如下 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

PayFeeOrderInfo 类型定义：

| 字段名 | 描述 | 类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| orderId | 订单 ID | String | 是 | 门诊缴费流水号 |
| patName | 就诊人姓名 | String | 是 |  |
| visitingTypeName | 就诊类型 | String | 是 | 取值为“自费”、“医保”、“省直医保”、“市直医保”、“其他” |
| deptId | 科室 ID | String | 否 | 用于上报 |
| deptName | 科室名称 | String | 是 |  |
| doctorId | 医生 ID | String | 否 | 用于上报 |
| doctorName | 医生名称 | String | 是 |  |
| fee | 支付总金额 | String | 是 | 例如“0.1” |
| hospName | 院区名称 | String | 是 |  |
| prescribeTime | 就诊日期 | String | 是 | 门诊缴费流水号 |
| orderStatus | 订单状态 | Number | 是 | 取值如下：10 - 待缴费，11 - 缴费失败有退款，12 - 缴费异常，20 / 30 - 缴费成功 |
| payFailMsg | 缴费失败原因 | String | 否 | 在缴费失败的情况下必填 |
| supportCertPay | 是否支持医保支付 | Boolean | 否 | 默认是 true |
| cardNumber | 就诊卡号 | String | 是 | 在 orderStatus 为 20 的时候有效 |
| notice | 温馨提醒 | String | 是 | 在 orderStatus 为 20 的时候有效 |
| bills | 门诊费用 | Array | 否 | 门诊缴费明细 |
| prescriptions | 缴费处方单 | Array | 否 | 和 bills 两个字段二选一，是处方单列表 |

**注意：bills 和 prescriptions 两个字段二选一，如果是按处方单缴费，则传 prescriptions 字段。**

Bill 类型的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| projectName | 缴费项目名称 | String | 是 |  |
| uintPrice | 单价 | number | 是 |  |
| projectAmount | 数量 | String | 是 |  |
| totalPrice | 总金额 | String | 是 | 单位“元” |

Prescription 类型的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| id | 处方单号 | String | 是 |  |
| doctorName | 医生名称 | String | 是 |  |
| time | 开单时间 | String | 是 | 格式化好的时间 |
| deptName | 部门名称 | String | 是 |  |
| totalPrice | 总金额 | String | 是 | 总价，单位“元” |
| projects | 收费项目列表 | Array<FeeProject> | 是 | FeeProject 定义如下 |

FeeProject 类型的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| projectName | 缴费项目名称 | String | 是 |  |
| uintPrice | 单价 | number | 是 |  |
| projectAmount | 数量 | String | 是 | 单位“元” |

点击自费支付，触发事件 `onPayFeeDetailPayOrder(detail)`，`detail` 是 `PayFeeOrderInfo` 类型。点击医保支付，触发事件 `onPayFeeDetailCertPayOrder(detail)`，`detail` 也是 `PayFeeOrderInfo` 类型。

如果是按处方单选择缴费，则事件参数 `detail.prescriptions[0].checked`属性为 true，开发者需要根据此字段计算出用户勾选的总价进行支付。按处方单缴费的交互如下

![](https://res.wx.qq.com/op_res/U3kal7FClvMCcrW_glp4c_OxDCg-jKizizNCSy3uEXJryBRt7vyXO6R43oS8hFH5bjTQpHe2bFlxLiuQIQPsQg)

在这些事件里面，可以下单、拉起微信支付/医保支付等进行支付并把支付结果通过 `updatePayFeeDetail(params)` 更新进来，`params` 的定义同 `setPayFeeDetail`，区别在于 detail 可以只传入修改的字段，比如只传入 `orderStatus`。

如果支付失败，可以通过 `setPayFeeErrorInfo(params)` 来显示报错的弹窗，`params` 的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| errcode | 错误码 | number | 是 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 是 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

#### [#](#_3-2-3-个人中心) 3.2.3 个人中心

![](https://res.wx.qq.com/op_res/NdJ9waGWoBwLBE7Y-ZBAoN8BGBAGIQbN1s7UI363jwYmetTzv8vvDTdZarFNyQLJ2_6BrvQ2Gid7IQhqeZk33g)

页面的链接是 `https://hostname/path?query#/personal-center`

点击挂号记录，会跳转到上面第九节的挂号记录页面，点击缴费记录会跳转到下一节的缴费记录的页面，默认会带页面的 URL 参数跳转过去。

#### [#](#_3-2-4-缴费记录) 3.2.4 缴费记录

![](https://res.wx.qq.com/op_res/U3kal7FClvMCcrW_glp4c09DuB2GeKCio10d8UFv8OoQ2Ou0TCZXQdd4LcKzbQYc2fiHyXcUNWofonxEFDF-oQ)

由于 UI 方面缴费记录和挂号记录类似，所以接口和挂号记录页面类似，只是 `recordType` 取值为 1，另外 `Record` 对象的定义不太一样，只有备注了缴费记录有效或者两者有效的才是此页面需要的字段。另外需要注意，这个页面是已缴费的记录才显示，待缴费的订单在第10节的页面显示。

### [#](#_3-3-报告查询) 3.3 报告查询

#### [#](#_3-3-1-选择报告类型) 3.3.1 选择报告类型

页面的链接是 `https://hostname/path?query#/report-type`

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrg1V6YK_JrD9Usfq3GMn2waLJP0G33SvSNW83gsni2e22GMJi57aVWqdr103UOKCAw)

#### [#](#_3-3-2-已发布报告) 3.3.2 已发布报告

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrvPN1GVRdZXij1m3Fjl0GO9iqWkr-J345vdXxj6YiRUhIR7r_yIu0zmhrFSW13E7QA)

页面的链接是 `https://hostname/path?query#/report-list?type=1`

type 为 1 时表示从检验报告跳转，type 为 2 时表示从检查报告跳转。

进入已发布报告页面会触发 `onReportListPageMount({pageIndex, pageSize, days})` 事件，`pageIndex`和 `pageSize` 是分页参数。days 是当前展示的报告的天数，比如最近一周的 days 是 7。可通过 `setReportList(params)` 接口设置报告的列表数据，params 的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| list | 报告列表 | Array[Report] | 是 | Report 定义如下 |
| hasNext | 是否有下一页 | boolean | 否 | 为 true 表示有下一页数据，滚到底部会触发分页事件 onReportListNextPage，没有分页可忽略此字段 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

Report 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| reportName | 报告名称 | String | 是 | 报告名称 |
| inspectTime | 检查时间 | String | 是 | 时间的格式为 YYYY-MM-DD HH:SS |
| reportId | 报告 ID | String | 是 | 报告唯一 ID，会带到报告详情页面 |
| reportType | 报告类型 | number | 是 | 检验报告取值为 1，检查报告取值为 2，会带到报告详情页面 |

点击上面的查询日期，会触发事件 `onReportDateClick({days, pageIndex, pageSize})`，在此事件里面重新拉一下数据。days 是用户选择的日期，如果选择的是全部，则 days 的值是 0，需要特殊处理一下。

点击下面的报告的某一项，会触发事件 `onReportItemClick(item)`，参数 item 为上面的 Report 对象，如果需要跳转到自己的报告详情页面，可在此事件处理。

#### [#](#_3-3-3-报告详情) 3.3.3 报告详情

![](https://res.wx.qq.com/op_res/U3kal7FClvMCcrW_glp4c8ZWYsPwe3bz4tZLMtGeaVtZ_OitU2LpDeAgWGBW7kSDp17c_c1DELH-ouCokZfaiQ)

进入此页面会触发事件 `onReportDetailPageMount({reportId, reportType})`，reportId 是报告的 id，`reportType` 的定义上面章节有说明。该页面获取报告的详细数据，并通过 `setReportDetail(params)` 接口设置，`params` 的定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| reportDetail | 报告详情信息 | ReportDetail | 是 | ReportDetail 定义如下 |
| errcode | 返回码 | number | 否 | 是否成功，0 表示成功，不填默认表示成功 |
| errmsg | 错误信息 | String | 否 | 当 errcode 为非 0 时候，此字段表示错误信息，前端会显示此错误信息 |

ReportDetail 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| outpatientDetail | 就诊信息 | OutpatientDetail | 是 | OutpatientDetail 定义如下 |
| list | 报告内容 | Array<ReportCheckContent | ReportInspectContent> | 是 | 当值 type 为 1，数组的每一项为 ReportInspectContent，当 type 为 2，数组的每一项为 ReportCheckContent |
| type | 报告类型 | number | 是 | 定义同上面的 reportType。检验报告取值为 1，检查报告取值为 2 |

OutpatientDetail 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| patName | 就诊人 | String | 是 |  |
| deptName | 开方科室 | String | 是 |  |
| doctorName | 开方医生 | String | 是 |  |
| inspectTime | 报告时间 | String | 是 |  |
| reportId | 报告单号 | String | 是 |  |

检验报告的内容 ReportInspectContent 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| itemName | 项目名称 | String | 是 |  |
| refRange | 参考值 | String | 是 |  |
| result | 结果 | String | 是 |  |

检查报告的内容 ReportCheckContent 定义如下：

| 字段名 | 参数描述 | 参数类型 | 必填 | 备注 |
| --- | --- | --- | --- | --- |
| checkPart | 检查部位 | String | 是 |  |
| checkSituation | 检查所见 | String | 是 |  |
| option | 诊断意见 | String | 是 |  |
| advice | 医嘱 | String | 是 |  |
| checkMethod | 检查方法 | String | 是 |  |

### [#](#_3-4-自定义页面颜色及按钮展示) 3.4 自定义页面颜色及按钮展示

通过 `elderMedicalSDK.setOptions(options)`，可以设置页面的一些选项，例如页面的一些颜色，挂号详情页面，是否显示取消挂号的按钮，参数 options 的结构可参考：

```
if (elderMedicalSDK.setOptions) {
  elderMedicalSDK.setOptions({
    autoJumpReportDetail: false, // 报告列表页面，是否自动跳转报告详情页面
    showCancelOrder: false, // 挂号详情页面，是否显示取消挂号，默认是true表示显示
    notice: {
      checkedBgColor: 'red', // 就医须知-勾选框颜色
      btnBgColor: 'red' // 就医须知-按钮背景色
    },
    chooseDoctor: {
      chooseDateBgColor: 'red', // 选择医生-当前日期背景色
      recentTagColor: 'blue', // 选择医生-最近就诊字体颜色
      chooseDateColor: 'red', // 选择医生-日期有号文字颜色
      canRegColor: 'green', // 选择医生-剩余号数量颜色
      chooseDateColor: 'blue', // 选择医生-已满颜色
    },
    choosePeriod: {
      color: 'red', // 选择就诊时段-文字颜色
    },
    payDetail: {
      btnBgColor: 'red' // 确认挂号-按钮背景色
    },
    ignoreNoticePage: false, // 是否跳过就医须知页面
  })
}
```

具体字段可参考如下截图

![](https://res.wx.qq.com/op_res/UhwTHK44oSpVoY7gO5Ajo4mF-lR3AWmtdX-5nMEJyvJ9mFQ5-nKXiBt7ldWNVRTtKv33JBHjTsc-m_35amlO_w) ![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrivNOzbxSk_pzpP_HLEaHmGtdSV40dRYmaMD5agXifdNwvrtHGHVZm6TJxPgEvjrIw) ![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrr_WnGtpVshK8W4d1g2lAtwGf8op66UB3dmtYGkqHi7rm0nVbgITAkuK6gPU-_wLVQ) ![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrlPCYfk74xupF8HXzTNYrmEZf4sr3Aj5G6iXr48xpWIx3CLM2CfwpnD_zh46J1DzUw)

### [#](#_3-5-设置页面-loading-状态) 3.5 设置页面 loading 状态

从版本 0.1.8 开始支持

页面的 loading 默认是 1s 消失，通过 `elderMedicalSDK.setOptions({manualHideLoading:{}})`，可以手动设置页面的 `loading` 状态，目前支持报告列表页面：

```
if (elderMedicalSDK.setOptions) {
  elderMedicalSDK.setOptions({
    manualHideLoading: {
      reportList: true, // 报告列表页面，手动隐藏loading
    }
  })
}
```

然后可在 onReportListPageMount 回调里面，通过 `elderMedicalSDK.setHideLoading()` 隐藏 loading

### [#](#_3-6-弹窗样式) 3.6 弹窗样式

从版本 0.2.0 开始支持

#### [#](#_3-6-1-基础弹窗) 3.6.1 基础弹窗

```
elderMedicalSDK.setDialogInfo({
  show: true,
  title: '标题',
  content: '内容',
  showCancel: false, // 是否显示取消按钮
  cancelText: '取消',
  confirmText: '确定',
  cancel: function() { // 点击取消按钮触发
    console.log('dialogInfo dialog cancel')
  },
  confirm: function() { // 点击确定按钮触发
    console.log('dialogInfo dialog confirm')
  }
})
```

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrl62HYUlK2BSJY5sXJYVvxvZOEiB07iuUyyFwJ96ziegbxLLrvQyuXVkef4rQKAbAQ)

#### [#](#_3-6-2-半屏弹窗) 3.6.2 半屏弹窗

```
elderMedicalSDK.setHalfDialogInfo({
  show: false,
  title: '标题',
  content: '内容',

  showCancel: false,
  cancelText: '取消',
  confirmText: '我知道了',
  confirmColor: 'red', // 确定按钮的文本色
  checkedColor: 'red', // 勾选框的颜色
  confirmBackgroundColor: 'red', // 确定按钮的背景色
  close: function() { // 关闭半屏弹窗触发
    console.log('HalfDialogInfo dialog close')
  },
  cancel: function() { // 点击取消按钮触发
    console.log('HalfDialogInfo dialog cancel')
  },
  confirm: function() { // 点击确定按钮触发
    console.log('HalfDialogInfo dialog confirm')
  }
})
```

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrtFQAl2StVbIcF-LuoVzfHIks_jGGyyMxR5QwOCaOu5zB6BRKgvm-j4rq-HZLDEysA)

### [#](#_3-7-关于-JSSDK) 3.7 关于 JSSDK

开发者需要调用 wx.config 来初始化 JSSDK 并通过 `elderMedicalSDK.jssdkReady()` 来通知 SDK 已 ready。初始化的参数 jsapiList 需要传接口 `hideAllNonBaseMenuItem`，在 SDK 里面需要调用此接口。例如：

```
wx.config({
    jsapiList: ["hideAllNonBaseMenuItem"],
    // ...
})
wx.ready(function() {
    elderMedicalSDK.jssdkReady()
})
```

## [#](#四、H5-整体方案示图) 四、H5 整体方案示图

![](https://res.wx.qq.com/op_res/874M7PpKfDZYCGAmxSGvrvwN007aIVPm8LV8IZwI1F7E3cX1rQyAzyxHAKWe7A6_jNoKjb3UVYOMHYa2GYTmPA)

Incorrect translation.