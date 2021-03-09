---
keyword: [Mac, rtc, 设备检测]
---

# Mac

RTC SDK为您提供了设备检测和管理的功能，您可以在加入频道之前检查硬件设备是否能正常工作。通过阅读本文，您可以了解设备检测和管理的方法。

## 功能简介

RTC SDK通过调用内部方法实现设备检测和管理。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

-   getCameraList（仅Mac可用）：获取摄像头列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getCameraList;
    ```

-   getCurrentCamera（仅Mac可用）：获取当前使用的摄像头名称。

    ```
    - (NSString *)getCurrentCamera;
    ```

-   setCurrentCamera（仅Mac可用）：选择摄像头。

    ```
    - (void)setCurrentCamera:(NSString *)camera;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |camera|NSString \*|摄像头名称。|

    **说明：** 必须先调用getCameraList接口获取设备列表后再调用此接口设置。

-   getAudioCaptures（仅Mac可用）：获取系统中的录音设备列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getAudioCaptures;
    ```

-   getCurrentAudioCapture（仅Mac可用）：获取当前使用的音频采集设备名称。

    ```
    - (NSString *)getCurrentAudioCapture;
    ```

-   setCurrentAudioCapture（仅Mac可用）：选择音频采集设备。

    ```
    - (void)setCurrentAudioCapture:(NSString *)capture;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |capture|NSString \*|音频采集设备名称。|

    **说明：** 必须先调用getCurrentAudioCapture接口获取设备列表后再调用此接口设置。

-   getAudioRenderers（仅Mac可用）：获取系统中的扬声器列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getAudioRenderers;
    ```

-   getCurrentAudioRenderer（仅Mac可用）：获取当前使用的音频播放设备。

    ```
    - (NSString *)getCurrentAudioRenderer;
    ```

-   setCurrentAudioRenderer（仅Mac可用）：选择音频播放设备。

    ```
    - (void)setCurrentAudioRenderer:(NSString *)renderer;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderer|NSString \*|音频播放设备名称。|

    **说明：** 必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。


