# Mac {#concept_1893922 .concept}

本文档为您介绍了音视频通信设置视频属性的功能简介和实现方法。您可以根据您的业务需求设置视频属性，获得更好的体验。

## 功能简介 {#section_alw_669_ra0 .section}

在音视频通信中，根据您的喜好和实际情况设置视频属性，调整视频画面的清晰度和流畅度。视频属性包含视频流规格、视频流类型。

视频流规格如下表所示。

|枚举名|描述|
|---|--|
|AliRTCSDK\_Video\_Profile\_Default|默认，分辨率480 \* 640，帧率15|
|AliRTCSDK\_Video\_Profile\_180\_320P\_15|分辨率180 \* 320，帧率15|
|AliRTCSDK\_Video\_Profile\_180\_320P\_30|分辨率180 \* 320，帧率30|
|AliRTCSDK\_Video\_Profile\_360\_640P\_15|分辨率360 \* 640，帧率15|
|AliRTCSDK\_Video\_Profile\_360\_640P\_30|分辨率360 \* 640，帧率30|
|AliRTCSDK\_Video\_Profile\_480\_640P\_15|分辨率480 \* 640，帧率15|
|AliRTCSDK\_Video\_Profile\_480\_640P\_30|分辨率480 \* 640，帧率30|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_15|分辨率720 \* 1280，帧率15|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_30|分辨率720 \* 1280，帧率30|
|AliRTCSDK\_Video\_Profile\_Max|占位值|

视频流类型如下表所示。

|枚举名|描述|
|---|--|
|AliRtcVideoTrackNo|无视频流|
|AliRtcVideoTrackCamera|相机流|
|AliRtcVideoTrackScreen|屏幕共享流|
|AliRtcVideoTrackBoth|相机流和屏幕共享流|

## 实现方法 {#section_6c4_ltt_uge .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

阿里云RTC SDK通过setVideoProfile方法设置视频属性。

setVideoProfile：设置视频流的参数。

``` {#codeblock_cxl_tkp_4vs .lanuage-c}
- (void)setVideoProfile:(AliRtcVideoProfile)profile forTrack:(AliRtcVideoTrack)track;
```

参数：

|参数|类型|描述|
|--|--|--|
|profile|[AliRtcVideoProfile](../cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md#)|视频流参数。|
|track|[AliRtcVideoTrack](../cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md#)|需要设置的videoTrack类型。|

获得更多视频类功能实现方法，请参见[AliRtcEngine接口](../cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md#)。

