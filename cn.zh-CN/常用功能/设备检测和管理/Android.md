---
keyword: [Android, rtc, 设备检测]
---

# Android

RTC SDK为您提供了设备检测和管理的功能，您可以在加入频道之前检查硬件设备是否能正常工作。通过阅读本文，您可以了解设备检测和管理的方法。

## 功能简介

RTC SDK通过调用内部方法实现设备检测和管理。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

以下为常用的设备检测和管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)。

-   getCurrentCameraType：获取当前摄像头类型。

    返回摄像头类型[AliRTCCameraType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。

    ```
    public abstract AliRTCCameraType getCurrentCameraType()                   
    ```

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


