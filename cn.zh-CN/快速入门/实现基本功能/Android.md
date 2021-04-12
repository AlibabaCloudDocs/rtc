---
keyword: [基本功能, Android]
---

# Android

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、订阅远端和离开频道等。通过阅读本文，您可以了解阿里云RTC的基本功能。

-   您已下载并集成最新版本的SDK。具体操作，请参见[Android端集成SDK](/cn.zh-CN/快速入门/集成客户端SDK/Android.md)。
-   您已获取加入频道必须的频道鉴权令牌（Token）。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

**说明：** 本文中的实现方法仅供参考，您可以根据实际业务需求进行开发。

1.  初始化SDK。

    您需要创建AliRtcEngine实例，并注册回调。相关回调有AliRtcEngineEventListener和AliRtcEngineNotify，具体回调接口请参见[回调及监听](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)。

    ```
    mEngine = AliRtcEngine.getInstance(getApplicationContext());
    mEngine.setRtcEngineEventListener(mEventListener);
    mEngine.setRtcEngineNotify(mEngineNotify);     
    ```

    **说明：** 该接口只能在主线程调用，目前暂不支持多实例。

    mEventListener：操作回调监听（回调接口都在子线程）。

    ```
    private AliRtcEngineEventListener mEventListener = new AliRtcEngineEventListener() {
    };           
    ```

    mEngineNotify：SDK事件通知（回调接口都在子线程）。

    ```
    private AliRtcEngineNotify mEngineNotify = new AliRtcEngineNotify() {    
    };           
    ```

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas布局进行本地预览视频。

        ```
        //创建canvas，canvas为SophonSurfaceView或者它的子类。
        AliRtcEngine.AliVideoCanvas canvas = new AliRtcEngine.AliVideoCanvas();
        //SDK内部提供进行播放的视图。
        SophonSurfaceView surfaceView = new SophonSurfaceView(this);
        surfaceView.setZOrderOnTop(true);
        surfaceView.setZOrderMediaOverlay(true);
        mSurfaceContainer.addView(surfaceView,new ViewGroup.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,ViewGroup.LayoutParams.MATCH_PARENT));
        /* 预览窗口的视图 */
        canvas.view = surfaceView; 
        canvas.renderMode = AliRtcRenderModeAuto;
        mEngine.setLocalViewConfig(canvas, AliRtcVideoTrackCamera);
        mEngine.startPreview();
        //mSurfaceContainer为包裹mCanvas的父视图。
        mSurfaceContainer.getChildAt(0).setVisibility(View.VISIBLE); 
        ```

        建议您把mAliVideoCanvas之上的所有视图单独放在一个透明的父布局，因为surfaceview的z-order问题可能会挡住contronlview的显示。

        **说明：**

        AliRtcRenderMirrorMode提供三种镜像模式。

        -   AliRtcRenderMirrorModeOnlyFront：只有前置摄像头预览镜像，其余不镜像。
        -   AliRtcRenderMirrorModeAllEnabled：全部镜像。
        -   AliRtcRenderMirrorModeAllDisable：全部不镜像。
        AliRtcRenderMode渲染模式有四种模式。

        -   AliRtcRenderModeAuto（推荐）：自动。
        -   AliRtcRenderModeStretch：拉伸填充视图，不保持视频比例。
        -   AliRtcRenderModeFill：在保持视频宽高比的同时缩放，填充黑边。
        -   AliRtcRenderModeClip：在保持视频宽高比的同时缩放，并裁剪以适合视图。
    2.  设置自动或者手动模式。

        **说明：** 默认实现自动发布和订阅，您也可以通过代码手动发布和订阅。

        -   自动发布模式： 如果您打开自动发布模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动发布模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动订阅模式： 如果您打开自动订阅模式，加入频道之后，SDK将会自动订阅当前频道内其他人的音视频流；如果关闭自动订阅模式，则需要您调用subscribe接口之后才会订阅其他人的音视频流。
        ```
        /**
        *设置自动发布和订阅，只能在加入频道之前设置。
        *@param autoPub：是否自动发布。取值：true|false。
        *@param autoSub：是否自动订阅。取值：true|false。
        */
        mEngine.setAutoPublish(true, true);           
        ```

