AI/视觉算法/VKBodyAnchor/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#VKBodyAnchor) VKBodyAnchor
> 基础库 2.28.0 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
人体 anchor
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#%E5%B1%9E%E6%80%A7) 属性
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#number-id) number id
唯一标识
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#number-type) number type
类型
\*\*type 的合法值\*\*
| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 5 | 人体 | |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#number-detectId) number detectId
识别序号
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#Object-size) Object size
相对视窗的尺寸，取值范围为 \[0, 1\]，0 为左/上边缘，1 为右/下边缘
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度 |
| height | number | 高度 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#Object-origin) Object origin
相对视窗的位置信息，取值范围为 \[0, 1\]，0 为左/上边缘，1 为右/下边缘
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | 横坐标 |
| y | number | 纵坐标 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#Array-number-confidence) Array. confidence
关键点的置信度
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#Array-Object-points) Array. points
关键点
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | 横坐标 |
| y | number | 纵坐标 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#number-score) number score
总体置信值
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/VKBodyAnchor.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
[静态图像body检测能力使用参考](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/photo-body-detect)
[实时摄像头body检测能力使用参考](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/body-detect)