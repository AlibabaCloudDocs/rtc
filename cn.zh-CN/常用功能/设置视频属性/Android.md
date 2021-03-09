---
keyword: [视频属性, Android, rtc]
---

# Android

RTC SDK为您提供设置视频流规格和类型的功能，您可以根据实际情况通过搭配视频流规格和类型设置视频属性，以达到更好的产品体验。通过阅读本文，您可以了解设置视频属性的方法。

## 功能简介

在音视频通信中，根据您的喜好和实际情况设置视频属性，调整视频画面的清晰度和流畅度。如果是一对一视频通信，您可以将分辨率和帧率调高，如果频道内有多个用户进行视频通信，您可以将分辨率和码率适当调低，以减少编解码的资源消耗和缓解下行带宽压力。视频属性包含视频流规格、视频流类型，如下所示：

视频流规格

|枚举名|描述|
|---|--|
|AliRTCSDK\_Video\_Profile\_Default|默认，分辨率480\*640，帧率15。|
|AliRTCSDK\_Video\_Profile\_180\_240P\_15|分辨率180\*240，帧率15。|
|AliRTCSDK\_Video\_Profile\_180\_320P\_15|分辨率180\*320，帧率15。|
|AliRTCSDK\_Video\_Profile\_180\_320P\_30|分辨率180\*320，帧率30。|
|AliRTCSDK\_Video\_Profile\_240\_320P\_15|分辨率240\*320，帧率15。|
|AliRTCSDK\_Video\_Profile\_360\_480P\_15|分辨率360\*480，帧率15。|
|AliRTCSDK\_Video\_Profile\_360\_480P\_30|分辨率360\*480，帧率30。|
|AliRTCSDK\_Video\_Profile\_360\_640P\_15|分辨率360\*640，帧率15。|
|AliRTCSDK\_Video\_Profile\_360\_640P\_30|分辨率360\*640，帧率30。|
|AliRTCSDK\_Video\_Profile\_480\_640P\_15|分辨率480\*640，帧率15。|
|AliRTCSDK\_Video\_Profile\_480\_640P\_30|分辨率480\*640，帧率30。|
|AliRTCSDK\_Video\_Profile\_720\_960P\_15|分辨率720\*960，帧率15。|
|AliRTCSDK\_Video\_Profile\_720\_960P\_30|分辨率720\*960，帧率30。|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_15|分辨率720\*1280，帧率15。|
|AliRTCSDK\_Video\_Profile\_720\_1280P\_30|分辨率720\*1280，帧率30。|
|AliRTCSDK\_Video\_Profile\_360\_640P\_15\_800Kb|360\*640分辨率，帧率15，800Kb码率。|
|AliRTCSDK\_Video\_Profile\_480\_840P\_15\_500Kb|480\*840分辨率，帧率15，500Kb码率。|
|AliRTCSDK\_Video\_Profile\_480\_840P\_15\_800Kb|480\*840分辨率，帧率15，800Kb码率。|
|AliRTCSDK\_Video\_Profile\_540\_960P\_15\_800Kb|540\*960分辨率，帧率15，800Kb码率。|
|AliRTCSDK\_Video\_Profile\_540\_960P\_15\_1200Kb|540\*960分辨率，帧率15，1200Kb码率。|
|AliRTCSDK\_Video\_Profile\_Max|占位值。|

视频流类型

|枚举名|描述|
|---|--|
|AliRtcVideoTrackNo|无视频流。|
|AliRtcVideoTrackCamera|相机流。|
|AliRtcVideoTrackScreen|屏幕共享流。|
|AliRtcVideoTrackBoth|相机流和屏幕共享流。|

## 实现方法

RTC SDK通过`setVideoProfile`方法设置视频属性。

```
public abstract void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)                   
```

|名称|类型|描述|
|--|--|--|
|profile|[AliRtcVideoProfile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流参数。默认分辨率480\*640，帧率15的相机流。|
|track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要设置的视频流类型，默认相机流。|