2.  加入频道。

    ```
    AliRtcAuthInfo userInfo = new AliRtcAuthInfo();
    userInfo.setConferenceId(/* 频道ID */);
    userInfo.setAppid(/* 应用ID */);
    userInfo.setNonce(/* 随机码 */);
    userInfo.setTimestamp(/* 时间戳*/);
    userInfo.setUserId(/* 用户ID */);
    userInfo.setGslb(/* GSLB地址*/);
    userInfo.setToken(/*鉴权令牌Token*/);
    if(mEngine != null) {    
    mEngine.joinChannel(userInfo, /* 用户显示名称 */);
    }
    ```

    |参数|描述|
    |--|--|
    |AppID|应用ID，在控制台**应用管理**页面创建和查看。|
    |ChannelId|频道ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。|
    |UserId|用户ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。 **说明：** 同一个用户ID在其他端登录，先入会的端会被后入会的端踢出频道。 |
    |Nonce|随机码。以前缀AK-开头，由大小写字母、数字组成，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |TimeStamp|过期时间戳。可以选择12小时、24小时、3天和7天，代表令牌有效时间。|
    |Token|频道鉴权令牌，计算方法：`token = sha256(appId + appKey + channelId + userId + nonce + timestamp)`。|
    |GSLB|服务地址，该参数是数组类型，当前请使用：`["https://rgslb.rtc.aliyuncs.com"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

3.  发布或取消发布本地流。

    -   发布本地流

        -   自动发布模式下：加入频道成功后，即可发布本地流，无需再次调用publish接口。
        -   手动发布模式下：加入频道成功后，可通过以下接口发布本地流。
        如果发布过程中需要变更配置或者停止发布，需要按如下流程先重新设置配置参数，然后再调用publish接口。

        ```
        //发布本地流设置。
        //true表示允许发布音频流，false表示不允许。
        mEngine.configLocalAudioPublish(true);
        //true表示允许发布相机流，false表示不允许。
        mEngine.configLocalCameraPublish(true);
        //true表示允许发布屏幕流，false表示不允许。
        mEngine.configLocalScreenPublish(true);
        //true表示允许发布次要视频流，false表示不允许。
        mEngine.configLocalSimulcast(true, AliRtcEngine.AliRtcVideoTrack.AliRtcVideoTrackCamera);
        mEngine.publish();
        ```

    -   取消发布本地流

        ```
        mEngine.configLocalAudioPublish(false);
        mEngine.configLocalCameraPublish(false);
        mEngine.configLocalScreenPublish(false);
        mEngine.configLocalSimulcast(false, AliRtcEngine.AliRtcVideoTrack.AliRtcVideoTrackCamera);
        mEngine.publish();
        ```

    发布和取消发布本地流回调代码如下所示：

    ```
    private AliRtcEngineEventListener mEventListener = new AliRtcEngineEventListener() {
    @Override
    public void onPublishResult(int result, String publishId) {
    //发布本地流回调。
    }
    @Override
    public void onUnpublishResult(int result) {
    //取消发布本地流回调。
    }
    }
    ```

4.  订阅或取消订阅远程流。

    -   订阅远程流

        -   自动订阅模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
        -   手动订阅模式下：加入频道成功后，可通过以下接口订阅远端流。
        如果订阅过程中需要变更配置或者停止订阅，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

        ```
        // 订阅远端音频流。
        mEngine.configRemoteAudio(/* remoteUserID */, true);
        // 订阅远端屏幕流。
        mEngine.configRemoteScreenTrack(/* remoteUserID */, true);
        // 订阅远端相机流。
        mEngine.configRemoteCameraTrack(/* remoteUserID */, true, true);
        // 订阅远端用户ID。
        mEngine.subscribe(/* remoteUserID */);
        ```

    -   取消订阅远程流

        ```
        mEngine.configRemoteAudio(/* remoteUserID */, false);
        mEngine.configRemoteScreenTrack(/* remoteUserID */, false);
        mEngine.configRemoteCameraTrack(/* remoteUserID */, true, false);
        mEngine.subscribe(/* remoteUserID */);
        ```

    远程流回调代码如下所示：

    ```
    private AliRtcEngineNotify mEngineNotify = new AliRtcEngineNotify() {
    @Override
    public void onRemoteUserUnPublish(AliRtcEngine rtcEngine, String userId) {
    //远端用户停止发布通知，处于OB（observer）状态。
    }
    @Override
    public void onRemoteUserOnLineNotify(String uid) {
    //远端用户上线通知。
    }
    @Override
    public void onRemoteUserOffLineNotify(String uid) {
    //远端用户下线通知。
    }
    @Override
    public void onRemoteTrackAvailableNotify(String uid,AliRtcEngine.AliRtcAudioTrackaudioTrack,AliRtcEngine.AliRtcVideoTrack videoTrack) {
    //远端用户发布音视频流变化通知。
    }
    public void onSubscribeResult(String uid,int result,AliRtcVideoTrack videoTrack,AliRtcAudioTrack audioTrack) {
    //订阅流回调，可以做UI及数据的更新。
    }
    }
    ```

5.  离开频道。

    -   如果SDK版本号大于1.7，请调用如下接口。

        ```
        mEngine.leaveChannel();
        ```

    -   如果SDK版本号小于等于1.7，请增加timeout参数，一般设置为1000，表示该接口的调用超时时间为1秒，建议您在Activity的onDestroy接口中调用。

        **说明：** 调用leaveChannel接口后请不要再操作AliRtcEngine实例。

        ```
        mEngine.leaveChannel(1000);
        ```


您可以下载示例代码，快速运行Demo，实现频道内和其他人进行实时音视频通话，详情请参见[t170945.md\#](/cn.zh-CN/快速入门/运行Demo示例/运行Android Demo.md)。

