# Mac {#concept_1909548 .concept}

本文档为您介绍了阿里云音视频通信的设备检测和管理功能，您可以检查硬件设备是否能正常工作。

## 功能简介 {#section_uys_vei_pcr .section}

阿里云音视频通信提供了检测和管理设备的功能，方便您测试和检测设备。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法 {#section_au1_22o_ctx .section}

在实现该功能之前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

具体实现方法如下所示。

-   getCameraList：获取摄像头列表。

    ``` {#codeblock_uq7_cwx_dd6}
    - (NSArray<NSString *> *)getCameraList;
    ```

-   getCurrentCamera：获取当前使用的摄像头名称。

    ``` {#codeblock_0ek_rq7_a4d}
    - (NSString *)getCurrentCamera;
    ```

-   setCurrentCamera：选择摄像头。必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_ire_hyo_c4k}
    - (void)setCurrentCamera:(NSString *)camera;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |camera|NSString \*|摄像头名称。|

-   isCameraOn：检查摄像头是否打开，YES表示摄像头已打开，NO表示摄像头没有打开。

    ``` {#d12e2548 .lanuage-c}
    - (BOOL)isCameraOn;
    ```

-   getAudioCaptures：获取音频采集设备列表。

    ``` {#codeblock_ff9_s22_e1x}
    - (NSArray<NSString *> *)getAudioCaptures;
    ```

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ``` {#codeblock_dro_lrh_nkn}
    - (NSString *)getCurrentAudioCapture;
    ```

-   setCurrentAudioCapture：选择音频采集设备。必须先调用getCurrentAudioCapture接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_448_ufd_pma}
    - (void)setCurrentAudioCapture:(NSString *)capture;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |capture|NSString \*|音频采集设备名称。|

-   getAudioRenderers：获取音频播放设备列表。

    ``` {#codeblock_051_ihl_mcq}
    - (NSArray<NSString *> *)getAudioRenderers;
    ```

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ``` {#codeblock_32i_dqb_2nc}
    - (NSString *)getCurrentAudioRenderer;
    ```

-   setCurrentAudioRenderer：选择音频播放设备。必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_9hw_7wv_sbj}
    - (void)setCurrentAudioRenderer:(NSString *)renderer;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |renderer|NSString \*|音频播放设备名称。|

-   enableSpeakerphone（仅iOS可用）：切换听筒、扬声器输出。

    ``` {#d12e2745 .lanuage-c}
     - (int)enableSpeakerphone:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为听筒模式，NO为扬声器模式。|


获得更多视频类功能实现方法，请参见[AliRtcEngine接口](../cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md#)。

