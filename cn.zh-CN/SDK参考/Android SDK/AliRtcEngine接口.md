---
keyword: [AliRtcEngine, Android]
---

# AliRtcEngine接口

本文为您介绍了Android SDK的AliRtcEngine接口详情。

## 目录

**说明：** 1.17及以上版本不再提供ALI\_RTC\_INTERFACE类，1.17以下版本的ALI\_RTC\_INTERFACE参数和枚举类统一迁移到AliRtcEngine类里面。推荐您使用setAutoPublishSubscribe接口设置是否自动发布、是否自动订阅。

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[setH5CompatibleMode](#li_kk1_04r_6ux)|设置H5兼容模式|1.1|
|[getH5CompatibleMode](#li_wq1_9ja_om7)|检查当前是否兼容H5|1.1|
|[getInstance](#li_pdy_xo7_9in)|创建AliRTCEngine实例（同一时间只会存在一个实例），只能在主线程调用|1.1|
|[setRtcEngineEventListener](#li_icu_cv1_fdn)|设置本地用户行为的回调事件的监听|1.1|
|[setRtcEngineNotify](#li_vu7_l6n_4rz)|设置远端用户行为的通知事件的监听|1.1|
|[destroy](#li_59b_i3u_fbj)|销毁SDK|1.1|
|[uploadLog](#li_968_ml9_2my)|上传日志|1.15|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAutoPublish](#li_n0w_col_w8x)|设置是否自动发布，是否自动订阅|1.1|
|[joinChannel](#li_sa3_855_y55)|加入频道|1.1|
|[leaveChannel](#li_85b_o3m_nin)|离开频道|1.1|
|[isInCall](#li_f5f_haq_bcx)|检查当前是否在频道中|1.1|
|[setChannelProfile](#li_gws_rtd_yjc)|设置频道模式|1.15|
|[setAutoPublishSubscribe](#li_k0i_cs3_gu5)|设置是否自动发布或自动订阅|1.17|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoPublish](#li_ojl_tan_suf)|查询当前是否为自动发布模式|1.1|
|[configLocalCameraPublish](#li_f95_zwd_2b6)|设置是否允许发布相机流|1.1|
|[isLocalCameraPublishEnabled](#li_985_026_dic)|查询当前是否允许发布相机流|1.1|
|[configLocalScreenPublish](#li_ntd_ygm_kdr)|设置是否允许发布屏幕流|1.1|
|[isLocalScreenPublishEnabled](#li_w2n_fvq_gd8)|查询当前是否允许发布屏幕流|1.1|
|[configLocalAudioPublish](#li_7cz_k4k_7a1)|设置是否允许发布音频流|1.1|
|[isLocalAudioPublishEnabled](#li_qqs_i72_9n6)|查询当前是否允许发布音频流|1.1|
|[configLocalSimulcast](#li_wlf_1jl_o7q)|设置是否允许发布次要视频流|1.1|
|[isLocalSimulcastEnabled](#li_kft_qow_6oi)|查询当前是否允许发布次要视频流|1.1|
|[publish](#li_x0v_woq_nnc)|手动发布视频和音频流|1.1|

订阅相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoSubscribe](#li_mhw_cxn_947)|查询当前是否为自动订阅模式|1.1|
|[configRemoteCameraTrack](#li_gv4_qr3_yxd)|设置是否订阅远端相机流|1.1|
|[configRemoteScreenTrack](#li_yz3_qcc_wci)|设置是否订阅远端屏幕流|1.1|
|[configRemoteAudio](#li_m90_crx_cyu)|设置是否订阅远端音频流|1.1|
|[subscribe](#li_i69_su8_ng6)|手动订阅视频和音频流|1.1|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#li_mfy_law_p9u)|设置视频流的参数|1.1|
|[getVideoProfile](#li_hd4_2kp_bth)|查询当前视频流参数|1.1|
|[setLocalViewConfig](#li_a11_wvh_suy)|为本地预览设置渲染窗口以及绘制参数|1.1|
|[muteLocalCamera](#li_tv8_5wp_myj)|设置是否停止发布本地视频流|1.1|
|[setRemoteViewConfig](#li_o9j_h6u_sct)|为远端的视频设置渲染窗口以及绘制参数|1.1|
|[switchCamera](#li_ysn_omu_f5w)|切换前后摄像头|1.1|
|[getCurrentCameraType](#li_76i_grc_ger)|获取当前摄像头类型|1.1|
|[setPreCameraType](#li_xnp_jbr_q7j)|预设值摄像头方向|1.1|
|[getPreCameraType](#li_wz9_cts_8ed)|获取预设值摄像头方向|1.1|
|[setCameraZoom](#li_rbn_p4j_i6s)|设置摄像头参数|1.1|
|[isCameraOn](#li_rbs_tbh_1hr)|检查摄像头是否打开|1.1|
|[isCameraSupportExposurePoint](#p_y4o_k7e_qef)|相机是否支持手动曝光|1.14|
|[isCameraSupportFocusPoint](#p_6r0_9oi_mnp)|相机是否支持手动聚焦|1.14|
|[setCameraExposurePoint](#p_yc7_zte_670)|设置手动曝光的坐标点|1.14|
|[setCameraFocusPoint](#p_3t6_1n0_aqp)|设置手动聚焦的坐标点|1.14|
|[isCameraFlash](#p_0x6_qmk_buf)|是否开启了闪光灯|1.14|
|[getCameraZoom](#p_wqr_v9v_667)|获取相机的zoom（变焦）值|1.14|
|[registerPreprocessVideoObserver](#p_n1m_7h0_3nd)|注册人脸识别预处理|1.14|
|[muteAllRemoteVideoRendering](#li_g7l_yl8_eyj)|mute或unmute远端的所有视频track的渲染|1.16.2|
|[setBeautyEffect](#li_aoy_4dz_gl4)|设置基础美颜|1.17.9|
|[registerVideoSampleObserver](#li_wuz_ib9_pbb)|注册视频数据回调|1.17|
|[unRegisterVideoSampleObserver](#li_y35_07t_0nt)|取消注册视频数据回调|1.17|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAudioOnlyMode](#li_qpx_158_6w6)|设置为纯音频模式还是音视频模式|1.1|
|[isAudioOnly](#li_cwx_qty_qbb)|查询当前是否为纯音频模式|1.1|
|[muteLocalMic](#li_5vx_o8j_tlo)|设置是否停止发布本地音频|1.1|
|[muteRemoteAudioPlaying](#li_wlu_fck_m75)|设置是否停止播放远端音频流|1.1|
|[startAudioCapture](#li_xto_65v_jbg)|切换听筒、扬声器输出|1.1|
|[isSpeakerOn](#li_x8k_hqf_0tw)|查询是否开启扬声器|1.1|
|[startAudioCapture](#li_g46_fsz_4kc)|开启音频采集|1.11|
|[stopAudioCapture](#li_o2b_5d5_k55)|关闭音频采集|1.11|
|[startAudioPlayer](#li_77n_4my_cr4)|开启音频播放|1.11|
|[stopAudioPlayer](#li_ujt_2yy_ii5)|关闭音频播放|1.11|
|[enableEarBack](#li_8ju_0go_yy1)|启用耳返|1.15|
|[startAudioAccompany](#li_0u9_6os_ak6)|开始播放伴奏|1.15|
|[pauseAudioAccompany](#li_2v6_188_ah0)|暂停播放伴奏|1.15|
|[resumeAudioAccompany](#li_tc9_d0h_qf9)|恢复播放伴奏|1.15|
|[stopAudioAccompany](#li_jek_esa_4yu)|结束播放伴奏|1.15|
|[setAudioAccompanyPublishVolume](#li_nn8_9ze_8on)|设置伴奏推流音量|1.15|
|[setAudioAccompanyPlayoutVolume](#li_llk_b64_fnw)|设置伴奏本地音量|1.15|
|[getAudioAccompanyPublishVolume](#li_2e0_voz_te4)|获取伴奏推流音量|1.15|
|[getAudioAccompanyPlayoutVolume](#li_3wj_1mh_c1r)|获取伴奏本地音量|1.15|
|[setAudioAccompanyVolume](#li_6mp_gxe_ca2)|设置伴奏推流和本地音量|1.15|
|[preloadAudioEffect](#li_ir1_p0g_d9a)|预加载音效|1.15|
|[unloadAudioEffect](#li_m5e_353_26b)|清除预加载音效|1.15|
|[playAudioEffect](#li_try_bjm_0sh)|开始播放音效|1.15|
|[setAudioEffectPublishVolume](#li_gvv_px1_alm)|设置音效推流音量|1.15|
|[getAudioEffectPublishVolume](#li_5kj_dgf_cva)|获取音效推流音量|1.15|
|[setAudioEffectPlayoutVolume](#li_4sm_sns_e9q)|设置音效本地音量|1.15|
|[getAudioEffectPlayoutVolume](#li_r7q_lif_dla)|获取音效本地音量|1.15|
|[pauseAudioEffect](#li_uof_c81_x9l)|暂停播放音效|1.15|
|[resumeAudioEffect](#li_odh_3fo_aip)|恢复播放音效|1.15|
|[stopAudioEffect](#li_1hp_b74_9cd)|停止播放音效|1.15|
|[setEarBackVolume](#li_zn0_q9c_g36)|设置耳返音量|1.15|
|[setRecordingVolume](#li_naz_gly_cns)|设置录音音量|1.16|
|[setPlayoutVolume](#li_wfa_f83_lmw)|设置播放音量|1.16|
|[muteAllRemoteAudioPlaying](#li_jhb_sgi_ab4)|停止远端的所有音频流的播放|1.16.2|
|[registerAudioVolumeObserver](#li_qib_6lx_z5k)|注册音量回调|1.16.2|
|[unRegisterAudioVolumeObserver](#li_u2o_2ad_d5m)|取消注册音量回调|1.16.2|
|[startRecord](#li_3av_jke_wo4)|开始录制文件|1.17|
|[stopRecord](#li_gpx_6oi_9a3)|停止录制文件|1.17|
|[setAudioEffectReverbMode](#li_yfc_42y_55e)|设置混响音效模式|1.17|
|[setAudioEffectReverbParamType](#li_fxm_avd_i0c)|设置混响音效类型|1.17|
|[setVolumeCallbackIntervalMs](#li_icv_m3o_c7a)|设置音量回调频率和平滑系数|1.17|
|[setExternalAudioSource](#li_6xs_t4c_lmv)|设置是否将外部音频数据作为推流的输入源|1.17.9|
|[pushExternalAudioFrameRawData](#li_mjo_nu2_gka)|输入音频数据|1.17.9|
|[setExternalAudioVolume](#li_qc7_5yk_cd9)|设置外部音频输入音量|1.17.9|
|[getExternalAudioVolume](#li_hcj_ni7_01q)|获取外部音频输入音量|1.17.9|
|[setMixedWithMic](#li_51g_9cp_n0h)|设置外部音频输入是否与麦克风采集音频混合|1.17.9|
|[setExteranlAudioRender](#li_wsf_k31_72b)|设置是否启用外部输入音频播放|1.17.9|
|[pushExternalAudioRenderRawData](#li_doq_352_mwd)|输入音频播放数据|1.17.9|
|[getCurrentClientRole](#li_scn_0s2_cyp)|获取当前角色|1.17.9|
|[setSubscribeAudioNumChannel](#li_29x_gdk_ae3)|设置回调音频声道数|1.17.13|
|[setSubscribeAudioSampleRate](#li_e5s_07m_i1v)|设置回调音频采样率|1.17.13|
|[requestAudioFocus](#li_ntb_ozk_tio)|请求音频焦点|1.17.19|
|[abandonAudioFocus](#li_731_6rm_u9l)|丢失音频焦点|1.17.19|
|[registerAudioObserver](#li_zhd_6te_0so)|注册音频数据回调|1.17|

预览接口

|API|描述|以上版本支持|
|---|--|------|
|[startPreview](#li_6nq_nbt_fnj)|开始本地预览|1.1|
|[stopPreview](#li_9f6_e1s_bco)|停止本地预览|1.1|
|[enableHighDefinitionPreview](#li_81c_3x0_ntd)|是否开启高清预览|1.16|

远端用户查询接口

|API|描述|以上版本支持|
|---|--|------|
|[getOnlineRemoteUsers](#li_m40_6lw_lzj)|获取远端在线用户列表|1.1|
|[getUserInfo](#li_tpg_8dp_rqf)|查询远端用户信息|1.1|
|[isUserOnline](#li_irn_g7z_gbv)|查询用户是否在线|1.1|
|[getMediaInfoWithUserId](#li_c3d_clo_1ly)|获取媒体流信息|1.9|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[setLogLevel](#li_ayc_d69_im9)|设置日志级别|1.1|
|[getSdkVersion](#li_97g_hks_qnu)|获取SDK版本号|1.1|
|[setClientRole](#li_5um_nfc_p65)|设置用户角色|1.16|
|[setLogDirPath](#li_z39_we0_bcn)|设置SDK日志文件保存路径|1.16.2|
|[setDeviceOrientationMode](#li_5vd_oz0_ja4)|设置设备横竖屏方向|1.16.2|
|[startNetworkQualityProbeTest](#li_uat_bok_sb0)|开始网络质量探测|1.16.2|
|[stopNetworkQualityProbeTest](#li_dpb_pxp_lco)|停止网络质量探测|1.16.2|
|[postFeedback](#li_vi0_45j_mms)|SDK问题反馈|1.17.13|
|[sendMediaExtensionMsg](#li_q9r_vcy_x1t)|发送媒体扩展信息|1.17.1|

## 接口详情

-   setH5CompatibleMode：设置是否兼容H5。

    ```
    AliRtcEngine.setH5CompatibleMode(int enable)           
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|int|0表示不兼容H5，1表示兼容H5。默认不兼容H5。|

    **说明：** 该接口仅支持在创建AliRtcEngine实例前调用。

-   getH5CompatibleMode：检查当前是否兼容H5。

    ```
    public static int getH5CompatibleMode()
    ```

    返回说明

    1表示兼容，0表示不兼容。

    **说明：** 该接口仅支持在创建AliRtcEngine实例后调用。

-   getInstance：创建AliRTCEngine实例。

    ```
    public static AliRtcEngineImpl getInstance(Context context)          
    ```

    |名称|类型|描述|
    |--|--|--|
    |context|Context|上下文。|

    **说明：** 同一时间只会存在一个实例，并且只能在主线程调用。

-   setRtcEngineEventListener：设置本地用户行为的回调事件的监听。

    ```
    public abstract void setRtcEngineEventListener(AliRtcEngineEventListener listener)                    
    ```

    |名称|类型|描述|
    |--|--|--|
    |listener|[AliRtcEngineEventListener](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|接收回调事件的监听器。|

-   setRtcEngineNotify：设置远端用户行为的通知事件的监听。

    ```
    public abstract void setRtcEngineNotify(AliRtcEngineNotify engineNotify)               
    ```

    |名称|类型|描述|
    |--|--|--|
    |engineNotify|[AliRtcEngineNotify](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|接收通知的监听器。|

-   destroy：销毁SDK。

    1.15及以上版本：销毁SDK只能通过destroy方法。

    1.15以下版本：离开频道时，AliRtcEngine实例会被销毁，如果需要继续加入频道等操作，需要先重新调用getInstance初始化AliRtcEngine实例。

    ```
    public abstract void destroy();                  
    ```

    **说明：** 该接口只能在主线程调用。

-   uploadLog：上传日志。

    ```
    AliRtcEngine.uploadLog();
    ```

    **说明：** 1.17及以上版本修改为静态方法，1.17以下版本请使用：`public abstract void uploadLog();`。

-   setAutoPublish：设置是否自动发布，是否自动订阅。

    ```
    public int setAutoPublish(boolean autoPub, boolean autoSub);
    ```

    |名称|类型|描述|
    |--|--|--|
    |autoPub|boolean|true表示自动发布，false表示手动发布。默认自动发布。|
    |autoSub|boolean|true表示自动订阅，false表示手动订阅。默认自动订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口必须在加入频道之前设置。

-   joinChannel：加入频道。

    加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道，如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ```
    public abstract void joinChannel(AliRtcAuthInfo authInfo, String userName)                    
    ```

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|鉴权信息。|
    |userName|String|用户的显示名称（非用户ID）。|

-   leaveChannel：离开频道。

    ```
    public abstract void leaveChannel()                          
    ```

    1.15及以上版本：调用leaveChannel不会销毁实例。

    1.15版本以下：离开频道时，AliRtcEngine实例会被销毁，如果需要继续加入频道等操作，需要先重新调用getInstance初始化AliRtcEngine实例。

    -   对于版本号大于1.7的SDK，请调用如下接口。

        ```
        public abstract void leaveChannel()                          
        ```

    -   对于版本号小于等于1.7的SDK，请增加timeout参数，一般建议设置为1000，表示该接口的调用超时时间为1秒。

        ```
        public abstract void leaveChannel(long timeout)                          
        ```

-   isInCall：检查当前是否在频道中。

    ```
    public abstract boolean isInCall()                  
    ```

    返回说明

    返回true表示在频道中，false表示不在频道中。

-   setChannelProfile：设置频道模式。

    ```
    public abstract int setChannelProfile(AliRTCSDK_Channel_Profile profile);
    ```

    |名称|类型|描述|
    |--|--|--|
    |profile|[AliRTCSDK\_Channel\_Profile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|频道模式类型。默认通信模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只可以在joinChannel之前调用，通信中不可以重新设置，在调用LeaveChannel后可以重新设置。

-   setAutoPublishSubscribe：设置是否自动发布或自动订阅。

    ```
    public abstract int setAutoPublishSubscribe(boolean autoPub, boolean autoSub);
    ```

    |名称|类型|描述|
    |--|--|--|
    |autoPub|boolean|true表示自动发布，false表示手动发布。默认自动发布。|
    |autoSub|boolean|true表示自动订阅，false表示手动订阅。默认自动订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口必须在加入频道之前设置。

-   isAutoPublish：查询当前是否为自动发布模式。

    ```
    public abstract boolean isAutoPublish()                  
    ```

    返回说明

    true表示自动发布，false表示手动发布。

-   configLocalCameraPublish：设置是否允许发布相机流。

    ```
    public abstract void configLocalCameraPublish(boolean enable)                
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true为允许发布相机流，false表示不允许。默认为允许发布相机流。|

    **说明：** 手动发布时，需要调用publish才能生效。

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流。

    ```
    public abstract boolean isLocalCameraPublishEnabled()                   
    ```

    返回说明

    true表示允许，false表示不允许。

-   configLocalScreenPublish：设置是否允许发布屏幕流。

    ```
    public abstract void configLocalScreenPublish(boolean enable)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示允许发布屏幕流，false表示不允许。默认为不允许发布屏幕流|

    **说明：** 手动发布时，需要调用publish才能生效。

-   isLocalScreenPublishEnabled：查询当前是否允许发布屏幕流。

    ```
    public abstract boolean isLocalScreenPublishEnabled()                   
    ```

    返回说明

    true表示允许发布屏幕流，false表示不允许发布屏幕流。

-   configLocalAudioPublish：设置是否允许发布音频流。

    ```
    public abstract void configLocalAudioPublish(boolean enable)          
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示允许，false表示不允许。默认为允许发布音频流。|

    **说明：** 手动发布时，需要调用publish才能生效。

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流。

    ```
    public abstract boolean isLocalAudioPublishEnabled()                
    ```

    返回说明

    true表示允许发布音频流，false表示不允许发布音频流。

-   configLocalSimulcast：设置是否允许发布次要视频流。

    ```
    public abstract int configLocalSimulcast(boolean enable, AliRtcVideoTrack track)        
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示允许发布次要流，false表示不允许。默认为允许发布次要视频流。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|流类型。当前只支持AliVideoTrackCamera（相机流）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 手动发布时，需要调用publish才能生效。

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流。

    ```
    public abstract boolean isLocalSimulcastEnabled()                  
    ```

    返回说明

    true表示允许发布次要视频流，false表示不允许发布次要视频流。

-   publish：手动发布视频和音频流。

    ```
    public abstract void publish()                  
    ```

    -   调用publish的实际表现需要结合configLocalCameraPublish、configLocalScreenPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述4个接口的参数，以发布相应的视频和音频流。
    -   发布和停止发布都是调用publish。
    -   如需停止发布，则需要上述4个配置接口的参数都置为false，再调用publish。
    -   需要在加入频道成功之后调用该接口。
-   isAutoSubscribe：查询当前是否为自动订阅模式。

    ```
    public abstract boolean isAutoSubscribe()                 
    ```

    返回说明

    true表示自动订阅，false表示手动订阅。

-   configRemoteCameraTrack：设置是否订阅远端相机流。

    ```
    public abstract void configRemoteCameraTrack(String uid, boolean master, boolean enable)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |master|boolean|true为优先订阅大流，false为订阅次小流。默认为订阅大流。|
    |enable|boolean|true为订阅远端相机流，false为停止订阅远端相机流。|

    **说明：** 该接口需要对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。

    ```
    public abstract void configRemoteScreenTrack(String uid, boolean enable)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |enable|boolean|true为订阅远端屏幕流，false为停止订阅远端屏幕流。默认为不订阅远端屏幕流。|

    **说明：** 该接口需要对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。

-   configRemoteAudio：设置是否订阅远端音频流。

    ```
    public abstract void configRemoteAudio(String uid, boolean enable)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |enable|boolean|true为订阅远端音频流，false为停止订阅远端音频流。默认为订阅远端音频流。|

    **说明：** 该接口需要对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。

-   subscribe：手动订阅视频和音频流。

    ```
    public abstract int subscribe(String uid)                 
    ```

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如需停止订阅，则需要上述3个配置接口的参数都置为false，再调用subscribe。
    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|

    返回说明

    0表示接口执行正常，是否订阅成功需要看订阅回调结果。非0表示接口执行异常中断，订阅失败。

-   setVideoProfile：设置视频流的参数。

    ```
    public abstract void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)                   
    ```

    |名称|类型|描述|
    |--|--|--|
    |profile|[AliRtcVideoProfile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|视频流参数。默认分辨率480\*640，帧率15的相机流。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要设置的视频流类型。|

-   getVideoProfile：查询当前视频流参数。

    ```
    public abstract AliRtcVideoProfile getVideoProfile(AliRtcVideoTrack track)                    
    ```

    |名称|类型|描述|
    |--|--|--|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要查询的视频流类型。|

    返回说明

    该接口返回[AliRtcVideoProfile](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)（视频流规格数据类型）。

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    ```
    public abstract int setLocalViewConfig(AliVideoCanvas viewConfig, AliRtcVideoTrack track)                   
    ```

    -   支持加入频道之前和之后切换窗口。如果viewConfig为NULL或者其成员渲染视图为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持viewConfig中其他成员变量不变，仅修改renderMode。
    -   viewConfig中渲染方式默认为AliRtcRenderModeAuto。
    |名称|类型|描述|
    |--|--|--|
    |viewConfig|[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|预览视频Track类型只允许AliVideoTrackCamera（相机流）。|

-   muteLocalCamera：设置是否停止发布本地视频流。

    ```
    public abstract int muteLocalCamera(boolean mute, AliRtcVideoTrack track)                   
    ```

    |名称|类型|描述|
    |--|--|--|
    |mute|boolean|true表示停止发布视频流，false表示恢复发布。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要改变发布状态的视频Track类型。|

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

    **说明：** 该接口不改变当前视频流的采集状态。

-   setRemoteViewConfig：远端的视频设置渲染窗口以及绘制参数。

    ```
    public abstract int setRemoteViewConfig(AliVideoCanvas canvas, String uid, AliRtcVideoTrack track)                    
    ```

    -   支持加入频道之前和之后切换窗口。如果canvas为NULL或者其成员渲染视图为NULL，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeAuto。
    -   建议在订阅结果回调之后调用。
    |名称|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|String|用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要设置的视频Track类型。|

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   switchCamera：切换前后摄像头。

    ```
    public abstract int switchCamera()                  
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   getCurrentCameraType：获取当前摄像头类型。

    返回摄像头类型[AliRTCCameraType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。

    ```
    public abstract AliRTCCameraType getCurrentCameraType()                   
    ```

-   setPreCameraType：预设值摄像头方向。

    ```
    public abstract void setPreCameraType(int faceTo)                    
    ```

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

    |名称|类型|描述|
    |--|--|--|
    |zoom|float|zoom变焦的级别（默认值：1.0）。|
    |flash|boolean|true表示打开闪光灯，false表示不打开闪光灯。|
    |autoFocus|boolean|true表示打开自动对焦，false表示不打开自动对焦。|

    返回说明

    0表示设置成功，其他表示设置失败。

-   isCameraOn：检查摄像头是否打开。

    ```
    public abstract boolean isCameraOn()                   
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

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

-   registerPreprocessVideoObserver：注册人脸识别预处理。

    ```
    public abstract void registerPreprocessVideoObserver(AliDetectObserver observer);
    ```

    |名称|类型|描述|
    |--|--|--|
    |observer|[AliDetectObserver](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|人脸识别预处理。|

-   muteAllRemoteAudioPlaying：停止远端的所有音频流的播放。

    ```
    public abstract int muteAllRemoteAudioPlaying(boolean mute);
    ```

    |名称|类型|描述|
    |--|--|--|
    |mute|boolean|true表示停止播放，false表示恢复播放。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 订阅和解码不受影响，支持加入频道之前或之后设置。

-   setAudioOnlyMode：设置为纯音频模式还是音视频模式。

    ```
    public abstract int setAudioOnlyMode(boolean audioOnly)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |audioOnly|boolean|true表示只有音频发布和订阅，false表示音视频都支持。|

    返回说明

    0表示设置成功，其他表示设置失败。

    **说明：** 该接口默认为音视频模式（非纯音频），必须在调用joinChannel之前设置。

-   isAudioOnly：查询当前是否为纯音频模式。

    ```
    public abstract boolean isAudioOnly()                 
    ```

    返回说明

    true表示纯音频，false表示音视频。

-   muteLocalMic：设置是否停止发布本地音频。

    **说明：** 该接口不改变当前音频的采集状态。

    ```
    public abstract int muteLocalMic(boolean mute)                    
    ```

    |名称|类型|描述|
    |--|--|--|
    |mute|boolean|true表示停止发布本地音频，false表示恢复发布。|

    返回说明

    0表示设置成功，-1表示设置失败。

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流。

    ```
    public abstract int muteRemoteAudioPlaying(String uid, boolean mute)                   
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|
    |mute|boolean|true表示停止播放，false表示恢复播放。|

    返回说明

    0表示设置成功，-1表示设置失败。

-   enableSpeakerphone：切换听筒、扬声器输出。

    ```
    public abstract int enableSpeakerphone(boolean enable)  
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true为扬声器模式，false为听筒模式。默认扬声器模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只能在主线程调用。

-   isSpeakerOn：查询是否开启扬声器。

    ```
    public abstract boolean isSpeakerOn()                  
    ```

    返回说明

    true表示已开启扬声器，false表示未开启扬声器。

-   startAudioCapture：开启音频采集。

    您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ```
    public int startAudioCapture();
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   stopAudioCapture：关闭音频采集。

    您可以控制关闭音频采集。

    ```
    public int stopAudioCapture();
    ```

-   startAudioPlayer：开启音频播放。

    您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ```
    public int startAudioPlayer();
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   stopAudioPlayer：关闭音频播放。

    ```
    public int stopAudioPlayer();
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

    **说明：** 该接口在入会前调用。

-   enableEarBack：启用耳返。

    ```
    public abstract int enableEarBack(boolean enable);
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启耳返，false表示关闭耳返。默认关闭耳返。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   startAudioAccompany：开始播放伴奏。

    ```
    public abstract int startAudioAccompany(String fileName, boolean onlyLocalPlay, boolean replaceMic, int loopCycles);
    ```

    |名称|类型|描述|
    |--|--|--|
    |fileName|String|伴奏文件路径，支持本地文件和网络url。|
    |onlyLocalPlay|boolean|是否仅本地播放，true表示仅仅本地播放，false表示本地播放且推流到远端。|
    |replaceMic|boolean|是否替换mic的音频流，true表示伴奏音频流替换本地mic音频流，false表示伴奏音频流和mic音频流同时推。|
    |loopCycles|int|循环播放次数，-1表示一直循环。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   pauseAudioAccompany：暂停播放伴奏。

    ```
    public abstract int pauseAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   resumeAudioAccompany：恢复播放伴奏。

    ```
    public abstract int resumeAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   stopAudioAccompany：结束播放伴奏。

    ```
    public abstract int stopAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   setAudioAccompanyPublishVolume：设置伴奏推流音量。

    ```
    public abstract int setAudioAccompanyPublishVolume(int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |volume|int|伴奏推流音量。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   setAudioAccompanyPlayoutVolume：设置伴奏本地音量。

    ```
    public abstract int setAudioAccompanyPlayoutVolume(int volume);
    ```

    |名称|类型|描述|
    |volume|int|伴奏本地播放音量。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   getAudioAccompanyPublishVolume：获取伴奏推流音量。

    返回0~100的伴奏推流音量，返回-1表示获取失败。

    ```
    public abstract int getAudioAccompanyPublishVolume();
    ```

    返回说明

    返回伴奏推流音量取值范围：0~100，返回-1表示获取失败。

-   getAudioAccompanyPlayoutVolume：获取伴奏本地音量。

    ```
    public abstract int getAudioAccompanyPlayoutVolume();
    ```

    返回说明

    返回伴奏推流音量取值范围：0~100，返回-1表示获取失败。

-   setAudioAccompanyVolume：设置伴奏推流和本地音量。

    返回0表示操作成功， 非0表示操作失败。

    ```
    public abstract int setAudioAccompanyVolume(int volume);
    ```

    返回说明

    0表示操作成功， 非0表示操作失败。

-   preloadAudioEffect：预加载音效。

    ```
    public abstract int preloadAudioEffect(int soundId, String filePath);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID（此ID由调用者生成）。|
    |filePath|String|音效文件路径。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   unloadAudioEffect：清除预加载音效。

    ```
    public abstract int unloadAudioEffect(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID（此ID应与预加载时传入的ID相同）。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   playAudioEffect：开始播放音效。

    ```
    public abstract int playAudioEffect(int soundId, String filePath, int cycles, boolean publish);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |filePath|String|音效文件路径，支持本地文件和网络url。|
    |cycles|int|循环播放次数。-1表示一直循环。|
    |publish|boolean|是否将音效音频流推到远端。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   setAudioEffectPublishVolume：设置音效推流音量。

    ```
    public abstract int setAudioEffectPublishVolume(int soundId, int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |volume|int|音效推流音量。取值范围：0～100。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   getAudioEffectPublishVolume：获取音效推流音量。

    返回0~100音效推流音量，返回-1表示获取失败。

    ```
    public abstract int getAudioEffectPublishVolume(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    返回音效推流音量取值范围：0~100，返回-1表示获取失败。

-   setAudioEffectPlayoutVolume：设置音效本地音量。

    ```
    public abstract int setAudioEffectPlayoutVolume(int soundId, int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |volume|int|音效本地播放音量。取值范围：0～100。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   getAudioEffectPlayoutVolume：获取音效本地音量。

    ```
    public abstract int getAudioEffectPlayoutVolume(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    返回音效本地播放音量取值范围：0~100，-1表示获取失败。

-   pauseAudioEffect：暂停播放音效。

    ```
    public abstract int pauseAudioEffect(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   resumeAudioEffect：恢复播放音效。

    ```
    public abstract int resumeAudioEffect(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   stopAudioEffect：停止播放音效。

    ```
    public abstract int stopAudioEffect(int soundId);
    ```

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   setEarBackVolume：设置耳返音量。

    ```
    public abstract int setEarBackVolume(int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |volume|int|耳返音量。取值：0～100（只有耳返开启时才能设置音量，否则该方法返回错误）。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   setRecordingVolume：设置录音音量。

    ```
    public abstract int setRecordingVolume(int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值：0~400，0表示静音。     -   当设置大于100：放大音量。
    -   当设置小于100：减小音量。 |

    返回说明

    0表示操作成功，非0表示操作失败。

    **说明：** 录音音量调节：当对端用户物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100~200，超过200会有影响音质的风险。

-   setPlayoutVolume：设置播放音量。

    ```
    public abstract int setPlayoutVolume(int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量。取值：0~400，0表示静音。     -   当设置大于100：放大音量。
    -   当设置小于100：减小音量。 |

    返回说明

    0表示操作成功，非0表示操作失败。

    **说明：** 播放音量调节：当本地物理按键调大最大，且依然觉得播放声音小时可以调用该接口，推荐值100~200，超过200会有影响音质的风险。

-   muteAllRemoteVideoRendering：mute或unmute远端的所有视频track的渲染。

    ```
    public abstract int muteAllRemoteVideoRendering(boolean mute);
    ```

    |名称|类型|描述|
    |--|--|--|
    |mute|boolean|true表示停止渲染，false表示恢复渲染。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 订阅和解码不受影响，支持加入频道之前或之后设置。

-   setBeautyEffect：设置基础美颜。

    ```
    public abstract int setBeautyEffect(boolean enable, AliRtcEngine.AliRtcBeautyConfig config);
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启，false表示关闭，默认为关闭。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|基础美颜参数。|

    返回说明

    0表示操作成功，非0表示操作失败。

    **说明：** 目前仅支持美白和磨皮。

-   registerVideoSampleObserver：注册视频数据回调。

    ```
    public abstract void registerVideoSampleObserver(AliRtcEngine.AliVideoObserver aliVideoObserver);
    ```

    可参见[音视频输出](https://help.aliyun.com/document_detail/156997.html)进行开发。

    |名称|类型|描述|
    |--|--|--|
    |aliVideoObserver|[AliVideoObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|视频数据回调接口|

-   unRegisterVideoSampleObserver：取消注册视频数据回调。

    ```
    public abstract void unRegisterVideoSampleObserver();
    ```

-   registerAudioVolumeObserver：注册音量回调。

    ```
    public abstract void registerAudioVolumeObserver(AliRtcEngine.AliRtcAudioVolumeObserver observer);
    ```

    |名称|类型|描述|
    |--|--|--|
    |observer|[AliRtcAudioVolumeObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|音量接口。|

-   unRegisterAudioVolumeObserver：取消注册音量回调。

    ```
    public abstract void unRegisterAudioVolumeObserver();
    ```

-   startRecord：开始录制文件。

    ```
    public abstract boolean startRecord(AliRtcEngine.AliRtcRecordType recordType, AliRtcEngine.AliRtcRecordFormat recordFormat, String path, AliRtcEngine.AliRtcRecordAudioConfig audioConfig, AliRtcEngine.AliRtcRecordVideoConfig videoConfig);
    ```

    录制音频包含外部输入PCM数据、本地采集音频和远端拉流音频数据。

    |名称|类型|描述|
    |--|--|--|
    |recordType|[AliRtcRecordType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制文件类型。|
    |recordFormat|[AliRtcRecordFormat](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制文件格式。|
    |path|String|录制文件存储路径。|
    |audioConfig|[AliRtcRecordAudioConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|录制音频属性配置。|

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   stopRecord：停止录制。

    ```
    public abstract void stopRecord();
    ```

    与startRecord一起配合使用，在调用leaveChannel之后方法会自动停止录制。

-   setAudioEffectReverbMode：设置混响音效模式。

    ```
    public abstract int setAudioEffectReverbMode(AliRtcEngine.AliRTCSDK_AudioEffect_Reverb_Mode mode);
    ```

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliRTCSDK\_AudioEffect\_Reverb\_Mode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|混响模式类型。|

    返回说明

    0表示成功，非0表示失败。

-   setAudioEffectReverbParamType：设置混响音效类型。

    ```
     public abstract int setAudioEffectReverbParamType(AliRtcEngine.AliRTCSDK_AudioEffect_Reverb_Param_Type type, float value);
    ```

    |名称|类型|描述|
    |--|--|--|
    |type|[AliRTCSDK\_AudioEffect\_Reverb\_Param\_Type](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|混响音效类型。|
    |value|float|对应混响音效类型的值。|

    返回说明

    0表示成功，非0表示失败。

-   setVolumeCallbackIntervalMs：设置音量回调频率和平滑系数。

    ```
    public abstract int setVolumeCallbackIntervalMs(int interval, int smooth, int reportVad);
    ```

    |名称|类型|描述|
    |--|--|--|
    |interval|int|时间间隔。单位：ms（毫秒），最小值不得小于10ms。|
    |smooth|int|平滑系数。数值越大平滑程度越高，反之越低，实时性越好。建议您设置为3，范围为0~9。|
    |reportVad|int|本地语音检测开关。取值：     -   1：开启，通过onAudioVolumeCallback接口回调。
    -   0：关闭。 |

    返回说明

    0表示成功，-1表示interval设置小于10，-2表示平滑系数超出范围。

-   setExternalAudioSource：设置是否将外部音频数据作为推流的输入源。

    ```
    public abstract int setExternalAudioSource(boolean enable, int sampleRate, int channelsPerFrame);
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示启用外部音频数据作为推流输入源，false表示停止。|
    |sampleRate|int|外部音频数据采样率。|
    |channelsPerFrame|int|外部音频数据声道数（目前支持单声道，双声道）。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   pushExternalAudioFrameRawData：输入音频数据。

    ```
    public abstract int pushExternalAudioFrameRawData(byte[] data, int samples, long timestamp);
    ```

    |名称|类型|描述|
    |--|--|--|
    |data|byte\[\]|音频数据，不建议超过40ms数据。|
    |samples|int|采样率。|
    |timestamp|long|时间戳，目前传0即可。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   setExternalAudioVolume：设置外部音频输入音量。

    ```
    public abstract int setExternalAudioVolume(int volume);
    ```

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量，0~100。|

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   getExternalAudioVolume：获取外部音频输入音量。

    ```
    public abstract int getExternalAudioVolume();
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   setMixedWithMic：设置外部音频输入是否与麦克风采集音频混合。

    ```
    public abstract int setMixedWithMic(boolean mixed);
    ```

    |名称|类型|描述|
    |--|--|--|
    |mixed|boolean|true表示混音，false表示完全替换麦克风采集数据。|

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   setExteranlAudioRender：设置是否启用外部输入音频播放。

    ```
    public abstract int setExteranlAudioRender(boolean enable, int sampleRate, int channelsPerFrame);
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启外部音频作为本地播放输入源，false表示停止。|
    |sampleRate|int|外部音频数据采样率。|
    |channelsPerFrame|int|外部音频数据声道数（目前支持单声道，双声道）。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   pushExternalAudioRenderRawData：输入音频播放数据。

    ```
    public abstract int pushExternalAudioRenderRawData(byte[] audioSamples, int sampleLength, int sampleRate, int channelsPerFrame, long timestamp);
    ```

    |名称|类型|描述|
    |--|--|--|
    |audioSamples|byte\[\]|音频数据。|
    |sampleLength|int|音频数据长度。|
    |sampleRate|int|音频采样率。|
    |channelsPerFrame|int|音频声道数。|
    |timestamp|long|时间戳，目前传0即可。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   getCurrentClientRole：获取当前角色。

    ```
    public abstract AliRtcEngine.AliRTCSDK_Client_Role getCurrentClientRole();
    ```

    返回说明

    返回当前的用户角色。

-   setSubscribeAudioNumChannel：设置回调音频声道数。

    ```
    public abstract void setSubscribeAudioNumChannel(AliRtcAudioNumChannel numChannel);
    ```

    |名称|类型|说明|
    |--|--|--|
    |numChannel|[AliRtcAudioNumChannel](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|音频编号通道。默认单声道音频。|

-   setSubscribeAudioSampleRate：设置回调音频采样率。

    ```
    public abstract void setSubscribeAudioSampleRate(AliRtcAudioSampleRate sampleRate);
    ```

    |名称|类型|说明|
    |--|--|--|
    |sampleRate|[AliRtcAudioSampleRate](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|音频采样率。默认16K。|

-   requestAudioFocus：请求音频焦点。

    ```
    public abstract int requestAudioFocus()
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   abandonAudioFocus：丢失音频焦点。

    ```
    public abstract int abandonAudioFocus()
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   registerAudioObserver：注册音频数据回调。

    ```
    public abstract void registerAudioObserver(AliRtcEngine.AliAudioType audioType, AliRtcEngine.AliAudioObserver audioObserver);
    ```

    指定需要输出的音频数据类型，如果需要输出多种类型数据，需要分别调用注册。注册完成后，音频数据将通过AliAudioObserver持续回调。可参见[音视频输出](https://help.aliyun.com/document_detail/156997.html?spm=a2c4g.11186623.6.655.187c5ff2Ccw9jb)。

    |名称|类型|描述|
    |--|--|--|
    |audioType|[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|回调音频数据的类型|
    |audioObserver|[AliAudioObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|音频数据回调接口|

-   startPreview：开始本地预览。

    ```
    public abstract int startPreview()
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

    **说明：** 您可以在加入频道之前开始本地预览。开始预览之前需要调用setLocalViewConfig。

-   stopPreview：停止本地预览。

    ```
    public abstract int stopPreview()                   
    ```

    返回说明

    0表示方法调用成功。其他表示方法调用失败。

-   enableHighDefinitionPreview：开启高清预览 。

    返回0成功，返回-1表示操作失败。

    ```
    public abstract int enableHighDefinitionPreview(boolean enable);
    ```

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启，false表示关闭。|

    返回说明

    0表示操作成功，-1表示操作失败。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    public abstract String[] getOnlineRemoteUsers()                
    ```

    返回说明

    返回用户ID列表。

    **说明：** 该方法在加入频道时调用有延时，建议您通过onRemoteUserOnLineNotify回调维护一个远端用户列表。

-   getUserInfo：查询远端用户信息。

    ```
    public abstract AliRtcRemoteUserInfo getUserInfo(String uid)                  
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|

    返回说明

    返回远程用户信息[AliRtcRemoteUserInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。

-   isUserOnline：查询用户是否在线。

    ```
    public abstract boolean isUserOnline(String uid)
    ```

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|

    返回说明

    true表示在线，false表示不在线。

-   getMediaInfoWithUserId：获取媒体流信息。

    ```
    public String getMediaInfoWithUserId(String userId, AliRtcVideoTrack track, String[] keys);
    ```

    |名称|类型|描述|
    |--|--|--|
    |userId|String|获取媒体流信息的用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|需要查询的媒体流类型。|
    |keys|String\[\]|查询key值数组。|

-   setLogLevel：设置日志级别。

    ```
    public abstract void setLogLevel(AliRtcLogLevel logLevel)         
    ```

    |名称|类型|描述|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|日志级别。|

-   getSdkVersion：获取SDK版本号。

    ```
    public abstract String getSdkVersion()                   
    ```

-   setClientRole：设置用户角色。

    ```
    public abstract int setClientRole(AliRTCSDK_Client_Role role);
    ```

    |名称|类型|描述|
    |--|--|--|
    |role|[AliRTCSDK\_Client\_Role](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|用户角色类型。默认为观看角色。|

    返回说明

    0表示成功，非0表示失败。

    **说明：** 您仅可以在频道模式为InteractiveLive下调用。入会前或会议中均可设置，设置成功会收到onUpdateRoleNotify。从Interactive转换为Live角色需要先停止推流，否则返回失败。

-   setLogDirPath：设置SDK日志文件保存路径。

    ```
    public static int setLogDirPath(String logDirPath)
    ```

    |名称|类型|描述|
    |--|--|--|
    |logDirPath|String|日志文件保存绝对路径。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 如需调用此接口，请在调用所有SDK接口前先进行设置，避免日志出现丢失，同时App必须保证指定的目录已存在且可写入。

-   setDeviceOrientationMode：设置设备横竖屏方向。

    ```
    public abstract void setDeviceOrientationMode(AliRtcEngine.AliRtcOrientationMode mode);
    ```

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|设备方向。取值：     -   AliRtcOrientationModePortrait（默认值）：固定竖屏模式。
    -   AliRtcOrientationModeLandscapeLeft：固定左横屏模式。
    -   AliRtcOrientationModeLandscapeRight：固定右横屏模式。
    -   AliRtcOrientationModeAuto：自适应模式。 |

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 当前只支持固定横竖屏模式，仅允许在发布和预览之前进行设置。

-   startNetworkQualityProbeTest：开始网络质量探测。

    ```
    public abstract int startNetworkQualityProbeTest();
    ```

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 您需要在加入频道之前调用，并且入会后会自动停止，探测结果在[onNetworkQualityProbeTest](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调。

-   stopNetworkQualityProbeTest：停止网络质量探测。

    ```
    public abstract int stopNetworkQualityProbeTest();
    ```

    返回说明

    0表示成功，其他返回错误码。

-   postFeedback：SDK问题反馈。

```
public abstract void postFeedback(String uid, String channelId, String description, AliRtcFeedbackType type, long timeStamp);
```

    |名称|类型|说明|
    |--|--|--|
    |uid|String|当前uid。|
    |channelId|String|当前channel id。|
    |description|String|问题描述（支持中英文）。|
    |type|[AliRtcFeedbackType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|问题类型（见AliRtcFeedbackType注释）。|
    |timeStamp|long|问题发生的时间戳（Unix时间戳，大致时间，无需特别精确，可以为0）。|

-   sendMediaExtensionMsg：发送媒体扩展信息。

    ```
    public abstract int sendMediaExtensionMsg(byte[]message, int repeatCount);
    ```

    |参数|类型|描述|
    |--|--|--|
    |message|String|自定义消息数据，目前长度限制为8Byte。|
    |repeatCount|int|消息发送次数。|

    返回说明

    -   0：发送成功。
    -   -1：当前未在推流状态，不能发送自定义消息。
    -   -2：参数设置错误，自定义消息长度超过8Byte，或者repeatCount<=0。
    -   -3：发送过于频繁，建议降低发送频率。
    **说明：** 使用音视频数据通道，将自定义消息发送给房间内其他用户，需要满足两个前提：

    -   己方正常入会，并且在推流中。
    -   房间内的其他用户需要订阅己方音视频流，发送成功之后可在[onMediaExtensionMsgReceived](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调中接收结果。

