---
keyword: [Web, 集成SDK, Rtc]
---

# Web

本文为您介绍了Web端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示：

**说明：** 集成Web客户端SDK必须使用HTTPS协议。

|操作系统|浏览器类型|浏览器最低版本要求|推流|拉流|屏幕分享|
|----|-----|---------|--|--|----|
|Mac OS|桌面版Safari浏览器|11+|支持|支持|支持（需要Safari 13及以上版本）|
|Mac OS|桌面版Chrome浏览器|60+|支持|支持|支持（需要 Chrome 72及以上版本）|
|Mac OS|桌面版Edge浏览器|80+|支持|支持|支持|
|Windows|桌面版Chrome浏览器|60+|支持|支持|支持（需要 Chrome 72及以上版本）|
|Windows|桌面版Edge浏览器|80+|支持|支持|支持|
|iOS 11.1.2及以上|移动版Safari浏览器|11+|支持|支持|不支持|
|Android|移动版Chrome浏览器|63+|支持|支持|不支持|

**说明：**

-   由于H.264版权限制，桌面浏览器RTC SDK不支持华为系统的Chrome浏览器和以Chrome WebView为内核的浏览器的正常运行。
-   [setAudioVolume](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)、[muteLocalCamera](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)、[muteLocalMic](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)接口在iOS系统目前存在兼容问题，暂不支持使用。
-   建议不要在移动端使用Web进行SDK推流，最好使用native。
-   纯订阅模式媒体文件播放失败，请参见[H5纯订阅模式媒体文件播放失败问题](/cn.zh-CN/常见问题/H5纯订阅模式媒体文件播放失败问题.md)。

1.  下载[SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  将AliWebRtcSDK包保存到本地项目下。

3.  在项目相应的前端页面文件中，对aliyun-webrtc-sdk.js文件进行引用。

    ![引入Web SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8395348951/p52262.png)

    **说明：** 本图片仅供参考，具体版本号和引入样式请您以实际为准。


完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Web基本功能](/cn.zh-CN/快速入门/实现基本功能/Web.md)。

