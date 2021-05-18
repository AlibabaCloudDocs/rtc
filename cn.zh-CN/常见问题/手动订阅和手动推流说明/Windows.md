# Windows

通过阅读本文，您可以了解手动推流和手动订阅的方法。

RTC SDK提供了`setAutoPublish`接口，支持设置自动推流或自动订阅，设置自动推流时SDK会在加入频道后自动推流，设置自动订阅时SDK会在频道中有其他用户推流时自动进行订阅拉流，无需App进行操作。如果您需要根据具体业务场景，按需进行推流或者拉流，可以使用手动推流或手动订阅。

## 手动推流

1.  创建引擎实例后，在加入频道前，设置关闭自动推流（设置参数autoPub为false）。

    ```
    // 创建引擎实例
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
    
    // 关闭自动推流、自动订阅
    pEngine->setAutoPublishSubscribe(false, false);
    ```

2.  配置后加入频道，并根据业务需要启动推流（音频、摄像头、屏幕采集），并通过回调确认推流是否成功，如果推流失败需要进行重试或提示用户。

    **说明：** 必须在加入频道成功后才能开始推流，否则推流会失败，您需要关注加入频道结果是否成功。

    ```
    // 配置推送音频流
    pEngine->configLocalAudioPublish(true);
    
    // 配置推送摄像头流
    pEngine->configLocalCameraPublish(true);
    
    // 配置推送屏幕分享流
    pEngine->configLocalScreenPublish(true);
    
    // 启动推流
    auto callback = [](void *opaque, int errorCode) {
        if (errorCode == 0) {
            // 推流成功
        } else {
            // 推流失败
        }
    };
    pEngine->publish(callback, this);
    ```

3.  当业务场景需要停止推流时，配置关闭上一步打开的媒体流并执行停止推流。

    ```
    // 配置停止推送音频流
    pEngine->configLocalAudioPublish(false);
    
    // 配置停止推送摄像头流
    pEngine->configLocalCameraPublish(false);
    
    // 配置停止推送屏幕分享流
    pEngine->configLocalScreenPublish(false);
    
    // 停止推流
    auto callback = [](void *opaque, int errorCode) {
    };
    pEngine->publish(callback, this);
    ```


## 手动订阅

1.  创建引擎实例后，在加入频道前，设置关闭自动订阅（设置参数autoSub为false）。

    ```
     // 创建引擎实例
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
    
    // 关闭自动推流/自动订阅
    pEngine->setAutoPublishSubscribe(false, false);
    ```

2.  配置后并成功加入频道，当频道中用户推流发送变化时，SDK会回调`onRemoteTrackAvailableNotify`进行通知，回调中指明了推流用户及推送的媒体流。

    -   audioTrack为AliRtcAudioTrackMic时，表示该远端用户推送了音频流。
    -   videoTrack为AliRtcVideoTrackCamera或AliRtcVideoTrackBoth时，表示该远端用户推送了摄像头视频流。
    -   videoTrack为AliRtcVideoTrackScreen或AliRtcVideoTrackBoth时，表示该远端用户推送了屏幕分享视频流。
    -   audioTrack为AliRtcAudioTrackNo并且videoTrack为AliRtcVideoTrackNo时，表示该远端用户已停止推流。
    ```
     // 接收到其他用户推流变化通知
    void onRemoteTrackAvailableNotify(const AliRtc::String &uid,
        AliRtcAudioTrack audioTrack,
        AliRtcVideoTrack videoTrack)
    {
        ...
    }
    ```

    **说明：**

    -   在加入频道成功后，才会接收到频道中其他用户推流回调onRemoteTrackAvailableNotify，您需要关注加入频道结果是否成功。
    -   回调onRemoteTrackAvailableNotify中指明了推流用户ID，以及该用户发生状态变更的媒体流，您需要记录该用户已推送媒体流。
3.  接收到推流回调后，可根据远端用户实际推送的媒体流及业务需要，配置订阅推流用户的媒体流，然后启动订阅。

    ```
    // 配置订阅指定用户音频流
    pEngine->configRemoteAudio(userId, true);
    
    // 配置订阅指定用户摄像头流
    pEngine->configRemoteCameraTrack(userId, false, true);
    
    // 配置订阅指定用户屏幕分享流
    pEngine->configRemoteScreenTrack(userId, true);
    
    // 启动订阅
    auto callback = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
    };
    pEngine->subscribe(userId, callback, this);
    ```

    **说明：**

    -   在接收到远端用户的推流回调之后，您才能对该用户进行订阅拉流，否则订阅失败。
    -   您需要关注回调中远端用户实际推送的媒体流，对于没有推送的媒体流，订阅无法成功。
    -   如果远端用户状态已变为停止推流后，您不能对该用户执行订阅操作，直到再次接收到该用户重新开始推送媒体流的回调。
4.  订阅成功后，订阅用户会接收到回调onSubscribeChangedNotify，此时可设置用于显示视频流的View（视图）。

    -   audioTrack为AliRtcAudioTrackMic时，表示已订阅远端用户推送了音频流。
    -   videoTrack为AliRtcVideoTrackCamera或AliRtcVideoTrackBoth时，表示已订阅远端用户摄像头视频流。
    -   videoTrack为AliRtcVideoTrackScreen或AliRtcVideoTrackBoth时，表示已订阅远端用户推送了屏幕分享视频流。
    ```
    void onSubscribeChangedNotify(const AliRtc::String &uid,
        AliRtcAudioTrack audioTrack,
        AliRtcVideoTrack videoTrack) {
    
        if (at == AliRtcAudioTrackMic) {
            // 订阅音频流成功
        }
    
        if (vt == AliRtcVideoTrackCamera || vt == AliRtcVideoTrackBoth) {
            // 订阅摄像头流成功
            AliVideoCanvas cameraCanvas;
            ...
            pEngine->setRemoteViewConfig(&cameraCanvas, uid, AliRtcVideoTrackCamera);
        }
    
        if (vt == AliRtcVideoTrackScreen || vt == AliRtcVideoTrackBoth) {
            // 订阅屏幕流成功
            AliVideoCanvas screenCanvas;
            ...
            pEngine->setRemoteViewConfig(&screenCanvas, uid, AliRtcVideoTrackScreen);
        }
    }
    ```

    **说明：** onSubscribeChangedNotify回调中返回了实际订阅远端用户媒体流的结果，您需要关注订阅结果是否与订阅配置一致，确认订阅是否成功。

5.  当业务场景不需要订阅指定用户媒体流，或远端用户已停止推流时（参见[步骤 2](#step_612_pef_i6v)中远端停止推流状态），配置并取消订阅对应用户。

    ```
    // 配置取消订阅指定用户音频流
    pEngine->configRemoteAudio(userId, false);
    
    // 配置取消订阅指定用户摄像头流
    pEngine->configRemoteCameraTrack(userId, false, false);
    
    // 配置取消订阅指定用户屏幕分享流
    pEngine->configRemoteScreenTrack(userId, false);
    
    // 取消订阅
    auto callback = [](void *opaque, const AliRtc::String &uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
    };
    pEngine->subscribe(userId, callback, this);
    ```


