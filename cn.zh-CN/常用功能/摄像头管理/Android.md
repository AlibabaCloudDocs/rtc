---
keyword: [Android, 摄像头]
---

# Android

RTC SDK为您提供了摄像头管理的接口方法，您可以在音视频通话之前对摄像头进行管理，以确保设备是否正常工作。通过阅读本文，您可以了解摄像头管理的方法。

## 功能简介

阿里云RTC提供一系列摄像头管理方法，包括切换前后置摄像头、缩放镜头、曝光设置和对焦功能，您可以在加入频道前进行设置，帮助您在通话时使成像更清晰、大小与亮度更适宜。

## 实现方法

以下为常用的摄像头管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)。

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

-   isCameraSupportExposurePoint：相机是否支持手动曝光。

    ```
    public abstract boolean isCameraSupportExposurePoint();
    ```

    返回说明

    true表示支持，false表示不支持。

-   isCameraSupportFocusPoint：相机是否支持手动聚焦。

    ```
    public abstract boolean isCameraSupportFocusPoint();
    ```

    返回说明

    true表示支持，false表示不支持。

-   setCameraExposurePoint：设置手动曝光的坐标点。

    ```
    public abstract int setCameraExposurePoint(float x, float y);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |x|float|x坐标。|
    |y|float|y坐标。|

    返回说明

    0表示设置成功，其他表示设置失败。

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

-   isCameraFlash：查看摄像头闪光灯是否开启。

    ```
    public abstract boolean isCameraFlash();
    ```

    返回说明

    true表示开启，false表示未开启。

-   getCameraZoom： 获取相机zoom（变焦）值。

    ```
    public abstract float getCameraZoom();
    ```

    返回说明

    返回值范围：0.0~1.0。0表示相机支持的最小值，1表示相机支持的最大值。


