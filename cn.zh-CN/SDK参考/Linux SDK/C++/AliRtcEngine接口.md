# AliRtcEngine接口

本文为您介绍了Linux SDK（C++）的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[CreateAliRTCEngine](#li_wpl_vhy_k45)|创建AliRTCEngine实例|1.16|
|[Release](#li_2cr_csc_hgv)|销毁AliRTCEngine实例|1.16|
|[GetEventHandler](#li_pm8_mct_3l0)|获取事件回调句柄|1.16|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[JoinChannel](#li_lp7_1fk_i0r)|加入频道|1.16|
|[LeaveChannel](#li_vk8_dmy_5qx)|离开频道|1.16|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[SetVideoProfile](#li_nbc_k0o_jkl)|设置视频流推流参数|1.16|
|[GetVideoProfile](#li_a5i_rk5_7ha)|获取视频流推流参数|1.16|
|[ConfigLocalCameraPublish](#li_gbb_iev_fo5)|设置是否允许推送相机流|1.16|
|[IsLocalCameraPublishEnabled](#li_sq5_96z_f8v)|查询是否允许推送相机流|1.16|
|[ConfigLocalScreenPublish](#li_f4d_pqa_91i)|设置是否允许推送屏幕流|1.16|
|[IsLocalScreenPublishEnabled](#li_o5a_ciq_xeq)|查询是否允许推送屏幕流|1.16|
|[ConfigLocalAudioPublish](#li_f7p_epu_ssn)|设置是否允许推送音频流|1.16|
|[IsLocalAudioPublishEnabled](#li_wzp_2al_2hs)|查询是否允许推送音频流|1.16|
|[ConfigLocalSimulcast](#li_pnj_yud_oi3)|设置是否允许推送次要视频流小流|1.16|
|[IsLocalSimulcastEnabled](#li_n1k_mm0_g3q)|查询是否允许推送次要视频流小流|1.16|
|[Publish](#li_p7r_dnm_syc)|手动推送视频和音频流|1.16|

录制相关接口

|API|描述|以上版本支持|
|---|--|------|
|[StartRecording](#li_au1_g0n_813)|手动开启录制|1.16|
|[StopRecording](#li_ylf_u1j_e81)|手动停止录制|1.16|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[SetExternalVideoSource](#li_gfj_kml_mjj)|设置是否启用外部视频输入源|1.16|
|[PushExternalVideoFrame](#li_y8p_drt_qih)|输入外部视频数据|1.16|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[SetExternalAudioSource](#li_vo8_1fn_wco)|设置是否启用外部音频输入推流|1.16|
|[PushExternalAudioFrameRawData](#li_3jo_g18_sbm)|输入外部音频数据推流|1.16|
|[SetExternalAudioPublishVolume](#li_etn_4fx_7t1)|设置外部输入音频推流混音音量|1.16|
|[GetExternalAudioPublishVolume](#li_afn_kpe_do4)|获取外部输入音频推流混音音量|1.16|

## 接口详情

-   CreateAliRTCEngine：创建AliRTCEngine实例。

```
AliRTCEngineInterface * CreateAliRTCEngine(EngineEventHandlerInterface * eventHandler,
                           int lowPort,
                           int highPort,
                           const char * logPath,
                           const char * coreServicePath);
                        
```

|参数名|类型|描述|
|---|--|--|
|eventHandler|EngineEventHandlerInterface \*|录制SDK所触发的事件通过EngineEventHandlerInterface类回调通知。|
|lowPort|int|最小的可用端口。**说明：** 创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。 |
|highPort|int|最大的可用端口。**说明：** 创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。 |
|logPath|const char \*|保存日志的路径。|
|coreServicePath|const char \*|AliRtcCoreService可执行程序存放的绝对路径。|

-   Release：销毁AliRTCEngine实例。

    ```
    virtual void Release() = 0;
    ```

-   GetEventHandler：获取事件回调句柄。

    ```
    virtual EngineEventHandlerInterface * GetEventHandler() = 0;
    ```

-   JoinChannel：加入频道。

    ```
    virtual int JoinChannel(const AuthInfo &authInfo, const JoinChannelConfig &config) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |authInfo|const [AuthInfo](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) &a|认证信息，从App Server获取。|
    |config|const [JoinChannelConfig](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) &|加入频道时的设置项。|

-   LeaveChannel：离开频道。

    ```
    virtual int LeaveChannel() = 0;
    ```

-   SetVideoProfile：设置视频流推流参数。

    **说明：** 设置之后等到下次推流的时候才能生效。

    ```
    virtual void SetVideoProfile(AliRTCSdk::Linux::VideoProfile profile, AliRTCSdk::Linux::VideoTrack track) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |profile|AliRTCSdk::Linux::[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|预定义的视频分辨率和帧率，详细请参见[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|
    |track|AliRTCSdk::Linux::[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   GetVideoProfile：获取视频流推流参数。

    **说明：** 返回的是正在使用的（已经推流中）或者即将被使用的（下一次推流才会生效）视频分辨率和帧率，详细请参见[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) 。返回值不一定是正在使用的[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)，另外VideoTrackScreen是不支持的。

    ```
    virtual AliRTCSdk::Linux::VideoProfile GetVideoProfile(AliRTCSdk::Linux::VideoTrack track) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |track|AliRTCSdk::Linux:[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   ConfigLocalCameraPublish：设置是否允许推送相机流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认允许相机流推流。

    ```
    virtual void ConfigLocalCameraPublish(bool enable) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送相机流。true：允许，false：禁止。|

-   IsLocalCameraPublishEnabled：查询是否允许推送相机流。返回值，true表示允许，false表示禁止。

    ```
    virtual bool IsLocalCameraPublishEnabled() = 0;
    ```

-   ConfigLocalScreenPublish：设置是否允许推送屏幕流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认不允许屏幕流推流。

    ```
    virtual void ConfigLocalScreenPublish(bool enable) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送屏幕流。true：允许，false：禁止。|

-   IsLocalScreenPublishEnabled：查询是否允许推送屏幕流。返回值，true表示允许，false表示禁止。

    ```
    virtual bool IsLocalScreenPublishEnabled() = 0;
    ```

-   ConfigLocalAudioPublish：设置是否允许推送音频流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效，默认允许音频推流。

    ```
    virtual void ConfigLocalAudioPublish(bool enable) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送音频流小流。true：允许，false：禁止。|

-   IsLocalAudioPublishEnabled：查询是否允许推送音频流小流。返回值，true表示允许，false表示禁止。

    ```
    virtual bool IsLocalAudioPublishEnabled() = 0;
    ```

-   ConfigLocalSimulcast：设置是否允许推送次要视频流小流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认允许推送次要视频流。目前只支持相机流，不支持屏幕流。

    ```
    virtual int ConfigLocalSimulcast(bool enabled, AliRTCSdk::Linux::VideoTrack track) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enabled|bool|是否允许推送次要视频流小流。true：允许，false：禁止。|
    |track|AliRTCSdk::Linux::[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   IsLocalSimulcastEnabled：查询是否允许推送次要视频流小流。返回值，true表示允许，false表示禁止。

    ```
    virtual bool IsLocalSimulcastEnabled() = 0;
    ```

-   Publish：手动推送视频和音频流。

    **说明：** 需要推送的流通过API [ConfigLocalAudioPublish](#li_f7p_epu_ssn)，[ConfigLocalCameraPublish](#li_gbb_iev_fo5)和[ConfigLocalScreenPublish](#li_f4d_pqa_91i)进行设置。

    ```
    virtual int Publish() = 0;
    ```

-   StartRecording：手动开启录制。

    **说明：** 如果需要手工配置所有推流和拉流，请通过[JoinChannelConfig](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)字段，再[JoinChannel](#li_lp7_1fk_i0r)时，选择RecordingManually。

    ```
    virtual int StartRecording() = 0;
    ```

-   StopRecording：手动停止录制。

    ```
    virtual int StopRecording() = 0;
    ```

-   SetExternalVideoSource：设置是否启用外部视频输入源。

    **说明：** 启用后使用PushExternalVideoFrame接口输入视频数据。

    ```
    virtual int SetExternalVideoSource(bool enable, bool useTexture, AliRTCSdk::Linux::VideoSource sourceType, AliRTCSdk::Linux::RenderMode renderMode = AliRTCSdk::Linux::RenderModeFill) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enabled|bool|是否启用外部视频输入源。true：允许，false：关闭。|
    |useTexture|bool|是否使用texture模式，目前仅支持false。|
    |sourceType|AliRTCSdk::Linux::[VideoSource](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|流类型。|

-   PushExternalVideoFrame：输入外部视频数据。

    **说明：** 目前输入视频类型只支持I420。

    ```
    virtual int PushExternalVideoFrame(AliRTCSdk::Linux::VideoDataSample *frame, AliRTCSdk::Linux::VideoSource sourceType) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |frame|AliRTCSdk::Linux::[VideoDataSample](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) \*|帧数据。|
    |sourceType|AliRTCSdk::Linux::[VideoSource](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|流类型。|

-   SetExternalAudioSource：设置是否启用外部音频输入推流。返回值，大于等于0表示成功，小于0表示失败。

    **说明：** 通过[SetExternalAudioPublishVolume](#li_s51_z44_wfb)设置输入音频推流音量。

    ```
    virtual int SetExternalAudioSource(bool enable, unsigned int sampleRate,  unsigned int channelsPerFrame) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否启用外部音频输入推流。true：开启，false：关闭。|
    |sampleRate|unsigned int|采样率。|
    |channelsPerFrame|unsigned int|采样率。|

-   PushExternalAudioFrameRawData：输入外部音频数据推流。返回值，大于等于0表示成功，小于0表示失败。

    **说明：** 当返回值为ERR\_AUDIO\_BUFFER\_FULL时，需要在间隔投递数据时间长度后再次重试投递。

    ```
    virtual int PushExternalAudioFrameRawData(const void* audioSamples, unsigned int sampleLength, long long timestamp) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |audioSamples|const void\*|音频数据。|
    |sampleLength|unsigned int|音频数据长度。|
    |timestamp|long long|时间戳。|

-   SetExternalAudioPublishVolume：设置外部输入音频推流混音音量。

    ```
    virtual int SetExternalAudioPublishVolume(int volume) = 0;
    ```

    |参数名|类型|描述|
    |---|--|--|
    |volume|int|音量，取值范围0~100。|

-   GetExternalAudioPublishVolume：获取外部输入音频推流混音音量。

    ```
    virtual int GetExternalAudioPublishVolume() = 0;
    ```


