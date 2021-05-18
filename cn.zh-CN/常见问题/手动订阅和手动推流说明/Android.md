# Android

通过阅读本文，您可以了解手动推流和手动订阅的方法。

RTC SDK提供了`setAutoPublish`接口，支持设置自动推流或自动订阅，设置自动推流时SDK会在加入频道后自动推流，设置自动订阅时SDK会在频道中有其他用户推流时自动进行订阅拉流，无需App进行操作。如果您需要根据具体业务场景，按需进行推流或者拉流，可以使用手动推流或手动订阅。

## 手动推流

1.  创建引擎实例后，在加入频道前，设置关闭自动推流和自动订阅。

    ```
    // 创建引擎实例
    AliRtcEngine mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
     mAliRtcEngine.setRtcEngineEventListener(new AliRtcEngineEventListener() {
    
                    @Override
                    public void onPublishResult(int result, String publishId) {
                        //异步推流的回调
                    }
    
                   @Override
                    public void onUnpublishResult(int result) {
                      //异步取消推流的回调
                    }
    
    });
    // 关闭自动推流和自动订阅
    mAliRtcEngine.setAutoPublish(false, false);
    ```

2.  配置后加入频道，并根据业务需要启动推流（音频、摄像头、屏幕分享），并通过回调确认推流是否成功，如果推流失败需要进行重试或用户提示。

    ```
    // 配置开启推送音频流
    mAliRtcEngine.configLocalAudioPublish(true);
    
    // 配置开启推送摄像头流
    mAliRtcEngine.configLocalCameraPublish(true);
    
    // 配置开启推送屏幕分享流
    mAliRtcEngine.configLocalScreenPublish(true);
    
    // 启动推流
    mAliRtcEngine.publish();
    ```

    **说明：** publish接口是异步接口，您在调用之后需要收到onPublishResult回调且result为0时表示推流成功，接口及对应回调请参见[setRtcEngineEventListener](/cn.zh-CN/SDK参考/Android SDK/Android SDK（v1.17）/AliRtcEngine接口.md)。

3.  当业务场景需要停止推流时，您需要关闭[步骤 2](#step_ot6_p81_gn2)配置的媒体流并执行停止推流。

    ```
    // 配置停止推送音频流
    mAliRtcEngine.configLocalAudioPublish(false);
    
    // 配置停止推送摄像头流
    mAliRtcEngine.configLocalCameraPublish(false);
    
    // 配置停止推送屏幕分享流
    mAliRtcEngine.configLocalScreenPublish(false);
    
    // 停止推流
    mAliRtcEngine.publish();
    ```


## 手动订阅

1.  创建引擎实例后，在加入频道前，设置关闭自动订阅。

    ```
    // 创建引擎实例
    AliRtcEngine mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
     mAliRtcEngine.setRtcEngineEventListener(new AliRtcEngineEventListener() {
    
                    @Override
                    public void onSubscribeResult(String uid, int result, AliRtcEngine.AliRtcVideoTrack vt,
                                          AliRtcEngine.AliRtcAudioTrack at) {
                       //异步订阅成功或者失败的回调
                    }
    
                    @Override
                  public void onUnsubscribeResult(int result, String userId) {
                      Log.d(TAG, "onUnsubscribeResult result : " + result);
                      //取消订阅成功或者失败的回调
                  }
    
                 @Override
                public void onRemoteTrackAvailableNotify(String uid, AliRtcEngine.AliRtcAudioTrack audioTrack,
                                                               AliRtcEngine.AliRtcVideoTrack videoTrack) {
                      //远端用户推流发生变化时回调
                 }
    });
    // 关闭自动推流和自动订阅
    mAliRtcEngine.setAutoPublish(false, false);
    ```

2.  配置后并成功加入频道，当频道中有用户推流发送变化时，SDK会收到`onRemoteTrackAvailableNotify`回调进行通知。

    onRemoteTrackAvailableNotify回调中指明了推流用户ID，以及该用户发生状态变更的媒体流，您需要记录该用户已推送媒体流：

    -   audioTrack为AliRtcAudioTrackMic时，表示该远端用户推送了音频流。
    -   videoTrack为AliRtcVideoTrackCamera或AliRtcVideoTrackBoth时，表示该远端用户推送了摄像头视频流。
    -   videoTrack为AliRtcVideoTrackScreen或AliRtcVideoTrackBoth时，表示该远端用户推送了屏幕分享视频流。
    -   audioTrack为AliRtcAudioTrackNo并且videoTrack为AliRtcVideoTrackNo时，表示该远端用户已停止推流。
    ```
    // 接收到其他用户推流变化通知
    @Override
    public void onRemoteTrackAvailableNotify(String uid, AliRtcEngine.AliRtcAudioTrack audioTrack,
                                                     AliRtcEngine.AliRtcVideoTrack videoTrack) {
    
    
    }
    ```

    **说明：** 必须在加入频道成功后，您才会接收到频道中其他用户推流的`onRemoteTrackAvailableNotify`回调，您需要查看加入频道结果是否成功，加入频道回调请参见[onJoinChannelResult](/cn.zh-CN/SDK参考/Android SDK/Android SDK（v1.17）/回调及监听.md)。

3.  接收到推流回调后，可根据业务需要对用户实际推送的媒体流进行配置，然后启动订阅。

    ```
    // 配置是否订阅指定用户音频流，可根据需要设置开启/关闭
    mAliRtcEngine.configRemoteAudio(userId, true|false);
    
    // 配置是否订阅指定用户摄像头流，可根据需要设置开启/关闭
    mAliRtcEngine.configRemoteCameraTrack(userId, false, true|false);
    
    // 配置是否订阅指定用户屏幕分享流，可根据需要设置开启/关闭
    mAliRtcEngine.configRemoteScreenTrack(userId, true|false);
    
    // 启动订阅
    mAliRtcEngine.subscribe(userId);
    ```

    **说明：** subscribe接口是异步接口，需要收到onSubscribeResult回调，详情请参见[onSubscribeResult](/cn.zh-CN/SDK参考/Android SDK/Android SDK（v1.17）/回调及监听.md)。

    -   必须在接收到频道内用户的推流回调之后，才能对该用户进行订阅拉流，否则订阅失败；如果频道内用户状态已变为停止推流，订阅无法成功。
    -   您需要关注回调中远端用户实际推送的媒体流，对于没有推送的媒体流，订阅无法成功。
    -   如果用户状态已变为停止推流后，不能在对该用户执行订阅操作，直到再次接收到回调（该用户重新开始推送媒体流）。
4.  订阅成功后，当业务场景需要取消订阅指定用户媒体流，或远端用户已停止推流（参考[步骤 2](#step_6nz_x58_y2a)中远端停止推流状态）时，配置并取消订阅对应用户。

    ```
    // 配置是否订阅指定用户音频流，可根据需要设置关闭
    mAliRtcEngine.configRemoteAudio(userId, false);
    
    // 配置是否订阅指定用户摄像头流，可根据需要设置关闭
    mAliRtcEngine.configRemoteCameraTrack(userId, false, false);
    
    // 配置是否订阅指定用户屏幕分享流，可根据需要设置关闭
    mAliRtcEngine.configRemoteScreenTrack(userId, false);
    
    // 取消订阅
    mAliRtcEngine.subscribe(userId);
    ```


