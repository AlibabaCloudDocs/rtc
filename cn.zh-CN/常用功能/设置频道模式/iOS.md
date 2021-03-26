# iOS

通过阅读本文，您可以了解实现教师端和学生端互动模式的接入流程。

## 教师端

1.  在教师加入频道之前设置频道模式为互动模式。

    ```
    [self.engine setChannelProfile:AliRtcChannelProfileInteractivelive];
    ```

2.  在教师加入频道之前设置为非自动发布和自动订阅模式。

    ```
    [self.engine setAutoPublish:NO withAutoSubscribe:YES];
    ```

3.  在教师加入频道之前设置角色为AliRtcClientRoleInteractive。

    ```
    [self.engine setClientRole:AliRtcClientRoleInteractive];
    ```

    AliRtcClientRole参数取值：

    -   AliRtcClientRoleInteractive：参与互动角色，可以推拉流。
    -   AliRtcClientRolelive：仅观看角色，只能拉流，适用于普通观众。
    **说明：** setClientRole接口暂时不要处理接口返回值。

4.  加入频道。

    ```
    [self.engine joinChannel:authInfo name:name onResult:^(NSInteger errCode){
        if (errCode == 0) {
        //加入频道成功
        } else {
        //加入频道失败
        }
    }];
    ```

5.  调用publish接口开始发布。

    ```
    [self.engine configLocalAudioPublish:YES];
    [self.engine configLocalCameraPublish:YES];
    [self.engine publish:^(int err) {
    
    }];
    ```

    **说明：** 在调用publish接口前必须确保加入频道已经成功，否则调用publish接口会失败。

6.  远端用户推流、停止推流消息回调（学生端收到远端用户推流消息的回调与教师端相同）。

    ```
    /**
     * @brief 当远端用户的流发生变化时，返回这个消息
     * @note 远方用户停止推流，也会发送这个消息
     */
    - (void)onRemoteTrackAvailableNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack;
    ```

    **说明：**

    -   audioTrack取值为AliRtcAudioTrackNo并且videoTrack取值为AliRtcVideoTrackNo时，表示远端用户停止推流；其他情况表示远端用户对应的推流状态。
    -   加入频道之后也可设置角色，设置成功后可收到回调。

        ```
        - (void)onUpdateRoleNotifyWithOldRole:(AliRtcClientRole)oldRole newRole:(AliRtcClientRole)newRole;
        ```

    -   需要业务侧关注一下当前的角色参数值，例如当前是AliRtcClientRoleInteractive角色，再次调用以下接口将不会收到回调，建议业务侧将角色切换和推拉流的逻辑区分开。。

        ```
        [self.engine setClientRole:AliRtcClientRoleInteractive];
        ```


## 学生端

学生加入频道之前设置频道模式为互动模式。

```
[self.engine setChannelProfile:AliRtcInteractivelive];
```

普通观众：设置为互动模式后，默认角色类型为“仅观看角色”，也就是只可拉流观看直播，不能推流。此角色适用于普通观众，无需其他操作。

连麦观众：角色类型为“参与互动角色”，可以推流，操作步骤如下所示：

1.  开始上麦。

    1.  如果普通观众需要上麦切换为连麦观众的话，需要先切换用户角色。

    2.  切换角色为AliRtcClientRoleInteractive（需要在调用publish接口进行推流前）。

        ```
        [self.engine setClientRole:AliRtcClientRoleInteractive];
        ```

        切换成功后可收到回调。

        ```
        - (void)onUpdateRoleNotifyWithOldRole:(AliRtcClientRole)oldRole newRole:(AliRtcClientRole)newRole;
        ```

    3.  收到回调后，调用publish接口开始推流。

        ```
        [self.engine configLocalAudioPublish:YES];
        [self.engine configLocalCameraPublish:YES];
        [self.engine publish:^(int err) {
        }];
        ```

2.  下麦。

    与上麦逻辑相反，如果连麦观众需要下麦切换为普通观众的话，需要先停止推流，再进行角色切换。

    1.  停止推流。

        ```
        [self.engine configLocalAudioPublish:NO];
        [self.engine configLocalCameraPublish:NO];
        [self.engine publish:^(int err) {
        }];
        ```

    2.  停止推流收到回调之后，即可切换为普通观众角色。

        ```
        [self.engine setClientRole:AliRtcClientRolelive];
        ```

    3.  切换成功后可收到回调。

        ```
        - (void)onUpdateRoleNotifyWithOldRole:(AliRtcClientRole)oldRole newRole:(AliRtcClientRole)newRole;
        ```


