# Windows {#concept_2022759 .concept}

本文档为您介绍了阿里云音视频通信的设备检测和管理功能，您可以检查硬件设备是否能正常工作。

## 功能简介 {#section_fnd_90m_w42 .section}

阿里云音视频通信提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法 {#section_k5t_tfv_4pu .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

具体实现方法如下所示。

-   getCameraList：获取摄像头列表。

    ``` {#d9e2440 .lanuage-c}
    void getCameraList(AliRtc::StringArray& array)                 
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|摄像头列表。|

-   getCurrentCamera：获取当前使用的摄像头名称。

    ``` {#d9e2495 .lanuage-c}
    AliRtc::String getCurrentCamera()                 
    ```

-   setCurrentCamera：选择摄像头。 必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ``` {#d9e2505 .lanuage-c}
    void setCurrentCamera(const AliRtc::String& camera)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |camera|const AliRtc::String&|摄像头名称。|

-   isCameraOn：检查摄像头是否打开。 true表示摄像头已打开；false表示摄像头未打开。

    ``` {#d9e2560 .lanuage-c}
    bool isCameraOn()                  
    ```

-   getAudioCaptures：获取音频采集设备列表。

    ``` {#d9e2760 .lanuage-c}
    void getAudioCaptures(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频采集设备列表。|

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ``` {#d9e2815 .lanuage-c}
    AliRtc::String getCurrentAudioCapture()
    ```

-   setCurrentAudioCapture：选择音频采集设备。必须先调用getAudioCaptures接口获取设备列表后再调用此接口设置。

    ``` {#d9e2824 .lanuage-c}
    void setCurrentAudioCapture(const AliRtc::String& capture)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |capture|String|音频采集设备名称。|

-   getAudioRenderers：获取音频播放设备列表。

    ``` {#d9e2879 .lanuage-c}
    void getAudioRenderers(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频播放设备列表。|

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ``` {#d9e2934 .lanuage-c}
    AliRtc::String getCurrentAudioRenderer()
    ```

-   setCurrentAudioRenderer：选择音频播放设备。必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。

    ``` {#d9e2943 .lanuage-c}
    void setCurrentAudioRenderer(const AliRtc::String &renderer)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |renderer|String|音频播放设备名称。|


更多接口实现方法，请参见[AliRtcEngine接口](../cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md#)。

