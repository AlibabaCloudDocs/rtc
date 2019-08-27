# Android {#task_1180891 .task}

阿里云音视频通信的基本功能包含初始化SDK、加入频道、本地发布和订阅远端、离开频道等。当您成功初始化SDK，您可以进行本地预览视频功能，进行简单的预览和测试，您也可以设置手动或者自动模式。

在实现基本功能前，请您确保下载最新SDK，请参见[SDK下载](../../../../cn.zh-CN/快速入门/SDK下载.md#)。

**说明：** 本文中的实现方法为主要功能方法，仅供参考，您可以根据您的业务需求进行实际开发。

1.  初始化SDK。 

    在app/src/main/java/come.xample.myapplication/MainActivity文件中，您需要调用onCreate方法创建AliRtcEngine实例，并注册回调。相关回调有AliRtcEngineEventListener和AliRtcEngineNotify。具体回调及监听请参见[回调及监听](../../../../cn.zh-CN/API参考/Android SDK/接口说明/回调及监听.md#)。

    ``` {#codeblock_2b8_1ou_4ge .language-java}
    mEngine = AliRtcEngine.getInstance(getApplicationContext());
    mEngine.setRtcEngineEventListener(mEventListener);
    mEngine.setRtcEngineNotify(mEngineNotify);     
    ```

    **说明：** 只能在主线程调用，暂不支持多实例。

    mEventListener：用户操作回调监听（回调接口都在子线程）。

    ``` {#codeblock_lbf_num_3rm .language-java}
    private AliRtcEngineEventListener mEventListener = new AliRtcEngineEventListener() {
    };           
    ```

    mEngineNotify：SDK事件通知（回调接口都在子线程）。

    ``` {#codeblock_qx9_wpl_hlt .language-java}
    private AliRtcEngineNotify mEngineNotify = new AliRtcEngineNotify() {    
    };           
    ```

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas进行本地预览视频。 

        ``` {#codeblock_df0_slj_a2x .language-java}
        //创建canvas，Canvas为SophonSurfaceView或者它的子类
        AliRtcEngine.AliVideoCanvas canvas = new AliRtcEngine.AliVideoCanvas();
        //SDK内部提供进行播放的view
        SophonSurfaceView surfaceView = new SophonSurfaceView(this);
        surfaceView.setZOrderOnTop(true);
        surfaceView.setZOrderMediaOverlay(true);
        mSurfaceContainer.addView(surfaceView,new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,ViewGroup.LayoutParams.MATCH_PARENT));
        /* 预览窗口的view */
        canvas.view = surfaceView; 
        //renderMode提供四种模式：Auto、Stretch、Fill、Crop，建议使用Auto模式。
        canvas.renderMode = AliRtcRenderModeAuto;
        mEngine.setLocalViewConfig(canvas, AliRtcVideoTrackCamera);
        mEngine.startPreview();
        //mSurfaceContainer为包裹mCanvas的父view
        mSurfaceContainer.getChildAt(0).setVisibility(View.VISIBLE); 
        ```

        建议您把mAliVideoCanvas之上的所有view单独放在一个透明的父布局，因为surfaceview的z-order问题可能会挡住contronlview的显示。

        mirrorMode提供三种模式：AliRtcRenderMirrorModeOnlyFront、AliRtcRenderMirrorModeAllEnabled、AliRtcRenderMirrorModeAllDisable。

    2.  设置自动或者手动模式。 

        **说明：** 阿里云音视频通信Android端默认实现自动发布和订阅，您也可以通过代码手动发布和订阅。

        -   自动Publish模式： 如果您打开自动Publish模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动Publish模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动Subscribe模式： 如果您打开自动Subscribe模式，加入频道之后，SDK将会自动订阅当前频道内其他用户的音视频流；如果关闭自动Subscribe模式，则需要您调用subscribe接口之后才会订阅其他用户的音视频流。
        ``` {#codeblock_5ok_l1v_dhu .language-java}
        /**
        *设置自动发布和订阅，只能在joinChannel之前设置
        *@param autoPub    true表示自动发布；false表示手动发布
        *@param autoSub    true表示自动订阅；false表示手动订阅
        */
        mEngine.setAutoPublish(true, true);           
        ```

2.  加入频道。 

    **说明：** AliRtcAuthInfo的各项参数均需要App Server通过API来获取，然后App Server下发至客户端，客户端将各项参数赋值后，就可以加入频道。

    -   name：无需APP Server下发。
    -   channelID 、userID、name命名要求：字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节，非法命名系统将拒绝提供服务。
    ``` {#codeblock_li5_4yx_lo2 .language-java}
    AliRtcAuthInfo userInfo = new AliRtcAuthInfo();
    userInfo.setConferenceId(/* 用户的channelID */);
    userInfo.setAppid(/* 用户的appid */);
    userInfo.setNonce(/* 用户的nonce */);
    userInfo.setTimestamp(/* 用户的timestamp */);
    userInfo.setUserId(/* 用户的userid */);
    userInfo.setGslb(/* 用户的gslb */);
    userInfo.setToken(/* 用户的token */);
    if(mEngine != null) {    
    mEngine.joinChannel(userInfo, /* name */);
    }
    ```

3.  发布或取消发布本地流。 

    发布本地流。

    -   自动pub模式下：加入频道成功后，即可发布本地流，无需再次调用publish接口。
    -   非自动pub模式下：加入成功后，可通过以下接口发布本地流。
    如果publish过程中需要变更配置或者停止publish，需要按如下流程先重新设置配置参数，然后再调用publish接口。

    ``` {#codeblock_n57_6ud_2t8 .language-java}
    //发布本地流设置
    //true表示允许发布音频流，false表示不允许
    mEngine.configLocalAudioPublish(true);
    //true表示允许发布相机流，false表示不允许
    mEngine.configLocalCameraPublish(true);
    //true表示允许发布屏幕流，false表示不允许
    mEngine.configLocalScreenPublish(true);
    //true表示允许发布次要视频流；false表示不允许
    mEngine.configLocalSimulcast(true, AliRtcEngine.AliRtcVideoTrack.AliRtcVideoTrackCamera);
    mEngine.publish();
    ```

    取消发布本地流。

    ``` {#codeblock_iri_faa_zo2 .language-java}
    mEngine.configLocalAudioPublish(false);
    mEngine.configLocalCameraPublish(false);
    mEngine.configLocalScreenPublish(false);
    mEngine.configLocalSimulcast(false, AliRtcEngine.AliRtcVideoTrack.AliRtcVideoTrackCamera);
    mEngine.publish();
    ```

    发布和取消发布本地流回调代码如下所示。

    ``` {#codeblock_qwo_62h_oa5 .language-java}
    private AliRtcEngineEventListener mEventListener = new AliRtcEngineEventListener() {
    @Override
    public void onPublishResult(int result, String publishId) {
    //发布本地流回调
    }
    @Override
    public void onUnpublishResult(int result) {
    //取消发布本地流回调
    }
    }
    ```

4.  订阅或取消订阅远程流。 

    订阅远程流。

    -   自动sub模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
    -   非自动sub模式下：加入频道成功后，可通过以下接口订阅远端流。
    如果subscribe过程中需要变更配置或者停止subscribe，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

    ``` {#codeblock_doe_w89_xls .language-java}
    // 订阅远端音频流
    mEngine.configRemoteAudio(/* remoteUserID */, true);
    // 订阅远端屏幕流
    mEngine.configRemoteScreenTrack(/* remoteUserID */, true);
    // 订阅远端相机流
    mEngine.configRemoteCameraTrack(/* remoteUserID */, true, true);
    // 订阅远端用户ID
    mEngine.subscribe(/* remoteUserID */);
    ```

    取消订阅远程流。

    ``` {#codeblock_qal_v1o_773 .language-java}
    mEngine.configRemoteAudio(/* remoteUserID */, false);
    mEngine.configRemoteScreenTrack(/* remoteUserID */, false);
    mEngine.configRemoteCameraTrack(/* remoteUserID */, true, false);
    mEngine.subscribe(/* remoteUserID */);
    ```

    远程流回调代码如下所示。

    ``` {#codeblock_2ak_k10_zff .language-java}
    private AliRtcEngineNotify mEngineNotify = new AliRtcEngineNotify() {
    @Override
    public void onRemoteUserUnPublish(AliRtcEngine rtcEngine, String userId) {
    //远端用户停止发布通知，处于OB（observer）状态
    }
    @Override
    public void onRemoteUserOnLineNotify(String uid) {
    //远端用户上线通知
    }
    @Override
    public void onRemoteUserOffLineNotify(String uid) {
    //远端用户下线通知
    }
    @Override
    public void onRemoteTrackAvailableNotify(String uid,AliRtcEngine.AliRtcAudioTrackaudioTrack,AliRtcEngine.AliRtcVideoTrack videoTrack) {
    //远端用户发布音视频流变化通知
    }
    public void onSubscribeResult(String uid,int result,AliRtcVideoTrack videoTrack,AliRtcAudioTrack audioTrack) {
    //订阅流回调，可以做UI及数据的更新
    }
    }
    ```

5.  离开频道。 

    -   对于版本号大于1.7的SDK，请调用如下接口。

        ``` {#codeblock_4w2_cvb_meg .language-java}
        mEngine.leaveChannel();
        ```

    -   对于版本号小于等于1.7的SDK，请增加timeout参数，一般建议设置为1000，表示该接口的调用超时时间为1秒，建议在Activity的onDestroy中调用。调用leavechannel后请不要再操作AliRtcEngine实例。

        ``` {#codeblock_lwo_9vs_50d .language-java}
        mEngine.leaveChannel(1000);
        ```

    您可以下载示例代码，快速跑通Demo，实现频道内和其他用户进行实时音视频通话，详情请参见[Android Demo](../../../../cn.zh-CN/Demo/Android Demo.md#)。


