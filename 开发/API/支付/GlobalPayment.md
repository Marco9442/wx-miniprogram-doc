# [#](#GlobalPayment) GlobalPayment

全球收银对象 GlobalPayment

## [#](#属性) 属性

### [#](#string-methodKey) string methodKey

初始值为null。当开发者调用 openMethodPicker 用户选中具体支付方式后确定，后续不再改变。

```
const goods = {
  goods_id: `goods_1`,
  goods_name: `拿铁`,
  goods_unit_price: {
    currency: 'SGD',
    total: 10,
  },
  goods_quantity: '1',
  goods_category: '1',
}

const globalPay = async () => {
  if (typeof wx.createGlobalPayment !== 'function') {
    // 基础库版本不支持
    // 方案一、微信支付做兜底
    wx.requestPayment({
      timeStamp: '',
      nonceStr: '',
      package: '',
      signType: '',
      paySign: '',
    })
    // 方案二、引导用户更新
    // 方案三、mp后台设置最低基础库版本 3.7.3
    return
  }

  const payment = wx.createGlobalPayment({ mchRegion: 'SG', isSandbox: true })

  try {
    const pickerResp = await payment.openMethodPicker({
      amount: goods.goods_unit_price,
    })

    console.log(`openMethodPicker resp: `, pickerResp)

    if (pickerResp.methodKey === 'WECHAT_PAY') {
      // 发起微信支付
    } else {
      // 后台接口发起预下单
      const preOrderResp = await preOrder(
        goods.goods_unit_price,
        [goods],
        pickerResp.methodKey
      )

      console.log(`preOrder resp: `, preOrderResp)

      const { payment_id, prepay_info } = preOrderResp

      const requestPaymentResp = await payment.requestGlobalPayment({
        paymentId: payment_id,
        prepayInfo: prepay_info,
      })

      console.log(`requestGlobalPayment resp: `, requestPaymentResp)
    }
  } catch (error) {
    console.log(error)
  }
}
```

## [#](#方法) 方法

### [#](#Promise-GlobalPayment-openMethodPicker-Object-object) [Promise GlobalPayment.openMethodPicker(Object object)](GlobalPayment.openMethodPicker.html)

拉起全球收银的支付方式选择面板。当用户选择支付方式或者关闭选择面板后，返回相应结果。
当用户选定支付方式后，globalPayment上的属性 methodKey 也会更新，后续该对象再次调用将直接失败，不再拉起选择面板。
若用户选择微信支付，请开发者按原微信支付接口 wx.requestPayment 调用完成后续支付流程。
若用户选择TPG的支付方式，流程会等待开发者前往TPG完成预下单后，携带预支付信息和交易单号调用 requestGlobalPayment，若开发者超时未调用，则会提示用户加载超时（超时时间暂定为30s）。
当用户关闭选择面板，即未选择支付方式，开发者后续仍可继续调用接口拉起支付方式选择面板。

### [#](#Promise-GlobalPayment-requestGlobalPayment-Object-object) [Promise GlobalPayment.requestGlobalPayment(Object object)](GlobalPayment.requestGlobalPayment.html)

开发者调用 openMethodPicker 并在返回值 methodKey 中接受到用户选择了TPG的支付方式后，可调用此接口接入TPG的支付流程。
当用户已成功完成当前订单支付后，再次调用该对象的 requestGlobalPayment 会失败。即每次支付都需创建新的 globalPayment 对象重走流程。
仅在 methodKey 为TPG支付类型才能进入全球收银的支付流程，其他情况会失败。
建议在接口返回后，不论成功或失败，均通过 TPG 接口 inquiry-payment 对订单状态进行查询。

### [#](#Promise-GlobalPayment-abort) [Promise GlobalPayment.abort()](GlobalPayment.abort.html)

用户选择TPG的支付方式，界面会进入加载的Toast，等待开发者前往TPG完成预下单后携带预支付信息和交易单号调用 requestGlobalPayment，若开发者在
TPG预下单未成功或出现异常情况，可调用该接口主动终止TPG支付流程，界面加载的Toast将会隐藏，提示用户下单失败。

Incorrect translation.