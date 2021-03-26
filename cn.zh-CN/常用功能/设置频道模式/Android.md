# Android

通过阅读本文，您可以了解实现教师端和学生端互动模式的接入流程。

## 教师端

1.  在教师加入频道之前设置频道模式为互动模式。

    ```
    aliRtcEngine.setChannelProfile(AliRTCSDK_Channel_Profile.AliRTCSDK_Interactive_live);
    ```

2.  在教师加入频道之前设置为非自动发布和自动订阅模式。

    ```
    aliRtcEngine.setAutoPublishSubscribe(false, true);
    ```

3.  在加入频道之前设置角色为AliRTCSDK\_Interactive。

    ```
    aliRtcEngine.setClientRole(AliRTCSDK_Client_Role.AliRTCSDK_Interactive);
    ```

    AliRTCSDK\_Client\_Role参数取值：

    -   AliRTCSDK\_Interactive：参与互动角色，可以推拉流。
    -   AliRTCSDK\_live：仅观看角色，只能拉流，适用于普通观众。
    **说明：** setClientRole接口暂时不要处理接口返回值。

4.  加入频道。

    ```
    aliRtcEngine.joinChannel(aliRtcAuthInfo, userName);
    ```

5.  调用publish接口开始发布。

    ```
    // 配置推送音频流，可根据需要开启
    aliRtcEngine.configLocalAudioPublish(true);
    // 配置推送摄像头流，可根据需要开启
    aliRtcEngine.configLocalCameraPublish(true);
    // 配置推送屏幕流，可根据需要开启
    aliRtcEngine.configLocalScreenPublish(true);
    //启动推流,注意publish是异步接口需要收到onPublishResult之后且result为0才能算推流成功，请参考设置setRtcEngineEventListener接口的相应回调
    aliRtcEngine.publish();
    ```

    **说明：** 在调用publish接口前必须确保加入频道已经成功，否则调用publish接口会失败。

6.  远端用户推流、停止推流消息回调（学生端收到远端用户推流消息的回调与教师端相同）。

    ```
        /**
         * 当远端用户的流发生变化时，返回这个消息
         * @note 远方用户停止推流，也会发送这个消息
         * @param uid User ID
         * @param audioTrack 音频
         * @param videoTrack 视频
         */
    void onRemoteTrackAvailableNotify(String uid, AliRtcAudioTrack audioTrack, AliRtcVideoTrack videoTrack);
    ```

    **说明：**

    -   audioTrack取值为AliRtcAudioTrackNo并且videoTrack取值为AliRtcVideoTrackNo时，表示远端用户停止推流；其他情况表示远端用户对应的推流状态。
    -   加入频道之后也可设置角色，设置成功后可收到回调。

        ```
        void onUpdateRoleNotify(AliRtcEngine.AliRTCSDK_Client_Role oldRole,            
        AliRtcEngine.AliRTCSDK_Client_Role newRole);
        ```

    -   需要业务侧关注一下当前的角色参数值，例如当前是AliRtcClientRoleInteractive角色，再次调用以下接口将不会收到回调，建议业务侧将角色切换和推拉流的逻辑区分开。

        ```
        aliRtcEngine.setClientRole(AliRTCSDK_Client_Role.AliRTCSDK_Interactive); 
        ```


## 学生端

学生加入频道之前设置频道模式为互动模式。

```
AliRtcEngine aliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
aliRtcEngine.setChannelProfile(AliRTCSDK_Channel_Profile.AliRTCSDK_Interactive_live);
```

普通观众：设置为互动模式后，默认角色类型为“仅观看角色”，即只可拉流观看直播，不能推流。此角色适用于普通观众，无需其他操作。

连麦观众：角色类型为“参与互动角色”，可以推流，操作步骤如下所示：

1.  开始上麦。

    1.  如果普通观众需要上麦切换为连麦观众的话，需要先切换用户角色。

    2.  切换角色为AliRTCSDK\_Interactive（需要在调用publish接口进行推流前）。

        ```
        aliRtcEngine.setClientRole(AliRTCSDK_Client_Role.AliRTCSDK_Interactive);
        ```

        切换成功后可收到回调。

        ```
        /**
             * 当前角色变化通知。当本地用户在加入频道后调用 setClientRole 切换角色成功时会触发此回调
             *
             * @ param oldRole 切换前的角色
             * @ param newRole 切换后的角色
             * @ return 无
             */
            void onUpdateRoleNotify(AliRtcEngine.AliRTCSDK_Client_Role oldRole, AliRtcEngine.AliRTCSDK_Client_Role newRole);
        ```

    3.  收到回调后，调用publish接口开始推流。

        ```
        // 配置推送音频流，可根据需要开启
        aliRtcEngine.configLocalAudioPublish(true);
        
        // 配置推送摄像头流，可根据需要开启
        aliRtcEngine.configLocalCameraPublish(true);
        
        // 配置推送屏幕流，可根据需要开启
        aliRtcEngine.configLocalScreenPublish(true);
        
        // 启动推流，publish是异步接口需要收到onPublishResult之后且result为0才能算推流成功，请参考设置setRtcEngineEventListener接口的相应回调
        aliRtcEngine.publish();
        ```

2.  下麦。

    与上麦逻辑相反，如果连麦观众需要下麦切换为普通观众的话，需要先停止推流，再进行角色切换。

    1.  停止推流。

        ```
        // 配置推送音频流，可根据需要关闭
        aliRtcEngine.configLocalAudioPublish(false);
        
        // 配置推送摄像头流，可根据需要关闭
        aliRtcEngine.configLocalCameraPublish(false);
        
        // 配置推送屏幕流，可根据需要关闭
        aliRtcEngine.configLocalScreenPublish(false);
        
        // 启动推流，publish是异步接口需要收到onPublishResult之后且result为0才能算推流成功，请参考设置setRtcEngineEventListener接口的相应回调
        aliRtcEngine.publish();
        ```

    2.  停止推流收到回调之后，即可切换为普通观众模式。

        ```
        aliRtcEngine.setClientRole(AliRTCSDK_Client_Role.AliRTCSDK_live);
        ```

    3.  切换成功后可收到onUpdateRoleNotify回调，继续保持拉流观看。


