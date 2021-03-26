# Windows

您可以阅读本文，了解Android端实现教师端和学生端的互动模式接入。

## 教师端

1.  在教师加入频道之前设置频道模式为互动模式。

    ```
    pEngine->setChannelProfile(AliRtcChannelProfileInteractiveLive);
    ```

2.  在教师加入频道之前设置为非自动发布和自动订阅模式。

    ```
    pEngine->setAutoPublishSubscribe(false, true);
    ```

3.  在教师加入频道之前设置角色为AliRtcClientRoleInteractive。

    ```
    pEngine->setClientRole(AliRtcClientRoleInteractive);
    ```

    AliRtcClientRole参数取值：

    -   AliRtcClientRoleInteractive：参与互动角色，可以推拉流。
    -   AliRtcClientRolelive：仅观看角色，只能拉流，适用于普通观众。
    **说明：** setClientRole接口暂时不要处理接口返回值。

4.  加入频道。

    ```
    pEngine->joinChannel(aliRtcAuthInfo, userName);
    ```

5.  调用publish接口开始推流。

    ```
    ​// 配置推送音频流，可根据需要开启
    pEngine->configLocalAudioPublish(true);
    // 配置推送摄像头流，可根据需要开启
    pEngine->configLocalCameraPublish(true);
    // 配置推送屏幕流，可根据需要开启
    pEngine->configLocalScreenPublish(true);
    //启动推流,注意publish是异步接口需要收到onPublishResult之后且result为0才能算推流成功，请参考设置setRtcEngineEventListener接口的相应回调
    pEngine->publish();
    ```

    **说明：** 在调用publish接口前必须确保加入频道已经成功，否则调用publish接口会失败。

6.  远端用户推流、停止推流消息回调（学生端收到远端用户推流消息的回调与教师端相同）。

    ```
    /**
     * @brief 当远端用户的流发生变化时，返回这个消息
     * @param uid         User ID。从App server分配的唯一标示符
     * @param audioTrack         音频流类型，详见AliRtcAudioTrack
     * @param videoTrack         视频流类型，详见AliRtcVideoTrack
     * @note 远方用户停止推流，也会发送这个消息
     */
    virtual void onRemoteTrackAvailableNotify(const AliRtc::String &uid,
                                                AliRtcAudioTrack audioTrack,
                                                AliRtcVideoTrack videoTrack)
    ```

    **说明：**

    -   audioTrack取值为AliRtcAudioTrackNo并且videoTrack取值为AliRtcVideoTrackNo时，表示远端用户停止推流；其他情况表示远端用户对应的推流状态。
    -   加入频道之后也可设置角色，设置成功后可收到回调。

        ```
        void onUpdateRoleNotify(const AliRtcClientRole old_role, const AliRtcClientRole new_role)
        ```

    -   需要业务侧关注一下当前的角色参数值，例如当前是AliRtcClientRoleInteractive角色，再次调用以下接口将不会收到回调。

        ```
        pEngine->setClientRole(AliRtcClientRoleInteractive);
        ```

        建议业务侧将角色切换和推拉流的逻辑区分开。


## 学生端

学生加入频道之前设置频道模式为互动模式。

```
AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(listener, "");
pEngine->setChannelProfile(AliRtcChannelProfileInteractiveLive);
```

普通观众：设置为互动模式后，默认角色类型为“仅观看角色”，即只可拉流观看直播，不能推流。此角色适用于普通观众，无需其他操作。

连麦观众：角色类型为“参与互动角色”，可以推流，操作步骤如下所示：

1.  开始上麦。

    1.  如果普通观众需要上麦切换为连麦观众的话，需要先切换用户角色。

    2.  切换角色为AliRtcClientRoleInteractive（需要在调用publish接口进行推流前）。

        ```
        pEngine->setClientRole(AliRtcClientRoleInteractive);
        ```

        切换成功后可收到回调。

        ```
        void onUpdateRoleNotify(const AliRtcClientRole old_role, const AliRtcClientRole new_role) {};
        ```

    3.  收到回调后，调用publish接口开始推流。

        ```
        pEngine->configLocalAudioPublish(true);
        pEngine->configLocalCameraPublish(true);
        
        auto callback = [](void *opaque, int errorCode) {
            if (errorCode == 0) {
                // 推流成功
            } else {
                // 推流失败
            }
        };
        pEngine->publish(callback, this);
        ```

2.  下麦。

    与上麦逻辑相反，如果连麦观众需要下麦切换为普通观众的话，需要先停止推流，再进行角色切换。

    1.  停止推流。

        ```
        pEngine->configLocalAudioPublish(false);
        pEngine->configLocalCameraPublish(false);
        
        auto callback = [](void *opaque, int errorCode) {
        };
        pEngine->publish(callback, this);
        ```

    2.  停止推流收到回调之后，即可切换为普通观众角色。

        ```
        pEngine->setClientRole(AliRtcClientRoleLive);
        ```

    3.  切换成功后可收到回调，继续保持拉流观看。

        ```
        void onUpdateRoleNotify(const AliRtcClientRole old_role, const AliRtcClientRole new_role)
        ```


