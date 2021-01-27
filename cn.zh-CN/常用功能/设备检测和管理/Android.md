---
keyword: [Android, rtc, 设备检测]
---

# Android

本文为您介绍了阿里云RTC的设备检测和管理功能，您可以在加入频道之前检查硬件设备是否能正常工作。

## 功能简介

AliRTCSDK提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

在实现该功能之前，需要您已经搭建AppServer、实现基本功能等操作。详情请参见[入门概述](/cn.zh-CN/快速入门/入门概述.md)。

具体实现方法如下所示。

-   getCurrentCameraType：获取当前摄像头类型。

    ```
    public abstract AliRTCCameraType getCurrentCameraType()                   
    ```

    返回摄像头的类型。

    |返回值|枚举名|描述|
    |---|---|--|
    |-1|AliRTCCameraInvalid|无效|
    |0|AliRTCCameraBack|后置摄像头|
    |1|AliRTCCameraFront|前置摄像头|

-   isCameraOn：检查摄像头是否打开。

    ```
    public abstract boolean isCameraOn()                   
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

-   isSpeakerOn：查询是否开启扬声器。

    ```
    public abstract boolean isSpeakerOn()                  
    ```

    返回说明

    true表示已开启扬声器，false表示未开启扬声器。

-   setPreCameraType：预设值摄像头方向。

    ```
    public abstract void setPreCameraType(int faceTo)                    
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |faceTo|int|0表示后置，1表示前置（默认值为1）。|

-   getPreCameraType：获取预设值摄像头方向。

    ```
    public abstract int getPreCameraType()                  
    ```

    返回说明

    0表示后置摄像头，1表示前置摄像头。

-   setCameraZoom：设置摄像头参数。

    ```
    public abstract int setCameraZoom(float zoom, boolean flash, boolean autoFocus)                  
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |zoom|float|zoom变焦的级别（默认值：1.0）。|
    |flash|boolean|true表示打开闪光灯，false表示不打开闪光灯。默认不打开闪光灯。|
    |autoFocus|boolean|true表示打开自动对焦，false表示不打开自动对焦。默认不打开自动对焦。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   enableSpeakerphone：切换听筒、扬声器输出。

    ```
    public abstract int enableSpeakerphone(boolean enable)  
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true为扬声器模式，false为听筒模式。默认扬声器模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只能在主线程调用。


获得更多功能实现方法，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)。

