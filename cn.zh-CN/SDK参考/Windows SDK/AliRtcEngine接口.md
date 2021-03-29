---
keyword: [Windows SDK, AliRtcEngine]
---

# AliRtcEngine接口

通过阅读本文，您可以了解到Windows SDK的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[setH5CompatibleMode](#li_eik_68q_ra3)|设置H5兼容模式。|1.1|
|[getH5CompatibleMode](#li_ivi_bi0_nsr)|检查当前是否兼容H5。|1.1|
|[sharedInstance](#li_ewc_69e_z4v)|创建AliRtcEngine实例（同一时间只会存在一个实例）。|1.1|
|[destroy](#p_atk_la4_6xb)|SDK资源释放。|1.1|
|[uploadLog](#p_g6j_jaw_lvz)|上传日志。|1.15|
|[setLogDirPath](#li_x23_2sw_0dj)|设置SDK日志文件保存路径。|1.16.2|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAutoPublishSubscribe](#li_20l_a4j_amg)|设置是否自动发布，是否自动订阅。|1.1|
|[joinChannel](#li_njy_0qb_ly6)|加入频道。|1.1|
|[leaveChannel](#li_26r_sr5_m42)|离开频道。|1.1|
|[isInCall](#li_o22_ahk_u9h)|检查当前是否在频道中。|1.1|
|[setChannelProfile](#p_lui_m89_8x0)|设置频道模式。|1.15|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoPublish](#li_y24_thz_rke)|查询当前是否为自动发布模式。|1.1|
|[configLocalCameraPublish](#li_mzv_wbb_7b4)|设置是否允许发布相机流。|1.1|
|[isLocalCameraPublishEnabled](#li_ccc_wma_el0)|查询当前是否允许发布相机流。|1.1|
|[configLocalScreenPublish](#ul_12h_ml2_gn3)|设置是否允许发布屏幕流。|1.1|
|[isLocalScreenPublishEnabled](#li_0yf_fds_qf7)|查询当前是否允许发布屏幕流。|1.1|
|[configLocalAudioPublish](#li_snp_x6o_6ke)|设置是否允许发布音频流。|1.1|
|[isLocalAudioPublishEnabled](#li_ple_3e4_knv)|查询当前是否允许推音频流。|1.1|
|[configLocalSimulcast](#li_4ed_zzo_ws7)|设置是否允许发布次要视频流。|1.1|
|[isLocalSimulcastEnabled](#li_zib_k44_u5n)|查询当前是否允许发布次要视频流。|1.1|
|[publish](#li_j0c_8ha_mkf)|手动发布视频和音频流。|1.1|

订阅相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoSubscribe](#li_y06_1v7_4yp)|查询当前是否为自动订阅模式。|1.1|
|[configRemoteCameraTrack](#li_hzh_mxa_dwd)|设置是否订阅远端相机流。|1.1|
|[configRemoteScreenTrack](#li_6bo_w1e_11x)|设置是否订阅远端屏幕流。|1.1|
|[configRemoteAudio](#li_ygq_c9o_8yv)|设置是否订阅远端音频流。|1.1|
|[subscribe](#li_tt0_qjx_7jd)|手动订阅视频和音频流。|1.1|
|[subscribeAudioData](#li_cdw_ssl_h9u)|订阅音频数据。|1.16.2|
|[unsubscribeAudioData](#li_wb3_ata_6pv)|取消订阅音频数据。|1.16.2|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#li_2yq_6hy_ly4)|设置视频流的参数。|1.1|
|[setLocalViewConfig](#li_boe_ta9_56c)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[muteLocalCamera](#li_zmn_zvo_xb3)|设置是否停止发布本地视频流。|1.1|
|[setRemoteViewConfig](#li_d82_b2q_rwp)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[getCameraList](#li_4s5_8op_9zp)|获取摄像头列表。|1.1|
|[getCurrentCamera](#li_699_y8a_roe)|获取当前使用的摄像头名称。|1.1|
|[setCurrentCamera](#li_dif_60c_bj0)|选择摄像头。|1.1|
|[isCameraOn](#li_blw_lj4_7ud)|检查摄像头是否打开。|1.1|
|[getScreenShareSourceInfo](#p_317_0qt_xk7)|获取屏幕分享源信息。|1.15|
|[getDesktopResolution](#p_zc1_t1e_xk0)|获取屏幕分享桌面分辨率。|1.15|
|[setScreenShareSource](#p_lpt_u8n_0ul)|设置屏幕分享源。|1.15|
|[getScreenShareSource](#p_l7r_n6o_duv)|获取屏幕分享源。|1.15|
|[getCurrentCameraId](#li_0mg_p84_wld)|获取当前使用的摄像头ID。|1.16.2|
|[setCurrentCameraById](#li_0m5_zo9_fx4)|通过设备ID选择摄像头。|1.16.2|
|[setExternalVideoSource](#li_0xy_z70_q7p)|启用外部视频输入源。|1.16.2|
|[pushExternalVideoFrame](#li_a8a_p29_jz6)|输入外部视频。|1.16.2|
|[registerVideoSampleObserver](#li_oiw_qeo_f47)|订阅视频数据输出。|1.16.2|
|[unRegisterVideoSampleObserver](#li_udw_myc_w1u)|取消订阅视频数据输出。|1.16.2|
|[stopRecord](#li_hil_ejg_u05)|停止录制。|1.17|
|[startRecord](#li_ibs_7or_7f1)|开始录制。|1.17|
|[setBeatutyEffect](#li_6ry_ktc_rwr)|设置基础美颜。|1.17.9|
|[setVideoEncoderConfiguration](#li_id4_n96_0s8)|设置视频编码属性。|1.17.31|
|[setScreenShareSourceByRegion](#li_43m_dpj_ium)|通过指定区域设置屏幕分享源。|1.17.38|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAudioOnlyMode](#li_b6f_8c6_gbf)|设置为纯音频模式还是音视频模式。|1.1|
|[isAudioOnly](#li_v3p_fn5_77l)|查询当前是否为纯音频模式。|1.1|
|[muteLocalMic](#li_2jh_h21_msx)|设置是否停止发布本地音频。|1.1|
|[muteRemoteAudioPlaying](#li_egc_9yv_5u1)|设置是否停止播放远端音频流。|1.1|
|[getAudioCaptures](#li_d9x_owo_4lz)|获取系统中的录音设备列表。|1.1|
|[getCurrentAudioCapture](#li_lab_wrn_ec1)|获取当前使用的音频采集设备名称。|1.1|
|[setCurrentAudioCapture](#li_yw8_27w_0ys)|选择音频采集设备。|1.1|
|[getAudioRenderers](#li_0nk_kuf_tsb)|获取系统中的扬声器列表。|1.1|
|[getCurrentAudioRenderer](#li_jb7_tgf_3za)|获取当前使用的音频播放设备。|1.1|
|[setCurrentAudioRenderer](#li_98c_3b6_tle)|选择音频播放设备。|1.1|
|[startAudioCapture](#li_fq9_umm_iw2)|开启音频采集。|1.11|
|[stopAudioCapture](#li_eid_iu8_qla)|关闭音频采集。|1.11|
|[startAudioPlayer](#li_03a_xze_kht)|开启音频播放设备。|1.11|
|[stopAudioPlayer](#li_1b2_wqw_476)|关闭音频播放。|1.11|
|[muteAllRemoteAudioPlaying](#li_zaz_6nd_45r)|停止远端的所有音频流的播放。|1.16.2|
|[getCurrentAudioCaptureId](#li_3u4_m7y_pds)|获取使用的录音设备ID。|1.16.2|
|[setCurrentAudioCaptureById](#li_qop_99b_tkd)|通过设备ID选择录音设备。|1.16.2|
|[getCurrentAudioRendererId](#li_vf6_e4h_s93)|获取当前使用的扬声器ID。|1.16.2|
|[setCurrentAudioRendererById](#li_bdg_sy1_eua)|通过设备ID选择扬声器。|1.16.2|
|[setRecordingVolume](#li_yfg_7nj_yng)|设置录音音量。|1.16.2|
|[setPlayoutVolume](#li_bkk_ap5_hz2)|设置播放音量。|1.16.2|
|[setSubscribeAudioNumChannel](#li_8gd_ys2_tza)|设置输出音频声道数。|1.16.2|
|[setSubscribeAudioSampleRate](#li_4u6_1ma_05h)|设置输出音频采样率。|1.16.2|
|[setExternalAudioSource](#li_ssg_4dq_tk0)|设置是否将外部音频数据作为推流的输入源。|1.16.2|
|[pushExternalAudioFrameRawData](#li_v45_qx6_mu1)|输入音频数据。|1.16.2|
|[setMixedWithMic](#li_gyr_ek2_3fr)|设置外部音频输入是否与麦克风采集音频混合。|1.16.2|
|[setExternalAudioPublishVolume](#li_xu2_obb_2s5)|设置外部音频输入音量。|1.16.2|
|[getExternalAudioPublishVolume](#li_hn9_iwe_78n)|获取外部音频输入音量。|1.17|
|[setExteranlAudioRender](#li_8f0_6i2_eao)|设置是否启用外部输入音频播放。|1.16.2|
|[pushExternalAudioRenderRawData](#li_33d_3yn_36j)|输入音频播放数据。|1.16.2|
|[setExternalAudioPlayoutVolume](#li_i7a_nbu_gst)|设置外部音频播放音量。|1.16.2|
|[getExternalAudioPlayoutVolume](#li_2l3_lox_gpi)|获取音频播放音量。|1.16.2|
|[setAudioEffectReverbMode](#li_oj3_h2z_bf0)|设置混响音效模式。|1.17|
|[setAudioEffectReverbParamType](#li_4de_b93_kur)|设置混响音效类型。|1.17|
|[setVolumeCallbackIntervalMs](#li_xnx_bpx_kaq)|设置音量回调频率和平滑系数。|1.17.9|
|[setRecordingDeviceVolume](#li_dmp_lyt_jvs)|设置音频采集设备音量。|1.17.30|
|[getRecordingDeviceVolume](#li_8us_jpf_f4z)|获取音频采集设备音量。|1.17.30|
|[setPlaybackDeviceVolume](#li_x38_l1w_yxl)|设置音频播放设备音量。|1.17.30|
|[getPlaybackDeviceVolume](#li_n3a_yap_ccy)|获取音频播放设备音量。|1.17.30|

预览接口

|API|描述|以上版本支持|
|---|--|------|
|[startPreview](#li_ekr_w7u_a2i)|开始本地预览。|1.1|
|[stopPreview](#li_oj2_j9e_a5l)|停止本地预览。|1.1|

远端用户查询接口

|API|描述|以上版本支持|
|---|--|------|
|[getOnlineRemoteUsers](#li_wn6_uv1_kz5)|获取远端在线用户列表。|1.1|
|[getUserInfo](#li_onp_yfn_0l9)|查询远端用户信息。|1.1|
|[isUserOnline](#li_a74_vi7_djz)|查询用户是否在线。|1.1|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[setLogLevel](#li_pq3_mnx_xoj)|设置日志级别。|1.1|
|[getSdkVersion](#li_eif_r1z_cp6)|获取SDK版本号。|1.1|
|[setClientRole](#li_f8v_rmb_nt5)|设置用户角色。|1.16|
|[startLastmileDetect](#li_86e_5vv_k9i)|开始网络质量探测。|1.16.2|
|[stopLastmileDetect](#li_lz0_f1w_8nd)|停止网络质量探测。|1.16.2|
|[postFeedback](#li_ycg_cei_k34)|SDK问题反馈。|1.17.12|
|[sendMediaExtensionMsg](#li_nsq_ydf_7w2)|发送媒体扩展信息。|1.17.1|
|[getClientRole](#li_x8l_wro_d8z)|获取用户角色。|1.17.19|
|[startIntelligentDenoise](#li_hpd_dpw_lv8)|开启智能降噪。|1.17.19|
|[stopIntelligentDenoise](#li_gcp_tcl_p5w)|关闭智能降噪。|1.17.19|
|[RefreshAuthInfo](#li_nle_9pj_7t0)|刷新令牌。|1.17.41|

## 接口详情

-   setH5CompatibleMode：设置是否兼容H5。

    ```
    static void setH5CompatibleMode(bool comp)         
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |comp|bool|true表示兼容H5，false表示不兼容H5。默认不兼容H5。|

    **说明：** 当前版本不支持在创建AliRtcEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此方法

-   getH5CompatibleMode：检查当前是否兼容H5。

    ```
    static bool getH5CompatibleMode()               
    ```

    返回说明

    true表示兼容H5，false表示不兼容H5。

-   sharedInstance：创建AliRTCEngine实例。

    ```
    static AliRtcEngine* sharedInstance(AliRtcEventListener* listener, const AliRtc::String &extras)         
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |listener|[AliRtcEventListener\*](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)|AliRtcEngine回调的监听器。|
    |extras|const AliRtc::String &|通过JSON配置SDK的特别功能，详情请参见[extras功能说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。|

    **说明：** 同一时间只会存在一个实例。

-   destroy：SDK资源释放。

    ```
    static AliRtcEngine::destroy();
    ```

    **说明：** 在所有操作结束之后调用。

-   uploadLog：上传日志。默认离会自动上传。

    ```
    static void uploadLog();
    ```

-   setLogDirPath：设置SDK日志文件保存路径。

    ```
    static int setLogDirPath(const AliRtc::String &logDirPath)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logDirPath|const AliRtc::String &|日志文件保存绝对路径。默认路径：%appdata%目录下。|

    返回说明

    0表示方法调用成功，非0表示方法调用失败。

    **说明：** 如需调用此接口，请在调用所有SDK接口前进行设置，避免日志出现丢失，同时App必须保证指定的目录已存在且可写入。

-   setAutoPublishSubscribe：设置是否自动发布和是否自动订阅。

    ```
    int setAutoPublishSubscribe(bool autoPub, bool autoSub)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |autoPub|bool|true表示自动发布，false表示手动发布。默认为true。|
    |autoSub|bool|true表示自动订阅，false表示手动订阅。默认为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口必须在加入频道之前调用。

-   joinChannel：加入频道。

    ```
    void joinChannel(const AliRtcAuthInfo& authInfo, const AliRtc::String& userName, void(*)(void* opaquePtr, int errCode) onResult, void* opaquePtr)                  
    ```

    加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道，如果加入频道失败，需要重试时，无需先调用leaveChannel。

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|const [AliRtcAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)&|鉴权信息。|
    |userName|const AliRtc::String&|用户的显示名称（不是用户ID）。|
    |onResult|void\(\)\(void opaquePtr, int errCode\)|加入频道执行结束后回调。|
    |opaquePtr|void\*|App提供的UserData，在调用onResult时传回App。|

    **说明：** 该接口是异步接口，是否成功加入频道，通过onResult判断，lambda表达式转换成onResult。

    ```
    void (*foo)(void*, int);
    foo = [](void* opaquePtr, int errCode) {
    ClassA *pThis = (ClassA *)opaquePtr;
    if(errCode != 0) {
    pThis->OutputError("Failed to exeucte joinChannel.");
    }
    };
    mpEngine->joinChannel(/*authInfo*/， /*userName*/， foo， /*opaquePtr*/)
    ```

-   leaveChannel：离开频道。

    ```
    void leaveChannel()
    ```

    1.15及以上版本：销毁引擎只能通过destroy方法。

    1.15以下版本：离开频道时，AliRtcEngine实例会被销毁，如需继续加入频道等操作，需要重新调用getInstance初始化AliRtcEngine实例。

    **说明：** 如果当前不在频道内，调用leaveChannel不会对实例产生任何影响，但会产生消息，通知频道内其他用户。

-   isInCall：检查当前是否在频道中。

    ```
    bool isInCall()                
    ```

    返回说明

    true表示在频道中，false表示不在频道中。

-   setChannelProfile：设置频道模式。

    ```
    int setChannelProfile(const AliRtcChannelProfile channelProfile)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |channelProfile|[AliRtcChannelProfile](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|频道类型。默认为AliRtcCommunication。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

-   isAutoPublish：查询当前是否为自动发布模式。

    ```
    bool isAutoPublish()                
    ```

    返回说明

    true表示自动发布，false表示手动发布。

-   configLocalCameraPublish：设置是否允许发布相机流。

    ```
    void configLocalCameraPublish(bool enable)               
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示允许发布相机流，false表示不允许发布相机流。默认为true。|

    **说明：** 该接口在手动调用时，需要调用publish才能生效。

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流。

    ```
    public abstract boolean isLocalCameraPublishEnabled()                   
    ```

    返回说明

    true表示允许发布相机流，false表示不允许发布相机流。

-   configLocalScreenPublish：设置是否允许发布屏幕流。

    ```
    void configLocalScreenPublish(bool enable)                
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示允许发布屏幕流，false表示不允许发布屏幕流。默认为false。|

    **说明：** 该接口在手动调用时，需要调用publish才能生效。

-   isLocalScreenPublishEnabled：查询当前是否允许发布屏幕流。

    ```
    bool isLocalScreenPublishEnabled()                
    ```

    返回说明

    true表示允许发布屏幕流，false表示不允许发布屏幕流。

-   configLocalAudioPublish：设置是否允许发布音频流。

    ```
    void configLocalAudioPublish(bool enable)        
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示允许发布音频流，false表示不允许发布音频流。默认为true。|

    **说明：** 该接口在手动调用时，需要调用publish才能生效。

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流。

    ```
    bool isLocalAudioPublishEnabled()               
    ```

    返回说明

    true表示允许发布音频流，false表示不允许发布音频流。

-   configLocalSimulcast：设置是否允许发布次要视频流。

    ```
    int AliRtcEngine::configLocalSimulcast(bool enabled, AliRtcVideoTrack track)     
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示允许发布次要视频流，false表示不允许发布次要视频流。默认为true。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|流类型，当前只支持AliVideoTrackCamera（相机流）。|

    **说明：** 该接口在手动调用时，需要调用publish才能生效。

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流。

    ```
    bool isLocalSimulcastEnabled()               
    ```

    返回说明

    true表示允许发布次要视频流，false表示不允许发布次要视频流。

-   publish：手动发布视频和音频流。

    ```
    void publish(void(*)(void* opaquePtr, int errCode) onResult, void* opaquePtr)             
    ```

    -   调用publish的实际表现需要结合configLocalCameraPublish、configLocalScreenPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述4个接口的参数，以发布相应的视频和音频流。
    参数说明

    |名称|类型|描述|
    |--|--|--|
    |onResult|void\(\)\(void opaquePtr, int errCode\)|调用publish执行结束后回调。|
    |opaquePtr|void\*|App提供的UserData，在调用onResult时传回App。|

    **说明：** 该接口是异步接口，通过onResult判断调用结果，lambda表达式转换成onResult。

    ```
    void (*foo)(void *, int);
    foo = [](void*opaquePtr,  int errCode) {
    ClassA *pThis = (ClassA *)opaquePtr;
    pThis->OutputError("publish result: %d", errCode);
    };
    publish(foo, /*UserData*/);
    ```

-   isAutoSubscribe：查询当前是否为自动订阅模式。

    ```
    bool isAutoSubscribe()                
    ```

    返回说明

    true表示自动订阅，false表示手动订阅。

-   configRemoteCameraTrack：设置是否订阅远端相机流。

    ```
    void configRemoteCameraTrack(const AliRtc::String& uid, bool preferMaster, bool enable)               
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |preferMaster|bool|true表示订阅大流，false表示订阅次小流。默认为true。|
    |enable|bool|true表示订阅远端相机流，false表示停止订阅远端相机流。默认不订阅。|

    **说明：** 该接口在调用对流进行操作时，例如：手动订阅，关闭订阅。必须调用subscribe才能生效。

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。

    ```
    void configRemoteScreenTrack(const AliRtc::String& uid, bool enable)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |enable|bool|true表示订阅远端屏幕流，false表示停止订阅远端屏幕流。默认为false。|

    **说明：** 该接口在调用对流进行操作时，例如：手动订阅，关闭订阅。必须调用subscribe才能生效。

-   configRemoteAudio：设置是否订阅远端音频流。

    ```
    void configRemoteAudio(const AliRtc::String& uid, bool enable)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |enable|bool|true表示订阅远端音频流，false表示停止订阅远端音频流。默认为true。|

    **说明：** 该接口在调用对流进行操作时，例如：手动订阅，关闭订阅。必须调用subscribe才能生效。

-   subscribe：手动订阅视频和音频流。

    ```
    void subscribe(const AliRtc::String& uid, void(*)(void* opaquePtr, const AliRtc::String& uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) onResult, void * opaquePtr)                
    ```

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频流和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如果需停止订阅，则需要上述3个配置接口的参数都置为false，然后调用subscribe。
    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |onResult|void\(\)\(void opaquePtr, const AliRtc::String& uid, [AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) vt, [AliRtcAudioTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) at\)|调用subscribe执行结束后回调。|
    |opaquePtr|void \*|App提供的UserData，在调用onResult时传回App。|

    返回说明

    0表示接口调用成功，但是否订阅成功还得看回调结果；其它表示接口执行异常中断，订阅失败。

    **说明：** 该接口是异步接口，通过onResult判断结果，lambda表达式转换成onResult。

    ```
    void (foo)(void*, const AliRtc::String&, AliRtcAudioTrack, AliRtcVideoTrack);
    foo = [](void *opaquePtr,const AliRtc::String &uid, AliRtcAudioTrack publishedAudioTrack,AliRtcVideoTrack publishedVideoTrack)
    {
    ClassA *pThis = (ClassA*)opaquePtr;
    OutputError("subscribe result: user: %s,audio: %d, video: %d", uid.asCString(),publishedAudioTrack,publishedVideoTrack);
    };
    publish(foo, this);
    ```

-   subscribeAudioData：订阅音频数据。默认不订阅音频数据。

    ```
    virtual void subscribeAudioData(AliRtcAudioSource audioSource)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliRtcAudioSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频数据源。|

    **说明：** 调用该接口前，需先通过setSubscribeAudioNumChannel与setSubscribeAudioSampleRate设置输出音频数据参数。

-   unsubscribeAudioData：取消订阅音频数据。

    ```
    virtual void unsubscribeAudioData(AliRtcAudioSource audioSource)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliRtcAudioSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频数据源。|

-   setVideoProfile：设置视频流的参数。

    ```
    void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)                 
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |profile|[AliRtcVideoProfile](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|视频流参数。默认为AliRtcVideoProfile\_Default。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|需要设置的视频流类型。|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    ```
    int setLocalViewConfig(const AliVideoCanvas& canvas, AliRtcVideoTrack track)                  
    ```

    -   支持加入频道之前和之后切换窗口。如果canvas中的hWnd为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeFill。
    参数说明

    |名称|类型|描述|
    |--|--|--|
    |canvas|const [AliVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)&|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|视频Track的类型，预览只允许AliVideoTrackCamera（摄像头流）。|

-   muteLocalCamera：设置是否停止发布本地视频流。

    ```
    int muteLocalCamera(bool mute, AliRtcVideoTrack track)              
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|true表示停止发布视频流，false表示恢复发布视频流。默认恢复发布。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|需要改变发布状态的视频Track类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 调用该接口不改变当前视频流的采集状态

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    ```
    public abstract int setRemoteViewConfig(AliVideoCanvas canvas, String uid, AliRtcVideoTrack track) int setRemoteViewConfig(AliVideoCanvas* canvas, const AliRtc::String& uid, AliRtcVideoTrack track)                   
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|const AliRtc::String&|用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|需要设置的视频Track类型。|

-   getCameraList：获取摄像头列表。

    ```
    void getCameraList(AliRtc::StringArray& array)                 
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|摄像头列表。|

-   getCurrentCamera：获取当前使用的摄像头名称。

    ```
    AliRtc::String getCurrentCamera()                 
    ```

-   setCurrentCamera：选择摄像头。

    ```
    void setCurrentCamera(const AliRtc::String& camera)                    
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |camera|const AliRtc::String&|摄像头名称。|

    **说明：** 该接口只可在调用getCameraList接口获取设备列表后才可调用。

-   isCameraOn：检查摄像头是否打开。

    ```
    bool isCameraOn()                  
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

-   getScreenShareSourceInfo：获取屏幕分享源信息。

    ```
    int getScreenShareSourceInfo(AliRtcScreenShareType source_type, AliRtcScreenSourceList &source_list)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |source\_type|[AliRtcScreenShareType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|桌面分享类型。|
    |source\_list|[AliRtcScreenSourceList](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|屏幕分享数据源信息。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   getCurrentCameraId：获取当前使用的摄像头ID。

    ```
    virtual AliRtc::String getCurrentCameraId()
    ```

-   setCurrentCameraById：通过设备ID选择摄像头。

    ```
    virtual void setCurrentCameraById(const AliRtc::String &cameraId)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |cameraId|const AliRtc::String &|摄像头ID。|

-   setExternalVideoSource：启用外部视频输入源。

    ```
    virtual int setExternalVideoSource(bool enable, bool useTexture, AliRtcVideoSource sourceType, AliRtcRenderMode renderMode)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示启用外部视频输入源，false表示关闭外部视频输入源。默认关闭外部视频输入源。|
    |useTexture|bool|true表示使用texture模式，false表示不使用texture模式。|
    |sourceType|[AliRtcVideoSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|流类型。|
    |renderMode|[AliRtcRenderMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|渲染模式。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

    **说明：** 该接口调用后方可调用pushExternalVideoFrame接口输入视频数据。

-   pushExternalVideoFrame：输入外部视频。

    ```
    virtual int pushExternalVideoFrame(AliRtcVideoDataSample *frame, AliRtcVideoSource sourceType)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |frame|[AliRtcVideoDataSample \*](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|帧数据。|
    |type|[AliRtcVideoSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|流类型。|

-   registerVideoSampleObserver：订阅视频数据输出。默认不订阅视频数据输出。

    ```
    virtual void registerVideoSampleObserver()
    ```

    **说明：** 该接口调用后，输出数据将通过onCaptureVideoSample及onRemoteVideoSample回调返回。

-   unRegisterVideoSampleObserver：取消订阅视频数据输出。

    ```
    virtual void unRegisterVideoSampleObserver()
    ```

-   startRecord：开始录制。

    ```
    virtual bool startRecord(AliRtcRecordType recordType, AliRtcRecordFormat recordFormat, const AliRtc::String& filePath, AliRtcRecordAudioConfig& audioConfig, AliRtcRecordVideoConfig& videoConfig, bool isFragment) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |recordType|[AliRtcRecordType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制类型。|
    |recordFormat|[AliRtcRecordFormat](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制格式。|
    |filePath|const AliRtc::String&|文件路径。|
    |audioConfig|[AliRtcRecordAudioConfig&](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制音频设置。|
    |videoConfig|[AliRtcRecordVideoConfig&](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制视频设置。|
    |isFragment|bool|是否支持mp4内部分段，只在录制mp4时有效。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   setBeatutyEffect：设置是否启用基础美颜。

    ```
    virtual int setBeatutyEffect(bool enable, AliRtcBeautyConfig config) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true：开启，false：关闭，默认为关闭。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|基础美颜参数。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

    **说明：** 该接口目前只支持美白和磨皮。

-   setVideoEncoderConfiguration： 设置视频编码属性。

    ```
    virtual void setVideoEncoderConfiguration(AliRtcVideoEncoderConfiguration &config) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|[AliRtcVideoEncoderConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|预定义的视频编码属性。|

-   setScreenShareSourceByRegion：通过指定区域设置屏幕分享源。

    **说明：** 此方法仅适用于桌面共享，设置窗口共享请使用[setScreenShareSource](#li_f8l_0uk_xza)接口。

    ```
    virtual int setScreenShareSourceByRegion(const AliRtcScreenShareRegion& screenRect, bool isShareByRegion, const AliRtcScreenShareRegion& regionRect) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |screenRect|[AliRtcScreenShareRegion](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|指定要共享的屏幕相对于虚拟屏幕的位置。虚拟屏幕位置请参见[The Virtual Screen](https://docs.microsoft.com/en-us/windows/win32/gdi/the-virtual-screen)。|
    |isShareByRegion|bool|是否只分享指定屏幕内特定区域。|
    |regionRect|[AliRtcScreenShareRegion](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|指定共享屏幕内要分享的区域（isShareByRegion为true时才需赋值）。**说明：**

    -   分享区域最小分辨率为16 x 16，当设置区域小于最小分辨率时重置为最小分辨率。
    -   分享区域超过实际桌面分辨率时，将分享整个桌面。 |

-   stopRecord：停止录制。

    ```
    virtual void stopRecord() = 0;                   
    ```

-   getDesktopResolution：获取屏幕分享桌面分辨率。

    ```
    int getDesktopResolution(const AliRtc::String& source_id, const AliRtc::String& source_title, int& width, int& height)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |source\_id|AliRtc::String|屏幕分享数据源ID。|
    |source\_title|AliRtc::String|屏幕分享数据源名称。|
    |width|int|屏幕分辨率宽。|
    |height|int|屏幕分辨率高。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   setScreenShareSource：设置屏幕分享源。

    ```
    int setScreenShareSource(const AliRtcScreenSource& source)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |source|[AliRtcScreenSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|屏幕分享源信息。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   getScreenShareSource：获取屏幕分享源。

    ```
    AliRtcScreenSource getScreenShareSource()
    ```

    返回说明

    返回当前设置的屏幕分享源。

-   setAudioOnlyMode：设置为纯音频模式还是音视频模式。

    ```
    int setAudioOnlyMode(bool audioOnly)              
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioOnly|bool|true表示音频发布和订阅，false表示音视频发布和订阅。默认为false。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

    **说明：** 该接口必须在加入频道之前调用。

-   isAudioOnly：查询当前是否为纯音频模式。

    ```
    bool isAudioOnly()
    ```

    返回说明

    true表示纯音频模式，false表示音视频模式。

-   muteLocalMic：设置是否停止发布本地音频。

    ```
    int muteLocalMic(bool mute)                   
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|true表示停止发布本地音频，false表示恢复发布本地音频。 默认恢复发布本地音频。|

    返回说明

    0表示方法调用成功，-1表示方法调用失败。

    **说明：** 该接口不改变当前音频的采集状态。

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流。

    ```
    int muteRemoteAudioPlaying(const AliRtc::String& uid, bool mute)                 
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |mute|bool|true表示停止播放，false表示恢复播放。|

    返回说明

    0表示方法调用成功，-1表示方法调用失败。

-   getAudioCaptures：获取系统中的录音设备列表。

    ```
    void getAudioCaptures(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频采集设备列表。|

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ```
    AliRtc::String getCurrentAudioCapture()
    ```

-   setCurrentAudioCapture：选择音频采集设备。

    ```
    void setCurrentAudioCapture(const AliRtc::String& capture)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |capture|String|音频采集设备名称。|

    **说明：** 该接口只可在getAudioCaptures接口后调用。

-   getAudioRenderers：获取系统中的扬声器列表。

    ```
    void getAudioRenderers(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频播放设备列表。|

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ```
    AliRtc::String getCurrentAudioRenderer()
    ```

-   setCurrentAudioRenderer：选择音频播放设备。

    ```
    void setCurrentAudioRenderer(const AliRtc::String &renderer)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderer|String|音频播放设备名称。|

    **说明：** 该接口只可在getAudioRenderers后调用。

-   startAudioCapture：开启音频采集。

    ```
    void startAudioCapture() = 0;
    ```

    **说明：** 您可以设置提前开启音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

-   stopAudioCapture：关闭音频采集。

    ```
    void stopAudioCapture();
    ```

    **说明：** 您可以设置关闭音频采集。

-   startAudioPlayer：开启音频播放设备。

    ```
     void startAudioPlayer();
    ```

    **说明：** 您可以设置提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

-   stopAudioPlayer：关闭音频播放。

    ```
    void stopAudioPlayer();
    ```

    **说明：**

    -   您可以设置关闭音频播放。
    -   该接口在入会前调用。
-   muteAllRemoteAudioPlaying：停止远端的所有音频流的播放。

    ```
    virtual int muteAllRemoteAudioPlaying(bool mute)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|true表示停止音频流播放，false表示不停止音频流播放。默认不停止音频流播放。|

    **说明：** 该接口调用后，订阅和解码不受影响。

-   getCurrentAudioCaptureId：获取使用的录音设备ID。

    ```
    virtual AliRtc::String getCurrentAudioCaptureId()
    ```

-   setCurrentAudioCaptureById：通过设备ID选择录音设备。

    ```
    virtual void setCurrentAudioCaptureById(const AliRtc::String &captureId)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |captureId|const AliRtc::String &|录音设备ID。从getAudioCaptures接口获取。|

-   getCurrentAudioRendererId ：获取当前使用的扬声器ID。

    ```
    virtual AliRtc::String getCurrentAudioRendererId()
    ```

-   setCurrentAudioRendererById：通过设备ID选择扬声器。

    ```
    virtual void setCurrentAudioRendererById(const AliRtc::String &rendererId)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |rendererId|const AliRtc::String &|扬声器ID。从getAudioRenderers接口获取。|

-   setRecordingVolume：设置录音音量。

    ```
    virtual int setRecordingVolume(int volume)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值范围：0~400。默认取值100。     -   0：静音。
    -   大于100：放大音量。
    -   小于100：减小音量。 |

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

    **说明：** 录音音量调节：当对端用户物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100-200，超过200会有影响音质的风险。

-   setPlayoutVolume：设置播放音量。

    ```
    virtual int setPlayoutVolume(int volume)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值范围：0~400。默认取值100。     -   0：静音。
    -   大于100：放大音量。
    -   小于100：减小音量。 |

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

    **说明：** 播放音量调节当本地物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100-200，超过200会有影响音质的风险。

-   setSubscribeAudioNumChannel：设置输出音频声道数。

    ```
    virtual void setSubscribeAudioNumChannel(AliRtcAudioNumChannelType audioNumChannel)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioNumChannel|[AliRtcAudioNumChannelType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频声道类型。默认为单声道。|

-   setSubscribeAudioSampleRate：设置输出音频采样率。

    ```
    virtual void setSubscribeAudioSampleRate(AliRtcAudioSampleRate audioSampleRate)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSampleRate|[AliRtcAudioSampleRate](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频采样率。默认为44.1k。|

-   setExternalAudioSource：设置是否将外部音频数据作为推流的输入源。

    ```
    virtual int setExternalAudioSource(bool enable, unsigned int sampleRate, unsigned int channelsPerFrame)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示启用外部音频输入源。false表示不启用外部音频输入源。默认不启用外部视频输入源。|
    |sampleRate|unsigned int|采样率。|
    |channelsPerFrame|unsigned int|声道数。取值范围：大于等于1。|

    返回说明

    返回值大于等于0，表示方法调用成功，其它表示方法调用失败。

-   pushExternalAudioFrameRawData：输入音频数据。

    ```
    virtual int pushExternalAudioFrameRawData(const void* audioSamples, unsigned int sampleLength, long long timestamp)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSamples|const void\*|音频数据。|
    |sampleLength|unsigned int|音频数据长度。|
    |timestamp|long long|时间戳。|

    返回说明

    -   返回值大于等于0表示方法调用成功。
    -   返回值小于0表示方法调用失败。
    -   返回值为ERR\_AUDIO\_BUFFER\_FULL表示需要在间隔投递数据时间长度后再次重试投递。
-   setMixedWithMic：设置外部音频输入是否与麦克风采集音频混合。

    ```
    virtual int setMixedWithMic(bool mixed)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mixed|bool|true表示外部音频输入与麦克风采集音频混合，false表示外部音频输入完全替换麦克风采集音频。默认为完全替代。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   setExternalAudioPublishVolume：设置外部音频输入音量。

    ```
    virtual int setExternalAudioPublishVolume(int volume)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值范围：0~100。默认取值100。|

    返回说明

    0表示设置成功，其他表示设置失败。

    **说明：** 1.17及以上版本setExternalAudioVolume接口名变更为setExternalAudioPublishVolume。

-   getExternalAudioPublishVolume：获取外部音频输入音量。

    ```
    virtual int getExternalAudioPublishVolume()
    ```

    返回说明

    大于等于0表示方法调用成功，其它表示方法调用失败返回的错误码。

    **说明：** 1.17及以上版本方法名getExternalAudioVolume改为getExternalAudioPublishVolume。

-   setExteranlAudioRender：设置是否启用外部输入音频播放。

    ```
    virtual int setExteranlAudioRender(bool enable, unsigned int sampleRate, unsigned int channelsPerFrame)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|true表示启用外部输入音频播放，false表示关闭外部输入音频播放。默认关闭外部输入音频播放。|
    |sampleRate|unsigned int|采样率。|
    |channelsPerFrame|unsigned int|采样率。|

    返回说明

    返回值大于等于0，表示方法调用成功，其它表示方法调用失败。

-   pushExternalAudioRenderRawData：输入音频播放数据。

    ```
    virtual int pushExternalAudioRenderRawData(const void* audioSamples, unsigned int sampleLength, 
    unsigned int sampleRate, unsigned int channelsPerFrame, long long timestamp)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSamples|const void\*|音频数据。|
    |sampleLength|unsigned int|音频数据长度。|
    |sampleRate|unsigned int|音频采样率。|
    |channelsPerFrame|unsigned int|音频声道数。|
    |timestamp|long long|时间戳。|

    返回说明

    返回值大于等于0，表示方法调用成功，其它表示方法调用失败。

-   setExternalAudioPlayoutVolume：设置外部音频播放音量。

    ```
    virtual int setExternalAudioPlayoutVolume(int volume)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值范围：0~100。默认取值100。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   getExternalAudioPlayoutVolume：获取音频播放音量。

    ```
    virtual int getExternalAudioPlayoutVolume()
    ```

-   setAudioEffectReverbMode：设置混响音效模式。

    ```
    virtual int setAudioEffectReverbMode(const AliRtcAudioEffectReverbMode mode) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |mode|const [AliRtcAudioEffectReverbMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|对应混响音效类型。默认无混响模式。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败返回的错误码。

-   setAudioEffectReverbParamType：设置混响音效类型。

    ```
    virtual int setAudioEffectReverbParamType(const AliRtcAudioEffectReverbParamType type, float value) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |type|const [AliRtcAudioEffectReverbParamType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|对应混响音效类型。|
    |value|float|对应混响音效类型值。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败返回的错误码。

-   setVolumeCallbackIntervalMs：设置音量回调频率和平滑系数。返回0表示成功，-1表示interval设置小于10，-2表示平滑系数超出范围。

    ```
    virtual int setVolumeCallbackIntervalMs(int interval, int smooth, int reportVad) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |interval|int|时间间隔，单位：ms。最小值不得小于10ms。默认值为160ms。|
    |smooth|int|平滑系数。数值越大平滑程度越高，反之越低，实时性越好。建议您设置3，范围为0~9。|
    |reportVad|int|本地语音检测开关。取值：     -   1：开启，通过onAudioVolumeCallback接口回调。
    -   0：关闭。 |

    返回说明

    -   0表示方法调用成功
    -   -1表示interval设置小于10
    -   -2表示平滑系数超出范围
-   setRecordingDeviceVolume：设置音频采集设备音量。

    ```
    virtual int setRecordingDeviceVolume(int volume) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |volume|int|音量，取值范围：0 ~ 100。默认取值100。|

-   getRecordingDeviceVolume： 获取音频采集设备音量。

    ```
    virtual int getRecordingDeviceVolume() = 0;
    ```

    返回说明

    返回当前音频采集设备音量。

-   setPlaybackDeviceVolume：设置音频播放设备音量。

    ```
    virtual int setPlaybackDeviceVolume(int volume) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |volume|int|音量，取值范围：0 ~ 100。默认取值100。|

    返回说明

    0表示成功，非0表示失败。

-   getPlaybackDeviceVolume：获取音频播放设备音量。

    ```
    virtual int getPlaybackDeviceVolume() = 0;
    ```

    返回说明

    返回当前音频播放设备音量。

-   startPreview：开始本地预览（在主线程调用）。

    ```
    int startPreview()              
    ```

    返回说明

    0表示成功，非0表示失败。

    **说明：** 该接口需要在setLocalViewConfig后由主线程调用。您可在加入频道之前调用该接口。

-   stopPreview：停止本地预览。

    ```
    int stopPreview()                  
    ```

    返回说明

    0表示成功，非0表示失败。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    void getOnlineRemoteUsers(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|用户列表（用户ID列表）。|

-   getUserInfo：查询远端用户信息。返回0表示成功获取，其他表示失败。

    ```
    int getUserInfo(const AliRtc::String& uid, AliRtc::Dictionary& dict)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |dict|AliRtc::Dictionary&|用于存放用户数据。取值：|

    dict当中key值包括：userID、isOnline、sessionID、callID、displayName、hasAudio,hasCameraMaster、hasCameraSlave、hasScreenSharing、requestAudio,requestCameraMaster、requestCameraSlave、requestScreenSharing、preferCameraMaster subScribedAudio、subScribedCameraMaster,subScribedCamearSlave、subScribedScreenSharing、hasCameraView、hasScreenView、muteAudioPlaying。

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   isUserOnline：查询用户是否在线。

    ```
    bool isUserOnline(const AliRtc::String& uid)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|

    返回说明

    true表示用户在线，false表示用户不在线。

-   createMediaDeviceTestInterface：创建音视频设备测试实例。

    ```
    AliMediaDeviceTestInterface * createMediaDeviceTestInterface(AliMediaDeviceTestEventListener * pMediaDeviceEventListener)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |pMediaDeviceEventListener|[AliMediaDeviceTestEventListener \*](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)|音频设备测试事件监听器。|

-   setLogLevel：设置日志级别。

    ```
    void setLogLevel(AliRtcLogLevel logLevel)        
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|日志级别。默认取值AliRtcLogLevelInfo。|

-   getSdkVersion：获取SDK版本号。

    ```
    static const char* getSdkVersion()                 
    ```

-   setClientRole：设置用户角色。返回0为成功，否则返回错误码。

    ```
    int setClientRole(const AliRtcClientRole clientRole) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |clientRole|[AliRtcClientRole](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|用户角色。默认为AliRtcClientRoleLive。|

    返回说明

    0表示方法调用成功，其它表示方法调用失败的错误码。

-   startLastmileDetect：开始网络质量探测。

    **说明：** 您需要在加入频道之前调用，并且入会后会自动停止，探测结果在[onLastmileDetectResultWithQuality](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调。

    ```
    virtual int startLastmileDetect()
    ```

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   stopLastmileDetect：停止网络质量探测。

    ```
    virtual int stopLastmileDetect()
    ```

-   postFeedback：SDK问题反馈。

    ```
        virtual void postFeedback(const AliRtc::String& uid, const AliRtc::String& channelId,
          const AliRtc::String& description, AliRtcFeedbackType type, long long timeStamp) = 0;
    ```

    参数说明

    |名称|类型|说明|
    |--|--|--|
    |uid|AliRtc::String|问题用户User ID。|
    |channelId|AliRtc::String|问题频道ID。|
    |description|AliRtc::String|问题描述。|
    |type|[AliRtcFeedbackType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|问题类型。|
    |timeStamp|long long|问题发生时间戳。|

-   sendMediaExtensionMsg：发送媒体扩展信息。

    -   0：发送成功。
    -   -1：当前未在推流状态，不能发送自定义消息。
    -   -2：参数设置错误，自定义消息长度超过8Byte，或者repeatCount<=0。
    -   -3：发送过于频繁，建议降低发送频率。
    **说明：** 使用音视频数据通道，将自定义消息发送给房间内其他用户，需要满足两个前提：

    -   己方正常入会，并且在推流中。
    -   房间内的其他用户需要订阅己方音视频流，发送成功之后可在[onMediaExtensionMsgReceived](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调中接收结果。
    ```
    virtual int sendMediaExtensionMsg(unsigned char *message, int size, int repeatCount) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |message|unsigned char \*|自定义消息数据。|
    |size|int|自定义消息数据长度，目前长度限制为8Byte。|
    |repeatCount|int|消息发送次数。|

-   getClientRole：获取用户角色。

    ```
     virtual AliRtcClientRole getClientRole() = 0;
    ```

-   startIntelligentDenoise：开启智能降噪。默认为关闭状态。

    ```
    virtual void startIntelligentDenoise() = 0;
    ```

    **说明：** 该接口可以在通话过程中控制打开智能降噪功能。

-   stopIntelligentDenoise：关闭智能降噪。

    ```
     virtual void stopIntelligentDenoise() = 0;
    ```

    **说明：** 该接口可以在通话过程中控制关闭智能降噪功能。

-   RefreshAuthInfo：刷新令牌。

    ```
     virtual int RefreshAuthInfo(const AliRtcAuthInfo& authInfo) = 0;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|新的鉴权信息。|

    返回说明

    0表示刷新令牌成功，其它表示刷新令牌失败。


