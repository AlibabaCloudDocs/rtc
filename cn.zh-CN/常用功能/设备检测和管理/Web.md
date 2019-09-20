# Web {#concept_1271894 .concept}

本文为您介绍了阿里云音视频通信Web端的设备检测和管理功能。您可以检查硬件设备是否能正常工作。

## 功能简介 {#section_7dm_ktc_1bk .section}

阿里云音视频通信提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法 {#section_1rr_y5d_bwi .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../../../../cn.zh-CN/快速入门/入门概述.md#)。

阿里音视频通信Web端SDK通过getDevices方法来获取设备信息。

``` {#codeblock_efd_gb7_c0h}
aliwebrtc.getDevices().then((obj)=>{
} ,(error)=>{
    console.log(error.message);
});
```

该方法返回摄像头和音频输入设备。

**说明：** 在Safari浏览器下面，如果外接设备重插拔后获取不到，请尝试重新启动电脑。

更多接口信息，请参见[接口说明](../../../../cn.zh-CN/API参考/Web SDK/AliRtcEngine接口.md#)。

