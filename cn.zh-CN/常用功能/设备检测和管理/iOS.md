# iOS {#concept_1909547 .concept}

本文档为您介绍了阿里云音视频通信的设备检测和管理功能，您可以检查硬件设备是否能正常工作。

## 功能简介 {#section_jzf_ert_uwq .section}

阿里云音视频通信提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法 {#section_ko6_9le_igl .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

具体实现方法如下所示。

-   switchCamera：切换前后摄像头。

    ``` {#codeblock_073_rws_sn0}
    - (int)switchCamera;
    ```

    该方法返回0为切换成功，其他为切换失败。

-   setCameraZoom：设置摄像头参数。

    ``` {#codeblock_xei_ki7_d4f}
     - (int)setCameraZoom:(float)zoom flash:(BOOL)flash autoFocus:(BOOL)autoFocus;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |zoom|float|zoom变焦的级别。|
    |flash|BOOL|是否打开闪光灯。|
    |autoFocus|BOOL|是否打开自动对焦。|

    该方法返回0表示设置成功，其他表示设置失败

-   isCameraOn：检查摄像头是否打开。

    ``` {#codeblock_3eu_36k_25k}
    - (BOOL)isCameraOn;
    ```

    该方法返回YES表示摄像头已打开，NO表示摄像头没有打开

-   enableSpeakerphone：切换听筒、扬声器输出。

    ``` {#codeblock_f4q_sa8_ppy}
     - (int)enableSpeakerphone:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为听筒模式，NO为扬声器模式。|


获得更多视频类功能实现方法，请参见[AliRtcEngine接口](../cn.zh-CN/API参考/iOS SDK/接口说明/AliRtcEngine接口.md#)。

