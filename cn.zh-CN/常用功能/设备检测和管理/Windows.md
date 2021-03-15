---
keyword: [Windows, rtc, 设备检测]
---

# Windows

RTC SDK为您提供了设备检测和管理的功能，您可以在加入频道之前检查硬件设备是否能正常工作。通过阅读本文，您可以了解设备检测和管理的方法。

## 功能简介

RTC SDK通过调用内部方法实现设备检测和管理。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

以下为常用的设备检测和管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)。

-   getCameraList：获取摄像头列表。

    ```
    void getCameraList(AliRtc::StringArray& array)                 
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|摄像头列表。|

-   getCurrentCamera：获取当前使用的摄像头名称。

    ```
    AliRtc::String getCurrentCamera()                 
    ```

-   setCurrentCamera：选择摄像头。

    ```
    void setCurrentCamera(const AliRtc::String& camera)                    
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |camera|const AliRtc::String&|摄像头名称。|

    **说明：** 该接口只可在调用getCameraList接口获取设备列表后才可调用。

-   isCameraOn：检查摄像头是否打开。

    ```
    bool isCameraOn()                  
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

-   getAudioCaptures：获取系统中的录音设备列表。

    ```
    void getAudioCaptures(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频采集设备列表。|

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ```
    AliRtc::String getCurrentAudioCapture()
    ```

-   setCurrentAudioCapture：选择音频采集设备。

    ```
    void setCurrentAudioCapture(const AliRtc::String& capture)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |capture|String|音频采集设备名称。|

    **说明：** 该接口只可在getAudioCaptures接口后调用。

-   getAudioRenderers：获取系统中的扬声器列表。

    ```
    void getAudioRenderers(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频播放设备列表。|

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ```
    AliRtc::String getCurrentAudioRenderer()
    ```

-   setCurrentAudioRenderer：选择音频播放设备。

    ```
    void setCurrentAudioRenderer(const AliRtc::String &renderer)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderer|String|音频播放设备名称。|

    **说明：** 该接口只可在getAudioRenderers后调用。


