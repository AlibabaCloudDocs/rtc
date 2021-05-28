---
keyword: [AliRtcEngine, Android]
---

# AliRtcEngine接口

通过阅读本文，您可以了解到Android SDK的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setH5CompatibleMode](#li_0f1_x7o_he8)|设置H5兼容模式。|1.1|
|[getH5CompatibleMode](#li_t2g_edf_kh8)|检查当前是否兼容H5。|1.1|
|[getInstance](#li_i9x_o2q_4jo)|创建AliRTCEngine实例（同一时间只会存在一个实例），只能在主线程调用。|1.17|
|[getInstance](#li_s34_9tb_mmm)|创建AliRTCEngine实例，支持通过传入参数配置SDK特别功能（同一时间只会存在一个实例），只能在主线程调用。|1.17|
|[destroy](#li_ezt_yf8_tdc)|销毁SDK。|1.1|
|[uploadLog](#li_ik1_9cq_07a)|主动上传日志。|1.1|
|[setLogDirPath](#li_l27_ydr_okh)|设置SDK日志文件保存路径。|1.17|
|[setRtcEngineEventListener](#li_d8q_wbs_u1x)|设置本地用户行为的回调事件的监听。|1.1|
|[setRtcEngineNotify](#li_w96_2q4_hr8)|设置远端用户行为的通知事件的监听。|1.1|

频道相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[joinChannel](#li_swo_yjn_89o)|加入频道。|1.1|
|[leaveChannel](#li_dx8_0lv_lm3)|离开频道。|1.1|
|[switchChannel](#li_ay6_94b_hdg)|切换频道|2.1|
|[isInCall](#li_ps9_7ql_oll)|检查当前是否在频道中。|1.1|
|[setChannelProfile](#li_edm_5i8_mks)|设置频道模式。|1.15|
|[createChannel](#li_8ln_v4y_dlg)|创建AliRtcEngine子频道实例。|2.1|
|[destroyChannel](#li_3bh_mtw_1kg)|销毁子频道实例。|2.1|

发布相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[publishLocalVideoStream](#li_bia_2ol_v2y)|设置是否发布视频流。|2.1|
|[isLocalVideoStreamPublished](#li_nje_vk5_rqz)|查询当前是否发布视频流。|1.1|
|[isScreenSharePublished](#li_3ty_rlt_6w3)|查询当前是否发布屏幕流。|1.1|
|[publishLocalAudioStream](#li_ine_jy2_cjh)|设置是否发布音频流。|2.1|
|[isLocalAudioStreamPublished](#li_q9l_pt9_pyn)|查询当前是否推音频流。|1.1|
|[publishLocalDualStream](#li_99b_ufs_gww)|设置是否发布次要视频流。|2.1|
|[isDualStreamPublished](#li_f52_268_cbr)|查询当前是否发布次要视频流。|2.1|

订阅相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setRemoteVideoStreamType](#li_m6x_6la_3kd)|设置订阅的相机流格式，大流或小流。|2.1|
|[setRemoteDefaultVideoStreamType](#li_1lq_jtq_hht)|设置默认订阅的相机流格式，大流或小流。|2.1|
|[setDefaultSubscribeAllRemoteAudioStreams](#li_go3_hvh_jai)|设置是否默认接收音频流。|2.1|
|[subscribeAllRemoteAudioStreams](#li_yca_yyf_qgw)|停止或恢复接收所有远端音频流。|2.1|
|[subscribeRemoteAudioStream](#li_hbh_7u6_ycr)|停止或恢复特定远端用户的音频流拉取。|2.1|
|[setDefaultSubscribeAllRemoteVideoStreams](#li_4gi_bee_cte)|设置是否默认接收视频流。|2.1|
|[subscribeAllRemoteVideoStreams](#li_xbv_xqk_nhp)|停止或恢复接收所有远端视频流。|2.1|
|[subscribeRemoteVideoStream](#li_tut_cqx_8ny)|停止或恢复特定远端用户的视频流拉取。|2.1|

视频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[createRenderSurfaceView](#li_p0b_xqr_zoo)|创建SurfaceView渲染视图。|2.1|
|[createRenderTextureView](#li_wt1_c8b_56e)|创建TextureView渲染视图。|2.1|
|[setScreenShareEncoderConfiguration](#li_60v_yvr_j3u)|设置屏幕共享编码属性。|2.1|
|[setLocalViewConfig](#li_19l_b99_byb)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[setCameraCapturerConfiguration](#li_mvf_438_yb4)|设置摄像头采集偏好。|2.1|
|[setDeviceOrientationMode](#li_x8h_f8q_voi)|设置设备方向。|2.1|
|[enableLocalVideo](#li_zdg_4qo_iaf)|禁用或重新启用本地视频采集。|2.1|
|[muteLocalCamera](#li_3yz_809_uf9)|设置是否停止发布本地视频流。|1.1|
|[muteAllRemoteVideoRendering](#li_ekd_d3m_gan)|停止或恢复远端所有的视频渲染。|2.1|
|[setRemoteViewConfig](#li_l5x_xh3_nsd)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[isCameraOn](#li_wzl_bbr_7wp)|检查摄像头是否打开。|1.1|
|[stopRecord](#li_2g6_bwx_4y0)|停止录制。|1.17|
|[startRecord](#li_lp4_o1h_br6)|开始录制。|1.17|
|[setBeautyEffect](#li_atk_laz_44p)|设置基础美颜。|1.17.9|
|[setVideoEncoderConfiguration](#li_ozj_dku_t0b)|设置视频编码属性。|2.1|
|[addVideoWatermark](#li_0t3_jmm_py2)|添加水印。|2.1|
|[clearVideoWatermark](#li_w5q_0ue_lyp)|清理对应数据流水印信息。|2.1|
|[snapshotVideo](#li_eix_lf1_5t5)|截图。|2.1|
|[switchCamera](#li_u8j_wps_qpq)|切换前后摄像头（默认为前置摄像头）。|1.1|
|[getCurrentCameraType](#li_ct1_qya_qa1)|获取当前摄像头方向。|1.1|
|[setCameraZoom](#li_dp1_mcp_ns8)|设置摄像头缩放比例。|1.1|
|[setCameraFlash](#li_b5n_1nz_e1b)|设置摄像头闪光灯是否打开。|1.14|
|[isCameraSupportFocusPoint](#li_c3c_gap_7pd)|摄像头是否支持手动聚焦。|1.14|
|[isCameraSupportExposurePoint](#li_n0g_dl2_uot)|摄像头是否支持设置曝光区域。|1.14|
|[setCameraFocusPoint](#li_2jv_lil_3h6)|设置摄像头手动聚焦。|1.14|
|[setCameraExposurePoint](#li_21n_82h_35w)|设置摄像头曝光点。|1.14|
|[isCameraAutoFocusFaceModeSupported](#li_jct_gl0_bqe)|摄像头是否支持人脸聚焦。|2.1|
|[setCameraAutoFocusFaceModeEnabled](#li_zmi_9jl_o6l)|设置摄像头人脸对焦。|2.1|

共享视频接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartScreenShare\[1/2\]](#li_zcr_gpn_k8i)|开始屏幕分享。|2.1|
|[StartScreenShare\[2/2\]](#li_oen_e52_rx6)|开始屏幕分享。|2.1|
|[StopScreenShare](#li_3hp_hro_a61)|停止屏幕分享。|2.1|

音频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setAudioOnlyMode](#li_yqo_xa0_8mx)|设置为纯音频模式还是音视频模式。|1.1|
|[isAudioOnly](#li_wic_jxw_szz)|查询当前是否为纯音频模式。|1.1|
|[muteLocalMic](#li_958_lzr_u98)|设置是否停止发布本地音频。|1.1|
|[muteRemoteAudioPlaying](#li_rvi_ca2_3d6)|设置是否停止播放远端音频流。|1.1|
|[muteAllRemoteAudioPlaying](#li_z49_qor_vey)|停止或恢复远端所有的音频播放。|1.16.2|
|[startAudioCapture](#li_e73_dpj_v18)|开启音频采集。|1.1|
|[stopAudioCapture](#li_o7w_2u1_bns)|关闭音频采集。|1.1|
|[startAudioPlayer](#li_6ga_pdo_ifu)|开启音频播放设备。|1.1|
|[stopAudioPlayer](#li_v17_agk_r4j)|关闭音频播放。|1.1|
|[setRemoteAudioVolume](#li_xel_hct_4s6)|设置本地播放的指定远端用户音量。|2.1|
|[enableSpeakerphone](#li_xg8_jc9_t36)|设置音频输出为听筒还是扬声器。|2.1|
|[isSpeakerOn](#li_j84_w5z_zu7)|获取当前音频输出为听筒还是扬声器。|2.1|
|[setRecordingVolume](#li_f95_ft1_8hy)|设置录音音量。|1.16.2|
|[setPlayoutVolume](#li_xzz_s1u_vod)|设置播放音量。|1.16.2|
|[enableAudioVolumeIndication](#li_70z_8m6_9yy)|设置音量回调频率和平滑系数。|1.17.9|
|[setAudioProfile](#li_5oi_mae_jvq)|设置音频Profile。|2.1|
|[enableAudioDTX](#li_kp7_ent_jwe)|开启本地音频流量控制（语音）。|2.1|
|[enableAudioAMD](#li_j8u_b70_kg2)|开启本地音频流量控制（麦克风）。|2.1|
|[setAudioEffectVoiceChangerMode](#li_cm7_je8_t4p)|设置变声音效模式。|2.1|
|[setAudioEffectPitchValue](#li_2qp_91e_x0e)|设置变调参数。|2.1|
|[setAudioEffectReverbMode](#li_7vr_13v_7pd)|设置混响音效模式。|2.1|
|[setAudioEffectReverbParamType](#li_x4j_90h_u6b)|设置混响音效类型和具体参数。|2.1|
|[startAudioAccompany](#li_2bn_ww0_28u)|开始混音。|1.15|
|[stopAudioAccompany](#li_jsp_tqn_cth)|停止混音。|1.15|
|[setAudioAccompanyVolume](#li_nmq_wc7_62h)|设置混音音量。|1.15|
|[setAudioAccompanyPublishVolume](#li_ymh_7hg_ts9)|设置混音之后推流出去的音量。|1.15|
|[getAudioAccompanyPublishVolume](#li_0ti_bys_y7b)|获取推流出去的混音音量。|1.15|
|[setAudioAccompanyPlayoutVolume](#li_uie_3fi_2bg)|设置混音之后本地播放的音量。|1.15|
|[getAudioAccompanyPlayoutVolume](#li_7u3_m5p_l7z)|获取混音本地播放的音量。|1.15|
|[pauseAudioAccompany](#li_fv2_7fi_wcx)|暂停混音。|1.15|
|[resumeAudioAccompany](#li_ge1_qld_6gf)|重新开始混音。|1.15|
|[getAudioAccompanyDuration](#li_0gp_rr1_nyb)|获取伴奏文件时长。|1.17.30|
|[getAudioAccompanyCurrentPosition](#li_863_lig_d69)|获取音乐文件播放进度。|1.17.30|
|[setAudioAccompanyPosition](#li_yjj_1d8_npy)|设置音频文件的播放位置。|1.17.30|
|[preloadAudioEffect](#li_1pe_mmm_f8o)|预加载音效文件。|1.15|
|[unloadAudioEffect](#li_x9a_56g_xjf)|删除预加载的音效文件。|1.15|
|[playAudioEffect](#li_lrn_6gh_dvv)|开始播放音效。|1.15|
|[stopAudioEffect](#li_qoa_whi_5jj)|停止播放音效。|1.15|
|[stopAllAudioEffects](#li_9hi_tvg_idj)|停止播放所有音效。|1.15|
|[setAudioEffectPublishVolume](#li_dne_07n_ts3)|设置音效推流音量。|1.15|
|[getAudioEffectPublishVolume](#li_l62_imi_p8g)|获取推流音效音量。|1.15|
|[setAudioEffectPlayoutVolume](#li_ba7_s58_gp9)|设置音效本地播放音量。|1.15|
|[getAudioEffectPlayoutVolume](#li_bg9_72u_cxz)|获取音效本地播放音量。|1.15|
|[setAllAudioEffectsPublishVolume](#li_6cx_swd_ax1)|设置所有音效本地播放音量。|1.15|
|[setAllAudioEffectsPlayoutVolume](#li_z7w_1nh_bzf)|设置所有音效推流音量。|1.15|
|[pauseAudioEffect](#li_e13_eda_xxm)|暂停音效。|1.15|
|[pauseAllAudioEffects](#li_ccz_y5x_sqf)|暂停所有音效。|1.15|
|[resumeAudioEffect](#li_up1_3gn_3it)|重新开始播放音效。|1.15|
|[resumeAllAudioEffects](#li_feo_8g7_zph)|重新开始播放所有音效。|1.15|
|[enableEarBack](#li_mdc_111_z3k)|启用耳返。|1.15|
|[setEarBackVolume](#li_jz5_5ad_cvq)|设置耳返音量。|1.15|
|[requestAudioFocus](#li_hwz_3bj_ev8)|请求音频焦点。|1.17.19|
|[abandonAudioFocus](#li_9ob_0p4_v95)|放弃音频焦点。|1.17.19|

媒体引擎接口

|API|描述|支持的最低版本|
|---|--|-------|
|[registerVideoSampleObserver](#li_ziq_fra_44g)|订阅视频数据输出。|1.17|
|[unRegisterVideoSampleObserver](#li_ha4_n0d_7dv)|取消订阅视频数据输出。|1.17|
|[registerLocalVideoTextureObserver](#li_4b6_0b6_9py)|订阅本地视频纹理数据。|1.15|
|[unRegisterLocalVideoTextureObserver](#li_5jk_b68_6h9)|取消本地视频纹理数据输出。|1.15|
|[registerAudioObserver](#li_wjs_5ax_y04)|订阅音频数据输出。|1.17|
|[unRegisterAudioObserver](#li_xa2_4z1_rd7)|取消音频数据输出。|1.17|
|[setSubscribeAudioNumChannel](#li_0my_lt2_z12)|设置输出音频声道数。|2.1|
|[setSubscribeAudioSampleRate](#li_fn1_i1j_v8d)|设置输出音频采样率。|2.1|
|[registerAudioVolumeObserver](#li_d7k_w8e_au5)|注册音量数据输出对象。|1.16.2|
|[unRegisterAudioVolumeObserver](#li_ggp_jl3_4od)|取消音量数据输出对象注册。|1.16.2|
|[setExternalVideoSource](#li_2yn_opu_25s)|启用外部视频输入源。|2.1|
|[pushExternalVideoFrame](#li_2yn_opu_25s)|输入视频数据。|2.1|
|[setExternalAudioSource](#li_fyr_py9_gq7)|设置是否启用外部音频输入源。|1.17.9|
|[pushExternalAudioFrameRawData](#li_y31_jei_vmh)|输入音频数据。|1.17.9|
|[setExternalAudioVolume](#li_zbd_duq_vly)|设置混音音量。|1.17.9|
|[getExternalAudioVolume](#li_7q3_wz3_c55)|获取混音音量。|1.17.9|
|[setMixedWithMic](#li_u0z_pgs_72i)|设置是否与麦克风采集音频混合。|1.17.9|
|[setExteranlAudioRender](#li_6u7_xem_jms)|设置是否启用外部输入音频播放。|1.17.9|
|[pushExternalAudioRenderRawData](#li_djt_utf_fsu)|输入外部音频播放数据。|1.17.9|

直播旁路接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startLiveStreaming](#li_ixf_hmb_n69)|开始直播拉流。|2.1|
|[stopLiveStreaming](#li_5h8_jkt_wzz)|停止直播拉流。|2.1|
|[startPublishLiveStream](#li_d2b_5hp_bme)|开启旁路直播。|2.1|
|[updatePublishLiveStream](#li_oxl_4qc_act)|更新旁路直播相关参数。|2.1|
|[stopPublishLiveStream](#li_cmj_t1c_khw)|停止旁路直播。|2.1|
|[setLiveStreamingViewConfig](#li_xak_ry0_y43)|设置直播拉流窗口及渲染参数。|2.1|

跨频道连麦接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startChannelRelay](#li_73s_4vq_f4w)|开启跨频道连麦。|2.1|
|[updateChannelRelay](#li_hg0_lsq_vu9)|更新跨频道连麦。|2.1|
|[stopChannelRelay](#li_t5r_39t_w40)|停止跨频道连麦。|2.1|

预览接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startPreview](#li_xvh_tsw_iw8)|开始本地预览。|1.1|
|[stopPreview](#li_e6j_aje_x87)|停止本地预览。|1.1|

远端用户查询接口

|API|描述|支持的最低版本|
|---|--|-------|
|[getOnlineRemoteUsers](#li_9lk_rak_x4y)|获取远端在线用户列表。|1.1|
|[getUserInfo](#li_eu3_45h_nc7)|查询远端用户信息。|1.1|
|[isUserOnline](#li_rl4_dj0_65q)|查询用户是否在线。|1.1|

其他接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setLogLevel](#li_wfs_u8q_la2)|设置日志级别。|1.1|
|[getSDKVersion](#li_8d1_rc4_j0k)|获取SDK版本号。|1.1|
|[getErrorDescription](#li_sq7_au9_d41)|获取错误码描述。|2.1|
|[setClientRole](#li_pg5_xjz_1z7)|设置用户角色。|1.16|
|[getCurrentClientRole](#li_qiv_aki_11p)|获取用户角色。|1.17.19|
|[startNetworkQualityProbeTest](#li_tp7_b2a_t19)|开始网络质量探测。|1.16.2|
|[stopNetworkQualityProbeTest](#li_ksc_aex_phu)|停止网络质量探测。|1.16.2|
|[respondMessageNotification](#li_ynz_pwx_n9a)|发送消息通知。|2.1|
|[uplinkChannelMessage](#li_khi_fh0_yka)|信令通道使用。|2.1|
|[postFeedback](#li_h5u_8on_rtt)|SDK问题反馈。|1.17.12|
|[sendMediaExtensionMsg](#li_2hr_v45_h04)|发送媒体扩展信息。|1.17.1|
|[startIntelligentDenoise](#li_cdf_dv7_eea)|开启智能降噪。|1.17.19|
|[stopIntelligentDenoise](#li_j9m_uhy_8x4)|关闭智能降噪。|1.17.19|
|[refreshAuthInfo](#li_nyd_yoh_98q)|刷新鉴权信息。|1.17.41|
|[getCurrentConnectionStatus](#li_4f6_0cb_6st)|获取当前网络链接状态。|2.1|

## 接口详情

-   SetH5CompatibleMode：设置是否兼容H5。

    ```
    public static int setH5CompatibleMode(int enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|int|设置是否兼容H5，取值：    -   0：不兼容H5。
    -   1：兼容H5。
默认值为0。|

    **说明：** 当前版本不支持在创建AliRtcEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此接口。

-   getH5CompatibleMode：检查当前是否兼容H5。

    ```
    public static int getH5CompatibleMode();
    ```

    返回说明

    1表示兼容H5，0表示不兼容H5。

-   getInstance：获取一个AliEngineEngine实例。

    ```
    public static AliRtcEngineImpl getInstance(Context context);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |context|Context|安卓（Android Activity）的上下文。|

    **说明：** 同一时间只会存在一个主实例，只能在主线程调用。

-   getInstance：获取一个AliEngineEngine实例。

    ```
    public static AliRtcEngineImpl getInstance(Context context,String extras);
    ```

    支持通过传入参数配置SDK特别功能。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |context|Context|安卓（Android Activity）的上下文。|
    |extras|String|通过JSON配置SDK的特别功能，更多信息，请参见[extras参数配置说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。无需特别功能，可填空字符：@""。|

    **说明：** 同一时间只会存在一个主实例，只能在主线程调用。

-   destroy：销毁SDK实例。

    ```
    public abstract void destroy();
    ```

    **说明：** 在所有操作结束之后调用。

-   uploadLog：上传日志。默认离会自动上传。

    ```
    public static void uploadLog();
    ```

-   setLogDirPath：设置SDK日志文件保存路径。

    ```
    public static int setLogDirPath(String logDirPath);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |logDirPath|String|日志文件保存绝对路径。默认路径：/sdcard/Ali\_RTC\_Log目录下。|

    返回说明

    0表示方法调用成功，非0表示方法调用失败。

    **说明：** 如需调用此接口，请在调用所有SDK接口前进行设置，避免日志丢失，同时App必须保证指定的路径已存在并且可写入。

-   setRtcEngineEventListener：设置本地用户行为的通知事件的监听。

    ```
    public abstract void setRtcEngineEventListener(AliRtcEngineEventListener listener);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |listener|AliRtcEngineEventListener|设置本地用户行为的通知事件的监听。|

-   setRtcEngineNotify：设置远端用户行为的通知事件的监听。

    ```
    public abstract void setRtcEngineNotify(AliRtcEngineNotify listener);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |listener|AliRtcEngineEventListener|设置远端用户行为的通知事件的监听。|

-   joinChannel：加入频道。

    ```
    public abstract int joinChannel(AliRtcAuthInfo authInfo, String userName);
    ```

    加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道，如果加入频道失败，需要重试时，无需先调用[leaveChannel](#li_dx8_0lv_lm3)。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|鉴权信息。|
    |userName|String|用户的显示名称（不是用户ID）。|

    返回说明

    0表示方法调用成功，非0表示方法调用失败。

    **说明：** 该接口是异步接口，是否成功加入频道，需要通过[onJoinChannelResult](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调判断。

-   leaveChannel：离开频道。

    ```
    public abstract int leaveChannel();
    ```

    返回说明

    0表示方法调用成功，非0表示方法调用失败。

    **说明：** 1.15及以上版本，销毁引擎只能通过[destroy](#li_ezt_yf8_tdc)接口。1.15以下版本，离开频道时，AliEngine实例会被销毁，如需继续加入频道等操作，需要重新调用[getInstance](#li_i9x_o2q_4jo)接口初始化AliEngine实例。

    如果当前不在频道内，调用leaveChannel不会对实例产生任何影响，但会产生消息，通知频道内其他用户。

-   switchChannel：切换频道。

    ```
    public abstract int switchChannel(AliRtcAuthInfo authInfo);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|鉴权信息。|

    返回说明

    此接口仅在互动模式AliRTCSdkInteractiveLive下使用，观看角色AliRTCSdkInteractive使用。

    此接口为异步接口，调用成功切换频道后，SDK会先触发离开原频道的回调[onLeaveChannelResult](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)，在返回加入新频道的回调[onJoinChannelResult](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)。

    0表示方法调用成功，非0表示方法调用失败。

    -   返回ERR\_SDK\_INVALID\_STATE请确认是否因为频道模式或角色不匹配，或者当前未加入任何频道中。
    -   返回ERR\_INVALID\_ARGUMENTS请确认鉴权信息是否合法，或者是否加入相同频道。
    -   返回ERR\_INNER为SDK内部状态错误。
-   isInCall：检查当前是否在频道中。

    ```
    public abstract boolean isInCall();
    ```

    返回说明

    true表示在频道中，false表示不在频道中。

-   setChannelProfile：设置频道模式。

    ```
    public abstract int setChannelProfile(AliRTCSdkChannelProfile channelProfile);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |channelProfile|[AliRTCSdkChannelProfile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|频道类型。默认值为AliEngineCommunication。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

-   createChannel：创建一个AliEngine子频道实例。

    ```
    public abstract AliRtcEngine createChannel(String extras);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |extras|String|通过JSON配置SDK的特别功能，更多信息，请参见[extras参数配置说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。无需特别功能，可填空字符：@""。|

    返回说明

    成功返回子频道实例，失败返回null。

-   destroyChannel：销毁CreateChannel创建的子频道。

    ```
    public abstract void destroyChannel();
    ```

-   publishLocalVideoStream：设置是否发布相机流。

    ```
    public abstract int publishLocalVideoStream(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否发布相机流，取值：    -   true：发布相机流。
    -   false：不发布相机流。
默认值为true。|

-   isLocalVideoStreamPublished：查询当前是否发布相机流。

    ```
    public abstract boolean isLocalVideoStreamPublished();
    ```

    返回说明

    true表示发布相机流，false表示不发布相机流。

-   isScreenSharePublished：查询当前是否发布屏幕流。

    ```
    public abstract boolean isScreenSharePublished();
    ```

    返回说明

    true表示发布屏幕流，false表示未发布屏幕流。

-   publishLocalAudioStream：设置是否发布音频流。

    ```
    public abstract int publishLocalAudioStream(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否发布音频流，取值：    -   true：发布音频流。
    -   false：不发布音频流。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isLocalAudioStreamPublished：查询当前是否发布音频流。

    ```
    public abstract boolean isLocalAudioStreamPublished();
    ```

    返回说明

    true表示发布音频流，false表示不发布音频流。

-   publishLocalDualStream：设置是否发布次要视频流。

    ```
    public abstract int publishLocalDualStream(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否发布次要视频流，取值：    -   true：发布次要视频流。
    -   false：不发布次要视频流。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isDualStreamPublished：查询当前是否发布次要视频流。

    ```
    public abstract boolean isDualStreamPublished();
    ```

    返回说明

    true表示发布次要视频流，false表示不发布次要视频流。

-   setRemoteVideoStreamType：设置订阅的相机流格式，大流或小流。

    ```
    public abstract int setRemoteVideoStreamType(String uid, AliRtcVideoStreamType streamType);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|远端用户ID。|
    |streamType|[AliRtcVideoStreamType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|相机流格式。默认值为AliRtcVideoStreamTypeHigh（大流）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setRemoteDefaultVideoStreamType：设置默认订阅的相机流格式，大流或小流。

    ```
    public abstract int setRemoteDefaultVideoStreamType(AliRtcVideoStreamType streamType);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |streamType|[AliRtcVideoStreamType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|相机流格式。默认值为AliRtcVideoStreamTypeHigh（大流）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDefaultSubscribeAllRemoteAudioStreams：设置是否默认接收音频流。

    ```
    public abstract int setDefaultSubscribeAllRemoteAudioStreams(boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |sub|boolean|是否默认接收音频流，取值：    -   true：默认接收音频流。
    -   false：默认不接收音频流。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   subscribeAllRemoteAudioStreams：设置是否接收所有远端音频流。

    ```
    public abstract int subscribeAllRemoteAudioStreams(boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |sub|boolean|是否接收所有远端音频流，取值：    -   true：接收所有远端音频流。
    -   false：不接收所有远端音频流。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   subscribeRemoteAudioStream：停止或恢复特定远端用户的音频流拉取。

    ```
    public abstract int subscribeRemoteAudioStream(String uid, boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|远端用户ID。|
    |sub|boolean|停止或恢复特定远端用户的音频流拉取，取值：    -   true：恢复。
    -   false：停止。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDefaultSubscribeAllRemoteVideoStreams：设置是否默认接收视频流。

    ```
    public abstract int setDefaultSubscribeAllRemoteVideoStreams(boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |sub|boolean|是否默认接收视频流，取值：    -   true：默认接收。
    -   false：默认不接收。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   subscribeAllRemoteVideoStreams：停止或恢复接收所有远端视频流。

    ```
    public abstract int subscribeAllRemoteVideoStreams(boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |sub|boolean|停止或恢复接收所有远端视频流，取值：    -   true：恢复。
    -   false：停止。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   subscribeRemoteVideoStream：停止或恢复特定远端用户的视频流拉取。

    ```
    public abstract int subscribeRemoteVideoStream(String uid, AliRtcVideoTrack track, boolean sub);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|Srring|远端用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流类型。|
    |sub|boolean|停止或恢复特定远端用户的视频流拉取，取值：    -   true：恢复。
    -   false：停止。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   createRenderSurfaceView：创建SurfaceView渲染视图。

    ```
    public abstract SophonSurfaceView createRenderSurfaceView(Context context);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |context|Context|安卓（Android Activity）的上下文。|

-   createRenderTextureView：创建TextureView渲染视图。

    ```
    public abstract SophonTextureView createRenderTextureView(Context context);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |context|Context|安卓（Android Activity）的上下文。|

-   setScreenShareEncoderConfiguration：设置屏幕共享编码属性。

    ```
    public abstract void setScreenShareEncoderConfiguration(AliRtcScreenShareEncoderConfiguration config);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |config|[AliRtcScreenShareEncoderConfiguration](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|屏幕共享编码属性。默认值：    -   dimensions：\[0,0\]
    -   frameRate：5
    -   bitrate：0
    -   rotation：0 |

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    ```
    public abstract int setLocalViewConfig(AliVideoCanvas viewConfig, AliRtcVideoTrack track);
    ```

    支持加入频道之前和之后切换窗口。如果[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)或者[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)中的view参数为空，则停止渲染。

    如果在播放过程中需要重新设置[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)的参数renderMode，请保持其他参数不变，仅修改renderMode。

    如果在播放过程中需要重新设置[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)的参数mirrorMode，请保持其他参数不变，仅修改mirrorMode。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |viewConfig|[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setCameraCapturerConfiguration：设置摄像头采集偏好。

    ```
    public abstract int setCameraCapturerConfiguration(AliEngineCameraCapturerConfiguration cameraCapturerConfiguration);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |cameraCapturerConfiguration|[AliEngineCameraCapturerConfiguration](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|摄像头采集偏好。默认值：    -   preference：0
    -   cameraDirection：0 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDeviceOrientationMode：设置设备方向。

    ```
    public abstract void setDeviceOrientationMode(AliRtcOrientationMode mode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|设备方向。默认值为AliRtcOrientationModeAuto（自适应横竖屏模式）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableLocalVideo：禁用或重新启用本地视频采集。

    ```
    public abstract int enableLocalVideo(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|禁用或重新启用本地视频采集，取值：    -   true：重新启用。
    -   false：禁用。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   muteLocalCamera：停止或恢复本地视频数据发送。

    ```
    public abstract int muteLocalCamera(boolean mute, AliRtcVideoTrack track);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mute|boolean|停止或恢复本地视频数据发送，取值：    -   true：停止。
    -   false：恢复。
默认值为false。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要改变发布状态的视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口只是控制指定视频流上是否发送黑帧，采集和数据发送不会停止。如果需要关闭采集请使用[enableLocalVideo](#li_zdg_4qo_iaf)接口，如果需要中止视频数据发送请使用[publishLocalVideoStream](#li_bia_2ol_v2y)接口。

-   muteAllRemoteVideoRendering：停止或恢复远端所有的视频渲染。

    ```
    public abstract int muteAllRemoteVideoRendering(boolean mute);
    ```

    拉流和解码不受影响。支持加入频道之前和之后设置。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mute|boolean|停止或恢复远端所有的视频渲染，取值：    -   true：停止渲染，所有视频为黑帧。
    -   false表示恢复渲染。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    ```
    public abstract int setRemoteViewConfig(AliVideoCanvas canvas, String uid,AliRtcVideoTrack track);
    ```

    支持加入频道之前和之后切换窗口。如果[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)或者[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)中的view参数为空，则停止渲染。

    如果在播放过程中需要重新设置[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)的参数renderMode，请保持其他参数不变，仅修改renderMode。

    如果在播放过程中需要重新设置[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)的参数mirrorMode，请保持其他参数不变，仅修改mirrorMode。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|String|用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要设置的视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isCameraOn：检查摄像头是否打开。

    ```
    public abstract boolean isCameraOn();
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

-   stopRecord：停止录制。

    ```
    public abstract void stopRecord();
    ```

-   startRecord：开始录制（非布局录制）。

    ```
    public abstract boolean startRecord(AliRtcRecordType recordType,AliRtcRecordFormat recordFormat,
                                        String filePath,AliRtcRecordAudioConfig audioConfig, 
                                        AliRtcRecordVideoConfig videoConfig);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |recordType|[AliRtcRecordType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制类型。|
    |recordFormat|[AliRtcRecordFormat](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制格式。|
    |filePath|String|文件路径。|
    |audioConfig|[AliRtcRecordAudioConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制音频文件参数配置。|
    |videoConfig|[AliRtcRecordVideoConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制视频文件参数配置（移动端不支持录制视频）。|

    返回说明

    true表示方法调用成功，false方法调用失败。

-   setBeautyEffect：设置是否启用基础美颜。

    ```
    public abstract int setBeautyEffect(boolean enable, AliRtcBeautyConfig config);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否启用基础美颜，取值：    -   true：开启美颜。
    -   false：关闭美颜。
默认false。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|基础美颜参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口目前只支持美白和磨皮。

-   setVideoEncoderConfiguration：设置视频编码属性。

    ```
    public abstract void setVideoEncoderConfiguration(AliRtcVideoEncoderConfiguration config);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |config|[AliRtcVideoEncoderConfiguration](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|预定义的编码属性。默认值：    -   dimensions：\[640,480\]
    -   frameRate：15
    -   bitrate：0
    -   mirrorMode：0
    -   orientationMode：0
    -   rotation：0 |

-   addVideoWatermark：添加水印。

    ```
    public abstract int addVideoWatermark(AliRtcVideoTrack track, String imageUrl, AliRtcWatermarkConfig config);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|数据流类型。|
    |imageUrl|String|水印图片路径。|
    |config|[AliRtcWatermarkConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|水印配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   clearVideoWatermark：清理对应数据流水印信息。

    ```
    public abstract int clearVideoWatermark(AliRtcVideoTrack track);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|数据流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   snapshotVideo：截图。

    ```
    public abstract int snapshotVideo(String userId, AliRtcVideoTrack trackType);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|
    |trackType|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。截图结果通过[onSnapshotComplete](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调返回。

-   switchCamera：切换前后摄像头（默认为前置摄像头）。

    ```
    public abstract int switchCamera();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentCameraType：获取当前摄像头方向。

    ```
    public abstract AliRTCCameraType getCurrentCameraType();
    ```

    返回说明

    返回摄像头方向枚举值。

-   setCameraZoom：设置摄像头缩放比例。

    ```
    public abstract int setCameraZoom(float zoom);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |zoom|float|zoom的级别。默认值为1.0。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setCameraFlash：设置摄像头闪光灯是否打开。

    ```
    public abstract int setCameraFlash(boolean flash);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |flash|boolean|摄像头闪光灯是否打开，取值：    -   true：开启。
    -   false：关闭。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isCameraSupportFocusPoint：摄像头是否支持手动聚焦。

    ```
    public abstract boolean isCameraSupportFocusPoint();
    ```

    返回说明

    true表示支持，false表示不支持。

-   isCameraSupportExposurePoint：摄像头是否支持设置曝光区域。

    ```
    public abstract boolean isCameraSupportExposurePoint();
    ```

    返回说明

    true表示支持，false表示不支持。

-   setCameraFocusPoint：设置摄像头手动聚焦。

    ```
    public abstract int setCameraFocusPoint(float pointX, float pointY);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |pointX|float|聚焦点X坐标。|
    |pointY|float|聚焦点Y坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setCameraExposurePoint：设置摄像头曝光点。

    ```
    public abstract int setCameraExposurePoint(float pointX, float pointY);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |pointX|float|聚焦点X坐标。|
    |pointY|float|聚焦点Y坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isCameraAutoFocusFaceModeSupported：摄像头是否支持人脸聚焦。

    ```
    public abstract boolean isCameraAutoFocusFaceModeSupported();
    ```

    返回说明

    true表示支持，false表示不支持。

-   setCameraAutoFocusFaceModeEnabled：设置摄像头人脸对焦。

    ```
    public abstract boolean setCameraAutoFocusFaceModeEnabled(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否开启摄像头人脸对焦，取值：    -   true：开启。
    -   false：关闭。
默认值为false。|

    返回说明

    true表示方法调用成功，false方法调用失败。

-   startScreenShare：开始屏幕分享。

    ```
    public abstract int startScreenShare();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startScreenShare：开始屏幕分享。

    ```
    public abstract int startScreenShare(Intent intent);
    ```

    可以在外部创建并启动屏幕分享。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |intent|Intent|外部创建并启动屏幕分享。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopScreenShare：停止屏幕分享。

    ```
    public abstract int stopScreenShare();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioOnlyMode：设置音频模式还是音视频模式。

    ```
    public abstract int setAudioOnlyMode(boolean audioOnly);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |audioOnly|boolean|设置音频模式还是音视频模式，取值：    -   true：只有音频推流和拉流。
    -   false：音视频都支持。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isAudioOnly：检查当前是否纯音频模式。

    ```
    public abstract boolean isAudioOnly();
    ```

    参数说明

    true纯音频模式，false音视频模式。

-   muteLocalMic：停止或恢复本地音频数据发送。

    ```
    public abstract int muteLocalMic(boolean mute, AliRtcMuteLocalAudioMode mode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mute|boolean|停止或恢复本地音频数据发送，取值：    -   true：本地音频发送静音帧。
    -   false：恢复。
默认值为false。|
    |mode|[AliRtcMuteLocalAudioMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|静音模式，默认麦克风静音模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。mute只是发送音频数据为静音帧，采集和编码模块仍然在工作。

-   muteRemoteAudioPlaying：停止或恢复远端的音频播放。

    ```
    public abstract int muteRemoteAudioPlaying(String uid, boolean mute);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |mute|boolean|停止或恢复远端的音频播放，取值：    -   true：停止播放。
    -   false：恢复播放。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   muteAllRemoteAudioPlaying：停止或恢复远端所有的音频播放。

    ```
    public abstract int muteAllRemoteAudioPlaying(boolean mute);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mute|boolean|停止或恢复远端所有的音频播放，取值：    -   true：停止播放。
    -   false：恢复播放。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startAudioCapture：开启音频采集。

    ```
    public abstract int startAudioCapture();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioCapture：关闭音频采集。

    ```
    public abstract int stopAudioCapture();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startAudioPlayer：开启音频播放设备。

    ```
    public abstract int startAudioPlayer();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioPlayer：关闭音频播放。

    ```
    public abstract int stopAudioPlayer();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setRemoteAudioVolume：设置本地播放的指定远端用户音量。

    ```
    public abstract int setRemoteAudioVolume(String uid, int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |int|volume|播放音量，取值范围：\[0,100\]。0表示静音，100表示原始音量，默认值为100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableSpeakerphone：设置音频输出为听筒还是扬声器。

    ```
    public abstract int enableSpeakerphone(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|音频输出为听筒还是扬声器，取值：    -   true（默认值）：扬声器模式。
    -   false：听筒模式。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isSpeakerOn：获取当前音频输出为听筒还是扬声器。

    ```
    public abstract boolean isSpeakerOn();
    ```

    返回说明

    true为听筒，false为扬声器。

-   setRecordingVolume：设置录音音量。

    ```
    public abstract int setRecordingVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|音量取值范围：\[0,400\]。0表示静音，100表示原始音量。大于100表示放大音量，小于100表示减小音量，默认值为100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setPlayoutVolume：设置播放音量。

    ```
    public abstract int setPlayoutVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|音量取值范围：\[0,400\]。0表示静音，100表示原始音量。大于100表示放大音量，小于100表示减小音量，默认值为100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableAudioVolumeIndication：设置音量回调频率和平滑系数。

    ```
    public abstract int enableAudioVolumeIndication(int interval, int smooth, int reportVad);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |interval|int|时间间隔，单位：毫秒，最小值不得小于10ms，建议设置范围：300~500。小于等于0表示不启用音量提示和说话人提示功能，默认值为300ms。|
    |smooth|int|平滑系数，数值越大平滑程度越高，反之越低，实时性越好，建议设置3，取值范围：\[0,9\]，默认值为3。|
    |reportVad|int|本地语音检测开关。    -   1：开启，通过[AliRtcAudioVolumeObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)接口回调。
    -   0（默认值）：关闭。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioProfile：设置音频Profile。

    ```
    public abstract int setAudioProfile(AliRtcAudioProfile profile, AliRtcAudioScenario scenario);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |profile|int|音频采集或编码模式参数，默认值为AliEngineBasicQualityMode。更多信息，请参见[AliRtcAudioProfile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。|
    |scenario|int|音频场景模式参数，默认值为AliEngineSceneDefaultMode。更多信息，请参见[AliRtcAudioScenario](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableAudioDTX：开启本地音频流量控制（语音）。

    ```
    public abstract int enableAudioDTX(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|开启本地音频流量控制，取值：    -   true：开启。
    -   false：关闭。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。推流之前调用有效。开启语音活动检测可以在检测到没有语音的情况下，发送字节数减少，节省用户流量。

-   enableAudioAMD：开启本地音频流量控制（麦克风）。

    ```
    public abstract int enableAudioAMD(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|开启本地音频流量控制，取值：    -   true：开启。
    -   false：关闭。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。推流之前调用有效。开启语音活动检测可以在检测到麦克风静音或者关闭麦克风时停止发送音频包。

-   setAudioEffectVoiceChangerMode：设置变声音效模式。

    ```
    public abstract int setAudioEffectVoiceChangerMode(AliRtcAudioEffectVoiceChangerMode mode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mode|[AliRtcAudioEffectVoiceChangerMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|变声音效模式，默认值为AliRtcSdk\_AudioEffect\_Voice\_Changer\_OFF（关闭）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPitchValue：设置变调参数。

    ```
    public abstract int setAudioEffectPitchValue(double value);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |value|double|参数取值范围：\[0.5,2.0\]，默认值为1.0，表示音调不变。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectReverbMode：设置混响音效模式。

    ```
    public abstract int setAudioEffectReverbMode(AliRtcAudioEffectReverbMode mode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mode|[AliRtcAudioEffectReverbMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|音效混响模式，默认值为AliRtcAudioEffectReverb\_Off（关闭）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectReverbParamType：设置混响音效类型和具体参数。

    ```
    public abstract int setAudioEffectReverbParamType(AliRtcAudioEffectReverbParamType type, float value);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |type|[AliRtcAudioEffectReverbParamType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|音效混响参数。|
    |value|float|具体参数值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startAudioAccompany：开始混音。

    ```
    public abstract int startAudioAccompany(String fileName, boolean onlyLocalPlay, boolean replaceMic, int loopCycles);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |filePath|String|混音文件路径。|
    |onlyLocalPlay|boolean|是否仅本地播放，取值：    -   true：仅本地播放。
    -   false：本地播放且推流到远端。 |
    |replaceMic|boolean|是否替换mic的音频流，    -   true：伴奏音频流替换本地mic音频流。
    -   false：伴奏音频流和mic音频流同时推。 |
    |loopCycles|int|循环次数，-1表示一直循环。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioAccompany：停止混音。

    ```
    public abstract int stopAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioAccompanyVolume：设置混音音量。

    ```
    public abstract int setAudioAccompanyVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。设置音量需要在startAudioAccompany后才能生效。

-   setAudioAccompanyPublishVolume：设置混音之后推流出去的音量（Android和iOS）。

    ```
    public abstract int setAudioAccompanyPublishVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。设置音量需要在startAudioAccompany后才能生效。

-   getAudioAccompanyPublishVolume：获取推流出去的混音音量。

    ```
    public abstract int getAudioAccompanyPublishVolume();
    ```

    返回说明

    返回推流出的混音音量。

-   setAudioAccompanyPlayoutVolume：设置混音之后本地播放的音量（Android和iOS）。

    ```
    public abstract int setAudioAccompanyPlayoutVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。设置音量需要在startAudioAccompany后才能生效。

-   getAudioAccompanyPlayoutVolume：获取混音本地播放的音量。

    ```
    public abstract int getAudioAccompanyPlayoutVolume();
    ```

    返回说明

    当前混音本地播放的音量大小。

-   pauseAudioAccompany：暂停混音。

    ```
    public abstract int pauseAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAudioAccompany：重新开始混音。

    ```
    public abstract int resumeAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioAccompanyDuration：获取伴奏文件时长。

    ```
    public abstract int getAudioAccompanyDuration();
    ```

    返回说明

    当前伴奏文件时长，单位为毫秒。

-   getAudioAccompanyCurrentPosition：获取音乐文件播放进度。

    ```
    public abstract int getAudioAccompanyCurrentPosition();
    ```

    返回说明

    当前音乐文件播放进度，单位为毫秒。

-   setAudioAccompanyPosition：设置音频文件的播放位置。

    ```
    public abstract int setAudioAccompanyPosition(int posMs);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |posMs|int|进度条位置，单位：毫秒。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   preloadAudioEffect：预加载音效文件。

    ```
    public abstract int preloadAudioEffect(int soundId, String filePath);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|
    |filePath|String|音效文件路径。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   unloadAudioEffect：删除预加载的音效文件。

    ```
    public abstract int unloadAudioEffect(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   playAudioEffect：开始播放音效。

    ```
    public abstract int playAudioEffect(int soundId, String filePath, int cycles, boolean publish);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|
    |filePath|String|音效文件路径。|
    |cycles|int|循环次数，-1表示一直循环。|
    |publish|boolean|是否将音效音频流推到远端，取值：    -   true：将音效音频流推到远端。
    -   false：不将音效音频流推到远端。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioEffect：停止播放音效。

    ```
    public abstract int stopAudioEffect(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAllAudioEffects：停止播放所有音效。

    ```
    public abstract int stopAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPublishVolume：设置音效推流音量。

    ```
    public abstract int setAudioEffectPublishVolume(int soundId, int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioEffectPublishVolume：获取推流音效音量。

    ```
    public abstract int getAudioEffectPublishVolume(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPlayoutVolume：设置音效本地播放音量。

    ```
    public abstract int setAudioEffectPlayoutVolume(int soundId, int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioEffectPlayoutVolume：获取音效本地播放音量（Android和iOS）。

    ```
    public abstract int getAudioEffectPlayoutVolume(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAllAudioEffectsPublishVolume：设置所有音效本地播放音量。

    ```
    public abstract int setAllAudioEffectsPublishVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAllAudioEffectsPlayoutVolume：设置所有音效推流音量（Android和iOS）。

    ```
    public abstract int setAllAudioEffectsPlayoutVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pauseAudioEffect：暂停音效。

    ```
    public abstract int pauseAudioEffect(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pauseAllAudioEffects：暂停所有音效。

    ```
    public abstract int pauseAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAudioEffect：重新开始播放音效。

    ```
    public abstract int resumeAudioEffect(int soundId);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |soundId|int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAllAudioEffects：重新开始播放所有音效。

    ```
    public abstract int resumeAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableEarBack：启用耳返。

    ```
    public abstract int enableEarBack(boolean enable);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否启用耳返，取值：    -   true：开启耳返。
    -   false：关闭耳返。
默认值为false。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setEarBackVolume：设置耳返音量。

    ```
    public abstract int setEarBackVolume(int volume);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |volume|int|音量，取值范围：0~100。默认值为100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   requestAudioFocus：请求音频焦点。

    ```
    public abstract int requestAudioFocus();
    ```

-   abandonAudioFocus：丢失音频焦点。

    ```
    public abstract int abandonAudioFocus();
    ```

-   registerVideoSampleObserver：订阅视频数据输出。

    ```
    public abstract void registerVideoSampleObserver(AliVideoObserver observer);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |observer|[AliVideoObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|视频数据接收对象。|

    返回说明

    输出数据将通过AliVideoObserver回调返回。

-   unRegisterVideoSampleObserver：取消订阅视频数据输出。

    ```
    public abstract void unRegisterVideoSampleObserver();
    ```

-   registerLocalVideoTextureObserver：订阅本地视频纹理数据。

    ```
    public abstract void registerLocalVideoTextureObserver(AliTextureObserver observer);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |observer|[AliTextureObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|视频数据接收对象。|

    返回说明

    输出数据将通过AliVideoObserver回调返回。

-   unRegisterLocalVideoTextureObserver：取消本地视频纹理数据输出。

    ```
    public abstract void  unRegisterLocalVideoTextureObserver();
    ```

-   registerAudioObserver：订阅音频数据输出。

    ```
    public abstract void registerAudioObserver(AliAudioType type, AliAudioObserver observer);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |type|[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|数据类型。|
    |observer|[AliVideoObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|音频数据接收对象。|

-   unRegisterAudioObserver：取消音频数据输出。

    ```
    public abstract void unRegisterAudioObserver(AliAudioType type);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |type|[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|数据类型。|

-   setSubscribeAudioNumChannel：设置输出音频声道数，默认单声道（混音前数据不支持该参数设置）。

    ```
    public abstract void setSubscribeAudioNumChannel(AliRtcAudioNumChannel numChannel);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |numChannel|[AliRtcAudioNumChannel](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|声道数。|

-   setSubscribeAudioSampleRate：设置输出音频采样率，默认44.1k（混音前数据不支持该参数设置）。

    ```
    public abstract void setSubscribeAudioSampleRate(AliRtcAudioSampleRate sampleRate );
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |sampleRate|[AliRtcAudioSampleRate](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|采样率。|

-   registerAudioVolumeObserver：注册音量数据输出对象。

    ```
    public abstract void registerAudioVolumeObserver(AliRtcAudioVolumeObserver observer);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |observer|[AliRtcAudioVolumeObserver](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|音量数据接收对象。|

-   unRegisterAudioVolumeObserver：取消注册音量数据输出对象。

    ```
    public abstract void unRegisterAudioVolumeObserver();
    ```

-   setExternalVideoSource：启用外部视频输入源。

    ```
    public abstract void setExternalVideoSource(boolean enable,boolean useTexture,
                                                AliRtcVideoTrack streamType,AliRtcRenderMode renderMode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|启用外部视频输入源，取值：    -   true：启用。
    -   false：关闭。
默认值为false。|
    |useTexture|boolean|是否使用texture模式，取值：    -   true：使用。
    -   fase：不使用。
默认值为false。|
    |type|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流类型。|
    |renderMode|[AliRtcRenderMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染模式。|

-   pushExternalVideoFrame：输入视频数据。

    ```
    public abstract int pushExternalVideoFrame(AliRawDataFrame aliRawDataFrame,AliRtcVideoTrack streameType);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |frame|[AliRawDataFrame](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|帧数据。|
    |type|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setExternalAudioSource：设置是否启用外部音频输入源。

    ```
    public abstract  int setExternalAudioSource(boolean enable ,int sampleRate,int channels);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否启用外部音频输入源。    -   true：开启。
    -   false：关闭。
默认值为false。|
    |sampleRate|int|采样率。|
    |channelsPerFrame|int|声道数，取值1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pushExternalAudioFrameRawData：输入音频数据。

    ```
    public abstract  int pushExternalAudioFrameRawData(byte[] samples,int samplesLength,long timestamp);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |samples|byte\[\]|音频数据，不建议超过40毫秒。|
    |samplesLength|int|采样。|
    |timestamp|double|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setExternalAudioVolume：设置混音音量。

    ```
    public abstract  int setExternalAudioVolume(int vol);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |vol|int|音量，取值范围：0~100，默认值为50。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getExternalAudioVolume：获取混音音量。

    ```
    public abstract  int getExternalAudioVolume();
    ```

    返回说明

    返回当前混音音量。

-   setMixedWithMic：设置是否与麦克风采集音频混合。

    ```
    public abstract int setMixedWithMic(boolean mixed);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |mixed|boolean|是否与麦克风采集音频混合，取值：    -   true：混合。
    -   false：完全替换麦克风采集数据。
默认值为true。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setExteranlAudioRender：设置是否启用外部输入音频播放。

    ```
    public abstract int setExteranlAudioRender(boolean enable,int sampleRate,int channelsPerFrame);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否启用外部输入音频播放，取值：    -   true：开启。
    -   false：关闭。
默认值为false。|
    |sampleRate|int|采样率。|
    |channelsPerFrame|int|声道数，取值1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pushExternalAudioRenderRawData：输入外部音频播放数据。

    ```
    public abstract int pushExternalAudioRenderRawData(byte[]audioSamples ,int sampleLength,int sampleRate,
                                                       int channelsPerFrame, long timestamp);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |audioSamples|byte\[\]|音频数据。|
    |sampleLength|int|音频数据长度。|
    |sampleRate|int|音频采样率。|
    |channelsPerFrame|int|音频声道数。|
    |timestamp|long|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startLiveStreaming：开始直播拉流。

    ```
    public abstract void startLiveStreaming(AliRtcAuthInfo aliRtcAuthInfo);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|入会鉴权信息。|

    **说明：** 通过onStartLiveStreamingResult回调反馈直播拉流成功与否。

-   stopLiveStreaming：停止直播拉流。

    ```
    public abstract int stopLiveStreaming();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startPublishLiveStream：开启旁路直播。

    ```
    public abstract int startPublishLiveStream(String streamUrl,AliRtcLiveTranscoding transcoding);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |streamUrl|String|推流地址。|
    |transcoding|[AliRtcLiveTranscoding](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   updatePublishLiveStream：更新旁路直播相关参数。

    ```
    public abstract int updatePublishLiveStream(String streamUrl,AliRtcLiveTranscoding transcoding);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |streamUrl|String|推流地址。|
    |transcoding|[AliRtcLiveTranscoding](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopPublishLiveStream：停止旁路直播。

    ```
    public abstract int stopPublishLiveStream(String streamUrl);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |streamUrl|String|推流地址。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setLiveStreamingViewConfig：设置直播拉流窗口及渲染参数。

    ```
    public abstract int setLiveStreamingViewConfig(AliVideoCanvas aliVideoCanvas,String uid);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |aliVideoCanvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|String|本地用户ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startChannelRelay：开启跨频道连麦。

    ```
    public abstract int startChannelRelay(AliRtcChannelRelayConfiguration configuration);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |configuration|[AliRtcChannelRelayConfiguration](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   updateChannelRelay：更新跨频道连麦。

    ```
    public abstract int updateChannelRelay(AliRtcChannelRelayConfiguration configuration);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |configuration|[AliRtcChannelRelayConfiguration](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopChannelRelay：停止跨频道连麦。

    ```
    public abstract int stopChannelRelay();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startPreview：开始本地预览。

    ```
    public abstract int startPreview();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopPreview：停止本地预览。

    ```
    public abstract int stopPreview();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    public abstract String[] getOnlineRemoteUsers();
    ```

    返回说明

    返回String\[\]表示用户列表，保存的是用户ID。

-   getUserInfo：查询远端用户的各种状态。

    ```
    public abstract AliRtcRemoteUserInfo getUserInfo(String uid);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|远端用户ID。从App server分配的唯一标示符。|

    返回说明

    返回一个远端用户对象。

-   isUserOnline：判断用户是否在线。

    ```
    public abstract boolean isUserOnline(String uid);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|用户ID。从App server分配的唯一标示符。|

    返回说明

    true为在线，false为未在线。

-   setLogLevel：设置日志等级。

    ```
    public static void setLogLevel(AliRtcLogLevel logLevel);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|Log级别。|

-   getSdkVersion：获取SDK版本号。

    ```
    public static String getSdkVersion();
    ```

    返回说明

    返回SDK版本号。

-   getErrorDescription：获取错误码描述。

    ```
    public static String getErrorDescription(int errorCode);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |errorCode|int|错误码。|

    返回说明

    返回错误码描述字符串。

-   setClientRole：设置用户角色。

    ```
    public abstract int setClientRole(AliRTCSdkClientRole clientRole);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |clientRole|[AliRTCSdkClientRole](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|用户角色类型，默认值为AliRtcClientRoleInteractive（主播角色）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentClientRole：获取用户角色。

    ```
    public abstract AliRTCSdkClientRole getCurrentClientRole();
    ```

    返回说明

    返回当前用户角色。

-   startNetworkQualityProbeTest：开始网络质量探测。

    ```
    public abstract int startNetworkQualityProbeTest();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。请在进入频道之前调用，探测结果通过[onNetworkQualityProbeTest](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调返回。

-   stopNetworkQualityProbeTest：停止网络质量探测。

    ```
    public abstract int stopNetworkQualityProbeTest();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   respondMessageNotification：发送消息通知。

    ```
    public abstract int respondMessageNotification(String tid, String contentType, String content);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |tid|String|信令ID。|
    |contentType|String|消息类型|
    |content|String|消息内容。|

-   uplinkChannelMessage：信令通道使用。

    ```
    public abstract int uplinkChannelMessage(String contentType, String content);
    ```

    Saas客户端发送信令消息到Saas服务端。

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |contentType|String|信令类型|
    |content|String|信令内容。|

-   postFeedback：问题反馈。

    ```
    public abstract void postFeedback(String uid,String channelId,String description,AliRtcFeedbackType type,long timeStamp);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |uid|String|当前用户ID（可为空）。|
    |channelId|String|当前频道ID（可为空）。|
    |description|String|问题描述（支持中英文，不为空）。|
    |type|[AliRtcFeedbackType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|问题类型。|
    |timeStamp|long|问题发生的时间戳（Unix时间戳，大致时间，无需特别精确，可以为0）。|

-   sendMediaExtensionMsg：发送媒体扩展信息。

    ```
    public abstract int sendMediaExtensionMsg(byte[]message, int repeatCount);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |message|byte\[\]|扩展信息。|
    |repeatCount|int|重复次数。|

    返回说明

    -   0：成功。
    -   -1：未推流。
    -   -2：参数错误。
    -   -3：过于频繁。
-   startIntelligentDenoise：开启智能降噪。

    ```
    public abstract int startIntelligentDenoise();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。此接口可以通话过程中控制打开智能降噪功能。

-   stopIntelligentDenoise：关闭智能降噪。

    ```
    public abstract void stopIntelligentDenoise();
    ```

-   refreshAuthInfo：刷新鉴权信息。

    ```
    public abstract int refreshAuthInfo(AliRtcAuthInfo authInfo);
    ```

    参数说明

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|鉴权信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentConnectionStatus：获取当前网络链接状态。

    ```
    public abstract AliRtcConnectionStatus getCurrentConnectionStatus();
    ```

    返回说明

    当前网络链接状态。


