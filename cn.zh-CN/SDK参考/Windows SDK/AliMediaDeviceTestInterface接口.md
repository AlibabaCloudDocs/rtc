# AliMediaDeviceTestInterface接口 {#concept_109126_zh .concept}

本文档为您介绍了Windows SDK的AliMediaDeviceTestInterface接口。

## 目录 {#section_4a7_zjy_cdl .section}

|API|描述|
|---|--|
|[StartTestAudioRecord](#table_zha_4a4_s2a)|开始测试麦克风设备|
|[StopTestAudioRecord](#section_zoz_o53_fsm)|停止测试麦克风设备|
|[StartTestAudioPlayout](#table_bzw_v0v_wl6)|开始测试音频播放设备|
|[StopTestAudioPlayout](#table_2it_aka_k4z)|停止测试音频播放设备|
|[Release](#table_2it_aka_k4z)|销毁音频设备测试实例|

## 接口详情 {#section_zoz_o53_fsm .section}

-   StartTestAudioRecord：开始测试麦克风设备，AliMediaDeviceTestInterface。

    ``` {#codeblock_n0f_rpa_1rv .lanuage-c}
    int StartTestAudioRecord(const char *deviceName, int nTimeInv)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |deviceName|const char\*|麦克风设备名称，从getAudioCaptures获取。|
    |nTimeInv|int|音量回调通知的时间间隔，单位为ms，必须大于0。|

    返回：

    -   0：成功。
    -   其他：失败。
-   StopTestAudioRecord：停止测试麦克风设备。

    ``` {#codeblock_uke_csu_g7a .lanuage-c}
    int StopTestAudioRecord()
    ```

    返回：

    -   0：成功。
    -   其他：失败。
-   StartTestAudioPlayout：开始测试音频播放设备。

    ``` {#codeblock_q8m_v3b_b99 .lanuage-c}
    int StartTestAudioPlayout(const char *deviceName, int nTimeInv, const char *wavFile)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |deviceName|const char\*|音频播放设备名称，从getAudioRenderers获取。|
    |nTimeInv|int|音量回调通知的时间间隔，单位为ms，必须大于0。|
    |wavFile|const char\*|需要播放的音频文件，例如`d:/test.wav`。|

    返回：

    -   0：成功。
    -   其他：失败。
-   StopTestAudioPlayout：停止测试音频播放设备。

    ``` {#codeblock_ycy_gfi_h60 .lanuage-c}
    int StopTestAudioPlayout()
    ```

-   Release：销毁音频设备测试实例。

    ``` {#codeblock_348_6gj_agt .lanuage-c}
    void Release()
    ```


