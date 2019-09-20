# Android {#concept_1130515 .concept}

本文档为您介绍了阿里云音视频通信的设备检测和管理功能，您可以检查硬件设备是否能正常工作。

## 功能简介 {#section_mng_zij_m4d .section}

阿里云音视频通信提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法 {#section_s2t_xuk_zcr .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../../../../cn.zh-CN/快速入门/入门概述.md#)。

具体实现方法如下所示。

-   getCurrentCameraType：获取当前摄像头类型。

    ``` {#codeblock_el7_691_zud .language-java}
    public abstract AliRTCCameraType getCurrentCameraType()
    ```

    返回摄像头的类型。

    |返回值|枚举名|描述|
    |---|---|--|
    |-1|AliRTCCameraInvalid|无效|
    |0|AliRTCCameraBack|后置摄像头|
    |1|AliRTCCameraFront|前置摄像头|
    |2|AliRTCCameraUsb|usb摄像头|

-   isCameraOn：检查摄像头是否打开。

    ``` {#codeblock_usu_mo2_v3i .language-java}
    public abstract boolean isCameraOn()
    ```

    该方法返回true表示摄像头已打开，false表示摄像头未打开。

-   isSpeakerOn：查询是否开启扬声器。

    ``` {#codeblock_fyl_1u0_z5r .language-java}
    public abstract boolean isSpeakerOn()
    ```

    该方法返回true表示已开启扬声器，false表示未开启扬声器。

-   setPreCameraType：预设值摄像头方向。

    ``` {#codeblock_jti_zzj_9lx .language-java}
    public abstract void setPreCameraType(int faceTo)
    ```

    参数说明：

    |参数|类型|说明|
    |--|--|--|
    |faceTo|int|0表示后置，1表示前置|

-   getPreCameraType：获取预设值摄像头方向。

    ``` {#codeblock_kjx_a3l_qyg .language-java}
    public abstract int getPreCameraType()
    ```

    该方法返回0为后置摄像头，1为前置摄像头。

-   setCameraZoom：设置摄像头参数。

    ``` {#codeblock_bpl_3m7_nk3 .language-java}
    public abstract int setCameraZoom(float zoom, boolean flash, boolean autoFocus)
    ```

    参数说明：

    |参数|类型|说明|
    |--|--|--|
    |zoom|float|zoom变焦的级别|
    |flash|boolean|是否打开闪光灯|
    |autoFocus|boolean|是否自动对焦|

    该方法返回0表示设置成功，其他表示设置失败。

-   enableSpeakerphone：切换听筒、扬声器输出。

    ``` {#codeblock_8wb_u9x_5oy .language-java}
    public abstract int enableSpeakerphone(boolean enable)
    ```

    参数说明：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true为扬声器模式，false为听筒模式|


更多接口实现方法，请参见[AliRtcEngine接口](../../../../cn.zh-CN/API参考/Android SDK/接口说明/AliRtcEngine接口.md#)。

