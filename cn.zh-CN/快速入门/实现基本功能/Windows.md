---
keyword: [基本功能, Windows]
---

# Windows

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、订阅远端和离开频道等。通过阅读本文，您可以了解阿里云RTC的基本功能。

-   您已下载并集成最新版本的SDK。具体操作，请参见[Windows端集成SDK](/cn.zh-CN/快速入门/集成客户端SDK/Windows.md)。
-   您已获取加入频道必须的频道鉴权令牌（Token）。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

**说明：** 本文中的实现方法仅供参考，您可以根据实际业务需求进行开发。

1.  初始化SDK。

    1.  如果CRtcSampleDlg类中有定义AliRTCEngine实例，则需要创建AliRTCEngine实例，并注册AliRtcEventListener监听相关回调。更多信息，请参见[回调及监听](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)。

        ```
        m_pEngine = AliRtcEngine::sharedInstance(AliRtcEventListener* pListener, char* pConfig);//pListener是您实现的AliRtcEventListener对象，用于接收SDK的回调。pConfig是SDK初始化配置，当前版本请使用空字符串
        ```

        **说明：** 目前暂不支持多实例。

    2.  创建canvas布局进行本地预览视频。

        -   开启本地预览。

            ```
            // 获取预览窗口
            AliVideoCanvas canvas;
            canvas.renderMode = AliRtcRenderModeAuto;
            canvas.hWnd = /*预览窗口句柄*/;
            // 设置预览窗口
            m_pEngine->setLocalViewConfig(canvas, AliRtcVideoTrackCamera);
            m_pEngine->startPreview();
            canvas.flip = true;//true表示镜像画面，false表示正常画面
            ```

            **说明：** AliRtcRenderMode提供四种渲染模式。

            -   （推荐）AliRtcRenderModeAuto：自动模式。
            -   AliRtcRenderModeStretch：拉伸填充视图，不保持视频比例。
            -   AliRtcRenderModeFill：在保持视频宽高比的同时缩放，填充黑边。
            -   AliRtcRenderModeCrop：在保持视频宽高比的同时缩放，并裁剪以适合视图。
        -   停止本地预览。

            ```
            m_pEngine->stopPreview();
            ```

    3.  设置自动或者手动模式。

        **说明：** 默认实现自动发布和订阅，您也可以通过代码手动发布和订阅。

        -   自动发布模式： 如果您打开自动发布模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动发布模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动订阅模式： 如果您打开自动订阅模式，加入频道之后，SDK将会自动订阅当前频道内其他人的音视频流；如果关闭自动订阅模式，则需要您调用subscribe接口之后才会订阅其他人的音视频流。
        ```
        /*
        设置自动发布和订阅，只能在joinChannel之前设置
        autoPub: true表示自动发布，false表示手动发布
        autoSub: true表示自动订阅，false表示手动订阅
        */ 
        m_pEngine->setAutoPublishSubscribe(bool autoPub, bool autoSub);
        ```

2.  加入频道。

    ```
    AliRtcAuthInfo authinfo;
    authinfo.channel   = /* 频道ID */;
    authinfo.appid     = /* 应用ID */;
    authinfo.token     = /* 频道鉴权令牌Token */;
    authinfo.nonce     = /* 随机码 */;
    authinfo.user_id   = /* 用户ID */;
    authinfo.timestamp = /* 时间戳 */;
    authinfo.gslb      = /* GSLB地址 */;
    ...
    // joinChannel是一个异步接口，设置回调函数
    auto onJoinResult = [](void *opaque, int errCode) {
        if (errCode == 0) {
            // 加入频道成功        
        } else {
            //加入频道失败
        }
    };
    m_pEngine->joinChannel(authinfo, /* 显示名称 */, onJoinResult, /*UserData，传递给onJoinResult回调函数*/);
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
        //发布本地流设置
        //true表示允许发布屏幕共享流，false表示不允许
        m_pEngine->configLocalScreenPublish(true);
        //true表示允许发布音频流，false表示不允许
        m_pEngine->configLocalAudioPublish(true);
        //true表示允许发布相机流，false表示不允许
        m_pEngine->configLocalCameraPublish(true);
        //true表示允许发布次要视频流；false表示不允许
        //子码流
        m_pEngine->configLocalSimulcast(true, AliRtcVideoTrack::AliRtcVideoTrackCamera); 
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

    -   取消发布本地流

        ```
        m_pEngine->configLocalScreenPublish(false);
        m_pEngine->configLocalAudioPublish(false);
        m_pEngine->configLocalCameraPublish(false);
        m_pEngine->configLocalSimulcast(false, AliRtcVideoTrack::AliRtcVideoTrackCamera);
        // 取消发布完成返回成功或者失败
        auto onPubResult = [](void *opaque, int errCode) {
            if (errCode == 0) {
               // 取消发布成功
            } else {
               // 取发布失败
            }
        };
        m_pEngine->publish(onPubResult, /*UserData，传递给onPubResult回调函数*/);
        ```

4.  订阅或取消订阅远程流。

    -   订阅远程流

        -   自动订阅模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
        -   手动订阅模式下：加入频道成功后，可通过以下接口订阅远端流。
        如果订阅过程中需要变更配置或者停止订阅，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

        ```
        //true表示允许订阅音频流，false表示不允许
        m_pEngine->configRemoteAudio(/* remoteUserID */, true);
        //true表示允许订阅屏幕共享流，false表示不允许
        m_pEngine->configRemoteScreenTrack(/* remoteUserID */, true);
        //第二个参数preferMaster true表示优先订阅大流，fales表示优先订阅次小流
        //第三个参数enable true表示允许订阅相机流，false表示不允许
        m_pEngine->configRemoteCameraTrack(/* remoteUserID */, true, true);
        //Call back when subscribe finished
        auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) { 
        };
        m_pEngine->subscribe(/* remoteUserID */, onSubResult, /*UserData*/);
        ```

        无论是自动模式还是非自动模式，当您订阅成功后，通您可以通过订阅的回调，进行相关UI操作或逻辑处理。

        ```
        auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
            ...
            // 设置视频流的窗口
            if (vt == AliRtcVideoTrack::AliRtcVideoTrackCamera || vt == AliRtcVideoTrack::AliRtcVideoTrackBoth) {
                /*设置远端视频预览*/
            }
        ```

        另外，您可以通过onRemoteTrackAvailableNotify回调获得远端用户的流状态变更。例如：手动模式下，收到此回调后，可以获取到远端用户的发布状态，然后相应做出订阅操作，或者更新UI等。

        ```
         void onRemoteTrackAvailableNotify(const AliRtc::String & uid,   AliRtcAudioTrack audioTrack, AliRtcVideoTrack videoTrack) {   
        }
        ```

    -   取消订阅远程流

        ```
        m_pEngine->configRemoteAudio(/* remoteUserID */, false);
        m_pEngine->configRemoteScreenTrack(/* remoteUserID */, false);
        m_pEngine->configRemoteCameraTrack(/* remoteUserID */, true, false);
        auto onSubResult = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
        };
        m_pEngine->subscribe(/* remoteUserID */, onSubResult, /*UserData*/);
        ```

5.  离开频道。

    ```
    m_pEngine->leaveChannel();
    ```


您可以下载示例代码，快速运行Demo，实现频道内和其他人进行实时音视频通话，详情请参见[t170947.md\#](/cn.zh-CN/快速入门/运行Demo示例/运行Windows Demo.md)。

