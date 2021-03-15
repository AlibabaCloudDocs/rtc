---
keyword: [摄像头, ios]
---

# iOS

RTC SDK为您提供了摄像头管理的接口方法，您可以在音视频通话之前对摄像头进行管理，以确保设备是否正常工作。通过阅读本文，您可以了解摄像头管理的方法。

## 功能简介

阿里云RTC提供一系列摄像头管理方法，包括切换前后置摄像头、缩放镜头、曝光设置和对焦功能，您可以在加入频道前进行设置，帮助您在通话时使成像更清晰、大小与亮度更适宜。

## 实现方法

以下为常用的摄像头管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)。

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

-   isCameraFocusPointSupported（仅iOS可用）：相机是否支持手动聚焦。

    ```
    - (BOOL)isCameraFocusPointSupported;
    ```

    返回说明

    YES表示支持手动聚焦，NO表示不支持手动聚焦。

-   isCameraExposurePointSupported（仅iOS可用）：相机是否支持手动曝光。

    ```
    - (BOOL)isCameraExposurePointSupported;
    ```

    返回说明

    YES表示支持手动曝光，NO表示不支持手动曝光。

-   setCameraFocusPoint：设置手动聚焦的坐标点。

    ```
    public abstract int setCameraFocusPoint(float x, float y);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |x|float|x坐标。|
    |y|float|y坐标。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   setCameraExposurePoint（仅iOS可用）：设置手动曝光的坐标点。

    ```
    - (int)setCameraExposurePoint:(CGPoint)point;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |point|CGPoint|曝光点坐标。|

    返回说明

    0表示成功，其他表示失败。


