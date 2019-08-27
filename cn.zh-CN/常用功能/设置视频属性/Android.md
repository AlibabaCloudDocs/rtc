# Android {#concept_1113530 .concept}

本文档为您介绍了音视频通信设置视频属性的功能简介和实现方法。您可以根据您的业务需求设置视频属性，获得更好的体验。

## 功能简介 {#section_qg4_c53_i6l .section}

在音视频通信中，根据您的喜好和实际情况设置视频属性，调整视频画面的清晰度和流畅度。视频属性包含视频流规格、视频流类型。

视频流规格如下表所示。

|枚举名|分辨率|帧率|
|---|---|--|
|AliRTCSDK\_Video\_Profile\_Default|默认，480 \* 640|15|
|AliRTCSDK\_Video\_Profile\_180\_320P\_15|180 \* 320|15|
|AliRTCSDK\_Video\_Profile\_180\_320P\_30|180 \* 320|30|
|AliRTCSDK\_Video\_Profile\_360\_640P\_15|360 \* 640|15|
|AliRTCSDK\_Video\_Profile\_360\_640P\_30|360 \* 640|30|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_15|720 \* 1280|15|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_30|720 \* 1280|30|
|AliRTCSDK\_Video\_Profile\_480\_640P\_15|480 \* 640|15|
|AliRTCSDK\_Video\_Profile\_480\_640P\_30|480 \* 640|30|

视频流类型如下表所示。

|枚举名|描述|
|---|--|
|AliRtcVideoTrackNo|无视频流|
|AliRtcVideoTrackCamera|相机流|
|AliRtcVideoTrackScreen|屏幕共享流|
|AliRtcVideoTrackBoth|相机流和屏幕共享流|

## 实现方法 {#section_fxt_107_r6b .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../../../../cn.zh-CN/快速入门/入门概述.md#)。

阿里云RTC SDK通过setVideoProfile方法设置视频属性。

``` {#codeblock_t4c_ltl_w7c .language-java}
public abstract void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)
```

参数说明：

|参数|类型|说明|
|--|--|--|
|profile|AliRtcVideoProfile|视频流规格，取值请参见[视频流规格表](#)。|
|track|AliRtcVideoTrack|视频流类型，取值请参见[视频流类型表](#)。|

获得更多视频类功能实现方法，请参见[AliRtcEngine接口](../../../../cn.zh-CN/API参考/Android SDK/接口说明/AliRtcEngine接口.md#)。

