---
keyword: [iOS, rtc, 设备检测]
---

# iOS

RTC SDK为您提供了设备检测和管理的功能，您可以在加入频道之前检查硬件设备是否能正常工作。通过阅读本文，您可以了解设备检测和管理的方法。

## 功能简介

RTC SDK通过调用内部方法实现设备检测和管理。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

-   switchCamera（仅iOS可用）：切换前后摄像头。

    ```
    - (int)switchCamera;
    ```

    返回说明

    0表示切换成功，其他表示切换失败。

-   setCameraZoom（仅iOS可用）：设置摄像头参数。

    ```
     - (int)setCameraZoom:(float)zoom flash:(BOOL)flash autoFocus:(BOOL)autoFocus;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |zoom|float|变焦的级别。取值范围：-3.0~3.0，默认取值1.0。|
    |flash|BOOL|是否打开闪光灯。YES为打开闪光灯，NO为不打开闪光灯。默认不打开闪光灯。|
    |autoFocus|BOOL|是否打开自动对焦。YES为打开自动对焦，NO为不打开自动对焦。默认不打开自动对焦。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   isCameraOn（仅iOS可用）：检查摄像头是否打开。

    ```
    - (BOOL)isCameraOn;
    ```

    返回说明

    YES表示摄像头已打开，NO表示摄像头没有打开。

-   enableSpeakerphone（仅iOS可用）：设置音频输出为听筒还是扬声器。

    ```
     - (int)enableSpeakerphone:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为扬声器模式，NO为听筒模式（默认值）。|

    返回说明

    0表示成功，其他返回错误码。


