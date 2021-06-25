# AliRtcEngine接口

通过阅读本文，您可以了解到Linux SDK（C++）的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|支持的最低版本|
|---|--|-------|
|[CreateAliRTCEngine](#li_wpl_vhy_k45)|创建AliRTCEngine实例。|1.18.1|
|[Release](#li_2cr_csc_hgv)|释放AliRTCEngine实例。|1.18.1|
|[GetEventHandler](#li_pm8_mct_3l0)|获取事件回调句柄。|1.18.1|

频道相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[JoinChannel](#li_lp7_1fk_i0r)|加入频道。|1.18.1|
|[LeaveChannel](#li_vk8_dmy_5qx)|离开频道。|1.18.1|

发布相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetVideoProfile](#li_nbc_k0o_jkl)|设置视频流推流参数。|1.18.1|
|[GetVideoProfile](#li_a5i_rk5_7ha)|获取视频流推流参数。|1.18.1|
|[ConfigLocalCameraPublish](#li_gbb_iev_fo5)|设置是否允许推送相机流。|1.18.1|
|[IsLocalCameraPublishEnabled](#li_sq5_96z_f8v)|查询是否允许推送相机流。|1.18.1|
|[ConfigLocalScreenPublish](#li_f4d_pqa_91i)|设置是否允许推送屏幕流。|1.18.1|
|[IsLocalScreenPublishEnabled](#li_o5a_ciq_xeq)|查询是否允许推送屏幕流。|1.18.1|
|[ConfigLocalAudioPublish](#li_f7p_epu_ssn)|设置是否允许推送音频流。|1.18.1|
|[IsLocalAudioPublishEnabled](#li_wzp_2al_2hs)|查询是否允许推送音频流。|1.18.1|
|[ConfigLocalSimulcast](#li_pnj_yud_oi3)|设置是否允许推送次要视频流小流。|1.18.1|
|[IsLocalSimulcastEnabled](#li_n1k_mm0_g3q)|查询是否允许推送次要视频流小流。|1.18.1|
|[Publish](#li_p7r_dnm_syc)|手动推送视频和音频流。|1.18.1|

录制相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartRecording](#li_au1_g0n_813)|手动开启录制。|1.18.1|
|[StopRecording](#li_ylf_u1j_e81)|手动停止录制。|1.18.1|

视频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetExternalVideoSource](#li_gfj_kml_mjj)|设置是否启用外部视频输入源。|1.18.1|
|[PushExternalVideoFrame](#li_y8p_drt_qih)|输入外部视频数据。|1.18.1|
|[AddVideoWatermark](#li_1qe_qv2_hhe)|添加水印。|1.18.11|
|[ClearVideoWatermark](#li_8br_ugg_9we)|清除对应数据流水印信息。|1.18.11|

音频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetExternalAudioSource](#li_vo8_1fn_wco)|设置是否启用外部音频输入推流。|1.18.1|
|[PushExternalAudioFrameRawData](#li_3jo_g18_sbm)|输入外部音频数据推流。|1.18.1|
|[SetExternalAudioPublishVolume](#li_etn_4fx_7t1)|设置外部输入音频推流混音音量。|1.18.1|
|[GetExternalAudioPublishVolume](#li_afn_kpe_do4)|获取外部输入音频推流混音音量。|1.18.1|
|[setAudioChannels](#li_co4_hyq_yos)|设置音频的推流模式。|1.18.12|

媒体播放器相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[CreateMediaPlayer](#li_wi0_ls1_7xl)|创建媒体播放器。|1.18.1|
|[DestroyMediaPlayer](#li_kyr_fyn_tn9)|销毁媒体播放器。|1.18.1|
|[SetEventHandler](#li_muq_76g_yj5)|设置播放器状态和事件回调通知。|1.18.1|
|[GetEventHandler](#li_fsx_klk_t63)|获取播放器状态和事件回调句柄。|1.18.1|
|[LoadResource](#li_hcf_awn_bxo)|加载播放资源。|1.18.1|
|[Start](#li_ial_sdk_l09)|开始播放。|1.18.1|
|[Stop](#li_py0_2t7_sp6)|停止播放。|1.18.1|
|[Pause](#li_3wh_pvh_lka)|暂停播放。|1.18.1|
|[Resume](#li_6rz_ukd_9rs)|恢复播放。|1.18.1|
|[SeekTo](#li_eyf_7me_0w6)|跳转播放。|1.18.1|
|[SetVolume](#li_my2_wxe_9sp)|设置播放器的音量（影响推流出去的音量）。|1.18.1|
|[SetVideoSource](#li_0w6_vud_bj3)|设置播放器的视频数据是否推流。|1.18.1|
|[EnableAudioSource](#li_z7m_8ba_gm8)|设置播放器的音频数据是否推流。|1.18.1|
|[GetDuration](#li_w9d_0ao_6kj)|获取播放的总时长。|1.18.1|
|[GetCurrentPlaybackTime](#li_gi8_5f3_d49)|获取当前的播放位置。|1.18.1|
|[GetCurrentVomume](#li_0n0_t05_4qx)|获取当前的播放音量。|1.18.1|
|[GetCurrentPlaybackState](#li_xzv_j0a_mo6)|获取当前的播放状态。|1.18.1|
|[GetIndex](#li_b9s_ki6_y50)|获取当前的播放器ID。|1.18.1|

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

-   Release：释放AliRTCEngine实例。

    ```
    void Release();
    ```

-   GetEventHandler：获取事件回调句柄。

    ```
    EngineEventHandlerInterface * GetEventHandler();
    ```

-   JoinChannel：加入频道。

    ```
    int JoinChannel(const AuthInfo &authInfo, const JoinChannelConfig &config);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |authInfo|const [AuthInfo](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) &a|认证信息，从App Server获取。|
    |config|const [JoinChannelConfig](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) &|加入频道时的设置项。|

-   LeaveChannel：离开频道。

    ```
    int LeaveChannel();
    ```

-   SetVideoProfile：设置视频流推流参数。

    **说明：** 设置之后等到下次推流的时候才能生效。

    ```
    void SetVideoProfile(AliRTCSdk::Linux::VideoProfile profile, AliRTCSdk::Linux::VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |profile|AliRTCSdk::Linux::[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|预定义的视频分辨率和帧率，详细请参见[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|
    |track|AliRTCSdk::Linux::[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   GetVideoProfile：获取视频流推流参数。

    **说明：** 返回的是正在使用的（已经推流中）或者即将被使用的（下一次推流才会生效）视频分辨率和帧率，详细请参见[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) 。返回值不一定是正在使用的[VideoProfile](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)，另外VideoTrackScreen是不支持的。

    ```
    AliRTCSdk::Linux::VideoProfile GetVideoProfile(AliRTCSdk::Linux::VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |track|AliRTCSdk::Linux:[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   ConfigLocalCameraPublish：设置是否允许推送相机流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认允许相机流推流。

    ```
    void ConfigLocalCameraPublish(bool enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送相机流。取值：    -   true：允许。
    -   false：禁止。 |

-   IsLocalCameraPublishEnabled：查询是否允许推送相机流。

    ```
    bool IsLocalCameraPublishEnabled();
    ```

    返回说明

    返回true表示允许，false表示禁止。

-   ConfigLocalScreenPublish：设置是否允许推送屏幕流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认不允许屏幕流推流。

    ```
    void ConfigLocalScreenPublish(bool enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送屏幕流。取值：    -   true：允许。
    -   false：禁止。 |

-   IsLocalScreenPublishEnabled：查询是否允许推送屏幕流。

    ```
    bool IsLocalScreenPublishEnabled();
    ```

    返回说明

    返回true表示允许，false表示禁止。

-   ConfigLocalAudioPublish：设置是否允许推送音频流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效，默认允许音频推流。

    ```
    void ConfigLocalAudioPublish(bool enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否允许推送音频流小流。取值：    -   true：允许。
    -   false：禁止。 |

-   IsLocalAudioPublishEnabled：查询是否允许推送音频流小流。

    ```
    bool IsLocalAudioPublishEnabled();
    ```

    返回说明

    返回true表示允许，false表示禁止。

-   ConfigLocalSimulcast：设置是否允许推送次要视频流小流。

    **说明：** 需要调用[Publish](#li_p7r_dnm_syc)接口才能生效。默认允许推送次要视频流。目前只支持相机流，不支持屏幕流。

    ```
    int ConfigLocalSimulcast(bool enabled, AliRTCSdk::Linux::VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enabled|bool|是否允许推送次要视频流小流。取值：    -   true：允许。
    -   false：禁止。 |
    |track|AliRTCSdk::Linux::[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频流的类型，详细请参见[VideoTrack](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)。|

-   IsLocalSimulcastEnabled：查询是否允许推送次要视频流小流。

    ```
    bool IsLocalSimulcastEnabled();
    ```

    返回说明

    返回true表示允许，false表示禁止。

-   Publish：手动推送视频和音频流。

    **说明：** 需要推送的流通过API [ConfigLocalAudioPublish](#li_f7p_epu_ssn)，[ConfigLocalCameraPublish](#li_gbb_iev_fo5)和[ConfigLocalScreenPublish](#li_f4d_pqa_91i)进行设置。

    ```
    int Publish();
    ```

-   StartRecording：手动开启录制。

    **说明：** 如果需要手工配置所有推流和拉流，请通过[JoinChannelConfig](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)字段，再[JoinChannel](#li_lp7_1fk_i0r)时，选择RecordingManually。

    ```
    int StartRecording();
    ```

-   StopRecording：手动停止录制。

    ```
    int StopRecording();
    ```

-   SetExternalVideoSource：设置是否启用外部视频输入源。

    **说明：** 启用后使用PushExternalVideoFrame接口输入视频数据。

    ```
    int SetExternalVideoSource(bool enable, bool useTexture, AliRTCSdk::Linux::VideoSource sourceType, AliRTCSdk::Linux::RenderMode renderMode = AliRTCSdk::Linux::RenderModeFill);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enabled|bool|是否启用外部视频输入源。取值：    -   true：启用。
    -   false：关闭。 |
    |useTexture|bool|是否使用texture模式，目前仅支持false。|
    |sourceType|AliRTCSdk::Linux::[VideoSource](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|流类型。|

-   PushExternalVideoFrame：输入外部视频数据。

    **说明：** 目前输入视频类型只支持I420。

    ```
    int PushExternalVideoFrame(AliRTCSdk::Linux::VideoDataSample *frame, AliRTCSdk::Linux::VideoSource sourceType);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |frame|AliRTCSdk::Linux::[VideoDataSample](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md) \*|帧数据。|
    |sourceType|AliRTCSdk::Linux::[VideoSource](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|流类型。|

-   AddVideoWatermark：添加水印。

    ```
    /**
     * @brief 通过本地文件路径添加水印
     * @param sourceType 添加水印的视频流类型
     * @param image_url 水印图片路径，只支持本地路径
     * @param options 水印配置
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否添加成功通过回调函数返回
     */
    int AddVideoWatermark(AliRTCSdk::Linux::VideoSource sourceType,
                                  const char* image_url,
                                  const AliRTCSdk::Linux::WaterMarkConfig & options);
    ```

    ```
    /**
     * @brief 通过图片内存地址添加水印
     * @param sourceType 添加水印的视频流类型
     * @param imageData 水印图片内存地址
     * @param imageLength 水印图片长度
     * @param options 水印配置
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否添加成功通过回调函数返回
     */
    int AddVideoWatermark(AliRTCSdk::Linux::VideoSource sourceType,
                                  const uint8_t* imageData,
                                  const int32_t imageLength,
                                const AliRTCSdk::Linux::WaterMarkConfig & options);
    ```

-   ClearVideoWatermark：清除对应数据流水印信息。

    ```
    /**
     * @brief 清除对应数据流水印信息
     * @param sourceType 清除水印的视频流类型
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否清除成功通过回调函数返回
     */
    virtual int ClearVideoWatermark(AliRTCSdk::Linux::VideoSource sourceType);
    ```

-   SetExternalAudioSource：设置是否启用外部音频输入推流。

    **说明：** 通过[SetExternalAudioPublishVolume](#li_etn_4fx_7t1)设置输入音频推流音量。

    ```
    int SetExternalAudioSource(bool enable, unsigned int sampleRate,  unsigned int channelsPerFrame);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否启用外部音频输入推流。取值：    -   true：启用。
    -   false：关闭。 |
    |sampleRate|unsigned int|采样率。|
    |channelsPerFrame|unsigned int|采样率。|

    返回说明

    返回值大于等于0表示设置成功，小于0表示设置失败。

-   PushExternalAudioFrameRawData：输入外部音频数据推流。

    **说明：** 当返回值为ERR\_AUDIO\_BUFFER\_FULL时，需要在间隔投递数据时间长度后再次重试投递。

    ```
    int PushExternalAudioFrameRawData(const void* audioSamples, unsigned int sampleLength, long long timestamp);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |audioSamples|const void\*|音频数据。|
    |sampleLength|unsigned int|音频数据长度。|
    |timestamp|long long|时间戳。|

    返回说明

    返回值大于等于0表示设置成功，小于0表示设置失败。

-   SetExternalAudioPublishVolume：设置外部输入音频推流混音音量。

    ```
    int SetExternalAudioPublishVolume(int volume);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |volume|int|音量，取值范围0~100。|

-   GetExternalAudioPublishVolume：获取外部输入音频推流混音音量。

    ```
    int GetExternalAudioPublishVolume();
    ```

-   setAudioChannels：设置音频的推流模式。

    ```
    int SetAudioChannels(AliRTCSdk::Linux::ExpectedAudioType type);
    ```

    参数说明

    |参数名|类型|描述|
    |---|--|--|
    |type|AliRTCSdk::Linux::[ExpectedAudioType](t2459682.md#)|声道数。|

    返回说明

    返回0表示调用成功，-1表示调用失败。

-   CreateMediaPlayer：创建媒体播放器。

    ```
    AliRTCMediaPlayerInterface * CreateMediaPlayer();
    ```

-   DestroyMediaPlayer：销毁媒体播放器。

    ```
    int DestroyMediaPlayer(AliRTCMediaPlayerInterface *mediaPlayer);
    ```

-   SetEventHandler：设置播放器状态和事件回调通知。返回0表示成功，其他表示失败。

    ```
    int SetEventHandler(AliRTCMediaPlayerEventHandlerInterface *eventHandler);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |eventHandler|AliRTCMediaPlayerEventHandlerInterface \*|播放器状态和事件回调句柄。|

    返回说明

    返回0表示设置成功，其他表示设置失败。

-   GetEventHandler：取播放器状态和事件回调句柄。

    ```
    AliRTCMediaPlayerEventHandlerInterface *GetEventHandler();
    ```

-   LoadResource：加载播放资源。真正加载资源的成功与否需要通过OnStateChange回调接口中的状态来确定。

    ```
    int LoadResource(const char *path);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |path|const char \*|播放资源的地址，目前支持本地绝对路径和在线地址。|

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   Start：开始播放。

    **说明：** 该接口需要等到播放器状态变为MediaPlayerStatePrepared才能调用。

    ```
    int Start();
    ```

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   Stop：停止播放。

    ```
    int Stop();
    ```

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   Pause：暂停播放。

    ```
    int Pause();
    ```

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   Resume：恢复播放。

    ```
    int Resume();
    ```

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   SeekTo：跳转播放。

    ```
    int SeekTo(unsigned long long millisecond);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |millisecond|unsigned long long|跳转到的播放位置，单位为毫秒。|

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   SetVolume：设置播放器的音量（影响推流出去的音量）。

    ```
    int SetVolume(int volume);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |volume|int|音量，取值范围0~100。|

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   SetVideoSource：设置播放器的视频数据是否推流。

    ```
    int SetVideoSource(bool enable, AliRTCSdk::Linux::VideoSource sourceType, AliRTCSdk::Linux::RenderMode renderMode);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否推流。取值：    -   true：允许。
    -   false：禁止。 |
    |sourceType|AliRTCSdk::Linux::[VideoSource](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|选择视频源推流。|
    |renderMode|AliRTCSdk::Linux::[RenderMode](/cn.zh-CN/SDK参考/Linux SDK/C++/数据类型.md)|视频源的缩放方式。|

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   EnableAudioSource：设置播放器的音频数据是否推流。

    ```
    int EnableAudioSource(bool enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|bool|是否推流。取值：    -   true：允许。
    -   false：禁止。 |

    返回说明

    返回0表示调用成功，其他表示调用失败。

-   GetDuration：获取播放的总时长。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的时长。

    ```
    unsigned long long GetDuration();
    ```

-   GetCurrentPlaybackTime：获取当前的播放位置。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的当前位置。

    ```
    unsigned long long GetCurrentPlaybackTime();
    ```

-   GetCurrentVomume：获取当前的播放音量。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的当前音量。

    ```
    int GetCurrentVomume();
    ```

-   GetCurrentPlaybackState：获取当前的播放状态。

    ```
    AliRTCSdk::Linux::MediaPlayerState GetCurrentPlaybackState();
    ```

-   GetIndex：获取当前的播放器ID。

    **说明：** 可以支持同时创建多个播放器，该接口可以用来区分各个播放器。

    ```
    int GetIndex();
    ```


