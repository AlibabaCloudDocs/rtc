# AliRtcEngine接口 {#concept_109125_zh .concept}

本文档为您介绍了Windows SDK的AliRtcEngine接口详情。

## 目录 {#section_346_4zl_fqx .section}

基础接口

|API|描述|
|---|--|
|[setH5CompatibleMode](#)|设置H5兼容模式|
|[getH5CompatibleMode](#)|检查当前是否兼容H5|
|[sharedInstance](#)|创建AliRtcEngine实例（同一时间只会存在一个实例）|

频道相关接口

|API|描述|
|---|--|
|[setAutoPublishSubscribe](#)|设置是否自动发布，是否自动订阅|
|[joinChannel](#)|加入频道|
|[leaveChannel](#)|离开频道|
|[isInCall](#)|检查当前是否在频道中|

发布相关接口

|API|描述|
|---|--|
|[isAutoPublish](#)|查询当前是否为自动发布模式|
|[configLocalCameraPublish](#)|设置是否允许发布相机流|
|[isLocalCameraPublishEnabled](#)|查询当前是否允许发布相机流|
|[configLocalScreenPublish](#)|设置是否允许发布屏幕共享流|
|[isLocalScreenPublishEnabled](#)|查询当前是否允许发布屏幕共享流|
|[configLocalAudioPublish](#)|设置是否允许发布音频流|
|[isLocalAudioPublishEnabled](#)|查询当前是否允许推音频流|
|[configLocalSimulcast](#)|设置是否允许发布次要视频流|
|[isLocalSimulcastEnabled](#)|查询当前是否允许发布次要视频流|
|[publish](#)|手动发布视频和音频流|

订阅相关接口

|API|描述|
|---|--|
|[isAutoSubscribe](#)|查询当前是否为自动订阅模式|
|[configRemoteCameraTrack](#)|设置是否订阅远端相机流|
|[configRemoteScreenTrack](#)|设置是否订阅远端屏幕流|
|[configRemoteAudio](#)|设置是否订阅远端音频流|
|[subscribe](#)|手动订阅视频和音频流|

视频相关接口

|API|描述|
|---|--|
|[setVideoProfile](#)|设置视频流的参数|
|[setLocalViewConfig](#)|为本地预览设置渲染窗口以及绘制参数|
|[muteLocalCamera](#)|设置是否停止发布本地视频流|
|[setRemoteViewConfig](#)|为远端的视频设置渲染窗口以及绘制参数|
|[getCameraList](#)|获取摄像头列表|
|[getCurrentCamera](#)|获取当前使用的摄像头名称|
|[setCurrentCamera](#)|选择摄像头|
|[isCameraOn](#)|检查摄像头是否打开|

音频相关接口

|API|描述|
|---|--|
|[setAudioOnlyMode](#)|设置为纯音频模式还是音视频模式|
|[isAudioOnly](#)|查询当前是否为纯音频模式|
|[muteLocalMic](#)|设置是否停止发布本地音频|
|[muteRemoteAudioPlaying](#)|设置是否停止播放远端音频流|
|[getAudioCaptures](#)|获取音频采集设备列表|
|[getCurrentAudioCapture](#)|获取当前使用的音频采集设备名称|
|[setCurrentAudioCapture](#)|选择音频采集设备|
|[getAudioRenderers](#)|获取音频播放设备列表|
|[getCurrentAudioRenderer](#)|获取当前使用的音频播放设备|
|[setCurrentAudioRenderer](#)|选择音频播放设备|
|[SetAudioVolume](#)|设置系统音量|
|[GetAudioVolume](#)|获取系统音量|
|[startAudioCapture](#)|开启音频采集|
|[stopAudioCapture](#)|关闭音频采集|
|[startAudioPlayer](#)|开启音频播放设备|
|[stopAudioPlayer](#)|关闭音频播放|

预览接口

|API|描述|
|---|--|
|[startPreview](#)|开始本地预览|
|[stopPreview](#)|停止本地预览|

远端用户查询接口

|API|描述|
|---|--|
|[getOnlineRemoteUsers](#)|获取远端在线用户列表|
|[getUserInfo](#)|查询远端用户信息|
|[isUserOnline](#)|查询用户是否在线|
|[getMediaInfoWithKeys](#)|获取媒体信息|

其他接口

|API|描述|
|---|--|
|[setLogLevel](#)|设置log级别|
|[getSdkVersion](#)|获取sdk版本号|

## 接口详情 {#section_aok_14o_kfo .section}

-   setH5CompatibleMode：设置是否兼容H5，当前版本不支持在创建AliRtcEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此方法，默认不兼容H5。

    ``` {#codeblock_zi7_xkh_mgo .lanuage-c}
    void setH5CompatibleMode(BOOL comp)         
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |comp|BOOL|0表示不兼容H5，1表示兼容H5|

-   getH5CompatibleMode：检查当前是否兼容H5，返回TRUE表示兼容H5；FALSE表示不兼容H5。

    ``` {#codeblock_231_0xj_ho7 .lanuage-c}
    BOOL getH5CompatibleModeine()               
    ```

-   sharedInstance：创建AliRTCEngine实例（同一时间只会存在一个实例）。

    ``` {#codeblock_8ny_1es_tdn .lanuage-c}
    AliRtcEngine* sharedInstance(AliRtcEventListener* listener, const AliRtc::String &extras)         
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |listener|AliRtcEventListener\*|AliRtcEngine回调的监听器|
    |extras|const AliRtc::String &|SDK初始化配置，目前请使用空字符串|

-   setAutoPublishSubscribe：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，必须在joinChannel之前设置。

    ``` {#codeblock_4q3_9ae_s9k .lanuage-c}
    int setAutoPublishSubscribe(bool autoPub, bool autoSub)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |autoPub|bool|true表示自动发布；false表示手动发布|
    |autoSub|bool|true表示自动订阅；false表示手动订阅|

-   joinChannel：加入频道。

    加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道，如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ``` {#codeblock_4jy_yid_rwc .lanuage-c}
    void joinChannel(const AliRtcAuthInfo& authInfo, const AliRtc::String& userName, void(*)(void* opaquePtr, int errCode) onResult, void* opaquePtr)                  
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |authInfo|const AliRtcAuthInfo&|鉴权信息，从App Server下发，APP Server可通过OpenAPI获取|
    |userName|const AliRtc::String&|用户的显示名称，不是uid|
    |onResult|void\(\)\(void opaquePtr, int errCode\)|当joinChannel执行结束后回调|
    |opaquePtr|void\*|app提供的UserData，在调用onResult时传回app|

    注解：异步接口，是否成功入会，通过onResult判断。lambda表达式转换成onResult。

    ``` {#codeblock_d9k_ree_hyb .lanuage-c}
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

    离开频道时，AliRtcEngine实例会被销毁，如需继续joinChannel等操作，需要先重新调用sharedInstance初始化AliRtcEngine实例。

    ``` {#codeblock_1nk_b5g_d93 .lanuage-c}
    void leaveChannel()
    ```

    注解：如果当前不在频道内，leaveChannel不会有任何影响，leaveChannel会产生消息通知频道内其他用户。

-   isInCall：检查当前是否在频道中，返回true表示在频道中，false表示不在频道中。

    ``` {#codeblock_qim_mf2_7kt .lanuage-c}
    bool isInCall()                
    ```

-   isAutoPublish：查询当前是否为自动发布模式，返回true为自动发布，false为手动发布。

    ``` {#codeblock_siy_ybl_gke .lanuage-c}
    bool isAutoPublish()                
    ```

-   configLocalCameraPublish：设置是否允许发布相机流。默认为允许发布相机流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_r7v_weu_sc8 .lanuage-c}
    void configLocalCameraPublish(bool enable)               
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|bool|true为允许发布相机流；false表示不允许|

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流，返回true为允许，false为不允许。

    ``` {#codeblock_v9i_8yi_bop .lanuage-c}
    public abstract boolean isLocalCameraPublishEnabled()                   
    ```

-   configLocalScreenPublish：设置是否允许发布屏幕流。默认为不允许发布屏幕流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_0tx_fdl_tmx .lanuage-c}
    void configLocalScreenPublish(bool enable)                
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|bool|true表示允许发布屏幕流；false表示不允许|

-   isLocalScreenPublishEnabled：查询当前是否允许发布屏幕流，返回true为允许，false为不允许。

    ``` {#codeblock_vz5_ygl_olr .lanuage-c}
    bool isLocalScreenPublishEnabled()                
    ```

-   configLocalAudioPublish：设置是否允许发布音频流。默认为允许发布音频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_c6d_h93_kze .lanuage-c}
    void configLocalAudioPublish(bool enable)        
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|bool|true表示允许；false表示不允许|

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流，返回true为允许，false为不允许。

    ``` {#codeblock_veo_vc4_1er .lanuage-c}
    bool isLocalAudioPublishEnabled()               
    ```

-   configLocalSimulcast：设置是否允许发布次要视频流。默认为允许发布次要视频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_i6i_y4x_bnb .lanuage-c}
    int AliRtcEngine::configLocalSimulcast(bool enabled, AliRtcVideoTrack track)     
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|bool|true表示允许发布次要流，false表示不允许|
    |track|AliRtcVideoTrack|流类型，当前只支持相机流：AliVideoTrackCamera|

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流，返回true为允许，false为不允许。

    ``` {#codeblock_axw_gkp_ho0 .lanuage-c}
    bool isLocalSimulcastEnabled()               
    ```

-   publish：手动发布视频和音频流。

    -   调用publish的实际表现需要结合configLocalCameraPublish、configLocalScreenPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述4个接口的参数，以发布相应的视频和音频流。
    -   发布和停止发布都是调用publish。
    -   如需停止发布，则需要上述4个配置接口的参数都置为false，再调用publish。
    ``` {#codeblock_ufo_v8e_3p9 .lanuage-c}
    void publish(void(*)(void* opaquePtr, int errCode) onResult, void* opaquePtr)             
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |onResult|void\(\)\(void opaquePtr, int errCode\)|当publish执行结束后回调|
    |opaquePtr|void\*|app提供的UserData，在调用onResult时传回app|

    注解：异步接口，通过onResult判断调用结果。lambda表达式转换成onResult。

    ``` {#codeblock_ksi_t7p_4u2 .lanuage-c}
    void (*foo)(void *, int);
    foo = [](void*opaquePtr,  int errCode) {
    ClassA *pThis = (ClassA *)opaquePtr;
    pThis->OutputError("publish result: %d", errCode);
    };
    publish(foo, /*UserData*/);
    ```

-   isAutoSubscribe：查询当前是否为自动订阅模式，返回true为自动订阅，false为手动订阅。

    ``` {#codeblock_d1a_3oc_7zi .lanuage-c}
    bool isAutoSubscribe()                
    ```

-   configRemoteCameraTrack：设置是否订阅远端相机流。默认为订阅大流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_50j_3gy_nb3 .lanuage-c}
    void configRemoteCameraTrack(const AliRtc::String& uid, bool preferMaster, bool enable)               
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符|
    |preferMaster|bool|是否优先订阅大流。preferMaster为YES，则订阅大流；preferMaster为NO，则订阅次小流|
    |enable|bool|true为订阅远端相机流，false为停止订阅远端相机流|

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。默认为不订阅远端屏幕流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_jx3_kb6_0re .lanuage-c}
    void configRemoteAudio(const AliRtc::String& uid, bool enable)             
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符|
    |enable|bool|true为订阅远端屏幕流，false为停止订阅远端屏幕流|

-   configRemoteAudio：设置是否订阅远端音频流。

    **说明：** 默认为订阅远端音频流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_ko1_vly_8fx}
    void configRemoteAudio(const AliRtc::String& uid, bool enable)
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符|
    |enable|bool|true为订阅远端音频流；false为停止订阅远端音频流|

-   subscribe：手动订阅视频和音频流。返回为0时说明接口执行正常，但是否订阅成功还得看回调结果；返回为非0时，说明接口执行异常中断，订阅失败。

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如需停止订阅，则需要上述3个配置接口的参数都置为false，再调用subscribe。
    ``` {#codeblock_vb4_t9s_nlx .lanuage-c}
    void subscribe(const AliRtc::String& uid, void(*)(void* opaquePtr, const AliRtc::String& uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) onResult, void * opaquePtr)                
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符|
    |onResult|void\(\)\(void opaquePtr, const AliRtc::String& uid, AliRtcVideoTrack vt, AliRtcAudioTrack at\)|当subscribe执行结束后回调|
    |opaquePtr|void \*|app提供的UserData，在调用onResult时传回app|

    注解：异步接口，通过onResult判断结果。lambda表达式转换成onResult。

    ``` {#codeblock_wrq_agm_and .lanuage-c}
    void (foo)(void*, const AliRtc::String&, AliRtcAudioTrack, AliRtcVideoTrack);
    foo = [](void *opaquePtr,const AliRtc::String &uid, AliRtcAudioTrack publishedAudioTrack,AliRtcVideoTrack publishedVideoTrack)
    {
    ClassA *pThis = (ClassA*)opaquePtr;
    OutputError("subscribe result: user: %s,audio: %d, video: %d", uid.asCString(),publishedAudioTrack,publishedVideoTrack);
    };
    publish(foo, this);
    ```

-   setVideoProfile：设置视频流参数。可以在joinChannel之前或者之后设置。

    ``` {#codeblock_t88_0ow_w02 .lanuage-c}
    void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)                 
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |profile|AliRtcVideoProfile|视频流参数|
    |track|AliRtcVideoTrack|需要设置的视频流类型|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果canvas中的hWnd为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeFill。
    ``` {#codeblock_2ji_0xd_58p .lanuage-c}
    int setLocalViewConfig(const AliVideoCanvas& canvas, AliRtcVideoTrack track)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |canvas|const AliVideoCanvas&|渲染参数，包含渲染窗口以及渲染方式|
    |track|AliRtcVideoTrack|预览只允许AliVideoTrackCamera|

-   muteLocalCamera：设置是否停止发布本地视频流。不改变当前视频流的采集状态。

    ``` {#codeblock_s0j_hme_z0u .lanuage-c}
    int muteLocalCamera(bool mute, AliRtcVideoTrack track)              
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |mute|bool|true表示停止发布视频流；false表示恢复发布|
    |track|AliRtcVideoTrack|需要改变发布状态的videoTrack类型|

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果canvas为NULL或者其成员渲染视图为NULL，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeAuto。
    ``` {#codeblock_0xi_pdn_6ke .lanuage-c}
    public abstract int setRemoteViewConfig(AliVideoCanvas canvas, String uid, AliRtcVideoTrack track) int setRemoteViewConfig(AliVideoCanvas* canvas, const AliRtc::String& uid, AliRtcVideoTrack track)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |canvas|AliVideoCanvas\*|渲染参数，包含渲染窗口以及渲染方式|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符|
    |track|AliRtcVideoTrack|需要设置的videoTrack类型|

-   getCameraList：获取摄像头列表。

    ``` {#codeblock_slz_jvm_9ce .lanuage-c}
    void getCameraList(AliRtc::StringArray& array)                 
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|摄像头列表|

-   getCurrentCamera：获取当前使用的摄像头名称。

    ``` {#codeblock_p5h_wt5_pcl .lanuage-c}
    AliRtc::String getCurrentCamera()                 
    ```

-   setCurrentCamera：选择摄像头。 必须先调用getCameraList接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_23t_n6f_ji3 .lanuage-c}
    void setCurrentCamera(const AliRtc::String& camera)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |camera|const AliRtc::String&|摄像头名称|

-   isCameraOn：检查摄像头是否打开。 true表示摄像头已打开；false表示摄像头未打开。

    ``` {#codeblock_5ja_fph_86d .lanuage-c}
    bool isCameraOn()                  
    ```

-   setAudioOnlyMode：设置为纯音频模式还是音视频模式，返回0代表设置成功，其他代表设置失败。

    ``` {#codeblock_4j3_0bd_1lq .lanuage-c}
    int setAudioOnlyMode(bool audioOnly)              
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |audioOnly|bool|true表示只有音频发布和订阅；false表示音视频都支持|

    注解：默认为音视频模式（非纯音频），必须在joinChannel之前设置。

-   isAudioOnly：查询当前是否为纯音频模式，返回true为纯音频，false为音视频。

    ``` {#codeblock_u8h_bl2_sv9 .lanuage-c}
    bool isAudioOnly()
    ```

-   muteLocalMic：设置是否停止发布本地音频。返回0表示设置成功，-1表示设置失败。不改变当前音频的采集状态。

    ``` {#codeblock_c0f_cse_f2q .lanuage-c}
    int muteLocalMic(bool mute)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |mute|bool|true表示停止发布本地音频；false表示恢复发布|

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流，返回0表示设置成功，-1表示设置失败。

    ``` {#codeblock_v7k_ajy_8nk .lanuage-c}
    int muteRemoteAudioPlaying(const AliRtc::String& uid, bool mute)                 
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符|
    |mute|bool|true表示停止播放；false表示恢复播放|

-   getAudioCaptures：获取音频采集设备列表。

    ``` {#codeblock_5td_w9x_nmv .lanuage-c}
    void getAudioCaptures(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频采集设备列表|

-   getCurrentAudioCapture：获取当前使用的音频采集设备名称。

    ``` {#codeblock_gbu_muy_nfe .lanuage-c}
    AliRtc::String getCurrentAudioCapture()
    ```

-   setCurrentAudioCapture：选择音频采集设备。必须先调用getAudioCaptures接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_k17_502_7be .lanuage-c}
    void setCurrentAudioCapture(const AliRtc::String& capture)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |capture|String|音频采集设备名称|

-   getAudioRenderers：获取音频播放设备列表。

    ``` {#codeblock_jrw_j5i_qxc .lanuage-c}
    void getAudioRenderers(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|音频播放设备列表|

-   getCurrentAudioRenderer：获取当前使用的音频播放设备。

    ``` {#codeblock_iig_u8u_q0i .lanuage-c}
    AliRtc::String getCurrentAudioRenderer()
    ```

-   setCurrentAudioRenderer：选择音频播放设备。必须先调用getAudioRenderers接口获取设备列表后再调用此接口设置。

    ``` {#codeblock_2xr_wvv_yp3 .lanuage-c}
    void setCurrentAudioRenderer(const AliRtc::String &renderer)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |renderer|String|音频播放设备名称|

-   SetAudioVolume：设置系统音量。

    ``` {#codeblock_ng1_cfv_c4m .lanuage-c}
    int SetAudioVolume(int audio_device, int volume)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |audio\_device|int|音频设备类型，1：麦克风, 3：扬声器/耳机|
    |volume|int|音量大小范围0~100|

-   GetAudioVolume：获取系统音量。返回音量大小范围0~100。

    ``` {#codeblock_uyr_kcm_acw .lanuage-c}
    int GetAudioVolume(int audio_device)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |audio\_device|int|音频设备类型，1：麦克风, 3：扬声器/耳机|

-   startAudioCapture：开启音频采集。您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ``` {#codeblock_pbs_bnz_m87 .lanuage-c}
    void startAudioCapture() = 0;
    ```

-   stopAudioCapture：关闭音频采集。您可以控制关闭音频采集。

    ``` {#codeblock_jyg_7bb_3dd .lanuage-c}
    void stopAudioCapture();
    ```

-   startAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ``` {#codeblock_sq0_fkx_mkx .lanuage-c}
     void startAudioPlayer();
    ```

-   stopAudioPlayer：关闭音频播放。您可以控制关闭音频播放。

    ``` {#codeblock_byl_ee2_fz7 .lanuage-c}
    void stopAudioPlayer();
    ```

-   startPreview：开始本地预览。可以在joinChannel之前就开启预览。

    ``` {#codeblock_lij_j1x_dsk .lanuage-c}
    int startPreview()              
    ```

-   stopPreview：停止本地预览。

    ``` {#codeblock_hvh_1ud_yn3 .lanuage-c}
    int stopPreview()                  
    ```

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ``` {#codeblock_5yv_l2j_stf .lanuage-c}
    void getOnlineRemoteUsers(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |array|AliRtc::StringArray&|用户列表，保存的是用户ID|

-   getUserInfo：查询远端用户信息。返回0表示成功获取，其他表示失败。

    ``` {#codeblock_t2q_7bd_8yi .lanuage-c}
    int getUserInfo(const AliRtc::String& uid, AliRtc::Dictionary& dict)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符。|
    |dict|AliRtc::Dictionary&|用于存放用户数据|

    dict当中key值包括：userID、isOnline、sessionID、callID、displayName、hasAudio,hasCameraMaster、hasCameraSlave、hasScreenSharing、requestAudio,requestCameraMaster、requestCameraSlave、requestScreenSharing、preferCameraMaster subScribedAudio、subScribedCameraMaster,subScribedCamearSlave、subScribedScreenSharing、hasCameraView、hasScreenView、muteAudioPlaying

-   isUserOnline：查询用户是否在线。返回true表示在线，false表示不在线。

    ``` {#codeblock_bob_wcu_etl .lanuage-c}
    bool isUserOnline(const AliRtc::String& uid)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符。|

-   getMediaInfoWithKeys：获取媒体信息。 返回key-value格式的json字符串。

    ``` {#codeblock_1wq_j8s_b15 .lanuage-c}
    AliRtc::String getMediaInfoWithKeys(const AliRtc::String& call_id, AliRtcVideoTrack track,const AliRtc::String key_list[],int length) = 0;
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |call\_id|AliRtc::String|需要查询的userId|
    |track|AliRtcVideoTrack|需要查询的媒体流类型|
    |length|int|数组长度|
    |key\_list|AliRtc::String|查询key值数组|

-   createMediaDeviceTestInterface：创建音视频设备测试实例。

    ``` {#codeblock_u5v_wsb_qed .lanuage-c}
    AliMediaDeviceTestInterface * createMediaDeviceTestInterface(AliMediaDeviceTestEventListener * pMediaDeviceEventListener)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |pMediaDeviceEventListener|AliMediaDeviceTestEventListener \*|音频设备测试事件监听器|

-   setLogLevel：设置log级别。

    ``` {#codeblock_uif_697_8f8 .lanuage-c}
    void setLogLevel(AliRtcLogLevel logLevel)        
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |logLevel|AliRtcLogLevel|log级别|

-   getSdkVersion：获取sdk版本号。

    ``` {#codeblock_o66_12l_sbd .lanuage-c}
    const char* getSdkVersion()                 
    ```


