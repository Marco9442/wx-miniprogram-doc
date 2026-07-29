# [#](#Web-SDK) Web SDK

以下是接入代码样例（注意：样例代码不能直接使用，需替换模板参数，建议创建 web 项目后使用「设置->采集配置」中的已适配好的接入代码）。

```
<script>
(function () {
    'use strict';

    const SCRIPT_URLs = [
        'https://dldir1.qq.com/WechatWebDev/devPlatform/px.min.js',
        'https://dev.weixin.qq.com/platform-console/proxy/assets/tel/px.min.js',
    ];
    const param = {
        maskMode: 'all-mask', // 隐私策略, all-mask 或 no-mask, 详见：https://www.npmjs.com/package/@wxobs/miniprogram-sdk#%E6%96%87%E6%A1%A3
        recordCanvas: false,  // 若要采集canvas, 设为true
        projectId: 'PROJECT_ID', // 项目 ID，需替换为体验分析项目 ID
        iframe: false, // 是否采集 iframe 页面
        console: true, // 是否采集 console 输出的错误日志
        network: true, // 是否采集网络错误
    };
    function loadScript(url) {
        return new Promise((resolve, reject) => {
            const scriptEle = document.createElement('script');
            scriptEle.type = 'text/javascript';
            scriptEle.async = true;
            scriptEle.src = url;
            scriptEle.onload = () => {
                resolve(url);
            };
            scriptEle.onerror = () => {
                reject(new Error(`Script load error for ${url}`));
            };
            document.head.appendChild(scriptEle);
        });
    }
    async function main() {
        try {
            sessionStorage.setItem('wxobs_start_timestamp', String(Date.now()));
            const fastestUrl = await Promise.race(SCRIPT_URLs.map(url => loadScript(url)));
            window.__startPX && window.__startPX(param);
        }
        catch (error) {
            console.error('Error loading scripts:', error);
        }
    }
    main();

})();

</script>
```

## [#](#接口) 接口

网页接入后，可通过 `window.__wxobs__` 访问 SDK 接口，拥有的接口和[小程序端 SDK](api)一致。

Incorrect translation.