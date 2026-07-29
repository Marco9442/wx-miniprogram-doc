## [#](#公众号使用云开发-极简示例-HTML) 公众号使用云开发 / 极简示例 / HTML

包含了登录逻辑、访问云资源、使用 JSSDK 的示例：

真机调试时需要注意 [第三方 Cookie 使用限制](../third-party-cookie)

```
<html>
  <head>
    <title>云开发 Web 能力极简示例</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1, maximum-scale=1">
    <script>
      window.onerror = e => {
        alert('window error ' + e)
      }
    </script>
    <!-- 调试用的移动端 console -->
    <script src="https://cdn.jsdelivr.net/npm/eruda"></script>
    <script>eruda.init();</script>
    <!-- 公众号 JSSDK -->
    <script src="https://res.wx.qq.com/open/js/jweixin-1.6.0.js"></script>
    <!-- 云开发 Web SDK -->
    <script src="https://res.wx.qq.com/open/js/cloudbase/1.1.0/cloud.js"></script>
    <script>
      // 公众号基本信息：请修改下列字段使用本示例
      const WX_RESOURCE_APPID = 'wxaaaaaaaaaaaaaaaa' /*         资源方 AppID */
      const WX_RESOURCE_ENVID = 'cloud1' /*                     资源方云开发环境 ID */
      const WX_OFFICIAL_ACCOUNT_APPID = 'wxaaaaaaaaaaaaaaaa'/*  公众号 AppID */
      const WX_AUTH_TYPE = 'snsapi_base' /*                     选择需要的授权方式，snsapi_base 或 snsapi_userinfo */
      const WX_REDIRECT_URI = 'https://example.com/' /*         回调 URL */

      // 示例配置
      const isPersistLoginInfo = false // 是否需要保留登录态信息到 window 中，只有 snsapi_userinfo 方式需要
      
      if (window.wx) {
        window.cloud = wx.cloud
      }

      var urlSearch = new URLSearchParams(location.search)
      var accessToken = urlSearch.get('access_token')
      var refreshToken = urlSearch.get('refresh_token')

      /**
       * 检查/发起登录
       * 1. 函数会检查当前是否已登录（checkLogin）
       * 2. 如果未登录，会 10s 后自动发起登录（startLogin）
       * 3. 如果已登录，会初始化实例，使用指定的微信云开发资源
       */
      window.doLogin = async () => {
        try {
          const checkLoginOptions = {
            provider: 'OfficialAccount',
            appid: WX_OFFICIAL_ACCOUNT_APPID,
          }

          if (urlSearch.get('oauthredirect') === '1') {
            checkLoginOptions.accessToken = accessToken
            checkLoginOptions.refreshToken = refreshToken
          }

          console.log(`checkLogin options: `, checkLoginOptions)
          const result = await cloud.checkLogin(checkLoginOptions)
          console.log(`checkLogin result: `, result)
          if (isPersistLoginInfo) {
            window.checkLoginRes = result
          }
          if (result.errCode === 0 && result.loggedIn) {
            console.log(`checkLogin success`)

            const instance = window.instance = new cloud.Cloud({
              appid: WX_OFFICIAL_ACCOUNT_APPID,
              resourceAppid: WX_RESOURCE_APPID,
              resourceEnv: WX_RESOURCE_ENVID,
            })
            const initResult = await instance.init()
            
            console.log(`instance inited`, initResult)
            console.log(`can use cloud instance to access resource now !`)

            const els = [...document.getElementsByClassName('display-none')]
            els.forEach(el => el.classList.remove('display-none'))
          } else {
            console.log(`checkLogin with sdk errCode ${result.errCode} errMsg ${result.errMsg}, will start oauth in 10s`)

            setTimeout(() => {
              try {
                cloud.startLogin({
                  provider: 'OfficialAccount',
                  appid: WX_OFFICIAL_ACCOUNT_APPID,
                  scope: WX_AUTH_TYPE,
                  redirectUri: WX_REDIRECT_URI,
                })
              } catch (e) {
                console.error(`startLogin fail: ${e}`)
                console.warn(`will start OfficialAccount OAuth login in 10s.`)
              }
            }, 10000)
          }
        } catch (e) {
          console.error(e)
        }
      }

      /**
       * 获取用户信息的示例
       * 1. 需在登录后调用
       * 2. 网页授权的方式需为 snsapi_userinfo
       * 3. 从 checkLogin 结果中获取用户信息 cloudID（已在 doLogin 函数中先暂存到全局变量 checkLoginRes）
       * 4. 调用云函数换取 cloudID 信息
       */
      window.getUserInfo = async () => {
        if (!checkLoginRes) throw new Error('获取登录信息失败，请确认授权方式以及是否保存了登录信息')
        try {
          if (checkLoginRes.cloudID) {
            const res = await instance.callFunction({
              name: 'echo',
              data: {
                userInfoData: new instance.CloudID(checkLoginRes.cloudID),
              },
            })

            const cloudData = res.result.userInfoData
            if (cloudData.data) {
              const userInfoImg = document.querySelector('#userinfo .avatar')
              userInfoImg.src = cloudData.data.avatarUrl

              const userInfoName = document.querySelector('#userinfo .name')
              userInfoName.innerText = cloudData.data.nickName

              const userInfoOpenID = document.querySelector('#userinfo .openid')
              userInfoOpenID.innerText = cloudData.data.openId

              const userInfoDiv = document.getElementById('userinfo')
              userInfoDiv.style.cssText = ''
            } else {
              console.warn(`cloudID data error: `, cloudData)
              alert(`cloudID 信息获取错误，请查看调试器报错信息`)
            }
          } else {
            alert(`找不到 cloudID，请确认网页授权方式为 snsnapi_userinfo`)
          }
        } catch (e) {
          console.error(`error: ${e} ${e.stack}`)
        }
      }

      /**
       * 使用 JSSDK 的示例
       * 1. 需在登录后调用
       * 2. 首先会使用云开发 web sdk 提供的 getJSSDKSignature 方法获取网页所需的 wx.config 的签名
       * 3. 调用 wx.config
       * 4. wx.config 成功之后尝试调用选择图片和获取地理位置作为示例
       */
      window.useJSSDK = async () => {
        try {
          const instance = window.instance

          console.log(`url: ${location.href}`)
          const res = await instance.getJSSDKSignature({
            url: location.href,
          })
          console.log(`jssdk sign res: ${JSON.stringify(res)}`)

          const configOpt = {
            debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
            appId: WX_OFFICIAL_ACCOUNT_APPID, // 必填，公众号的唯一标识
            timestamp: res.timestamp + '', // 必填，生成签名的时间戳
            nonceStr: res.nonceStr, // 必填，生成签名的随机串
            signature: res.signature,// 必填，签名
            jsApiList: ['chooseImage', 'getLocation'] // 必填，需要使用的JS接口列表
          }

          console.log(`wx.config opt ${JSON.stringify(configOpt)}`)
          wx.config(configOpt)
          console.log(`wx.config executed`)

          wx.ready(() => {
            console.log(`wx.ready triggered`)

            setTimeout(() => {
              wx.chooseImage({
                count: 5, 
                sizeType: ['original', 'compressed'], 
                sourceType: ['album', 'camera'],
                success : function(res) {
                  alert('已选择 ' + res.localIds.length + ' 张图片');
                },
                fail: function(err) {
                  console.error(`chooseImage fail ${JSON.stringify(err)}`)
                },
              })

              wx.getLocation({
                type: 'wgs84', // 默认为wgs84的gps坐标，如果要返回直接给openLocation用的火星坐标，可传入'gcj02'
                success: function (res) {
                  var latitude = res.latitude; // 纬度，浮点数，范围为90 ~ -90
                  var longitude = res.longitude; // 经度，浮点数，范围为180 ~ -180。
                  var speed = res.speed; // 速度，以米/每秒计
                  var accuracy = res.accuracy; // 位置精度
                  console.log(`getLocation ${JSON.stringify(res)}`)
                },
                fail: err => {
                  console.log(`getLocation fail ${JSON.stringify(err)}`)
                }
              });
            }, 2000)
          })

          wx.error(err => {
            console.error(`wx.error ${JSON.stringify(err)}`)
          })

        } catch (e) {
          console.error(`error: ${e} ${e.stack}`)
        } 
      }

      /**
       * 带登录态访问资源方的云开发资源，调用方式见文档，与小程序一致
       */
      window.accessResource = async () => {
        try {
          const c = window.instance
          await runWithLogs(() => c.database().collection('test').where({}).get(), `start db`, `db res`)
        } catch (e) {
          console.error('logs', `error: ${e}`)
        }
      }

      /**
       * 未登录模式下访问微信云开发的资源示例
       */
      window.accessResourceWithoutAuth = async () => {
        var c = new cloud.Cloud({
          identityless: true, // 表示是未登录模式
          resourceAppid: WX_RESOURCE_APPID,
          resourceEnv: WX_RESOURCE_ENVID,
        })

        await c.init()

        await runWithLogs(() => c.database().collection('test').where({}).get(), `start db`, `db res`)
      }

      window.runWithLogs = async (fn, before, after) => {
        try {
          console.log(before)
          const res = await fn()
          console.log(`${after}: ${JSON.stringify(res)}`)
        } catch (e) {
          console.error(`error: ${e}`)
        }
      }
    </script>
    <style>
      .display-none {
        display: none;
      }

      .userinfo {
        display: flex;
        flex-direction: column;
        align-items: center;
      }

      .userinfo .avatar {
        width: max-content;
        box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1), 0 0 0 2px rgb(255,255,255), 0.3em 0.3em 1em rgba(0,0,0,0.3);
      }

      .userinfo .name {
        border-bottom: 2px solid gray;
        padding: 0 5px 5px 5px;
      }
    </style>
  </head>
  <body>
    <h2>云开发 Web 能力极简示例</h2>
    <p>请注意按照文档说明配置好，主要包括：</p>
    <p>1. 配置好公众号的授权回调域名及 JS 安全域名</p>
    <p>2. 配置好云开发授权关系（小程序授权云开发资源给公众号）</p>
    <p>3. 将代码中相应需要填入小程序/公众号 AppID 的地方进行相应改动</p>
    <p>4. 编写部署好微信云开发对应云环境的 cloudbase_auth 云函数和 echo 云函数</p>
    <p>5. 准备好后，页面加载后先点击登录，登录后再执行访问资源等其他操作，日志可在调试器查看</p>
    <div id="userinfo" class="userinfo" style="display: none">
      <img class="avatar" />
      <p class="name"></p>
      <p class="openid"></p>
    </div>
    <p><a href="javascript:;" onclick="doLogin()">登录（云开发公众号网页授权）</a></p>
    <p><a href="javascript:;" class="display-none" onclick="getUserInfo()">获取用户信息</a></p>
    <p><a href="javascript:;" class="display-none" onclick="useJSSDK()">使用 JSSDK</a></p>
    <p><a href="javascript:;" class="display-none" onclick="accessResource()">访问云资源</a></p>
    <p><a href="javascript:;" class="display-none" onclick="accessResourceWithoutAuth()">未登录模式下访问云资源</a></p>
  </body>
</html>
```

Incorrect translation.