---
keyword: [iOS SDK, AliRtcEngine, Mac]
---

# AliRtcEngine接口

本文为您介绍了iOS SDK和Mac SDK的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[setH5CompatibleMode](#li_zvd_xcd_bxn)|设置H5兼容模式|1.1|
|[getH5CompatibleMode](#li_71g_5p7_32q)|检查当前是否兼容H5|1.1|
|[sharedInstance](#li_fmb_gdb_ge2)|创建AliRtcEngine实例（同一时间只会存在一个实例）|1.1|
|[destroy](#p_5hl_yyf_r60)|销毁SDK|1.1|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAutoPublish](#li_lft_8h9_jqi)|设置是否自动发布，是否自动订阅|1.1|
|[joinChannel](#li_z31_yrd_vbt)|加入频道|1.1|
|[leaveChannel](#li_l7y_g8o_fgg)|离开频道|1.1|
|[isInCall](#li_0ca_603_a3d)|检查当前是否在频道中|1.1|
|[setChannelProfile](#li_5kv_g49_ikw)|设置频道模式|1.15|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoPublish](#li_qqg_vyl_bt3)|查询当前是否为自动发布模式|1.1|
|[configLocalCameraPublish](#li_kwv_2i8_sd4)|设置是否允许发布相机流|1.1|
|[isLocalCameraPublishEnabled](#li_hcs_1dd_bln)|查询当前是否允许发布相机流|1.1|
|[configLocalScreenPublish](#p_n1k_21p_irq)|设置是否允许发布屏幕流（仅Mac）|1.1|
|[isLocalScreenPublishEnabled](#p_1eo_h2v_dn3)|查询当前是否允许发布屏幕流（仅Mac）|1.1|
|[configLocalAudioPublish](#li_525_rs6_oj8)|设置是否允许发布音频流|1.1|
|[isLocalAudioPublishEnabled](#li_2ru_aqb_gcm)|查询当前是否允许发布音频流|1.1|
|[configLocalSimulcast](#li_ibe_2it_cyz)|设置是否允许发布次要视频流|1.1|
|[isLocalSimulcastEnabled](#li_hz3_udy_dgl)|查询当前是否允许发布次要视频流|1.1|
|[publish](#li_92h_h5u_2ag)|手动发布视频和音频流|1.1|

订阅相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoSubscribe](#li_uuk_rj3_lte)|查询当前是否为自动订阅模式|1.1|
|[configRemoteCameraTrack](#li_l4g_r3v_7r3)|设置是否订阅远端相机流|1.1|
|[configRemoteScreenTrack](#li_1hw_2s1_jv2)|设置是否订阅远端屏幕流|1.1|
|[configRemoteAudio](#li_k2j_q1m_zde)|设置是否订阅远端音频流|1.1|
|[subscribe](#li_6g2_cou_e7q)|手动订阅视频和音频流|1.1|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#li_t9j_e1u_hs9)|设置视频流的参数|1.1|
|[setLocalViewConfig](#li_8vs_laf_z52)|为本地预览设置渲染窗口以及绘制参数|1.1|
|[muteLocalCamera](#li_uh1_f0x_xj8)|设置是否停止发布本地视频流|1.1|
|[setRemoteViewConfig](#li_qyi_2t2_y74)|为远端的视频设置渲染窗口以及绘制参数|1.1|
|[getCameraList](#p_l4e_608_tmk)|获取摄像头列表（仅Mac）|1.1|
|[getCurrentCamera](#p_lem_5zy_vpe)|获取当前使用的摄像头名称（仅Mac）|1.1|
|[setCurrentCamera](#p_76j_262_w5e)|选择摄像头（仅Mac）|1.1|
|[switchCamera](#li_h2e_aoe_xf3)|切换前后摄像头（仅iOS）|1.1|
|[setCameraZoom](#li_9vd_uc5_y2a)|设置摄像头参数（仅iOS）|1.1|
|[isCameraOn](#li_vld_1lu_21t)|检查摄像头是否打开（仅iOS）|1.1|
|[isCameraFocusPointSupported](#p_3a1_06a_v3q)|相机是否支持手动聚焦（仅iOS）|1.14|
|[isCameraExposurePointSupported](#p_6i5_olk_1qe)|相机是否支持手动曝光（仅iOS）|1.14|
|[setCameraFocusPoint](#p_gtd_y01_ktx)|设置手动聚焦的坐标点（仅iOS）|1.14|
|[setCameraExposurePoint](#p_j3w_dim_okj)|设置手动曝光的坐标点（仅iOS）|1.14|
|[subscribeVideoPreprocessData](#p_cpm_jsb_n60)|订阅采集视频前处理裸数据（仅iOS）|1.14|
|[unSubscribeVideoPreprocessData](#p_7vb_6t5_oin)|取消采集订阅前处理裸数据（仅iOS）|1.14|
|[enableHighDefinitionPreview](#p_6av_1ta_r7c)|是否允许高清预览，默认打开（仅iOS）|1.14|
|[registerVideoSampleObserver](#li_xvn_1ji_k2g)|订阅视频数据输出|1.16.2|
|[unregisterVideoSampleObserver](#li_vdc_xs1_qtj)|取消订阅视频数据输出|1.16.2|
|[setVideoSwapWidthAndHeight](#li_ug1_79s_6l6)|设置视频track是否需要交换宽高|1.16.2|
|[muteAllRemoteVideoRendering](#li_th1_i1s_nif)|mute或unmute远端的所有视频track的渲染|1.16.2|
|[getCurrentCameraID](#li_sqt_0h7_tfq)|获取当前使用的摄像头ID（仅Mac）|1.16.2|
|[setCurrentCameraWithID](#li_1sw_qzu_eg4)|通过设备ID选择摄像头（仅Mac）|1.16.2|
|[setExternalVideoSource](#li_a5l_pum_fl4)|启用外部视频输入源|1.17.9|
|[pushExternalVideoFrame](#li_2bt_fyg_e1k)|输入外部视频|-   Mac：1.16.2
-   iOS：1.17.9 |
|[setBeautyEffect](#li_lx4_vn7_0qc)|设置基础美颜|1.17.9|
|[getCurrentCameraDirection](#li_y28_5g4_k5k)|获取当前摄像头方向（仅iOS）|1.17.20|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAudioOnlyMode](#li_lzf_npx_uem)|设置为纯音频模式还是音视频模式|1.1|
|[isAudioOnly](#li_25q_wmj_o3s)|查询当前是否为纯音频模式|1.1|
|[muteLocalMic](#li_0zq_pe4_6t8)|设置是否停止发布本地音频|1.1|
|[muteRemoteAudioPlaying](#li_3cc_r53_5no)|设置是否停止播放远端音频流|1.1|
|[enableSpeakerphone](#li_l5p_922_m67)|切换听筒、扬声器输出（仅iOS）|1.1|
|[getAudioCaptures](#p_wc1_6po_2b5)|获取系统中的录音设备列表（仅Mac）|1.1|
|[getCurrentAudioCapture](#p_mid_xth_r5y)|获取当前使用的音频采集设备名称（仅Mac）|1.1|
|[setCurrentAudioCapture](#p_8aq_ksp_81h)|选择音频采集设备（仅Mac）|1.1|
|[getAudioRenderers](#p_rqs_i7a_nea)|获取系统中的扬声器列表（仅Mac）|1.1|
|[getCurrentAudioRenderer](#p_1gq_qwj_qug)|获取当前使用的音频播放设备（仅Mac）|1.1|
|[setCurrentAudioRenderer](#p_bxi_yg5_oqv)|选择音频播放设备（仅Mac）|1.1|
|[startAudioCapture](#li_0vf_8eq_so2)|开启音频采集|1.11|
|[stopAudioCapture](#li_b1e_hol_fbs)|关闭音频采集|1.11|
|[startAudioPlayer](#li_d2k_tlz_si0)|开启音频播放|1.11|
|[stopAudioPlayer](#li_bgy_g1o_buu)|关闭音频播放|1.11|
|[startAudioAccompanyWithFile](#li_uwn_629_c4w)|开始播放伴奏（仅iOS）|1.15|
|[stopAudioAccompany](#li_218_p1z_1uo)|停止伴奏（仅iOS）|1.15|
|[setAudioAccompanyVolume](#li_wb3_729_udm)|设置伴奏音量（仅iOS）|1.15|
|[setAudioAccompanyPublishVolume](#li_gs9_h6o_c6s)|设置伴奏之后推流出去的音量（仅iOS）|1.15|
|[getAudioAccompanyPublishVolume](#li_bmr_h33_aqw)|获取伴奏推流音量（仅iOS）|1.15|
|[setAudioAccompanyPlayoutVolume](#li_sr5_sh5_u2x)|设置伴奏本地音量（仅iOS）|1.15|
|[getAudioAccompanyPlayoutVolume](#li_fxq_irq_lav)|获取伴奏本地音量（仅iOS）|1.15|
|[pauseAudioAccompany](#li_ri8_t4a_o59)|暂停播放伴奏（仅iOS）|1.15|
|[resumeAudioAccompany](#li_drs_dy0_pk4)|恢复播放伴奏（仅iOS）|1.15|
|[preloadAudioEffectWithSoundId](#li_hl4_fu8_0qn)|预加载音效（仅iOS）|1.15|
|[unloadAudioEffectWithSoundId](#li_i59_bwx_4a1)|清除预加载音效（仅iOS）|1.15|
|[playAudioEffectWithSoundId](#li_h2x_eg3_jhl)|开始播放音效（仅iOS）|1.15|
|[stopAudioEffectWithSoundId](#li_01f_5po_4qb)|停止播放音效（仅iOS）|1.15|
|[setAudioEffectPublishVolumeWithSoundId](#li_el9_56g_5wj)|设置音效推流音量（仅iOS）|1.15|
|[getAudioEffectPublishVolumeWithSoundId](#li_79i_m6o_t72)|获取音效推流音量（仅iOS）|1.15|
|[setAudioEffectPlayoutVolumeWithSoundId](#li_pt8_85u_g7f)|设置音效本地音量（仅iOS）|1.15|
|[getAudioEffectPlayoutVolumeWithSoundId](#li_oxn_hjv_pi7)|获取音效本地音量（仅iOS）|1.15|
|[pauseAudioEffectWithSoundId](#li_8px_y9z_6bz)|暂停播放音效（仅iOS）|1.15|
|[resumeAudioEffectWithSoundId](#li_5xu_2op_ji7)|恢复播放音效（仅iOS）|1.15|
|[enableEarBack](#li_cs9_bc7_svx)|启用耳返（仅iOS）|1.15|
|[setEarBackVolume](#li_371_mdg_jqy)|设置耳返音量（仅iOS）|1.15|
|[setSubscribeAudioNumChannel](#li_c2k_eer_yox)|设置回调音频声道数|1.15|
|[setSubscribeAudioSampleRate](#li_lr2_1gv_s6m)|设置回调音频采样率|1.15|
|[setAudioSessionOperationRestriction](#li_nmd_9ei_3dy)|设置SDK对AVAudioSession的控制权限（仅iOS）|1.15|
|[setRecordingVolume](#li_0nn_8x8_xdw)|设置录音音量（仅iOS）|1.16|
|[setPlayoutVolume](#li_hwq_dnw_twq)|设置播放音量（仅iOS）|1.16|
|[subscribeAudioData](#li_aj2_sst_2u7)|订阅音频数据|1.16|
|[unSubscribeAudioData](#li_3ku_zve_t4r)|取消订阅音频数据|1.16|
|[muteAllRemoteAudioPlaying](#li_rr9_wyq_rdw)|停止远端的所有音频流的播放|1.16.2|
|[setExteranlAudioRender](#li_zjw_x7t_a71)|设置是否启用外部输入音频播放|1.16.2|
|[pushExternalAudioRenderRawData](#li_b25_kva_xz4)|输入音频播放数据|1.16.2|
|[isEnableSpeakerphone](#li_z35_6bu_wbl)|获取当前音频输出为听筒还是扬声器（仅iOS）|1.16.2|
|[getCurrentAudioCaptureID](#li_wcd_z9d_avc)|获取使用的录音设备ID（仅Mac）|1.16.2|
|[setCurrentAudioCaptureWithID](#li_c7x_3s7_400)|通过设备ID选择录音设备（仅Mac）|1.16.2|
|[getCurrentAudioRendererID](#li_jl1_ozt_0mf)|获取当前使用的扬声器ID（仅Mac）|1.16.2|
|[setCurrentAudioRendererWithID](#li_nxl_51j_w2s)|通过设备ID选择扬声器（仅Mac）|1.16.2|
|[startTestAudioRecordWithName](#li_v86_swh_3o5)|开始测试音频采集设备（仅Mac）|1.16.2|
|[stopTestAudioRecord](#li_ubb_ze3_j1a)|停止测试音频采集设备（仅Mac）|1.16.2|
|[startTestAudioPlayoutWithName](#li_nb8_shn_1d3)|开始测试音频播放设备（仅Mac）|1.16.2|
|[stopTestAudioPlayout](#li_4gm_adq_wst)|停止测试音频播放设备（仅Mac）|1.16.2|
|[setExternalAudioSource](#li_qk5_zk7_kek)|设置是否将外部音频数据作为推流的输入源|-   Mac：1.16.2
-   iOS：1.17.9 |
|[pushExternalAudioFrameRawData](#li_w6f_6ml_v01)|输入音频数据|-   Mac：1.16.2
-   iOS：1.17.9 |
|[setExternalAudioVolume](#li_7aq_b0v_fni)|设置外部音频输入音量|-   Mac：1.16.2
-   iOS：1.17.9 |
|[getExternalAudioVolume](#li_lgw_hg9_6kx)|获取外部音频输入音量|-   Mac：1.16.2
-   iOS：1.17.9 |
|[setMixedWithMic](#li_irz_td7_o60)|设置外部音频输入是否与麦克风采集音频混合|-   Mac：1.16.2
-   iOS：1.17.9 |
|[setExternalAudioRenderVolume](#li_hhu_x0j_c4n)|设置外部音频播放音量（仅Mac）|1.16.2|
|[getExternalAudioRenderVolume](#li_it0_eim_jv8)|获取音频播放音量（仅Mac）|1.16.2|
|[setVolumeCallbackIntervalMs](#li_0gk_1wo_pb9)|设置音量回调频率和平滑系数|1.17|
|[setAudioEffectReverbMode](#li_slu_1uw_9d7)|设置混响音效模式|1.17|
|[setAudioEffectReverbParamType](#li_qfi_0vw_hco)|设置混响音效类型|1.17|

预览接口

|API|描述|以上版本支持|
|---|--|------|
|[startPreview](#li_pp8_zof_82j)|开始本地预览|1.1|
|[stopPreview](#li_js8_nsv_91v)|停止本地预览|1.1|

远端用户查询接口

|API|描述|以上版本支持|
|---|--|------|
|[getOnlineRemoteUsers](#li_h5x_502_n29)|获取远端在线用户列表|1.1|
|[getUserInfo](#li_tvs_dq0_orq)|查询远端用户信息|1.1|
|[isUserOnline](#li_gpg_5h3_n48)|查询用户是否在线|1.1|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[setLogLevel](#li_qs2_3ga_k7w)|设置日志级别|1.1|
|[getSdkVersion](#li_rec_gk3_tpc)|获取SDK版本号|1.1|
|[uploadLog](#li_plb_zzq_zjs)|上传日志|1.15|
|[startIntelligentDenoise](#li_3rx_l2i_zuk)|开启智能降噪（仅Mac）|1.15|
|[stopIntelligentDenoise](#li_a9r_uwd_l3b)|关闭智能降噪（仅Mac）|1.15|
|[setClientRole](#li_a9r_uwd_l3b)|设置用户角色|1.16|
|[setLogDirPath](#li_bsb_0fx_wqb)|设置SDK日志文件保存路径|1.16.2|
|[setDeviceOrientationMode](#li_55e_csm_nzc)|设置设备横竖屏方向|1.16.2|
|[startLastmileDetect](#li_hdf_f4z_oce)|开始网络质量探测|1.16.2|
|[stopLastmileDetect](#li_28f_ppz_519)|停止网络质量探测|1.16.2|
|[startRecord](#li_gwj_7xq_3hq)|开始录制|1.17.1|
|[stopRecord](#li_xx9_l0p_1ua)|停止录制|1.17|
|[getCurrentClientRole](#li_9en_124_dws)|获取当前用户角色（仅iOS）|1.17.9|
|[postFeedbackWithUid](#li_yrm_t6e_vur)|SDK问题反馈|-   Mac：1.17.10
-   iOS：1.17.13 |
|[sendMediaExtensionMsg](#li_ynk_vxv_g9u)|发送媒体扩展信息|1.17.1|
|[getClientRole](#li_srk_c0i_j20)|获取当前用户角色（仅Mac）|1.17.19|

## 接口详情

-   setH5CompatibleMode：设置H5兼容模式，默认不兼容H5。

    **说明：** 该接口仅支持在创建AliRtcEngine实例前调用。

    ```
    + (void)setH5CompatibleMode:(BOOL)comp;
    ```

    |参数|类型|描述|
    |--|--|--|
    |comp|BOOL|YES为兼容H5模式，NO为不兼容H5。|

-   getH5CompatibleMode：检查当前是否兼容H5，返回YES标识兼容H5，NO表示不兼容H5。

    **说明：** 该接口仅支持在创建AliRtcEngine实例前调用。

    ```
    + (BOOL)getH5CompatibleMode;
    ```

-   sharedInstance:：创建AliRtcEngine实例（同一时间只会存在一个实例）。

    ```
    + (instancetype)sharedInstance:(id<AliRtcEngineDelegate>)delegate extras:(NSString *)extras;
    ```

    |参数|类型|描述|
    |--|--|--|
    |delegate|[AliRtcEngineDelegate](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)类型的代理|监听回调的代理。|
    |extras|NSString \*|SDK初始化配置，目前请使用`@””`。|

-   destroy：销毁SDK，在所有操作结束之后调用。

    ```
    + (void)destroy;
    ```

-   setAutoPublish：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，必须在加入频道之前设置。

    ```
    - (int)setAutoPublish:(BOOL)autoPub withAutoSubscribe:(BOOL)autoSub;
    ```

    |参数|类型|描述|
    |--|--|--|
    |autoPub|BOOL|YES表示自动发布，NO表示手动发布。|
    |autoSub|BOOL|YES表示自动订阅，NO表示手动订阅。|

-   joinChannel：加入频道。加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道；如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ```
    - (void)joinChannel:(AliRtcAuthInfo *)authInfo name:(NSString *)userName onResult:(void(^)(NSInteger errCode))onResult;
    ```

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo \*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|鉴权信息。|
    |userName|NSString \*|用户的显示名称（ 非用户ID）。|
    |onResult|void\(^\)\(NSInteger errCode\)|当joinChannel执行结束后回调。|

-   leaveChannel：离开频道。

    1.15及以上版本：销毁引擎只能通过destroy方法。

    1.15以下版本：离开频道时，AliRtcEngine实例会被销毁，如需继续加入频道等操作，需要先重新调用getInstance初始化AliRtcEngine实例。

    ```
    - (void)leaveChannel;
    ```

-   isInCall：检查当前是否在频道中，返回YES表示在频道中，NO表示不在频道中。

    ```
    - (BOOL)isInCall;
    ```

-   setChannelProfile：设置频道模式，返回0为成功，非0表示失败。

    **说明：** 只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

    ```
    - (int)setChannelProfile:(AliRtcChannelProfile)profile;
    ```

    |参数|类型|描述|
    |--|--|--|
    |profile|[AliRtcChannelProfile](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|频道模式类型。默认为AliRtcCommunication通信模式。|

-   isAutoPublish：查询当前是否为自动发布模式，返回YES为自动发布，NO为手动发布。

    ```
    - (BOOL)isAutoPublish;
    ```

-   configLocalCameraPublish：设置是否允许发布相机流。默认为允许发布相机流，手动发布时，需要调用publish才能生效。

    ```
    - (void)configLocalCameraPublish:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布相机流，NO为不允许。|

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流，返回YES为允许，NO为不允许。

    ```
    - (BOOL)isLocalCameraPublishEnabled;
    ```

-   configLocalScreenPublish（仅Mac可用）：设置是否允许发布屏幕流。默认为不允许发布屏幕流，手动发布时，需要调用publish才能生效。

    ```
    - (void)configLocalScreenPublish:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布屏幕流，NO为不允许发布屏幕流。|

-   isLocalScreenPublishEnabled（仅Mac可用）：查询当前是否允许发布屏幕流，返回YES为允许，NO为不允许。

    ```
    - (BOOL)isLocalScreenPublishEnabled;
    ```

-   configLocalAudioPublish：设置是否允许发布音频流。默认为允许发布音频流，手动发布时，需要调用publish才能生效。

    ```
    - (void)configLocalAudioPublish:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布音频流，NO为不允许。|

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流，返回YES为允许，NO为不允许。

    ```
    - (BOOL)isLocalAudioPublishEnabled;
    ```

-   configLocalSimulcast：设置是否允许发布次要视频流。默认为允许发布次要视频流，手动发布时，需要调用publish才能生效。

    ```
    - (int)configLocalSimulcast:(BOOL)enabled forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enabled|BOOL|YES表示允许发布次要流，NO表示不允许。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|流类型。当前只支持AliVideoTrackCamera（相机流）。|

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流，返回YES为允许，NO为不允许。

    ```
    - (BOOL)isLocalSimulcastEnabled;
    ```

-   publish：手动发布视频和音频流。

    -   调用publish的实际表现需要结合configLocalCameraPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以发布相应的视频和音频流。
    -   发布和停止发布都是调用publish。
    -   如需停止发布，则需要上述3个配置接口的参数都置为NO，再调用publish。
    -   需要在加入频道成功之后调用该接口。
    ```
    - (void)publish:(void (^)(int errCode))onResult;
    ```

    |参数|类型|描述|
    |--|--|--|
    |onResult|void \(^\)\(int errCode\)|当调用publish执行结束后回调。|

-   isAutoSubscribe：查询当前是否为自动订阅模式，返回YES为自动订阅，NO为手动订阅。

    ```
    - (BOOL)isAutoSubscribe;
    ```

-   configRemoteCameraTrack：设置是否订阅远端相机流。默认为订阅大流。当对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。

    ```
    - (void)configRemoteCameraTrack:(NSString *)uid preferMaster:(BOOL)master enable:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |master|BOOL|YES为订阅大流，NO为订阅次小流。|
    |enable|BOOL|YES为订阅远端相机流，NO为停止订阅远。端相机流|

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。默认为不订阅远端屏幕流。当对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。。

    ```
    - (void)configRemoteScreenTrack:(NSString *)uid enable:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |enable|BOOL|YES为订阅远端屏幕流，NO为停止订阅远端屏幕流。|

-   configRemoteAudio：设置是否订阅远端音频流。默认为订阅远端音频流。当对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。。

    ```
    - (void)configRemoteAudio:(NSString *)uid enable:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |enable|BOOL|YES为订阅远端音频流，NO为停止订阅远端音频流。|

-   subscribe：手动订阅视频和音频流。

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如需停止订阅，则需要上述3个配置接口的参数都置为false，再调用subscribe。
    ```
    - (void)subscribe:(NSString *)uid onResult:(void (^)(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at))onResult;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |onResult|void \(^\)\(NSString \*uid, [AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) vt, [AliRtcAudioTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) at\)|当调用subscribe执行结束后回调。|

-   setVideoProfile：设置视频流的参数。

    ```
    - (void)setVideoProfile:(AliRtcVideoProfile)profile forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |profile|[AliRtcVideoProfile](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流参数。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要设置的视频Track类型。|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果viewConfig为NULL或者其成员渲染视图为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持viewConfig中其他成员变量不变，仅修改renderMode。
    -   viewConfig中渲染方式默认为AliRtcRenderModeAuto。
    ```
    - (int)setLocalViewConfig:(AliVideoCanvas *)viewConfig forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |viewConfig|[AliVideoCanvas \*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|预览只允许AliVideoTrackCamera（相机流）。|

-   muteLocalCamera：设置是否停止发布本地视频流，不改变当前视频流的采集状态。

    ```
    - (int)muteLocalCamera:(BOOL)mute forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止发布视频流，NO表示恢复发布。默认NO。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要改变发布状态的视频Track类型。|

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    -   支持加入频道之前和之后切换窗口。如果canvas为NULL或者其成员渲染视图为NULL，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeAuto。
    -   建议在订阅结果回调之后调用。
    ```
    - (int)setRemoteViewConfig:(AliVideoCanvas *)canvas uid:(NSString *)uid forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas \*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|NSString \*|用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要设置的视频Track类型。|

-   getCameraList（仅Mac可用）：获取摄像头列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getCameraList;
    ```

-   getCurrentCamera（仅Mac可用）：获取当前使用的摄像头名称。

    ```
    - (NSString *)getCurrentCamera;
    ```

-   setCurrentCamera（仅Mac可用）：选择摄像头。必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ```
    - (void)setCurrentCamera:(NSString *)camera;
    ```

    |参数|类型|描述|
    |--|--|--|
    |camera|NSString \*|摄像头名称。|

-   switchCamera（仅iOS可用）：切换前后摄像头，返回0为切换成功，其他为切换失败。

    ```
    - (int)switchCamera;
    ```

-   setCameraZoom（仅iOS可用）：设置摄像头参数，返回0表示设置成功，其他表示设置失败。

    ```
     - (int)setCameraZoom:(float)zoom flash:(BOOL)flash autoFocus:(BOOL)autoFocus;
    ```

    |参数|类型|描述|
    |--|--|--|
    |zoom|float|变焦的级别。取值：-3~3，默认为1.0。|
    |flash|BOOL|是否打开闪光灯。取值：YES\|NO。默认NO。|
    |autoFocus|BOOL|是否打开自动对焦。取值：YES\|NO。默认NO。|

-   isCameraOn（仅iOS可用）：检查摄像头是否打开，YES表示摄像头已打开，NO表示摄像头没有打开。

    ```
    - (BOOL)isCameraOn;
    ```

-   isCameraFocusPointSupported（仅iOS可用）：相机是否支持手动聚焦。

    ```
    - (BOOL)isCameraFocusPointSupported;
    ```

    该方法返回YES表示支持，NO表示不支持。

-   isCameraExposurePointSupported（仅iOS可用）：相机是否支持手动曝光。

    ```
    - (BOOL)isCameraExposurePointSupported;
    ```

    该方法返回YES表示支持，NO表示不支持。

-   setCameraFocusPoint（仅iOS可用）：设置手动聚焦的坐标点。

    ```
    - (int)setCameraFocusPoint:(CGPoint)point;
    ```

    |参数|类型|描述|
    |--|--|--|
    |point|CGPoint|聚焦点坐标。|

    该方法返回0表示成功，其他表示失败。

-   setCameraExposurePoint（仅iOS可用）：设置手动曝光的坐标点。

    ```
    - (int)setCameraExposurePoint:(CGPoint)point;
    ```

    |参数|类型|描述|
    |--|--|--|
    |point|CGPoint|曝光点坐标。|

    该方法返回0表示成功，其他表示失败。

-   subscribeVideoPreprocessData（仅iOS可用）：订阅采集视频前处理裸数据。

    ```
    - (void)subscribeVideoPreprocessData:(AliRtcVideoSource)videoSource;
    ```

    |参数|类型|描述|
    |--|--|--|
    |videoSource|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流类型。|

-   unSubscribeVideoPreprocessData（仅iOS可用）：取消采集订阅前处理裸数据。

    ```
    - (void)unSubscribeVideoPreprocessData:(AliRtcVideoSource)videoSource;
    ```

    |参数|类型|描述|
    |--|--|--|
    |videoSource|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流类型。|

-   enableHighDefinitionPreview（仅iOS可用）：是否允许高清预览，默认打开。

    **说明：** 需要在开启预览和开启推流之前调用。

    ```
    - (BOOL)enableHighDefinitionPreview:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示允许，NO表示不允许。|

    该方法返回0表示成功，其他表示失败。

-   setVideoSwapWidthAndHeight：设置视频track是否需要交换宽高。

    ```
    - (void)setVideoSwapWidthAndHeight:(BOOL)swapWidthAndHeight forTrack:(AliRtcVideoTrack)track;
    ```

    |参数|类型|描述|
    |--|--|--|
    |swapWidthAndHeight|BOOL|YES表示需要交换宽高，NO表示不需要。默认NO。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要设置的视频Track类型。|

-   muteAllRemoteVideoRendering：mute或unmute远端的所有视频track的渲染。返回0为成功，其他返回错误码。

    ```
    - (int)muteAllRemoteVideoRendering:(BOOL)mute;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止渲染，NO表示恢复渲染。默认NO。|

-   getCurrentCameraID（仅Mac可用）：获取当前使用的摄像头ID。·

    ```
    - (NSString *)getCurrentCameraID;
    ```

-   setCurrentCameraWithID（仅Mac可用）：通过设备ID选择摄像头。

    ```
    - (void)setCurrentCameraWithID:(NSString *)cameraID;
    ```

    |参数|类型|描述|
    |--|--|--|
    |cameraID|NSString \*|摄像头ID。|

-   setExternalVideoSource：启用外部视频输入源。返回\>=0表示成功，<0表示失败。

    ```
    - (int)setExternalVideoSource:(BOOL)enable useTexture:(BOOL)useTexture sourceType:(AliRtcVideoSource)type renderMode:(AliRtcRenderMode)renderMode
    ```

    | | | |
    |--|--|--|
    |enable|BOOL|YES表示启用外部视频数据作为推流输入源，NO表示停止。|
    |useTexture|BOOL|是否使用texture模式，目前暂不支持。|
    |type|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流类型。|
    |renderMode|[AliRtcRenderMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|渲染模式（输入视频比例和推流profile不一致时，按照设置的renderMode进行对应处理 ）。|

-   pushExternalVideoFrame：输入外部视频。返回\>=0表示成功，<0表示失败。

    ```
    - (int)pushExternalVideoFrame:(AliRtcVideoDataSample *)frame sourceType:(AliRtcVideoSource)type;
    ```

    |参数|类型|描述|
    |--|--|--|
    |frame|[AliRtcVideoDataSample](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*|帧数据。|
    |type|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流类型。|

-   setBeautyEffect：设置基础美颜。返回0表示操作成功，非0表示操作失败。

    -   iOS代码和参数，如下所示：

        ```
        - (int)setBeautyEffect:(BOOL)enable config:(AliRtcBeautyConfig)config;
        ```

        |参数|类型|描述|
        |--|--|--|
        |enable|BOOL|YES表示开启基础美颜，NO表示关闭，默认为关闭。|
        |confg|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|美颜参数配置。|

    -   Mac代码和参数，如下所示：

        ```
        - (int)setBeatutyEffect:(bool)enable config:(AliRtcBeautyConfig)confg;
        ```

        |参数|类型|描述|
        |--|--|--|
        |enable|bool|true表示开启基础美颜，false表示关闭，默认为关闭。|
        |confg|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|美颜参数配置。|

-   getCurrentCameraDirection（仅iOS可用）：获取当前摄像头方向，默认前置摄像头。

    ```
    - (AliRtcCameraDirection)getCurrentCameraDirection;
    ```

-   registerVideoSampleObserver：订阅视频数据输出。

    ```
    - (void)registerVideoSampleObserver;
    ```

-   unregisterVideoSampleObserver：取消订阅视频数据输出。

    ```
    - (void)unregisterVideoSampleObserver;
    ```

-   setAudioOnlyMode：设置为纯音频模式还是音视频模式，默认为音视频模式（非纯音频）。返回0代表设置成功，其他代表设置失败。

    **说明：** 必须在调用joinChannel之前设置。

    ```
    - (int)setAudioOnlyMode:(BOOL)audioOnly;
    ```

    |参数|类型|描述|
    |--|--|--|
    |audioOnly|BOOL|YES表示只有音频发布和订阅，NO表示音视频都支持。|

-   isAudioOnly：查询当前是否为纯音频模式，返回YES为纯音频，NO为音视频。

    ```
    - (BOOL)isAudioOnly;
    ```

-   muteLocalMic：设置是否停止发布本地音频，返回0表示设置成功，-1表示设置失败。不改变当前音频的采集状态。

    ```
    - (int)muteLocalMic:(BOOL)mute;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止发布本地音频，NO表示恢复发布。默认NO。|

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流，返回0表示设置成功，-1表示设置失败。

    ```
    - (int)muteRemoteAudioPlaying:(NSString *)uid mute:(BOOL)mute;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |mute|BOOL|YES表示停止播放，NO表示恢复播放。默认NO。|

-   enableSpeakerphone（仅iOS可用）：设置音频输出为听筒还是扬声器。返回0为成功，其他返回错误码。

    ```
     - (int)enableSpeakerphone:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为扬声器模式，NO为听筒模式（默认值）。|

-   getAudioCaptures（仅Mac可用）：获取系统中的录音设备列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getAudioCaptures;
    ```

-   getCurrentAudioCapture（仅Mac可用）：获取当前使用的音频采集设备名称。

    ```
    - (NSString *)getCurrentAudioCapture;
    ```

-   setCurrentAudioCapture（仅Mac可用）：选择音频采集设备。必须先调用getCurrentAudioCapture接口获取设备列表后再调用此接口设置。

    ```
    - (void)setCurrentAudioCapture:(NSString *)capture;
    ```

    |参数|类型|描述|
    |--|--|--|
    |capture|NSString \*|音频采集设备名称。|

-   getAudioRenderers（仅Mac可用）：获取系统中的扬声器列表。

    ```
    - (NSArray<AliRtcDeviceInfo *> *)getAudioRenderers;
    ```

-   getCurrentAudioRenderer（仅Mac可用）：获取当前使用的音频播放设备。

    ```
    - (NSString *)getCurrentAudioRenderer;
    ```

-   setCurrentAudioRenderer（仅Mac可用）：选择音频播放设备。必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。

    ```
    - (void)setCurrentAudioRenderer:(NSString *)renderer;
    ```

    |参数|类型|描述|
    |--|--|--|
    |renderer|NSString \*|音频播放设备名称。|

-   startAudioCapture：开启音频采集。您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ```
    - (void)startAudioCapture;
    ```

-   stopAudioCapture：关闭音频采集。您可以控制关闭音频采集。

    ```
    - (void)stopAudioCapture;
    ```

-   startAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ```
    - (void)startAudioPlayer;
    ```

-   stopAudioPlayer：关闭音频播放。您可以控制关闭音频播放。

    ```
    - (void)stopAudioPlayer;
    ```

    **说明：** 该接口在入会前调用。

-   startAudioAccompanyWithFile（仅iOS可用）：开始播放伴奏。返回0为成功，否则返回错误码。

    **说明：** 支持本地资源和网络资源播放。

    ```
    - (int)startAudioAccompanyWithFile:(NSString *)filePath onlyLocalPlay:(BOOL)onlyLocalPlay replaceMic:(BOOL)replaceMic loopCycles:(NSInteger)loopCycles;
    ```

    |参数|类型|描述|
    |--|--|--|
    |filePath|NSString \*|文件路径。|
    |onlyLocalPlay|BOOL|是否只本地播放。取值：YES\|NO。|
    |replaceMic|BOOL|是否替换MIC（麦克风）。取值：YES\|NO。|
    |loopCycles|NSInteger|循环次数。可以设置为-1或者正整数。|

-   stopAudioAccompany（仅iOS可用）：停止伴奏。返回0为成功，否则返回错误码。

    ```
    - (int)stopAudioAccompany;
    ```

-   setAudioAccompanyVolume：设置伴奏音量。返回0为成功，否则返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

    ```
    - (int)setAudioAccompanyVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值：0~100。默认50。|

-   setAudioAccompanyPublishVolume（仅iOS可用）：设置伴奏之后推流出去的音量。返回0为成功，否则返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

    ```
    - (int)setAudioAccompanyPublishVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值：0~100。默认50。|

-   getAudioAccompanyPublishVolume（仅iOS可用）：获取伴奏推流音量。返回0为成功，否则返回错误码。

    ```
    - (int)getAudioAccompanyPublishVolume;
    ```

-   setAudioAccompanyPlayoutVolume（仅iOS可用）：设置伴奏本地音量。返回0为成功，否则返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

    ```
    - (int)setAudioAccompanyPlayoutVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值：0~100。默认50。|

-   getAudioAccompanyPlayoutVolume（仅iOS可用）：获取伴奏本地音量。返回0为成功，否则返回错误码。

    ```
    - (int)getAudioAccompanyPlayoutVolume;
    ```

-   pauseAudioAccompany（仅iOS可用）：暂停播放伴奏。返回0为成功，否则返回错误码。

    ```
    - (int)pauseAudioAccompany;
    ```

-   resumeAudioAccompany（仅iOS可用）：恢复播放伴奏。返回0为成功，否则返回错误码。

    ```
    - (int)resumeAudioAccompany;
    ```

-   preloadAudioEffectWithSoundId（仅iOS可用）：预加载音效。返回0为成功，否则返回错误码。

    ```
    - (int)preloadAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *)filePath;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*|音效文件路径。|

-   unloadAudioEffectWithSoundId（仅iOS可用）：清除预加载音效。返回0为成功，否则返回错误码。

    ```
    - (int)unloadAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   playAudioEffectWithSoundId（仅iOS可用）：开始播放音效。返回0为成功，否则返回错误码。

    ```
    - (int)playAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *)filePath cycles:(NSInteger)cycles publish:(BOOL)publish;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*|音效文件路径。|
    |cycles|NSInteger|循环次数。可以设置-1或者正整数。|
    |publish|BOOL|是否发布。取值：YES\|NO。|

-   stopAudioEffectWithSoundId（仅iOS可用）：停止播放音效。返回0为成功，否则返回错误码。

    ```
    - (int)stopAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   setAudioEffectPublishVolumeWithSoundId（仅iOS可用）：设置音效推流音量。返回0为成功，否则返回错误码。

    ```
    - (int)setAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量。取值：0~100。默认50。|

-   getAudioEffectPublishVolumeWithSoundId（仅iOS可用）：获取音效推流音量。返回0~100为成功，否则返回错误码。

    ```
    - (int)getAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   setAudioEffectPlayoutVolumeWithSoundId（仅iOS可用）：设置音效本地音量。返回0为成功，否则返回错误码。

    ```
    - (int)setAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量。取值：0~100。默认50。|

-   getAudioEffectPlayoutVolumeWithSoundId（仅iOS可用）：获取音效本地音量。返回0为成功，否则返回错误码。

    ```
    - (int)getAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   pauseAudioEffectWithSoundId（仅iOS可用）：暂停播放音效。返回0为成功，否则返回错误码。

    ```
    - (int)pauseAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   resumeAudioEffectWithSoundId（仅iOS可用）：恢复播放音效。返回0为成功，否则返回错误码。

    ```
    - (int)resumeAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    |参数|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

-   enableEarBack（仅iOS可用）：启用耳返。返回0为成功，否则返回错误码。

    ```
    - (int)enableEarBack:(BOOL)enable;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|是否启用耳返。取值：YES\|NO。默认不启用。|

-   setEarBackVolume（仅iOS可用）：设置耳返音量。返回0为成功，否则返回错误码。

    ```
    - (int)setEarBackVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|音量。取值：0~100，默认100。|

-   setSubscribeAudioNumChannel：设置回调音频声道数，默认单声道。

    ```
    - (void)setSubscribeAudioNumChannel:(AliRtcAudioNumChannel)audioNumChannel;
    ```

    |参数|类型|描述|
    |--|--|--|
    |audioNumChannel|[AliRtcAudioNumChannel](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频编号通道。|

-   setSubscribeAudioSampleRate：设置回调音频采样率，默认44.1k。

    ```
    - (void)setSubscribeAudioSampleRate:(AliRtcAudioSampleRate)audioSampleRate;
    ```

    |参数|类型|描述|
    |--|--|--|
    |audioSampleRate|[AliRtcAudioSampleRate](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频采样率。|

-   setAudioSessionOperationRestriction（仅iOS可用）：设置SDK对AVAudioSession的控制权限。

    ```
    - (int)setAudioSessionOperationRestriction:(AliRtcAudioSessionOperationRestriction)restriction;
    ```

    |参数|类型|描述|
    |--|--|--|
    |restriction|[AliRtcAudioSessionOperationRestriction](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|设置权限类型。|

-   setRecordingVolume（仅iOS可用）：设置录音音量，返回0表示操作成功，非0表示操作失败。

    ```
    - (int)setRecordingVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|音量。取值：0~400，0表示静音 。默认100。    -   当设置\>100时，表示增大音量。
    -   当设置<100时，表示减小音量。 |

    **说明：** 录音音量调节：当对端用户物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100-200，超过200会有影响音质的风险。

-   setPlayoutVolume（仅iOS可用）：设置播放音量，返回0表示操作成功，非0表示操作失败。

    ```
    - (int)setPlayoutVolume:(NSInteger)volume;
    ```

    |参数|类型|描述|
    |--|--|--|
    |volume|NSInteger|音量。取值：0~400，0表示静音。默认100。     -   当设置\>100时，表示增大音量。
    -   当设置<100时，表示减小音量。 |

    **说明：** 播放音量调节：当本地物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100-200，超过200会有影响音质的风险。

-   subscribeAudioData：订阅音频数据。

    ```
    - (void)subscribeAudioData:(AliRtcAudioSource)audioSource;
    ```

-   unSubscribeAudioData：取消订阅音频数据。

    ```
    - (void)unSubscribeAudioData:(AliRtcAudioSource)audioSource;
    ```

-   muteAllRemoteAudioPlaying：停止远端的所有音频流的播放。返回0为成功，其他返回错误码。

    ```
    - (int)muteAllRemoteAudioPlaying:(BOOL)mute;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止播放；NO表示恢复播放。|

-   setExteranlAudioRender：设置是否启用外部输入音频播放（返回0为成功，其他返回错误码）。

    ```
    - (int)setExteranlAudioRender:(BOOL)enable sampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示启用外部音频数据作为推流输入源，NO表示停止。|
    |sampleRate|NSUInteger|外部音频数据的采样率。|
    |channelsPerFrame|NSUInteger|外部音频数据的声道数（目前支持单声道，双声道）。|

-   pushExternalAudioRenderRawData：输入音频播放数据。返回\>=0为成功，返回<0失败。

    ```
    - (int)pushExternalAudioRenderRawData:(const void* _Nullable)audioSamples sampleLength:(NSUInteger)sampleLength sampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame timestamp:(long long)timestamp;
    ```

    |参数|类型|描述|
    |--|--|--|
    |audioSamples|const void\* \_Nullable|音频数据。|
    |sampleLength|NSUInteger|音频数据长。|
    |sampleRate|NSUInteger|音频采样率。|
    |channelsPerFrame|NSUInteger|音频声道数。|
    |timestamp|long long|时间戳。|

-   isEnableSpeakerphone（仅iOS可用）：获取当前音频输出为听筒还是扬声器。返回YES为扬声器模式；NO为听筒模式。

    ```
    - (BOOL)isEnableSpeakerphone;
    ```

-   getCurrentAudioCaptureID（仅Mac可用）：获取使用的录音设备ID。

    ```
    - (NSString *)getCurrentAudioCaptureID;
    ```

-   setCurrentAudioCaptureWithID（仅Mac可用）：通过设备ID选择录音设备。

    ```
    - (void)setCurrentAudioCaptureWithID:(NSString *)captureID;
    ```

    |参数|类型|描述|
    |--|--|--|
    |captureID|NSString \*|设备录音ID。|

-   getCurrentAudioRendererID（仅Mac可用）：获取当前使用的扬声器ID。

    ```
    - (NSString *)getCurrentAudioRendererID;
    ```

-   setCurrentAudioRendererWithID（仅Mac可用）：通过设备ID选择扬声器。

    ```
    - (void)setCurrentAudioRendererWithID:(NSString *)rendererID;
    ```

    |参数|类型|描述|
    |--|--|--|
    |rendererID|NSString \*|扬声器ID。|

-   startTestAudioRecordWithName（仅Mac可用）：开始测试音频采集设备。返回0表示成功，非0表示失败。

    **说明：** 请您在加入频道之前调用。

    ```
    - (int)startTestAudioRecordWithName:(NSString *)deviceName;
    ```

    |参数|类型|描述|
    |--|--|--|
    |deviceName|NSString \*|音频采集设备名字。|

-   stopTestAudioRecord（仅Mac可用）：停止测试音频采集设备。返回0表示成功，非0表示失败。

    **说明：** 请您在加入频道之前调用。

    ```
    - (int)stopTestAudioRecord;
    ```

-   startTestAudioPlayoutWithName（仅Mac可用）：开始测试音频播放设备。返回0表示成功，非0表示失败。

    **说明：** 请您在加入频道之前调用。

    ```
    - (int)startTestAudioPlayoutWithName:(NSString *)deviceName filePath:(NSString *)filePath loopCycles:(NSInteger)loopCycles;
    ```

    |参数|类型|描述|
    |--|--|--|
    |deviceName|NSString \*|音频播放设备名字。|
    |filePath|NSString \*|音频文件路径。|
    |loopCycles|NSInteger|重复播放次数。-1为循环播放。|

-   stopTestAudioPlayout（仅Mac可用）：停止测试音频播放设备。返回0表示成功，非0表示失败。

    **说明：** 请您在加入频道之前调用。

    ```
    - (int)stopTestAudioPlayout;
    ```

-   setExternalAudioSource：设置是否将外部音频数据作为推流的输入源。返回\>=0成功，<0失败。

    ```
    - (int)setExternalAudioSource:(BOOL)enable withSampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示启用外部音频数据作为推流输入源，NO表示停止。|
    |sampleRate|NSUInteger|外部音频数据的采样率。|
    |channelsPerFrame|NSUInteger|外部音频数据声道数（目前支持单声道，双声道）。|

-   pushExternalAudioFrameRawData：输入音频数据。返回\>=0成功，<0失败。

    ```
    - (int)pushExternalAudioFrameRawData:(void *_Nonnull)data samples:(NSUInteger)samples timestamp:(NSTimeInterval)timestamp;
    ```

    |参数|类型|描述|
    |--|--|--|
    |data|void \*\_Nonnull|音频数据，不建议超过40ms数据。|
    |samples|NSUInteger|采样率。|
    |timestamp|NSTimeInterval|时间戳，目前传0即可。|

-   setExternalAudioVolume：设置外部音频输入音量。

    ```
    - (int)setExternalAudioVolume:(int)vol;
    ```

    |参数|类型|描述|
    |--|--|--|
    |vol|int|音量。取值：0～100。默认50。|

-   getExternalAudioVolume：获取外部音频输入音量。

    ```
    - (int)getExternalAudioVolume;
    ```

-   setMixedWithMic：设置外部音频输入是否与麦克风采集音频混合。（返回0为成功，其他返回错误码）。

    ```
    - (int)setMixedWithMic:(BOOL)mixed;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mixed|BOOL|YES表示混音，NO表示完全替换麦克风采集数据。默认YES。|

-   setExternalAudioRenderVolume（仅Mac可用）：设置外部音频播放音量。

    ```
    - (int)setExternalAudioRenderVolume:(int)vol;
    ```

    |参数|类型|描述|
    |--|--|--|
    |vol|int|音量。取值：0～100。默认50。|

-   getExternalAudioRenderVolume（仅Mac可用）：获取音频播放音量。

    ```
    - (int)getExternalAudioRenderVolume;
    ```

-   setVolumeCallbackIntervalMs：设置音量回调频率和平滑系数。返回0为成功，-1表示interval设置小于10，-2表示平滑系数超出范围。

    ```
    - (int)setVolumeCallbackIntervalMs:(NSInteger)interval smooth:(NSInteger)smooth reportVad:(NSInteger)reportVad;
    ```

    |参数|类型|描述|
    |--|--|--|
    |interval|NSInteger|时间间隔。单位：毫秒，最小值不得小于10ms。|
    |smooth|NSInteger|平滑系数。数值越大平滑程度越高，反之越低，实时性越好。，建议您设置3，范围为0~9。|
    |reportVad|NSInteger|本地语音检测开关。     -   1：开启，通过onAudioVolumeCallback接口回调。
    -   0：关闭。 |

-   setAudioEffectReverbMode：设置混响音效模式。成功返回0，失败返回错误码。

    ```
    - (int)setAudioEffectReverbMode:(AliRtcAudioEffectReverbMode)mode;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mode|[AliRtcAudioEffectReverbMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|混响模式类型。|

-   setAudioEffectReverbParamType：设置混响音效类型。成功返回0，失败返回错误码。

    ```
    - (int)setAudioEffectReverbParamType:(AliRtcAudioEffectReverbParamType)type value:(float)value;
    ```

    |参数|类型|描述|
    |--|--|--|
    |type|[AliRtcAudioEffectReverbParamType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|混响音效类型。|
    |value|float|对应混响音效类型值。|

-   startPreview：开始本地预览，开始预览之前需要设置setLocalViewConfig。

    ```
    - (int)startPreview;
    ```

    **说明：** 您可以在加入频道之前开始本地预览。

-   stopPreview：停止本地预览。

    ```
    - (int)stopPreview;
    ```

-   getOnlineRemoteUsers：获取远端在线用户列表，返回用户ID列表。

    ```
    - (NSArray<NSString *> *)getOnlineRemoteUsers;
    ```

-   getUserInfo：查询远端用户信息。

    ```
    - (NSDictionary *)getUserInfo:(NSString *)uid;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|

-   isUserOnline：查询用户是否在线，YES表示在线，NO表示不在线。

    ```
    - (BOOL)isUserOnline:(NSString *)uid;
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|

-   getMediaInfoWithUserId： 获取当前的媒体流信息。返回key-value的json格式字符串。

    ```
    - (NSString *)getMediaInfoWithUserId:(NSString *)userId videoTrack:(AliRtcVideoTrack)videoTrack keys:(NSArray<NSString *> *)keys;
    ```

    |参数|类型|描述|
    |--|--|--|
    |userId|NSString \*|需要查询的用户ID，self请赋值空字符串。|
    |videoTrack|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要查询的媒体流类型。|
    |keys|NSArray<NSString \*\> \*|查询key值数组。|

-   setLogLevel：设置日志级别。

    ```
    - (void)setLogLevel:(AliRtcLogLevel)logLevel;
    ```

    |参数|类型|描述|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|日志级别。默认AliRtcLogLevelInfo。|

-   getSdkVersion：获取SDK版本号。

    ```
    + (NSString *)getSdkVersion;
    ```

-   uploadLog：上传日志。

    ```
    + (void)uploadLog;
    ```

-   startIntelligentDenoise（仅Mac可用）：开启智能降噪，该接口可以在通话过程中打开智能降噪功能。

    ```
    - (void)startIntelligentDenoise;
    ```

-   stopIntelligentDenoise（仅Mac可用）：关闭智能降噪，该接口可以在通话过程中关闭智能降噪功能。

    ```
    - (void)stopIntelligentDenoise;
    ```

-   setClientRole：设置用户角色。返回0表示成功，非0表示失败。

    ```
    - (int)setClientRole:(AliRtcClientRole)role;
    ```

    |参数|类型|描述|
    |--|--|--|
    |role|[AliRtcClientRole](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.mdtable_4b2_m8b_w04)|用户角色类型。默认AliRtcClientRolelive。|

-   setLogDirPath：设置SDK日志文件保存路径。返回0为成功，其他返回错误码。

    ```
    + (int)setLogDirPath:(NSString *)logDirPath;
    ```

    |参数|类型|描述|
    |--|--|--|
    |logDirPath|NSString \*|日志文件保存绝对路径。    -   iOS Log日志默认存储路径Library/Caches/Ali\_RTC\_Log。
    -   mac Log日志默认存储路径/Users/xxx/Documents（文稿）/Ali\_RTC\_Log。 |

-   setDeviceOrientationMode：设置设备横竖屏方向。返回0为成功，其他返回错误码。当前只支持固定横竖屏模式，仅允许在发布和预览之前进行设置。

    ```
    - (int)setDeviceOrientationMode:(AliRtcOrientationMode)mode;
    ```

    |参数|类型|描述|
    |--|--|--|
    |mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|设备方向。取值：     -   AliRtcOrientationModePortrait（默认值）：固定竖屏模式。
    -   AliRtcOrientationModeLandscapeLeft：固定左横屏模式。
    -   AliRtcOrientationModeLandscapeRight：固定右横屏模式。
    -   AliRtcOrientationModeAuto：自适应横竖屏模式。 |

-   startLastmileDetect：开始网络质量探测。返回0为成功，其他返回错误码。·

    **说明：** 您需要在加入频道之前调用，并且入会后会自动停止，探测结果在[onLastmileDetectResultWithQuality](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)回调。

    ```
    - (int)startLastmileDetect;
    ```

-   stopLastmileDetect：停止网络质量探测。返回0为成功，其他返回错误码。

    ```
    - (int)stopLastmileDetect;
    ```

-   startRecord：开始录制。返回成功/失败 。

    ```
    - (BOOL)startRecord:(AliRtcRecordType)recordType recordFormat:(AliRtcRecordFormat)recordFormat filePath:(NSString*)filePath audioConfig:(AliRtcRecordAudioConfig*)audioConfig videoConfig:(AliRtcRecordVideoConfig*)videoConfig isFragment:(BOOL)isFragment
    ```

    |参数|类型|描述|
    |--|--|--|
    |recordType|[AliRtcRecordType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制类型。|
    |recordFormat|[AliRtcRecordFormat](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制文件格式。|
    |filePath|NSString\*|文件路径。|
    |audioConfig|[AliRtcRecordAudioConfig\*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制音频设置。|
    |videoConfig|[AliRtcRecordVideoConfig\*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制视频设置（仅Mac可用）。|
    |isFragment|BOOL|是否支持mp4内部分段，只在录制mp4时有效（仅Mac可用）。|

-   stopRecord：停止录制。

    ```
    - (void)stopRecord;
    ```

-   getCurrentClientRole（仅iOS可用）：获取当前用户角色。返回当前用户角色。

    ```
    - (AliRtcClientRole)getCurrentClientRole;
    ```

-   postFeedbackWithUid：SDK问题反馈。

    ```
    - (void)postFeedbackWithUid:(NSString *_Nullable)uid channleId:(NSString *_Nullable)channelId description:(NSString *_Nonnull)description type:(AliRtcFeedbackType)type timeStamp:(NSTimeInterval)timeStamp
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|当前 uid（允许为nil）。|
    |channelId|NSString \*|当前channel id（允许为nil）。|
    |description|NSString \*|问题描述（支持中英文，Nonnull）。|
    |type|[AliRtcFeedbackType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|问题类型（见AliRtcFeedbackType注释）。|
    |timeStamp|NSTimeInterval|问题发生的时间戳（Unix时间戳，大致时间，无需特别精确，可以为0）。|

-   sendMediaExtensionMsg：发送媒体扩展信息。

    返回值定义，如下所示：

    -   0：发送成功。
    -   -1：当前未在推流状态，不能发送自定义消息。
    -   -2：参数设置错误，自定义消息长度超过8Byte，或者repeatCount<=0。
    -   -3：发送过于频繁，建议降低发送频率。
    **说明：** 使用音视频数据通道，将自定义消息发送给房间内其他用户，需要满足两个前提：

    -   己方正常入会，并且在推流中。
    -   房间内的其他用户需要订阅己方音视频流，发送成功之后可在[onMediaExtensionMsgReceived](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)回调中接收结果。
    ```
    - (int)sendMediaExtensionMsg:(NSData *)data repeatCount:(int)repeatCount;
    ```

    |参数|类型|描述|
    |--|--|--|
    |data|NSData|自定义消息数据，目前长度限制为8Byte。|
    |repeatCount|int|消息发送次数。|

-   getClientRole（仅Mac可用）：获取用户角色。返回当前用户角色。

    ```
    - (AliRtcClientRole)getClientRole;
    ```


