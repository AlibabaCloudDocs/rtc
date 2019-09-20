# Web {#concept_2245121 .concept}

本文档为您介绍了音视频通信设置视频属性的功能简介和实现方法。您可以根据您的业务需求设置视频属性，获得更好的体验。

## 功能简介 {#section_8rh_8ou_c20 .section}

在阿里云音视频通信中，根据您的喜好和实际情况设置视频属性，调整视频画面的清晰度和流畅度。视频属性包含分辨率、帧率。

设置视频属性之前，您需要调用getAvailableResolutions\(\)返回支持的分辨率和帧率。

## 实现方法 {#section_45q_zhl_ogm .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

阿里云RTC SDK通过videoProfile方法设置视频属性，然后调用publish\(\)才能生效。

**说明：** 如果您设置的分辨率不合适，系统会自动进行调整。

``` {#codeblock_fet_ejs_h45}
aliWebrtc.videoProfile = { 
  frameRate:20,
  width: 640,
  height: 480
};
```

参数：

|参数|类型|描述|
|--|--|--|
|frameRate|int|帧率（5~30）。|
|width|int|视频宽度。|
|height|int|设备高度。|

