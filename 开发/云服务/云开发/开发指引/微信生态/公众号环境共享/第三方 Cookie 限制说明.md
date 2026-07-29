# [#](#第三方-Cookie-限制说明) 第三方 Cookie 限制说明

在使用公众号访问云开发时，登录态信息需要以第三方 Cookie 的形式保存到浏览器中。

由于 iOS 14 开始不再允许设置第三方 Cookie，非「未登录模式」的云开发请求，需要开发者配置自己域名下的云开发转发地址，将登录鉴权和云开发请求代理至第一方域名下（即 `__wx__` 开头的地址）

**推荐使用 [静态网站托管](../staticstorage/introduction) 绑定的默认域名，不需要手动配置转发规则和运维服务器，即可使用所有公众号访问云开发功能。**

## [#](#SDK-版本需求) SDK 版本需求

从 Cloud SDK 1.2.0 开始，默认采用第一方 Cookie 登录鉴权。需要替换 HTML 模板中引入的对应脚本。

```
<script src="https://res.wx.qq.com/open/js/cloudbase/1.2.0/cloud.js"></script>
```

## [#](#服务器如何配置转发) 服务器如何配置转发

对于自建服务器，开发者需要手动配置自己域名下的 `__wx__` 路径的反向代理转发：将同域名下 `__wx__` 部分转发至 `https://servicewechat.com/wxa-qbase/`

参考 Nginx 配置方式：将如下 Location 添加至 server 块中

```
location /__wx__/ {
        proxy_pass https://servicewechat.com/wxa-qbase/;
}
```

参考 Apache 配置方式：将如下配置添加到 .htaccess 或 Location 块中

```
RewriteRule ^__wx__/(.*)$ http://servicewechat.com/wxa-qbase/$1 [P,L]
```

## [#](#FAQ) FAQ

> 我配置了转发域名，还是无法登录？

云开发下发的 Cookie 为 `Secure`，`SameSite=None` 和 `HttpOnly` 形式：

- 请务必确认 OAuth 配置的 `redirect_uri` 和用户访问时使用的域名都为 **HTTPS** 协议，否则无法使用。
- 部分较旧浏览器或系统 WebView 将无法识别，如 macOS 10.14 或 iOS 12 系统自带 Safari 等。

> 提示 redirect\_uri 错误？

如果使用 `snsapi_userinfo` 等 scope，需要在「公众号平台 - 开发 - 接口权限 - 网页服务 - 网页授权 - 网页授权获取用户基本信息」中配置域名。

Incorrect translation.