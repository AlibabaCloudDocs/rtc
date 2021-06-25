# IAliRtcEngine接口

通过阅读本文，您可以了解到Unity SDK的IAliRtcEngine接口详情。

## 目录

基础接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetH5CompatibleMode](#li_vxt_gz9_qqm)|设置H5兼容模式。|1.15|
|[GetH5CompatibleMode](#li_5yq_r4f_jbn)|检查当前是否兼容H5。|1.15|
|[GetEngine](#li_cm7_m68_lfx)|创建IAliRtcEngine实例（同一时间只会存在一个实例）。|1.15|
|[QueryEngine](#li_9t4_j8g_ek4)|查询IAliRtcEngine实例。|1.15|
|[Destroy](#li_cwq_gem_umt)|销毁SDK。|1.15|

频道相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetAutoPublish](#li_tpm_vei_wk1)|设置是否自动发布，是否自动订阅。|1.15|
|[JoinChannel](#li_0do_wfw_25n)|加入频道。|1.15|
|[LeaveChannel](#li_qla_3ql_d4a)|离开频道。|1.15|
|[IsInCall](#li_l67_4l1_acn)|检查当前是否在频道中。|1.15|
|[SetChannelProfile](#li_jw3_0ud_qad)|设置频道模式。|1.15|

发布相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[IsAutoPublish](#li_tai_xlw_36d)|查询当前是否为自动发布模式。|1.15|
|[ConfigLocalCameraPublish](#li_a1t_jz0_znq)|设置是否允许发布相机流。|1.15|
|[IsLocalCameraPublishEnabled](#li_06o_v8e_ifs)|查询当前是否允许发布相机流。|1.15|
|[ConfigLocalScreenPublish](#li_cjv_wft_253)|设置是否允许发布屏幕流（仅Mac、Windows）。|1.15|
|[IsLocalScreenPublishEnabled](#li_wxt_7pq_6ux)|查询当前是否允许发布屏幕流（仅Mac、Windows）。|1.15|
|[ConfigLocalAudioPublish](#li_m2n_lkm_o0b)|设置是否允许发布音频流。|1.15|
|[IsLocalAudioPublishEnabled](#li_uay_apm_0rm)|查询当前是否允许发布音频流。|1.15|
|[ConfigLocalSimulcast](#li_0e4_q2h_1mt)|是否允许发布次要视频流。|1.15|
|[IsLocalSimulcastEnabled](#li_gjj_ax5_l4f)|查询当前是否允许发布次要视频流。|1.15|
|[Publish](#li_yui_kk1_n8h)|手动发布视频和音频流。|1.15|

订阅相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[IsAutoSubscribe](#li_gab_q95_i89)|查询当前是否为自动订阅模式。|1.15|
|[ConfigRemoteCameraTrack](#li_gk1_ize_cca)|设置是否订阅远端相机流。|1.15|
|[ConfigRemoteScreenTrack](#li_53z_cnu_j6k)|设置是否订阅远端屏幕流。|1.15|
|[ConfigRemoteAudio](#li_svj_8wm_4df)|设置是否订阅远端音频流。|1.15|
|[Subscribe](#li_h1d_7of_vpx)|手动订阅视频和音频流。|1.15|

视频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetVideoProfile](#li_17u_pzn_5v4)|设置视频流的参数。|1.15|
|[GenerateTexture](#li_whn_mry_c8u)|生成渲染纹理（仅iOS、Android）。|1.15|
|[SetTexture](#li_eee_98k_fte)|设置纹理（仅iOS、Android）。|1.15|
|[RemoveTexture](#li_nrz_bc4_p5j)|移除渲染纹理（仅iOS、Android）。|1.15|
|[ConfigExternalVideoRendering](#li_2jk_8bf_tkf)|设置外部渲染（仅Mac、Windows）。|1.15|
|[GetVideoRenderData](#li_afb_sxy_5i6)|获取视频数据（仅Mac、Windows）。|1.15|
|[SetLocalViewConfig](#li_f0u_8zz_492)|为本地预览设置镜像（仅Mac、Windows）。|1.15|
|[MuteLocalCamera](#li_or0_neo_rk4)|设置是否停止发布本地视频流。|1.15|
|[GetCameraList](#li_gj1_dm7_iqj)|获取摄像头列表（仅Mac、Windows）。|1.15|
|[GetCurrentCamera](#li_pvu_biy_dg9)|获取当前使用的摄像头名称（仅Mac、Windows）。|1.15|
|[SetCurrentCamera](#li_r1w_mdw_8uo)|选择摄像头（仅Mac、Windows）。|1.15|
|[SwitchCamera](#li_ugv_6la_cxh)|切换前后摄像头（仅iOS、Android）。|1.15|
|[SetCameraZoom](#li_1wp_49x_hmg)|设置摄像头参数（仅iOS、Android）。|1.15|
|[IsCameraOn](#li_968_m1o_7zl)|检查摄像头是否打开（仅iOS、Android）。|1.15|
|[IsCameraFocusPointSupported](#li_rlz_oxj_ald)|摄像头是否支持手动聚焦（仅iOS、Android）。|1.15|
|[IsCameraExposurePointSupported](#li_efs_os6_nxu)|摄像头是否支持设置曝光区域（仅iOS、Android）。|1.15|
|[SetCameraFocusPoint](#li_b3k_jdh_ovc)|设置摄像头手动聚焦（仅iOS、Android）。|1.15|
|[SetCameraExposurePoint](#li_173_j44_mip)|设置摄像头曝光点（仅iOS、Android）。|1.15|

音频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetAudioOnlyMode](#li_z8q_jwb_qjp)|设置是否为纯音频模式还是音视频模式。|1.15|
|[IsAudioOnly](#li_xp9_sab_nnc)|查询当前是否为纯音频模式。|1.15|
|[MuteLocalMic](#li_1ak_53n_t4j)|设置是否停止发布本地音频。|1.15|
|[MuteRemoteAudioPlaying](#li_gg5_ovp_c55)|设置是否停止播放远端音频流。|1.15|
|[EnableSpeakerphone](#li_ljz_9hw_h41)|切换听筒、扬声器输出（仅iOS、Android）。|1.15|
|[GetAudioCaptures](#li_vhx_oek_ub4)|获取音频采集设备列表（仅Mac、Windows）。|1.15|
|[GetCurrentAudioCapture](#li_oqd_a4q_mvp)|获取当前使用的音频采集设备名称（仅Mac、Windows）。|1.15|
|[SetCurrentAudioCapture](#li_ecg_fu5_g9i)|选择音频采集设备（仅Mac、Windows）。|1.15|
|[GetAudioRenderers](#li_upu_iga_x5v)|获取音频播放设备列表（仅Mac、Windows）。|1.15|
|[GetCurrentAudioRenderer](#li_fc7_ogb_qrh)|获取当前使用的音频播放设备（仅Mac、Windows）。|1.15|
|[SetCurrentAudioRenderer](#li_op2_1z8_rr1)|选择音频播放设备（仅Mac、Windows）。|1.15|
|[StartAudioPlayer](#li_ofs_awo_mxz)|开启音频播放。|1.15|
|[StopAudioPlayer](#li_3oi_gmv_rnp)|关闭音频播放。|1.15|

预览接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartPreview](#li_4qc_6m1_pwd)|开始本地预览。|1.15|
|[StopPreview](#li_8v5_m41_8mp)|停止本地预览。|1.15|

远端用户查询接口

|API|描述|支持的最低版本|
|---|--|-------|
|[GetOnlineRemoteUsers](#li_io3_ppc_2t8)|获取远端在线用户列表。|1.15|

其他接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetLogLevel](#li_i6q_4wg_f7t)|设置日志级别。|1.15|
|[GetSdkVersion](#li_azz_yg7_emu)|获取SDK版本号。|1.15|
|[SetClientRole](#li_tor_i4a_rm5)|设置用户角色。|1.15|

## 接口详情

-   SetH5CompatibleMode：检查当前是否兼容H5。

    您需要在创建AliRtcEngine实例前调用该接口。

    ```
    public static void SetH5CompatibleMode(bool comp);
    ```

    |参数|类型|描述|
    |--|--|--|
    |comp|bool|YES为兼容H5模式，NO为不兼容H5。|

-   GetH5CompatibleMode：检查当前是否兼容H5。

    您需要在创建AliRtcEngine实例前调用该接口。

    ```
     public static bool GetH5CompatibleMode();
    ```

    返回说明

    返回true表示兼容H5，false表示不兼容H5。

-   GetEngine：创建AliRtcEngine实例。

    ```
     public static IAliRtcEngine GetEngine(string extras);
    ```

    |参数|类型|描述|
    |--|--|--|
    |extras|string|SDK初始化配置，目前请使用@””。|

-   QueryEngine：查询AliRtcEngine实例。

    ```
     public static IAliRtcEngine QueryEngine();
    ```

-   Destroy：销毁AliRtcEngine实例。

    ```
     public static void Destroy();
    ```

-   SetAutoPublish：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，您必须在加入频道之前设置。

    ```
    public void SetAutoPublish(bool autoPub, bool autoSub);
    ```

    |参数|类型|描述|
    |--|--|--|
    |autoPub|bool|true表示自动发布，false表示手动发布。|
    |autoSub|bool|true表示自动订阅，false表示手动订阅。|

-   JoinChannel：加入频道。

    加入频道成功后，如果中途需要加入其他频道，您必须先调用LeaveChannel离开当前频道；如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ```
    public void JoinChannel(AliRTCAuthInfo authInfo, string userName);
    ```

    |参数|类型|描述|
    |--|--|--|
    |authInfo|AliRTCAuthInfo|鉴权信息，从AppServer下发，AppServer通过API获取。|
    |userName|string|用户的显示名称，不是用户ID。|

-   LeaveChannel：离开频道。

    ```
    public void LeaveChannel();
    ```

-   IsInCall：检查当前是否在频道中。

    ```
    public bool IsInCall();
    ```

    返回说明

    返回true表示在频道中，false表示不在频道中。

-   SetChannelProfile：设置频道模式。

    **说明：** 您只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

    ```
    public void SetChannelProfile(int profile);
    ```

    |参数|类型|描述|
    |--|--|--|
    |profile|int|频道模式类型。|

-   IsAutoPublish：查询当前是否为自动发布模式。

    ```
    public bool IsAutoPublish();
    ```

    返回说明

    返回true表示自动发布，false表示手动发布。

-   ConfigLocalCameraPublish：设置是否允许发布相机流。默认为允许发布相机流，手动发布时，需要调用publish才能生效。

    ```
    public void ConfigLocalCameraPublish(bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|bool|true为允许发布相机流，false为不允许。|

-   IsLocalCameraPublishEnabled：查询当前是否允许发布相机流。

    ```
    public bool IsLocalCameraPublishEnabled();
    ```

    返回说明

    返回true表示允许，false表示不允许。

-   ConfigLocalScreenPublish（仅Mac、Windows可用）：设置是否允许发布屏幕流。默认为不允许发布屏幕流，手动发布时，需要调用publish才能生效。

    ```
    public void ConfigLocalScreenPublish(bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|bool|true为允许发布屏幕流，false为不允许发布屏幕流。|

-   IsLocalScreenPublishEnabled（仅Mac、Windows可用）：查询当前是否允许发布屏幕流。

    ```
    public bool IsLocalScreenPublishEnabled();
    ```

    返回说明

    返回true表示允许，false表示不允许。

-   ConfigLocalAudioPublish：设置是否允许发布音频流。默认为允许发布音频流，手动发布时，需要调用publish才能生效。

    ```
    public void ConfigLocalAudioPublish(bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|bool|true为允许发布音频流，false为不允许。|

-   IsLocalAudioPublishEnabled：查询当前是否允许发布音频流。

    ```
    public void ConfigLocalSimulcast(bool enable, int track);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enabled|bool|true表示允许发布次要流，false表示不允许。|
    |track|AliRTCVideoTrack|流类型，当前只支持相机流：VIDEO\_TRACK\_CAMERA。|

-   ConfigLocalSimulcast：设置是否允许发布次要视频流。默认为允许发布次要视频流，手动发布时，需要调用publish才能生效。

    ```
    public void ConfigLocalSimulcast(bool enable, int track);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enabled|bool|true表示允许发布次要流，false表示不允许。|
    |track|AliRTCVideoTrack|流类型，当前只支持相机流：VIDEO\_TRACK\_CAMERA。|

-   IsLocalSimulcastEnabled：查询当前是否允许发布次要视频流。

    ```
    public bool IsLocalSimulcastEnabled();
    ```

    返回说明

    返回true表示允许，false表示不允许。

-   Publish：手动发布视频和音频流。

    -   调用Publish的实际表现需要结合ConfigLocalCameraPublish、ConfigLocalAudioPublish、ConfigLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以发布相应的视频和音频流。
    -   发布和停止发布都是调用Publish。
    -   如果需要停止发布，则需要上述3个配置接口的参数都置为NO，再调用Publish。
    -   需要在加入频道成功之后调用该接口。
    ```
    public void Publish();
    ```

-   IsAutoSubscribe：查询当前是否为自动订阅模式。

    ```
    public bool IsAutoSubscribe();
    ```

    返回说明

    返回true表示自动订阅，false表示手动订阅。

-   ConfigRemoteCameraTrack：设置是否订阅远端相机流。默认为订阅大流，手动订阅时，需要调用Subscribe才能生效。

    ```
    public void ConfigRemoteCameraTrack(string userId, bool master, bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |userId|string|用户ID，从AppServer获取的唯一标示符。|
    |master|bool|是否优先订阅大流。true为订阅大流，false为订阅次小流。|
    |enable|bool|true为订阅远端相机流，false为停止订阅远端相机流。|

-   ConfigRemoteScreenTrack：设置是否订阅远端屏幕流。默认为不订阅远端屏幕流，手动订阅时，需要调用Subscribe才能生效。

    ```
    public void ConfigRemoteScreenTrack(string userId, bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |userId|string|用户ID，从AppServer获取的唯一标示符。|
    |enable|bool|true为订阅远端屏幕流，false为停止订阅远端屏幕流。|

-   ConfigRemoteAudio：设置是否订阅远端音频流。默认为订阅远端音频流，手动订阅时，需要调用Subscribe才能生效。

    ```
    public void ConfigRemoteAudio(string userId, bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |userId|string|用户ID，从AppServer获取的唯一标示符。|
    |enable|bool|true为订阅远端音频流，false为停止订阅远端音频流。|

-   Subscribe：手动订阅视频和音频流。

    -   调用Subscribe的实际表现需要结合ConfigRemoteCameraTrack、ConfigRemoteScreenTrack、ConfigRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用Subscribe。
    -   如果需要停止订阅，则需要上述3个配置接口的参数都置为false，再调用Subscribe。
    ```
    public void Subscribe(string uid);
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|string|用户ID，从AppServer获取的唯一标示符。|

-   setVideoProfile：设置视频流的参数。

    ```
    public void SetVideoProfile(int profile, int track);
    ```

    |参数|类型|描述|
    |--|--|--|
    |profile|AliRTCVideoProfile|视频流参数。|
    |track|AliRTCVideoTrack|需要设置的videoTrack类型。|

-   GenerateTexture（仅iOS、Android可用）：生成渲染纹理。

    ```
    public int GenerateTexture();
    ```

    返回说明

    返回值大于0表示有效的纹理ID，其他表示无效。

-   SetTexture：设置纹理（仅iOS、Android可用）。

    ```
    public int SetTexture(AliRTCTextureInfo textureInfo, int track, string userId);
    ```

    |参数|类型|描述|
    |--|--|--|
    |textureInfo|AliRTCTextureInfo|纹理信息。|
    |track|AliRTCVideoTrack|需要设置的videoTrack类型。|
    |userId|int|用户ID。|

-   RemoveTexture：移除纹理（仅iOS、Android可用）。

    ```
    public void RemoveTexture(int textureId);
    ```

    |参数|类型|描述|
    |--|--|--|
    |textureId|int|纹理ID。|

-   ConfigExternalVideoRendering：设置外部渲染模式（仅Mac、Windows可用）。

    ```
    public void ConfigExternalVideoRendering(bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|bool|true为设置外部渲染模式，false为禁止外部渲染模式。|

-   GetVideoRenderData：设置外部渲染模式（仅Mac、Windows可用）。

    ```
    public bool GetVideoRenderData(string uid, int track, IntPtr data, ref int width, ref int height);
    ```

    |参数|类型|描述|
    |--|--|--|
    |uid|string|用户ID。|
    |track|AliRTCVideoTrack|videoTrack类型。|
    |data|IntPtr|数据输出指针。|
    |width|int|数据宽度。|
    |height|int|数据高度。|

-   SetLocalViewConfig：为本地预览设置渲染参数。

    ```
    public void SetLocalViewConfig(bool flip);
    ```

    |参数|类型|描述|
    |--|--|--|
    |flip|bool|true 表示打开镜像，false表示关闭镜像。|

-   MuteLocalCamera：设置是否停止发布本地视频流，不改变当前视频流的采集状态。

    ```
    public void MuteLocalCamera(bool mute, int track);
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|bool|true表示停止发布视频流，false表示恢复发布。|
    |track|AliRTCVideoTrack|需要改变发布状态的videoTrack类型。|

-   GetCameraList（仅Mac、Windows可用）：获取摄像头列表。

    ```
    public string GetCameraList();
    ```

-   GetCurrentCamera（仅Mac、Windows可用）：获取当前使用的摄像头名称。

    ```
    public string GetCurrentCamera();
    ```

-   SetCurrentCamera（仅Mac、Windows可用）：选择摄像头。必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ```
    public void SetCurrentCamera(string deviceName);
    ```

    |参数|类型|描述|
    |--|--|--|
    |deviceName|string|摄像头名称。|

-   SwitchCamera（仅iOS、Android可用）：切换前后摄像头。

    ```
    public int SwitchCamera();
    ```

    返回说明

    返回0表示切换成功，其他表示切换失败。

-   SetCameraZoom（仅iOS、Android可用）：设置摄像头参数。

    ```
    public int SetCameraZoom(float zoom, bool flash, bool autoFocus);
    ```

    |参数|类型|描述|
    |--|--|--|
    |zoom|float|zoom变焦的级别，取值：-3~3，默认为0。|
    |flash|bool|是否打开闪光灯。|
    |autoFocus|bool|是否打开自动对焦。|

    返回说明

    返回0表示设置成功，其他表示设置失败。

-   IsCameraOn：检查摄像头是否打开。

    ```
    public bool IsCameraOn();
    ```

    返回说明

    返回true表示摄像头已打开，false表示摄像头没有打开。

-   IsCameraFocusPointSupported（仅iOS、Android可用）：摄像头是否支持手动聚焦。

    ```
    public bool IsCameraFocusPointSupported();
    ```

    返回说明

    返回true表示支持，false表示不支持。

-   IsCameraExposurePointSupported（仅iOS、Android可用）：摄像头是否支持设置曝光区域。

    ```
    public bool IsCameraExposurePointSupported();
    ```

    返回说明

    返回true表示支持，false表示不支持。

-   SetCameraFocusPoint（仅iOS、Android可用）：设置摄像头手动聚焦。

    ```
    public int SetCameraFocusPoint(float x, float y);
    ```

    |参数|类型|描述|
    |--|--|--|
    |x|float|聚焦点x坐标。|
    |y|float|聚焦点y坐标。|

    返回说明

    返回0表示设置成功，其他表示设置失败。

-   SetCameraExposurePoint（仅iOS、Android可用）：设置摄像头曝光点。

    ```
    public int SetCameraExposurePoint(float x, float y);
    ```

    |参数|类型|描述|
    |--|--|--|
    |x|float|聚焦点x坐标。|
    |y|float|聚焦点y坐标。|

    返回说明

    返回0表示设置成功，其他表示设置失败。

-   SetAudioOnlyMode：设置是否为纯音频模式还是音视频模式。默认为音视频模式（非纯音频），必须在JoinChannel之前设置。

    ```
    public void SetAudioOnlyMode(bool audioOnly);
    ```

    |参数|类型|描述|
    |--|--|--|
    |audioOnly|bool|true表示只有音频发布和订阅，false表示音视频都支持。|

-   IsAudioOnly：查询当前是否为纯音频模式。

    ```
    public bool IsAudioOnly();
    ```

    返回说明

    返回true表示纯音频，false表示音视频。

-   MuteLocalMic：设置是否停止发布本地音频，不改变当前音频的采集状态。

    ```
    public void MuteLocalMic(bool mute);
    ```

    |参数|类型|描述|
    |--|--|--|
    |mute|bool|true表示停止发布本地音频，false表示恢复发布。|

-   MuteRemoteAudioPlaying：设置是否停止播放远端音频流。

    ```
    public int MuteRemoteAudioPlaying(string userId, bool mute);
    ```

    |参数|类型|描述|
    |--|--|--|
    |userId|string|用户ID，从AppServer获取的唯一标示符。|
    |mute|bool|true表示停止播放，false表示恢复播放。|

    返回说明

    返回0表示设置成功，-1表示设置失败。

-   EnableSpeakerphone（仅iOS、Android可用）：切换听筒、扬声器输出。

    ```
    public int EnableSpeakerphone(bool enable);
    ```

-   GetAudioCaptures（仅Mac、Windows可用）：获取音频采集设备列表。

    ```
    public string GetAudioCaptures();
    ```

-   GetCurrentAudioCapture（仅Mac、Windows可用）：获取当前使用的音频采集设备名称。

    ```
    public string GetCurrentAudioCapture();
    ```

-   SetCurrentAudioCapture（仅Mac、Windows可用）：选择音频采集设备。必须先调用GetCurrentAudioCapture接口获取设备列表后再调用此接口设置。

    ```
    public void SetCurrentAudioCapture(string deviceName);
    ```

    |参数|类型|描述|
    |--|--|--|
    |deviceName|string|音频采集设备名称。|

-   GetAudioRenderers（仅Mac、Windows可用）：获取音频播放设备列表。

    ```
    public string GetAudioRenderers();
    ```

-   GetCurrentAudioRenderer（仅Mac、Windows可用）：获取当前使用的音频播放设备。

    ```
    public string GetCurrentAudioRenderer();
    ```

-   SetCurrentAudioRenderer（仅Mac、Windows可用）：选择音频播放设备。必须先调用GetAudioRenderers接口获取设备列表后再调用此接口设置。

    ```
    public void SetCurrentAudioRenderer(string deviceName);
    ```

    |参数|类型|描述|
    |--|--|--|
    |deviceName|string|音频播放设备名称。|

-   StartAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ```
    public void StartAudioPlayer();
    ```

-   StopAudioPlayer：关闭音频播放。

    ```
    public void StopAudioPlayer();
    ```

-   StartPreview：开始本地预览，开始预览之前需要设置SetLocalViewConfig。

    您可以在加入频道之前开始本地预览。

    ```
    public void StartPreview();
    ```

-   StopPreview：停止本地预览。

    ```
    public void StopPreview();
    ```

-   GetOnlineRemoteUsers：获取远端在线用户列表，返回用户ID列表。

    ```
    public string GetOnlineRemoteUsers();
    ```

-   SetLogLevel：设置日志级别。

    ```
    public void SetLogLevel(int logLevel);
    ```

    |参数|类型|描述|
    |--|--|--|
    |logLevel|AliRTCLogLevel|日志级别。|

-   GetSdkVersion：获取SDK版本号。

    ```
    public static string GetSdkVersion();
    ```

-   SetClientRole：设置频道模式。

    -   您仅可以在频道模式为InteractiveLive下调用。
    -   入会前或会议中均可设置，设置成功会收到OnUpdateRoleNotify。
    -   从Interactive转换为Live角色需要先停止推流，否则返回失败。
    ```
     public void SetClientRole(int role);
    ```

    |参数|类型|描述|
    |--|--|--|
    |role|AliRTCClientRole|用户角色类型。|


