# AliRtcEngine接口

通过阅读本文，您可以了解到Linux SDK（Java）的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[createInstance](#li_0fz_o4e_94s)|创建AliRTCEngine实例。|1.18.1|
|[destroy](#li_n0w_nj6_9ks)|销毁AliRTCEngine实例。|1.18.1|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[joinChannel](#li_ewc_9e8_wqb)|加入频道。|1.18.1|
|[leaveChannel](#li_6uz_mpg_9jz)|离开频道。|1.18.1|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#li_t59_nbp_sf4)|设置视频流推流参数。|1.18.1|
|[getVideoProfile](#li_pz0_k9d_80p)|获取视频流推流参数。|1.18.1|
|[configLocalCameraPublish](#li_79a_htx_se4)|设置是否允许推送相机流。|1.18.1|
|[isLocalCameraPublishEnabled](#li_gl1_97m_l04)|查询是否允许推送相机流。|1.18.1|
|[configLocalScreenPublish](#li_mqm_aep_88e)|设置是否允许推送屏幕流。|1.18.1|
|[isLocalScreenPublishEnabled](#li_vtg_elw_mpd)|查询是否允许推送屏幕流。|1.18.1|
|[configLocalAudioPublish](#li_e12_sbu_n5h)|设置是否允许推送音频流。|1.18.1|
|[isLocalAudioPublishEnabled](#li_nv2_k5j_dsc)|查询是否允许推送音频流。|1.18.1|
|[configLocalSimulcast](#li_aim_aw8_mpj)|设置是否允许推送次要视频流小流。|1.18.1|
|[isLocalSimulcastEnabled](#li_8b5_n46_f8n)|查询是否允许推送次要视频流小流。|1.18.1|
|[publish](#li_7rq_pvj_lxs)|手动推送视频和音频流。|1.18.1|

录制相关接口

|API|描述|以上版本支持|
|---|--|------|
|[startRecording](#li_37q_jb1_tfr)|手动开启录制。|1.18.1|
|[stopRecording](#li_hxw_9ba_wag)|手动停止录制。|1.18.1|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setExternalVideoSource](#li_4yu_74q_31m)|设置是否启用外部视频输入源。|1.18.1|
|[pushExternalVideoFrame](#li_i55_kih_8sw)|输入外部视频数据。|1.18.1|
|[addVideoWatermark](#li_304_swt_rsf)|添加水印。|1.18.11|
|[clearVideoWatermark](#li_e1s_7fa_nad)|清除对应数据流水印信息。|1.18.11|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setExternalAudioSource](#li_rg0_qma_zc3)|设置是否启用外部音频输入推流。|1.18.1|
|[pushExternalAudioFrameRawData](#li_6oq_ux1_0w6)|输入外部音频数据推流。|1.18.1|
|[setExternalAudioPublishVolume](#li_8y8_bso_w1d)|设置外部输入音频推流混音音量。|1.18.1|
|[getExternalAudioPublishVolume](#li_xx2_wkl_ren)|获取外部输入音频推流混音音量。|1.18.1|

媒体播放器相关接口

|API|描述|以上版本支持|
|---|--|------|
|[createMediaPlayer](#li_uu2_b7c_ml2)|创建媒体播放器。|1.18.1|
|[destroyMediaPlayer](#li_ubz_21z_drb)|销毁媒体播放器。|1.18.1|
|[setEventHandler](#li_xd8_47w_whn)|设置播放器状态和事件回调通知。|1.18.1|
|[loadResource](#li_4an_r0j_kyf)|加载播放资源。|1.18.1|
|[start](#li_egq_g9x_50x)|开始播放。|1.18.1|
|[stop](#li_4zv_ejz_kfx)|停止播放。|1.18.1|
|[pause](#li_y0w_ob4_w6n)|暂停播放。|1.18.1|
|[resume](#li_nlx_s1w_kpr)|恢复播放。|1.18.1|
|[seekTo]()|跳转播放。|1.18.1|
|[setVideoSource](#li_ptj_b6e_oec)|设置播放器的视频数据是否推流。|1.18.1|
|[enableAudioSource](#li_da7_ltl_xxv)|设置播放器的音频数据是否推流。|1.18.1|
|[setVolume](#li_f52_kaz_o1s)|设置播放器的音量（影响推流出去的音量）。|1.18.1|
|[getDuration](#li_61p_vvc_hgd)|获取播放的总时长。|1.18.1|
|[getCurrentPlaybackTime](#li_wfg_l2d_q34)|获取当前的播放位置。|1.18.1|
|[getCurrentVomume](#li_x1x_904_qaa)|获取当前的播放音量。|1.18.1|
|[getCurrentPlaybackState](#li_g10_s0n_wcl)|获取当前的播放状态。|1.18.1|
|[getIndex](#li_bvf_wn4_4i0)|获取当前的播放器ID。|1.18.1|

## 接口详情

-   createInstance：创建AliRTCEngine实例。

    ```
    public static AliRTCLinuxEngine createInstance(AliRTCLinuxEngineListener listener, int lowPort, int highPort, String logPath, String coreServicePath) {
                        return new AliRTCLinuxEngineImpl(listener, lowPort, highPort, logPath, coreServicePath);
                    }
    ```

    |参数名|类型|描述|
    |---|--|--|
    |listener|AliRTCLinuxEngineListener|录制SDK所触发的事件通过 AliRTCLinuxEngineListener类回调通知。|
    |lowPort|int|最小的可用端口。 **说明：** 创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。 |
    |highPort|int|最大的可用端口。 **说明：** 创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。 |
    |logPath|String|保存日志的路径。|
    |coreServicePath|String|AliRtcCoreService可执行程序存放的绝对路径。|

-   destroy：销毁AliRTCEngine实例。

    ```
    public abstract void destroy();
    ```

-   joinChannel：加入频道。

    ```
    public abstract int joinChannel(AuthInfo authInfo, JoinChannelConfig config);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |authInfo|[AuthInfo](#li_840_oxo_a2y)|认证信息，从App Server获取。|
    |config|[JoinChannelConfig](#li_hsk_phh_cpy)|加入频道时的设置项。|

-   leaveChannel：离开频道。

    ```
    public abstract int leaveChannel();
    ```

-   setVideoProfile：设置视频流推流参数。

    **说明：** 设置之后等到下次推流的时候才能生效。

    ```
    public abstract void setVideoProfile(VideoProfile profile, VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |profile|[VideoProfile](#li_dpv_hd0_mk2)|预定义的视频分辨率和帧率，具体请参见[VideoProfile](#li_dpv_hd0_mk2)。|
    |track|[VideoTrack](#li_eny_1bk_jqr)|视频流的类型，具体请参见[VideoTrack](#li_eny_1bk_jqr)。|

-   getVideoProfile：获取视频流推流参数。

    **说明：** 返回的是正在使用的（已经推流中）或者即将被使用的（下一次推流才会生效）视频分辨率和帧率，具体请参见[VideoProfile](#li_dpv_hd0_mk2)。返回值不一定是正在使用的[VideoProfile](#li_dpv_hd0_mk2)，另外不支持VideoTrackScreen。

    ```
    public abstract int getVideoProfile(VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |track|[VideoTrack](#li_eny_1bk_jqr)|视频流的类型，具体请参见[VideoTrack](#li_eny_1bk_jqr)。|

-   configLocalCameraPublish：设置是否允许推送相机流。

    **说明：** 需要调用[publish](#li_7rq_pvj_lxs)才能生效。默认允许相机流推流。

    ```
    public abstract void configLocalCameraPublish(boolean enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否允许推送相机流。true：允许，false：禁止。|

-   isLocalCameraPublishEnabled：查询是否允许推送相机流。返回值，true表示允许，false表示禁止。

    ```
    public abstract boolean isLocalCameraPublishEnabled();
    ```

-   configLocalScreenPublish：设置是否允许推送屏幕流。

    **说明：** 需要调用[publish](#li_7rq_pvj_lxs)接口才能生效。默认不允许屏幕流推流。

    ```
    public abstract void configLocalScreenPublish(boolean enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否允许推送屏幕流。true：允许，false：禁止。|

-   isLocalScreenPublishEnabled：查询是否允许推送屏幕流。返回值，true表示允许，false表示禁止。

    ```
    public abstract boolean isLocalScreenPublishEnabled();
    ```

-   configLocalAudioPublish：设置是否允许推送音频流。

    **说明：** 需要调用[publish](#li_7rq_pvj_lxs)接口才能生效，默认允许音频推流。

    ```
    public abstract void configLocalAudioPublish(boolean enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否允许推送音频流。true：允许，false：禁止。|

-   isLocalAudioPublishEnabled：查询是否允许推送音频流。返回值，true表示允许，false表示禁止。

    ```
    public abstract boolean isLocalAudioPublishEnabled();
    ```

-   configLocalSimulcast：设置是否允许推送次要视频流小流。

    **说明：** 需要调用[publish](#li_7rq_pvj_lxs)接口才能生效。默认允许推送次要视频流。目前只支持相机流，不支持屏幕流。

    ```
    public abstract int configLocalSimulcast(boolean enabled, VideoTrack track);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enabled|boolean|是否允许推送次要视频流小流。true：允许，false：禁止。|
    |track|[VideoTrack](#li_eny_1bk_jqr)|视频流的类型，详细请参见[VideoTrack](#li_eny_1bk_jqr)。|

-   isLocalSimulcastEnabled：查询是否允许推送次要视频流小流。返回值，true表示允许，false表示禁止。

    ```
    public abstract boolean isLocalSimulcastEnabled();
    ```

-   publish：手动推送视频和音频流。

    **说明：** 需要推送的流通过API [configLocalAudioPublish](#li_e12_sbu_n5h)，[configLocalCameraPublish](#li_79a_htx_se4)和[configLocalScreenPublish](#li_mqm_aep_88e)进行设置。

    ```
    public abstract int publish();
    ```

-   startRecording：手动开启录制。

    **说明：** 如果需要手工配置所有推流和拉流，请通过[JoinChannelConfig](#li_hsk_phh_cpy)字段，再[joinChannel](#li_ewc_9e8_wqb)时，选择RecordingManually。

    ```
    public abstract int startRecording();
    ```

-   stopRecording：手动停止录制。

    ```
    public abstract int stopRecording();
    ```

-   setExternalVideoSource：设置是否启用外部视频输入源。

    **说明：** 启用后使用[PushExternalVideoFrame](#li_i55_kih_8sw)接口输入视频数据。

    ```
    public abstract int setExternalVideoSource(boolean enable, boolean useTexture, VideoSource source, RenderMode renderMode);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否启用外部视频输入源。true：开启，false：关闭。|
    |useTexture|boolean|是否使用texture模式，目前只支持false。|
    |source|[VideoSource](#li_pg5_xu6_yt9)|流类型。|
    |renderMode|[RenderMode](#li_dv2_e64_nnt)|绘制模式。|

-   pushExternalVideoFrame：输入外部视频数据。

    **说明：** 目前输入视频类型只支持I420。

    ```
    public abstract int pushExternalVideoFrame(VideoDataSample frame, VideoSource source);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |frame|[VideoDataSample](#li_lf0_zi6_ibk)|帧数据。|
    |source|[VideoSource](#li_pg5_xu6_yt9)|流类型。|

-   addVideoWatermark：添加水印。

    ```
    /**
     * @brief 通过本地文件路径添加水印
     * @param sourceType 添加水印的视频流类型
     * @param image_url 水印图片路径，只支持本地路径
     * @param config 水印配置
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否添加成功通过回调函数返回
    */
    public abstract int addVideoWatermark(VideoSource sourceType, String imageUrl, WaterMarkConfig config);
    ```

    ```
    /**
     * @brief 通过图片内存地址添加水印
     * @param sourceType 添加水印的视频流类型
     * @param imageData 水印图片内存地址
     * @param imageLength 水印图片长度
     * @param config 水印配置
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否添加成功通过回调函数返回
     */
    public abstract int addVideoWatermark(VideoSource sourceType, byte[] imageData, int imageLength, WaterMarkConfig config);
    ```

-   clearVideoWatermark：清除对应数据流水印信息。

    ```
    /**
     * @brief 清除对应数据流水印信息
     * @param sourceType 清除水印的视频流类型
     * @return 0:接口调用成功，-1:接口调用失败
     * @note 该接口返回值只表示接口调用是否成功，真正的水印是否清除成功通过回调函数返回
       */
      public abstract int clearVideoWatermark(VideoSource sourceType);
    ```

-   setExternalAudioSource：设置是否启用外部音频输入推流。返回值，大于等于0表示成功，小于0表示失败。

    **说明：** 您可以通过[setExternalAudioPublishVolume](#li_8y8_bso_w1d)设置输入音频推流音量。

    ```
    public abstract int setExternalAudioSource(boolean enable, int sampleRate, int channelsPerFrame);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否启用外部音频输入推流。true：开启，false：关闭。|
    |sampleRate|int|采样率。|
    |channelsPerFrame|int|采样率。|

-   pushExternalAudioFrameRawData：输入外部音频数据推流。返回值，大于等于0表示成功，小于0表示失败。

    **说明：** 当返回值为ERR\_AUDIO\_BUFFER\_FULL时，需要在间隔投递数据时间长度后再次重试投递。

    ```
    public abstract int pushExternalAudioFrameRawData(byte[] audioSamples, int sampleLength, long timestamp);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |audioSamples|byte\[\]|音频数据。|
    |sampleLength|int|音频数据长度。|
    |timestamp|long|时间戳。|

-   setExternalAudioPublishVolume：设置外部输入音频推流混音音量。

    ```
    public abstract int setExternalAudioPublishVolume(int volume);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |volume|int|音量，取值范围0~100。|

-   getExternalAudioPublishVolume：获取外部输入音频推流混音音量。

    ```
    public abstract int getExternalAudioPublishVolume();
    ```

-   createMediaPlayer：创建媒体播放器。

    ```
    public abstract AliRTCLinuxMediaPlayer createMediaPlayer();
    ```

-   destroyMediaPlayer：销毁媒体播放器。

    ```
    public abstract int destroyMediaPlayer(AliRTCLinuxMediaPlayer player);
    ```

-   setEventHandler：设置播放器状态和事件回调通知。返回0表示成功，其他表示失败。

    ```
    public int setEventHandler(AliRTCLinuxMediaPlayerListener eventHandler);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |eventHandler|AliRTCLinuxMediaPlayerListener|播放器状态和事件回调句柄。|

-   loadResource：加载播放资源。返回0表示接口调用成功，其他表示失败。真正加载资源的成功与否需要通过OnStateChange回调接口中的状态来确定。

    ```
    public int loadResource(String path);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |path|String|播放资源的地址，目前支持本地绝对路径和在线地址。|

-   start：开始播放。返回0表示接口调用成功，其他表示失败。

    **说明：** 该接口需要等到播放器状态变为MediaPlayerStatePrepared才能调用。

    ```
    public int start();
    ```

-   stop：停止播放。return 0表示接口调用成功，其他表示接口调用失败。

    ```
    public int stop();
    ```

-   pause：暂停播放。返回0表示接口调用成功，其他表示失败。

    ```
    public int pause();
    ```

-   resume：恢复播放。返回0表示接口调用成功，其他表示失败。

    ```
    public int resume();
    ```

-   seekTo：跳转播放。返回0表示接口调用成功，其他表示失败。

    ```
    public int seekTo(long millisecond);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |millisecond|long|跳转到的播放位置，毫秒为单位。|

-   setVideoSource：设置播放器的视频数据是否推流。返回0为接口调用成功，其他表示失败。

    ```
    public int setVideoSource(boolean enable, AliRTCLinuxEngine.VideoSource source, AliRTCLinuxEngine.RenderMode renderMode);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否推流。true：允许，false：禁止。|
    |source|AliRTCLinuxEngine.[VideoSource](#li_pg5_xu6_yt9)|选择视频源推流。|
    |renderMode|AliRTCLinuxEngine.[RenderMode](#li_dv2_e64_nnt)|视频源的缩放方式。|

-   enableAudioSource：设置播放器的音频数据是否推流。返回0为接口调用成功，其他表示失败。

    ```
    public int enableAudioSource(boolean enable);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |enable|boolean|是否推流。true：允许，false：禁止。|

-   setVolume：设置播放器的音量（影响推流出去的音量）。返回0为接口调用成功，其他表示失败。

    ```
    public int setVolume(int volume);
    ```

    |参数名|类型|描述|
    |---|--|--|
    |volume|int|音量，取值范围0~100。|

-   getDuration：获取播放的总时长。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的时长。

    ```
    public long getDuration();
    ```

-   getCurrentPlaybackTime：获取当前的播放位置。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的当前位置。

    ```
    public long getCurrentPlaybackTime();
    ```

-   getCurrentVomume：获取当前的播放音量。

    **说明：** 需要等到播放器的状态为MediaPlayerStatePrepared才能获取到准确的当前音量。

    ```
    public int getCurrentVomume();
    ```

-   getCurrentPlaybackState：获取当前的播放状态。

    ```
    public MediaPlayerState getCurrentPlaybackState();
    ```

-   getIndex：获取当前的播放器ID。

    **说明：** 支持同时创建多个播放器，该接口可以用来区分各个播放器。

    ```
    public int getIndex();
    ```


