---
keyword: [Web, SDK, 集成]
---

# Web

通过阅读本文，您可以了解Web端集成SDK的方法。

## 注意事项

集成Web客户端SDK必须使用HTTPS协议。

## 环境要求

|操作系统|浏览器类型|版本要求|推流|拉流|屏幕分享|
|----|-----|----|--|--|----|
|Mac|Safari|Safari 11或以上版本|支持|支持|不支持|
|Chrome|Chrome 60或以上版本|支持|支持|支持（需要Chrome 72或以上版本）|
|Edge|Edge 80或以上版本|支持|支持|支持（需要Edge 80或以上版本）|
|Windows|Chrome|Chrome 60或以上版本|支持|支持|支持（需要Chrome 72或以上版本）|
|Edge|Edge 80或以上版本|支持|支持|支持（需要Edge 80或以上版本）|
|iOS（11.1.2及以上版本）|Safari|Safari 11或以上版本|支持|支持|不支持|
|Android|Chrome|Chrome 63或以上版本|支持|支持|不支持|

**说明：**

-   由于H.264版权限制，桌面浏览器RTC SDK不支持华为系统的Chrome浏览器和以Chrome WebView为内核的浏览器的正常运行。
-   [setAudioVolume](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)、[muteLocalCamera](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)、[muteLocalMic](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)接口在iOS系统目前存在兼容问题，暂不支持使用。
-   不建议使用移动端Web进行推流，最好使用本地Native端。
-   关于纯订阅模式媒体文件播放失败的问题，请参见[H5纯订阅模式媒体文件播放失败问题](/cn.zh-CN/常见问题/H5纯订阅模式媒体文件播放失败问题.md)。

## 操作步骤

1.  下载并解压Web SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  新建工程，将解压后的SDK文件复制到项目中。

3.  在项目相应的前端页面文件中，对aliyun-webrtc-sdk.js文件进行引用。

    ![引入Web SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8395348951/p52262.png)

    **说明：** 此处SDK文件名称仅供参考，具体名称请以实际为准。


完成集成SDK操作后，您可以实现音视频通信的基本功能，详情请参见[Web端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Web.md)。

