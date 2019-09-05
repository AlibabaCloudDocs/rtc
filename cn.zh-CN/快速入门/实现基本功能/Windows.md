# Windows {#task_2022320 .task}

阿里云音视频通信的基本功能包含初始化SDK、加入频道、本地发布和订阅远端、离开频道等。当您成功初始化SDK，您可以进行本地预览视频功能，进行简单的预览和测试，您也可以设置手动或者自动模式。

在实现基本功能前，请您确保下载最新SDK，请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#)。

**说明：** 本文中的实现方法为主要功能方法，仅供参考，您可以根据您的业务需求进行实际开发。

1.  初始化SDK。 

    如果您在CRtcSampleDlg中持有AliRTCEngine实例。代码如下所示。

    ``` {#codeblock_4ho_4xl_svp}
    class CRtcSampleDlg : public AliRtcEventListener
    {
    ...
        AliRtcEngine *m_pEngine;
    ...
    }
    ```

    您需要创建AliRTCEngine实例，并注册AliRtcEventListener监听相关回调，详细回调方法请参见[回调及监听](../../../../cn.zh-CN/SDK参考/Windows SDK/回调及监听.md#)。

    -   第一个参数是您实现的AliRtcEventListener对象，用于接收SDK的回调。
    -   第二个参数是SDK初始化配置，当前版本请使用空字符串。
    ``` {#codeblock_nrl_661_z24}
    m_pEngine = AliRtcEngine::sharedInstance(/*AliRtcEventListener实例*/, /* 配置参数*/);
    ```

    **说明：** 暂不支持多实例

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas进行本地预览视频。 

        开启本地预览。

        ``` {#codeblock_6yj_e4x_fph}
        // 获取预览窗口
        AliVideoCanvas canvas;
        canvas.renderMode = AliRtcRenderModeAuto;
        canvas.hWnd = /*预览窗口句柄*/;
        // 设置预览窗口
        m_pEngine->setLocalViewConfig(canvas, AliRtcVideoTrackCamera);
        m_pEngine->startPreview();
        canvas.flip = true：镜像画面 false：正常画面;//
        ```

        **说明：** renderMode提供四种模式：Auto、Stretch、Fill、Crop，建议您使用Auto模式。hWnd必须是预览窗口句柄。

        停止本地预览。

        ``` {#codeblock_pyg_snu_pup}
        m_pEngine->stopPreview();
        ```

    1.  设置自动或者手动模式。 

        -   自动Publish模式： 如果您打开自动Publish模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动Publish模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动Subscribe模式： 如果您打开自动Subscribe模式，加入频道之后，SDK将会自动订阅当前频道内其他用户的音视频流；如果关闭自动Subscribe模式，则需要您调用subscribe接口之后才会订阅其他用户的音视频流。
        ``` {#codeblock_bpz_86v_z8k}
        /*
        设置自动发布和订阅，只能在joinChannel之前设置
        autoPub: true表示自动发布，false表示手动发布
        autoSub: true表示自动订阅，false表示手动订阅
        */ 
        m_pEngine->setAutoPublishSubscribe(true, true);
        ```

2.  加入频道。 

    **说明：** AliRtcAuthInfo的各项参数均需要App Server通过API来获取，然后App Server下发至客户端，客户端将各项参数赋值后，就可以加入频道。

    -   name：无需APP Server下发。
    -   channelID 、userID、name命名要求：字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节，非法命名系统将拒绝提供服务。
    ``` {#codeblock_4j7_9mi_nio}
    AliRtcAuthInfo authinfo;
    authinfo.channel   = /* 用户的channelId */;
    authinfo.appid     = /* 用户的Appid */;
    authinfo.token     = /* 用户的token */;
    authinfo.nonce     = /* 用户的nonce */;
    authinfo.user_id   = /* 用户的userId */;
    authinfo.token     = /* 用户的token */;
    authinfo.timestamp = /* 用户的timestamp */;
    authinfo.gslb      = /* 用户的gslb */;
    ...
    // joinChannel是一个异步接口，设置回调函数
    auto onJoinResult = [](void *opaque, int errCode) {
        // join成功
        if (errCode == 0) {
            // 加入频道成功        
        } else {
            //加入频道失败
        }
    };
    m_pEngine->joinChannel(authinfo, /* name */, onJoinResult, /*UserData，传递给onJoinResult回调函数*/);
    ```

3.  发布或取消发布本地流。 

    发布本地流。

    -   自动pub模式下：加入频道成功后，即可发布本地流，无需再次调用publish接口。
    -   非自动pub模式下：加入成功后，可通过以下接口发布本地流。
    如果publish过程中需要变更配置或者停止publish，需要按如下流程先重新设置配置参数，然后再调用publish接口。

    ``` {#codeblock_r1r_ye7_rlf}
    //发布本地流设置
    //true表示允许发布屏幕共享流，false表示不允许
    m_pEngine->configLocalScreenPublish(true);
    //true表示允许发布音频流，false表示不允许
    m_pEngine->configLocalAudioPublish(true);
    //true表示允许发布相机流，false表示不允许
    m_pEngine->configLocalCameraPublish(true);
    //true表示允许发布次要视频流；false表示不允许
    m_pEngine->configLocalSimulcast(true, AliRtcVideoTrack::AliRtcVideoTrackCamera); //子码流
    //屏幕共享流不支持子码流，因此第二个参数只能为AliRtcVideoTrack::AliRtcVideoTrackCamera。 
    // Call back when publish finished
    auto onPubResult = [](void *opaque, int errCode) {
        if (errCode == 0) {
           // 发布成功
        } else {
           // 发布失败
        }
    };
    m_pEngine->publish(onPubResult, /*UserData，传递给onPubResult回调函数*/);
    ```

    取消发布本地流。

    ``` {#codeblock_r87_s61_i3x}
    m_pEngine->configLocalScreenPublish(false);
    m_pEngine->configLocalAudioPublish(false);
    m_pEngine->configLocalCameraPublish(false);
    m_pEngine->configLocalSimulcast(false, AliRtcVideoTrack::AliRtcVideoTrackCamera);
    // Call back when publish finished
    auto onPubResult = [](void *opaque, int errCode) {
        if (errCode == 0) {
           // 取消发布成功
        } else {
           // 取消发布失败
        }
    };
    m_pEngine->publish(onPubResult, /*UserData，传递给onPubResult回调函数*/);
    ```

4.  订阅或取消订阅远程流。 

    订阅远程流。

    -   自动sub模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
    -   非自动sub模式下：加入频道成功后，可通过以下接口订阅远端流。
    如果subscribe过程中需要变更配置或者停止subscribe，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

    ``` {#codeblock_80v_wth_w91}
    //true表示允许订阅音频流，false表示不允许
    m_pEngine->configRemoteAudio(/* remoteUserID */, true);
    //true表示允许订阅屏幕共享流，false表示不允许
    m_pEngine->configRemoteScreenTrack(/* remoteUserID */, true);
    //第二个参数：true表示优先订阅大流
    //第三个参数：true表示允许订阅相机流，false表示不允许
    m_pEngine->configRemoteCameraTrack(/* remoteUserID */, true, true);
    //Call back when subscribe finished
    auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) { 
    };
    m_pEngine->subscribe(/* remoteUserID */, onSubResult, /*UserData*/);
    ```

    不论自动模式还是非自动模式下，订阅成功后，通过订阅的callback，然后您可以进行相关UI操作或逻辑处理

    ``` {#codeblock_xs0_i68_2hx}
    auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
        ...
        // 设置视频流的窗口
        if (vt == AliRtcVideoTrack::AliRtcVideoTrackCamera || vt == AliRtcVideoTrack::AliRtcVideoTrackBoth) {
            /*设置远端视频预览*/
        }
    ```

    另外，您可以通过onRemoteTrackAvailableNotify回调获得远端用户的流状态变更。例如，手动模式下，收到此回调后，可以获取到远端用户的发布状态，然后相应做出subscribe操作，或者更新UI等。

    ``` {#codeblock_7ub_w59_2fg}
     void onRemoteTrackAvailableNotify(const AliRtc::String & uid,   AliRtcAudioTrack audioTrack, AliRtcVideoTrack videoTrack) {   
    }
    ```

    取消订阅远程流。

    ``` {#codeblock_ah6_hvh_o5e}
    m_pEngine->configRemoteAudio(/* remoteUserID */, false);
    m_pEngine->configRemoteScreenTrack(/* remoteUserID */, false);
    m_pEngine->configRemoteCameraTrack(/* remoteUserID */, true, false);
    auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
    };
    m_pEngine->subscribe(/* remoteUserID */, onSubResult, /*UserData*/);
    ```

5.  离开频道。 

    ``` {#codeblock_mxb_aoi_kfi}
    m_pEngine->leaveChannel();
    ```

     您可以下载示例代码，快速跑通Demo，实现频道内和其他用户进行实时音视频通话，详情请参见[Windows Demo](../../../../cn.zh-CN/Demo/Windows Demo.md#)。


