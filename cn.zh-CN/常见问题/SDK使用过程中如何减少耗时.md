# SDK使用过程中如何减少耗时

本文为您介绍在使用SDK过程中减少耗时的方法。

## 配置合理的自动订阅和自动推流

以下建议可以为您减少耗时：

-   如果您的场景中，入会后会默认推流，建议您采用自动推流模式。
-   如果您的场景中，入会后默认会订阅频道中的人，建议您采用自动订阅的模式。自动订阅模式在接收到远端用户回调之后，不需要再手动订阅，能更加节省时间。

通过以下接口设置自动订阅和自动推流：

setAutoPublish：设置是否自动发布，是否自动订阅。默认是自动发布和订阅，必须在加入频道之前设置。

```
- (int)setAutoPublish:(BOOL)autoPub withAutoSubscribe:(BOOL)autoSub;
```

## 合理的使用publish和subscribe接口

以下建议可以为您减少耗时：

-   publish和subscribe接口用于手动推流、手动订阅、以及会议中推流和订阅配置的变更。
-   publish接口需要配合configLocalCameraPublish、configLocalScreenPublish、configLocalAudioPublish接口使用。
-   subscribe接口需要配合configRemoteCameraTrack、configRemoteScreenTrack、configRemoteAudio接口使用。
-   根据自身的需要，合理使用大小流。目前默认推小流，如果无需小流，建议关闭。
-   需要注意：每次config完之后调用一次publish接口或者subscribe接口就可以，无需重复调用。

    如：当前相机流（大流）和音频流需要调用publish接口，而屏幕共享流不需要调用。

    -   正确的调用方式如下：

        ```
        [self.engine configLocalAudioPublish:YES];
        [self.engine configLocalCameraPublish:YES];
        [self.engine configLocalScreenPublish:NO];
        [self.engine configLocalSimulcast:NO forTrack:AliRtcVideoTrackCamera];
        [self.engine publish:^(int err) {
            // 相关UI操作。
        }]; 
        ```

    -   错误的调用方式如下：

        ```
        [self.engine configLocalAudioPublish:YES];
        [self.engine publish:^(int err) {
            // 相关UI操作。
        }]; 
        
        [self.engine configLocalCameraPublish:YES];
        [self.engine publish:^(int err) {
            // 相关UI操作。
        }]; 
        
        [self.engine configLocalScreenPublish:NO];
        [self.engine publish:^(int err) {
            // 相关UI操作。
        }]; 
        
        [self.engine configLocalSimulcast:NO forTrack:AliRtcVideoTrackCamera];
        [self.engine publish:^(int err) {
            // 相关UI操作。
        }]; 
        ```


## 场景中存在频繁切换频道或者频繁入离会

以下建议可以为您减少耗时：

-   维护一个SDK的示例，避免频繁的创建和销毁sdk带来的耗时。通过一个SDK实例的入离会来达到切换频道的效果。
-   可以根据需要，提前打开音频设备，节省每次入离会的耗时。比如：

    在语音直播间的场景，可以在创建SDK后调用一次startAudioPlayer接口提前打开播放设备。在销毁sdk前调用stopAudioPlayer接口关闭播放设备。中间切换频道和入离会均无需再额外调用。

    startAudioPlayer：开启音频播放。您可以控制提前打开音频播放，如果不设置，SDK会在订阅成功的时候打开音频播放。

    ```
    - (void)startAudioPlayer;
    ```

    stopAudioPlayer：关闭音频播放。您可以控制关闭音频播放。

    ```
    - (void)stopAudioPlayer;
    ```

-   音频采集设备也可以根据自身的场景决定是否提前打开。

    startAudioCapture：开启音频采集。您可以控制提前打开音频采集，如果不设置，SDK会在开始推流的时候打开音频采集。

    ```
    - (void)startAudioCapture;
    ```

    stopAudioCapture：关闭音频采集。您可以控制关闭音频采集。

    ```
    - (void)stopAudioCapture;
    ```


