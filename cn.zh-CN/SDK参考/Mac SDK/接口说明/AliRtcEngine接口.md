# AliRtcEngine接口 {#concept_109116_zh .concept}

本文档为您介绍了Mac SDK的AliRtcEngine接口详情。

## 目录 {#section_adu_i2s_s22 .section}

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[setH5CompatibleMode](#)|设置H5兼容模式。|1.1|
|[getH5CompatibleMode](#)|检查当前是否兼容H5。|1.1|
|[sharedInstance](#)|创建AliRtcEngine实例（同一时间只会存在一个实例）。|1.1|
|[destroy](#)|销毁SDK。|1.1|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAutoPublish](#)|设置是否自动发布，是否自动订阅。|1.1|
|[joinChannel](#)|加入频道。|1.1|
|[leaveChannel](#)|离开频道。|1.1|
|[isInCall](#)|检查当前是否在频道中。|1.1|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoPublish](#)|查询当前是否为自动发布模式。|1.1|
|[configLocalCameraPublish](#)|设置是否允许发布相机流。|1.1|
|[isLocalCameraPublishEnabled](#)|查询当前是否允许发布相机流。|1.1|
|[configLocalScreenPublish](#)|设置是否允许发布屏幕流。|1.1|
|[isLocalScreenPublishEnabled](#)|查询当前是否允许发布屏幕流。|1.1|
|[configLocalAudioPublish](#)|设置是否允许发布音频流。|1.1|
|[isLocalAudioPublishEnabled](#)|查询当前是否允许发布音频流。|1.1|
|[configLocalSimulcast](#)|设置是否允许发布次要视频流。|1.1|
|[isLocalSimulcastEnabled](#)|查询当前是否允许发布次要视频流。|1.1|
|[publish](#)|手动发布视频和音频流。|1.1|

订阅相关接口

|API|描述|以上版本支持|
|---|--|------|
|[isAutoSubscribe](#)|查询当前是否为自动订阅模式。|1.1|
|[configRemoteCameraTrack](#)|设置是否订阅远端相机流。|1.1|
|[configRemoteScreenTrack](#)|设置是否订阅远端屏幕流。|1.1|
|[configRemoteAudio](#)|设置是否订阅远端音频流。|1.1|
|[subscribe](#)|手动订阅视频和音频流。|1.1|
|[getMediaInfoWithUserId](#)|获取当前的媒体流信息。|1.9|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#)|设置视频流的参数。|1.1|
|[setLocalViewConfig](#)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[muteLocalCamera](#)|设置是否停止发布本地视频流。|1.1|
|[setRemoteViewConfig](#)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[getCameraList](#)|获取摄像头列表。|1.1|
|[getCurrentCamera](#)|获取当前使用的摄像头名称。|1.1|
|[setCurrentCamera](#)|选择摄像头。|1.1|
|[isCameraOn](#)|检查摄像头是否打开。|1.1|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAudioOnlyMode](#)|设置纯音频模式还是音视频模式。|1.1|
|[isAudioOnly](#)|查询当前是否为纯音频模式。|1.1|
|[muteLocalMic](#)|设置是否停止发布本地音频。|1.1|
|[muteRemoteAudioPlaying](#)|设置是否停止播放远端音频流。|1.1|
|[getAudioCaptures](#)|获取音频采集设备列表。|1.1|
|[getCurrentAudioCapture](#)|获取当前使用的音频采集设备名称。|1.1|
|[setCurrentAudioCapture](#)|选择音频采集设备。|1.1|
|[getAudioRenderers](#)|获取音频播放设备列表。|1.1|
|[getCurrentAudioRenderer](#)|获取当前使用的音频播放设备。|1.1|
|[setCurrentAudioRenderer](#)|选择音频播放设备。|1.1|
|[startAudioCapture](#)|开启音频采集。|1.11|
|[stopAudioCapture](#)|关闭音频采集。|1.11|
|[startAudioPlayer](#)|开启音频播放。|1.11|
|[stopAudioPlayer](#)|关闭音频播放。|1.11|

预览接口

|API|描述|以上版本支持|
|---|--|------|
|[startPreview](#)|开始本地预览。|1.1|
|[stopPreview](#)|停止本地预览。|1.1|

远端用户查询接口

|API|描述|以上版本支持|
|---|--|------|
|[getOnlineRemoteUsers](#)|获取远端在线用户列表。|1.1|
|[getUserInfo](#)|查询远端用户信息。|1.1|
|[isUserOnline](#)|查询用户是否在线。|1.1|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[setLogLevel](#)|设置log级别。|1.1|
|[getSdkVersion](#)|获取SDK版本号。|1.1|

## 接口详情 {#section_6de_6os_4em .section}

-   setH5CompatibleMode：设置H5兼容模式，当前版本不支持在创建SDK实例之后更改H5兼容模式，必须在创建实例之前就调用此方法，默认不兼容H5。

    ``` {#codeblock_ejy_61n_o1e .lanuage-c}
    + (void)setH5CompatibleMode:(BOOL)comp;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |comp|BOOL|YES为兼容H5模式，NO为不兼容H5。|

-   getH5CompatibleMode：检查当前是否兼容H5，返回YES标识兼容H5，NO表示不兼容H5。

    ``` {#codeblock_3ap_pnm_mnh .lanuage-c}
    + (BOOL)getH5CompatibleMode;
    ```

-   sharedInstance：创建AliRtcEngine实例（同一时间只会存在一个实例）。

    ``` {#codeblock_uid_jlm_b6i .lanuage-c}
    + (instancetype)sharedInstance:(id<AliRtcEngineDelegate>)delegate extras:(NSString *)extras;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |delegate|AliRtcEngineDelegate类型的代理|监听回调的代理。|
    |extras|NSString \*|SDK初始化配置，目前请使用@””。|

-   destroy：销毁SDK，在所有操作结束之后调用。

    ``` {#codeblock_anx_q7u_u9n}
    + (void)destroy;
    ```

-   setAutoPublish：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，必须在joinChannel之前设置。

    ``` {#codeblock_fuw_jeh_y6x .lanuage-c}
    - (int)setAutoPublish:(BOOL)autoPub withAutoSubscribe:(BOOL)autoSub;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |autoPub|BOOL|YES表示自动发布；NO表示手动发布。|
    |autoSub|BOOL|YES表示自动订阅；NO表示手动订阅。|

-   joinChannel：加入频道。加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道；如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ``` {#codeblock_ciy_fd2_5hq .lanuage-c}
    - (void)joinChannel:(AliRtcAuthInfo *)authInfo name:(NSString *)userName onResult:(void(^)(NSInteger errCode))onResult;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo \*](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|鉴权信息，从App Server下发，APP Server可通API获取。|
    |userName|NSString \*|用户的显示名称，不是uid。|
    |onResult|void\(^\)\(NSInteger errCode\)|当joinChannel执行结束后回调。|

-   leaveChannel：离开频道。离开频道时，AliRtcEngine实例会被销毁，如需继续joinChannel等操作，需要先重新调用sharedInstance初始化AliRtcEngine实例。

    ``` {#codeblock_p4r_tri_wbc .lanuage-c}
    - (void)leaveChannel;
    ```

-   isInCall：检查当前是否在频道中，返回YES表示在频道中，NO表示不在频道中。

    ``` {#codeblock_gmi_729_iz6 .lanuage-c}
    - (BOOL)isInCall;
    ```

-   isAutoPublish：查询当前是否为自动发布模式，返回YES为自动发布，NO为手动发布。

    ``` {#codeblock_jmq_ldu_tm9 .lanuage-c}
    - (BOOL)isAutoPublish;
    ```

-   configLocalCameraPublish：设置是否允许发布相机流。默认为允许发布相机流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_nhb_el6_8vq .lanuage-c}
    - (void)configLocalCameraPublish:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布相机流；NO为不允许发布相机流。|

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流，返回YES为允许，NO为不允许。

    ``` {#codeblock_0sz_zkh_vl5 .lanuage-c}
    - (BOOL)isLocalCameraPublishEnabled;
    ```

-   configLocalScreenPublish：设置是否允许发布屏幕流。默认为不允许发布屏幕流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_cc0_pvu_neo .lanuage-c}
    - (void)configLocalScreenPublish:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布屏幕流，NO为不允许发布屏幕流。|

-   isLocalScreenPublishEnabled：查询当前是否允许发布屏幕流，返回YES为允许，NO为不允许。

    ``` {#codeblock_c9i_nw4_5zi .lanuage-c}
    - (BOOL)isLocalScreenPublishEnabled;
    ```

-   configLocalAudioPublish：设置是否允许发布音频流，默认为允许发布音频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_db6_9jy_f56 .lanuage-c}
    - (void)configLocalAudioPublish:(BOOL)enable;
    ```

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流，返回YES为允许，NO为不允许。

    ``` {#codeblock_thi_o9v_nkn .lanuage-c}
    - (BOOL)isLocalAudioPublishEnabled;
    ```

-   configLocalSimulcast：设置是否允许发布次要视频流。默认为允许发布次要视频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_17z_vhv_3tk .lanuage-c}
    - (int)configLocalSimulcast:(BOOL)enabled forTrack:(AliRtcVideoTrack)track;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enabled|BOOL|YES表示允许发布次要流，NO表示不允许。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|流类型，当前只支持相机流：AliVideoTrackCamera。|

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流，返回YES为允许，NO为不允许。

    ``` {#codeblock_hqy_jlt_jh0 .lanuage-c}
    - (BOOL)isLocalSimulcastEnabled;
    ```

-   publish：手动发布视频和音频流。

    -   调用publish的实际表现需要结合configLocalCameraPublish、 configLocalScreenPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述4个接口的参数，以发布相应的视频和音频流 。
    -   发布和停止发布都是调用publish。
    -   如需停止发布，则需要上述3个配置接口的参数都置为NO，再调用publish。
    ``` {#codeblock_4d4_98n_nth .lanuage-c}
    - (void)publish:(void (^)(int errCode))onResult;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |onResult|void \(^\)\(int errCode\)|当publish执行结束后回调。|

-   isAutoSubscribe：查询当前是否为自动订阅模式，返回YES为自动订阅，NO为手动订阅。

    ``` {#codeblock_cqz_m29_cci .lanuage-c}
    - (BOOL)isAutoSubscribe;
    ```

-   configRemoteCameraTrack：设置是否订阅远端相机流。默认为订阅大流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_1x2_n9c_wqp .lanuage-c}
    - (void)configRemoteCameraTrack:(NSString *)uid preferMaster:(BOOL)master enable:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |master|BOOL|是否优先订阅大流。YES为订阅大流；NO为订阅次小流。|
    |enable|BOOL|YES为订阅远端相机流，NO为停止订阅远端相机流。|

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。默认为不订阅远端屏幕流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_zlm_hsc_p0f .lanuage-c}
    - (void)configRemoteScreenTrack:(NSString *)uid enable:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |enable|BOOL|YES为订阅远端屏幕流，NO为停止订阅远端屏幕流。|

-   configRemoteAudio：设置是否订阅远端音频流。默认为订阅远端音频流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_195_16k_fan .lanuage-c}
    - (void)configRemoteAudio:(NSString *)uid enable:(BOOL)enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |enable|BOOL|YES为订阅远端音频流，NO为停止订阅远端音频流。|

-   subscribe：手动订阅视频和音频流。

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如需停止订阅，则需要上述3个配置接口的参数都置为false，再调用subscribe。
    ``` {#codeblock_gtm_a1t_ai8 .lanuage-c}
    - (void)subscribe:(NSString *)uid onResult:(void (^)(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at))onResult;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |onResult|void \(^\)\(NSString \*uid, [AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#) vt, [AliRtcAudioTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#) at\)|当subscribe执行结束后回调。|

-   getMediaInfoWithUserId： 获取当前的媒体流信息。

    ``` {#codeblock_qq5_me7_9wq}
    - (NSString *)getMediaInfoWithUserId:(NSString *)userId videoTrack:(AliRtcVideoTrack)videoTrack keys:(NSArray<NSString *> *)keys;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|NSString \*|需要查询的userId，self请赋值空字符串。|
    |videoTrack|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|需要查询的媒体流类型。|
    |keys|NSArray<NSString \*\> \*|查询key值数组。|

    返回key-value的json格式字符串。

-   setVideoProfile：设置视频流的参数。

    ``` {#codeblock_nkn_b6v_btt .lanuage-c}
    - (void)setVideoProfile:(AliRtcVideoProfile)profile forTrack:(AliRtcVideoTrack)track;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |profile|[AliRtcVideoProfile](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|视频流参数。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|需要设置的videoTrack类型。|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果viewConfig为NULL或者其成员渲染视图为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持viewConfig中其他成员变量不变，仅修改renderMode。
    -   viewConfig中渲染方式默认为AliRtcRenderModeAuto。
    ``` {#codeblock_03t_8sq_0vi .lanuage-c}
    - (int)setLocalViewConfig:(AliVideoCanvas *)viewConfig forTrack:(AliRtcVideoTrack)track;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |viewConfig|[AliVideoCanvas \*](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|预览只允许AliVideoTrackCamera。|

-   muteLocalCamera：设置是否停止发布本地视频流，不改变当前视频流的采集状态。

    ``` {#codeblock_a7v_c5b_mc7 .lanuage-c}
    - (int)muteLocalCamera:(BOOL)mute forTrack:(AliRtcVideoTrack)track;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止发布视频流；NO表示恢复发布。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|需要改变发布状态的videoTrack类型。|

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果canvas为NULL或者其成员view为NULL，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeAuto。
    ``` {#codeblock_qqp_plg_u6q .lanuage-c}
    - (int)setRemoteViewConfig:(AliVideoCanvas *)canvas uid:(NSString *)uid forTrack:(AliRtcVideoTrack)track;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas \*](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|需要设置的videoTrack类型。|

-   getCameraList：获取摄像头列表。

    ``` {#codeblock_9nk_j7q_qrx .lanuage-c}
    - (NSArray<NSString *> *)getCameraList;
    ```

-   getCurrentCamera：获取当前使用的摄像头名称。

    ``` {#codeblock_0nz_p13_3ar .lanuage-c}
    - (NSString *)getCurrentCamera;
    ```

-   setCurrentCamera：选择摄像头。必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_gnd_0re_hmf .lanuage-c}
    - (void)setCurrentCamera:(NSString *)camera;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |camera|NSString \*|摄像头名称。|

-   isCameraOn：检查摄像头是否打开，YES表示摄像头已打开，NO表示摄像头没有打开。

    ``` {#codeblock_t1v_nxz_00q .lanuage-c}
    - (BOOL)isCameraOn;
    ```

-   setAudioOnlyMode：设置是否为纯音频模式还是音视频模式，返回0代表设置成功，其他代表设置失败。默认为音视频模式（非纯音频），必须在joinChannel之前设置。

    ``` {#codeblock_jh0_mjd_6vj .lanuage-c}
    - (int)setAudioOnlyMode:(BOOL)audioOnly;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |audioOnly|BOOL|YES表示只有音频发布和订阅；NO表示音视频都支持。|

-   isAudioOnly：查询当前是否为纯音频模式，返回YES为纯音频，NO为音视频。

    ``` {#codeblock_jv9_04m_6g4 .lanuage-c}
    - (BOOL)isAudioOnly;
    ```

-   muteLocalMic：设置是否停止发布本地音频，返回0表示设置成功，-1表示设置失败。不改变当前音频的采集状态。

    ``` {#codeblock_6p5_z8q_zwz .lanuage-c}
    - (int)muteLocalMic:(BOOL)mute;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止发布本地音频；NO表示恢复发布。|

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流，返回0表示设置成功，-1表示设置失败。

    ``` {#codeblock_zis_2k3_749 .lanuage-c}
    - (int)muteRemoteAudioPlaying:(NSString *)uid mute:(BOOL)mute;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|
    |mute|BOOL|YES表示停止播放；NO表示恢复播放。|

-   getAudioCaptures：获取音频采集设备列表。

    ``` {#codeblock_xzo_okx_h9q .lanuage-c}
    - (NSArray<NSString *> *)getAudioCaptures;
    ```

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ``` {#codeblock_1w1_xow_9hm .lanuage-c}
    - (NSString *)getCurrentAudioCapture;
    ```

-   setCurrentAudioCapture：选择音频采集设备。必须先调用getCurrentAudioCapture接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_jtm_sz8_6cn .lanuage-c}
    - (void)setCurrentAudioCapture:(NSString *)capture;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |capture|NSString \*|音频采集设备名称。|

-   getAudioRenderers：获取音频播放设备列表。

    ``` {#codeblock_onk_5hf_svv .lanuage-c}
    - (NSArray<NSString *> *)getAudioRenderers;
    ```

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ``` {#codeblock_glv_u0w_4f4 .lanuage-c}
    - (NSString *)getCurrentAudioRenderer;
    ```

-   setCurrentAudioRenderer：选择音频播放设备。必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_ino_yfo_d8e .lanuage-c}
    - (void)setCurrentAudioRenderer:(NSString *)renderer;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |renderer|NSString \*|音频播放设备名称。|

-   startAudioCapture：开启音频采集。您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ``` {#codeblock_tkj_rij_2ds}
    - (void)startAudioCapture;
    ```

-   stopAudioCapture：关闭音频采集。您可以控制关闭音频采集。

    ``` {#codeblock_5zt_4fn_2y6}
    - (void)stopAudioCapture;
    ```

-   startAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ``` {#codeblock_yvs_lct_q6z}
    - (void)startAudioPlayer;
    ```

-   stopAudioPlayer：关闭音频播放。您可以控制关闭音频播放。

    ``` {#codeblock_c3u_5ev_od6}
    - (void)stopAudioPlayer;
    ```

-   startPreview：开始本地预览，可以在joinChannel之前就开启预览。

    ``` {#codeblock_5i8_cng_jx3 .lanuage-c}
    - (int)startPreview;
    ```

-   stopPreview：停止本地预览。

    ``` {#codeblock_2oq_734_u9y .lanuage-c}
    - (int)stopPreview;
    ```

-   getOnlineRemoteUsers：获取远端在线用户列表，返回用户ID列表。

    ``` {#codeblock_bom_6al_drj .lanuage-c}
    - (NSArray<NSString *> *)getOnlineRemoteUsers;
    ```

-   getUserInfo：查询远端用户信息。

    ``` {#codeblock_a8o_csa_mbj .lanuage-c}
    - (NSDictionary *)getUserInfo:(NSString *)uid;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|

-   isUserOnline：查询用户是否在线，YES表示在线，NO表示不在线。

    ``` {#codeblock_0ox_65t_5a6 .lanuage-c}
    - (BOOL)isUserOnline:(NSString *)uid;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|

-   setLogLevel：设置log级别。

    ``` {#codeblock_0jm_puh_qdt .lanuage-c}
    - (void)setLogLevel:(AliRtcLogLevel)logLevel;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](cn.zh-CN/SDK参考/Mac SDK/接口说明/数据类型.md#)|log级别。|

-   getSdkVersion：获取SDK版本号。

    ``` {#codeblock_z4m_myr_3ng .lanuage-c}
    + (NSString *)getSdkVersion;
    ```


