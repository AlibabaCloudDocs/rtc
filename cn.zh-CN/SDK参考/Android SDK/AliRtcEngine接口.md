# AliRtcEngine接口 {#reference13896 .reference}

本文档为您介绍了Android SDK的AliRtcEngine接口详情。

## 目录 {#section_r7c_d64_vsh .section}

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[setH5CompatibleMode](#)|设置H5兼容模式。|1.1|
|[getH5CompatibleMode](#)|检查当前是否兼容H5。|1.1|
|[getInstance](#)|创建AliRTCEngine实例（同一时间只会存在一个实例），只能在主线程调用。|1.1|
|[setRtcEngineEventListener](#)|设置本地用户行为的回调事件的监听。|1.1|
|[setRtcEngineNotify](#)|设置远端用户行为的通知事件的监听。|1.1|
|[destroy](#)|销毁引擎。|1.1|

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

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setVideoProfile](#)|设置视频流参数。|1.1|
|[getVideoProfile](#)|查询当前视频流参数。|1.1|
|[setLocalViewConfig](#)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[muteLocalCamera](#)|设置是否停止发布本地视频流。|1.1|
|[setRemoteViewConfig](#)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[switchCamera](#)|切换前后摄像头。|1.1|
|[getCurrentCameraType](#)|获取当前摄像头类型。|1.1|
|[setPreCameraType](#)|预设值摄像头方向。|1.1|
|[getPreCameraType](#)|获取预设值摄像头方向。|1.1|
|[setCameraZoom](#)|设置摄像头参数。|1.1|
|[isCameraOn](#)|检查摄像头是否打开。|1.1|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[setAudioOnlyMode](#)|设置纯音频模式还是音视频模式。|1.1|
|[isAudioOnly](#)|查询当前是否为纯音频模式。|1.1|
|[muteLocalMic](#)|设置是否停止发布本地音频。|1.1|
|[muteRemoteAudioPlaying](#)|设置是否停止播放远端音频流。|1.1|
|[enableSpeakerphone](#)|切换听筒、扬声器输出。|1.1|
|[isSpeakerOn](#)|查询是否开启扬声器。|1.1|
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
|[isUserOnline](#)|判断用户是否在线。|1.1|
|[getMediaInfoWithUserId](#)|获取媒体流信息。|1.9|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[setLogLevel](#)|设置log级别。|1.1|
|[getSdkVersion](#)|获取SDK版本号。|1.1|

## 接口详情 {#section_8vc_ul5_3s7 .section}

-   setH5CompatibleMode：设置是否兼容H5，当前版本不支持在创建AliRtcEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此方法，默认不兼容H5。

    ``` {#codeblock_bsk_zsx_4es .language-java}
    AliRtcEngine.setH5CompatibleMode(int enable)           
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|int|0表示不兼容H5，1表示兼容H5。|

-   getH5CompatibleMode：检查当前是否兼容H5，返回1表示兼容，0表示不兼容。

    ``` {#codeblock_2ui_2o3_vhc .language-java}
    public static int getH5CompatibleMode()                 
    ```

-   getInstance：创建AliRTCEngine实例（同一时间只会存在一个实例），只能在主线程调用。

    ``` {#codeblock_wa6_yqy_5sv .language-java}
    public static AliRtcEngineImpl getInstance(Context context)          
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |context|Context|上下文。|

-   setRtcEngineEventListener：设置本地用户行为的回调事件的监听。

    ``` {#codeblock_hzr_4f2_qrr .language-java}
    public abstract void setRtcEngineEventListener(AliRtcEngineEventListener listener)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |listener|[AliRtcEngineEventListener](cn.zh-CN/SDK参考/Android SDK/回调及监听.md#)|接收回调事件的监听器。|

-   setRtcEngineNotify：设置远端用户行为的通知事件的监听。

    ``` {#codeblock_7vq_kq9_h7n .language-java}
    public abstract void setRtcEngineNotify(AliRtcEngineNotify engineNotify)               
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |engineNotify|[AliRtcEngineNotify](cn.zh-CN/SDK参考/Android SDK/回调及监听.md#)|接收通知的监听器。|

-   destroy：销毁引擎，和leaveChannel中两者调用一个即可。

    离开频道时，AliRtcEngine实例会被销毁，如需继续joinChannel等操作，需要先重新调用getInstance初始化AliRtcEngine实例。

    ``` {#codeblock_c0u_ib9_15u .language-java}
    public abstract void destroy();                  
    ```

-   setAutoPublish：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，必须在joinChannel之前设置。

    参数：

    |参数|类型|说明|
    |--|--|--|
    |autoPub|boolean|true表示自动发布；false表示手动发布。|
    |autoSub|boolean|true表示自动订阅；false表示手动订阅。|

-   joinChannel：加入频道。

    加入频道成功后，如果中途需要加入其他频道，必须先调用leaveChannel离开当前频道，如果加入频道失败，需要重试时，无需先调用leaveChannel。

    ``` {#codeblock_aqp_zaz_r95 .language-java}
    public abstract void joinChannel(AliRtcAuthInfo authInfo, String userName)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|鉴权信息，从App Server下发，APP Server可通过API获取。|
    |userName|String|用户的显示名称，不是uid。|

-   leaveChannel：离开频道。

    离开频道时，AliRtcEngine实例会被销毁，如需继续joinChannel等操作，需要先重新调用getInstance初始化AliRtcEngine实例。

    -   对于版本号大于1.7的sdk，请调用如下接口。

        ``` {#codeblock_5qp_zq1_rm3 .language-java}
        public abstract void leaveChannel()                          
        ```

    -   对于版本号小于等于1.7的sdk，请增加timeout参数，一般建议设置为1000，表示该接口的调用超时时间为1秒。

        ``` {#codeblock_fs2_ho0_gdh .language-java}
        public abstract void leaveChannel(long timeout)                          
        ```

-   isInCall：检查当前是否在频道中，返回true表示在频道中，false表示不在频道中。

    ``` {#codeblock_f7k_b72_8eo .language-java}
    public abstract boolean isInCall()                  
    ```

-   isAutoPublish：查询当前是否为自动发布模式，返回true为自动发布，false为手动发布。

    ``` {#codeblock_51p_19d_1p1 .language-java}
    public abstract boolean isAutoPublish()                  
    ```

-   configLocalCameraPublish：设置是否允许发布相机流。默认为允许发布相机流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_ovs_gl4_l9n .language-java}
    public abstract void configLocalCameraPublish(boolean enable)                
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true为允许发布相机流；false表示不允许。|

-   isLocalCameraPublishEnabled：查询当前是否允许发布相机流，返回true为允许，false为不允许。

    ``` {#codeblock_4fk_hvt_mhx .language-java}
    public abstract boolean isLocalCameraPublishEnabled()                   
    ```

-   configLocalScreenPublish：设置是否允许发布屏幕流。默认为不允许发布屏幕流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_tvx_p3x_wv6 .language-java}
    public abstract void configLocalScreenPublish(boolean enable)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true表示允许发布屏幕流；false表示不允许。|

-   isLocalScreenPublishEnabled：查询当前是否允许发布屏幕流，返回true为允许，false为不允许。

    ``` {#codeblock_9z2_8pn_s2l .language-java}
    public abstract boolean isLocalScreenPublishEnabled()                   
    ```

-   configLocalAudioPublish：设置是否允许发布音频流。默认为允许发布音频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_m20_c65_ybh .language-java}
    public abstract void configLocalAudioPublish(boolean enable)          
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true表示允许；false表示不允许。|

-   isLocalAudioPublishEnabled：查询当前是否允许发布音频流，返回true为允许，false为不允许。

    ``` {#codeblock_25q_gj9_8u4 .language-java}
    public abstract boolean isLocalAudioPublishEnabled()                
    ```

-   configLocalSimulcast：设置是否允许发布次要视频流。默认为允许发布次要视频流，手动发布时，需要调用publish才能生效。

    ``` {#codeblock_23j_712_06b .language-java}
    public abstract int configLocalSimulcast(boolean enable, AliRtcVideoTrack track)        
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true表示允许发布次要流，false表示不允许。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|流类型，当前只支持相机流：AliVideoTrackCamera。|

-   isLocalSimulcastEnabled：查询当前是否允许发布次要视频流，返回true为允许，false为不允许。

    ``` {#codeblock_rge_5ah_elc .language-java}
    public abstract boolean isLocalSimulcastEnabled()                  
    ```

-   publish：手动发布视频和音频流。

    -   调用publish的实际表现需要结合configLocalCameraPublish、configLocalScreenPublish、configLocalAudioPublish、configLocalSimulcast等接口才能确定。
    -   根据您的具体业务需求配置上述4个接口的参数，以发布相应的视频和音频流。
    -   发布和停止发布都是调用publish。
    -   如需停止发布，则需要上述4个配置接口的参数都置为false，再调用publish。
    ``` {#codeblock_9o0_32n_13f .language-java}
    public abstract void publish()                  
    ```

-   isAutoSubscribe：查询当前是否为自动订阅模式，返回true为自动订阅，false为手动订阅。

    ``` {#codeblock_4ho_5dj_k0k .language-java}
    public abstract boolean isAutoSubscribe()                 
    ```

-   configRemoteCameraTrack：设置是否订阅远端相机流。默认为订阅大流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_2j9_ehu_3hz .language-java}
    public abstract void configRemoteCameraTrack(String uid, boolean master, boolean enable)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|
    |master|boolean|是否优先订阅大流。true为订阅大流；false为订阅次小流。|
    |enable|boolean|true为订阅远端相机流，false为停止订阅远端相机流。|

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。默认为不订阅远端屏幕流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_vuk_1mx_gk1 .language-java}
    public abstract void configRemoteScreenTrack(String uid, boolean enable)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|
    |enable|boolean|true为订阅远端屏幕流，false为停止订阅远端屏幕流。|

-   configRemoteAudio：设置是否订阅远端音频流。默认为订阅远端音频流，手动订阅时，需要调用subscribe才能生效。

    ``` {#codeblock_9na_n05_tjx .language-java}
    public abstract void configRemoteAudio(String uid, boolean enable)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|
    |enable|boolean|true为订阅远端音频流，false为停止订阅远端音频流。|

-   subscribe：手动订阅视频和音频流。返回为0时说明接口执行正常，但是否订阅成功还得看回调结果；返回为非0时，说明接口执行异常中断，订阅失败。

    -   调用subscribe的实际表现需要结合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio等接口才能确定。
    -   根据您的具体业务需求配置上述3个接口的参数，以订阅相应的视频和音频流。
    -   订阅和停止订阅都是调用subscribe。
    -   如需停止订阅，则需要上述3个配置接口的参数都置为false，再调用subscribe。
    ``` {#codeblock_emn_p6l_vk9 .language-java}
    public abstract int subscribe(String uid)                 
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|

-   setVideoProfile：设置视频流参数。

    ``` {#codeblock_hof_y19_oof .language-java}
    public abstract void setVideoProfile(AliRtcVideoProfile profile, AliRtcVideoTrack track)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |profile|[AliRtcVideoProfile](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|视频流参数。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|需要设置的视频流类型。|

-   getVideoProfile：查询当前视频流参数。

    ``` {#codeblock_xkj_k7v_147 .language-java}
    public abstract AliRtcVideoProfile getVideoProfile(AliRtcVideoTrack track)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|需要查询的视频流类型。|

    返回值：

    |返回值|描述|
    |---|--|
    |[AliRtcVideoProfile](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|视频流规格|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果viewConfig为NULL或者其成员渲染视图为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持viewConfig中其他成员变量不变，仅修改renderMode。
    -   viewConfig中渲染方式默认为AliRtcRenderModeAuto。
    ``` {#codeblock_fyl_zon_s1l .language-java}
    public abstract int setLocalViewConfig(AliVideoCanvas viewConfig, AliRtcVideoTrack track)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |viewConfig|[AliVideoCanvas](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|预览只允许AliVideoTrackCamera。|

-   muteLocalCamera：设置是否停止发布本地视频流。不改变当前视频流的采集状态。

    ``` {#codeblock_wra_684_jip .language-java}
    public abstract int muteLocalCamera(boolean mute, AliRtcVideoTrack track)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |mute|boolean|true表示停止发布视频流；false表示恢复发布。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|需要改变发布状态的videoTrack类型。|

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    -   支持joinChannel之前和之后切换窗口。如果canvas为NULL或者其成员渲染视图为NULL，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliRtcRenderModeAuto。
    ``` {#codeblock_deb_bnq_znl .language-java}
    public abstract int setRemoteViewConfig(AliVideoCanvas canvas, String uid, AliRtcVideoTrack track)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |canvas|[AliVideoCanvas](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|String|用户ID，从App server分配的唯一标示符。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|需要设置的videoTrack类型。|

-   switchCamera：切换前后摄像头，返回0为切换成功，其他为切换失败。

    ``` {#codeblock_i5a_3gv_ykq .language-java}
    public abstract int switchCamera()                  
    ```

-   getCurrentCameraType：获取当前摄像头类型，返回摄像头的类型。

    ``` {#codeblock_bz7_6fm_44x .language-java}
    public abstract AliRTCCameraType getCurrentCameraType()                   
    ```

    |返回值|描述|
    |---|--|
    |[AliRTCCameraType](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|摄像头类型|

-   setPreCameraType：预设值摄像头方向。

    ``` {#codeblock_wii_j9h_2at .language-java}
    public abstract void setPreCameraType(int faceTo)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |faceTo|int|0表示后置，1表示前置。|

-   getPreCameraType：获取预设值摄像头方向。返回0为后置摄像头，1为前置摄像头。

    ``` {#codeblock_lxs_8ux_8jd .language-java}
    public abstract int getPreCameraType()                  
    ```

-   setCameraZoom：设置摄像头参数。返回0表示设置成功，其他表示设置失败。

    ``` {#codeblock_1vi_afp_xcn .language-java}
    public abstract int setCameraZoom(float zoom, boolean flash, boolean autoFocus)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |zoom|float|zoom变焦的级别。|
    |flash|boolean|是否打开闪光灯。|
    |autoFocus|boolean|是否打开自动对焦。|

-   isCameraOn：检查摄像头是否打开。返回true表示摄像头已打开，false表示摄像头未打开。

    ``` {#codeblock_814_rwa_s0j .language-java}
    public abstract boolean isCameraOn()                   
    ```

-   setAudioOnlyMode：设置纯音频模式还是音视频模式。返回0代表设置成功，其他代表设置失败。默认为音视频模式（非纯音频），必须在joinChannel之前设置。

    ``` {#codeblock_pf1_8nl_8rt .language-java}
    public abstract int setAudioOnlyMode(boolean audioOnly)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |audioOnly|boolean|true表示只有音频发布和订阅；false表示音视频都支持。|

-   isAudioOnly：查询当前是否为纯音频模式，返回true为纯音频，false为音视频。

    ``` {#codeblock_13q_i9c_aab .language-java}
    public abstract boolean isAudioOnly()                 
    ```

-   muteLocalMic：设置是否停止发布本地音频。返回0表示设置成功，-1表示设置失败。不改变当前音频的采集状态。

    ``` {#codeblock_62r_4i6_2kx .language-java}
    public abstract int muteLocalMic(boolean mute)                    
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |mute|boolean|true表示停止发布本地音频；false表示恢复发布。|

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流，返回0表示设置成功，-1表示设置失败。

    ``` {#codeblock_au6_k8p_fmu .language-java}
    public abstract int muteRemoteAudioPlaying(String uid, boolean mute)                   
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|
    |mute|boolean|true表示停止播放；false表示恢复播放。|

-   enableSpeakerphone：切换听筒、扬声器输出。

    ``` {#codeblock_xwi_8w4_phz .language-java}
    public abstract int enableSpeakerphone(boolean enable)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |enable|boolean|true为扬声器模式；false为听筒模式。|

-   isSpeakerOn：查询是否开启扬声器。返回true表示已开启扬声器，false表示未开启扬声器。

    ``` {#codeblock_ekf_een_vrq .language-java}
    public abstract boolean isSpeakerOn()                  
    ```

-   startAudioCapture：开启音频采集。您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ``` {#codeblock_5np_fsr_oxs .language-java}
    public int startAudioCapture();
    ```

-   stopAudioCapture：关闭音频采集。您可以控制关闭音频采集。

    ``` {#codeblock_gxr_fbx_jyi .language-java}
    public int stopAudioCapture();
    ```

-   startAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ``` {#codeblock_iu8_9t7_2r2 .language-java}
    public int startAudioPlayer();
    ```

-   stopAudioPlayer：关闭音频播放。您可以控制关闭音频播放。

    ``` {#codeblock_qpo_sd7_3nf .language-java}
    public int stopAudioPlayer();
    ```

-   startPreview：开始本地预览。可以在joinChannel之前就开启预览。

    ``` {#codeblock_hri_c2y_i4q .language-java}
    public abstract int startPreview()                  
    ```

-   stopPreview：停止本地预览。

    ``` {#codeblock_rgt_sdx_hd6 .language-java}
    public abstract int stopPreview()                   
    ```

-   getOnlineRemoteUsers：获取远端在线用户列表，返回用户ID列表。

    ``` {#codeblock_p47_4sy_lag .language-java}
    public abstract String[] getOnlineRemoteUsers()                
    ```

-   getUserInfo：查询远端用户信息。

    ``` {#codeblock_sk6_6l4_m0q .language-java}
    public abstract AliRtcRemoteUserInfo getUserInfo(String uid)                  
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|

    返回值：

    |返回值|描述|
    |[AliRtcRemoteUserInfo](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|远程用户信息|

-   isUserOnline：查询用户是否在线，返回true表示在线，false表示不在线。

    ``` {#codeblock_80s_h22_qms .language-java}
    public abstract boolean isUserOnline(String uid)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server分配的唯一标示符。|

-   getMediaInfoWithUserId：获取媒体流信息。

    ``` {#codeblock_3yr_7ar_wu6 .language-java}
    public String getMediaInfoWithUserId(String userId, AliRtcVideoTrack track, String[] keys);
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |userId|String|用户的userId。|
    |track|[AliRtcVideoTrack](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|需要查询的媒体流类型。|
    |keys|String\[\]|查询key值数组。|

-   setLogLevel：设置log级别。

    ``` {#codeblock_lcl_ysv_nit .language-java}
    public abstract void setLogLevel(AliRtcLogLevel logLevel)         
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |logLevel|[AliRtcLogLevel](cn.zh-CN/SDK参考/Android SDK/数据类型.md#)|log级别。|

-   getSdkVersion：获取SDK版本号。

    ``` {#codeblock_wms_y5j_6tk .language-java}
    public abstract String getSdkVersion()                   
    ```


