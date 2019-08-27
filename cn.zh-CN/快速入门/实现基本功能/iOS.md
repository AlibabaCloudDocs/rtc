# iOS {#task_1180893 .task}

阿里云音视频通信的基本功能包含初始化SDK、加入频道、本地发布和订阅远端、离开频道等。当您成功初始化SDK，您可以进行本地预览视频功能，进行简单的预览和测试，您也可以设置手动或者自动模式。

在实现基本功能前，请您确保下载最新SDK，请参见[SDK下载](../../../../cn.zh-CN/快速入门/SDK下载.md#)。

**说明：** 本文中的实现方法为主要功能方法，仅供参考，您可以根据您的业务需求进行实际开发。

1.  请您先初始化SDK。 

    首先您需要创建AliRtcEngine实例，并注册AliRtcEngineDelegate监听相关回调。如果您在ViewController中持有AliRtcEngine实例，请声明属性。

    ``` {#codeblock_mx1_gvr_pgd}
    @interface ViewController () <AliRtcEngineDelegate>
    @property (nonatomic, strong) AliRtcEngine *engine;
    @end          
    ```

    创建SDK实例并注册delegate。

    iOS回调详情请参见[回调及监听](../../../../cn.zh-CN/API参考/iOS SDK/接口说明/回调及监听.md#)。

    ``` {#codeblock_tpn_i2f_tra}
    self.engine = [AliRtcEngine sharedInstance:self extras:@""];            
    ```

    **说明：** 目前SDK暂不支持多实例。

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas进行本地预览视频。 

        ``` {#codeblock_vmb_8zz_ji4}
        AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
        canvas.renderMode = AliRtcRenderModeAuto;
        canvas.view = (AliRenderView *)view; /* 预览窗口view */
        canvas.mirrorMode = AliRtcRenderMirrorModeOnlyFrontCameraPreviewEnabled;
        [self.engine setLocalViewConfig:canvas forTrack:AliRtcVideoTrackCamera];
        [self.engine startPreview];           
        ```

        您也可以取消本地预览。

        ``` {#codeblock_q59_fw7_9hm}
        [self.engine stopPreview];           
        ```

        **说明：** 

        -   renderMode提供四种模式：Auto、Stretch、Fill、Crop，建议使用Auto模式。
        -   view必须是AliRenderView或者其子类。
        -   mirrorMode在本地或远端均可设置镜像模式。
        -   mirrorMode提供三种模式：OnlyFrontCameraPreviewEnabled、AllEnabled、AllDisabled。
    2.  设置自动或者手动模式。 

        **说明：** 阿里云音视频通信iOS端默认实现自动发布和订阅，您也可以通过代码手动发布和订阅。

        -   自动Publish模式： 如果您打开自动Publish模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动Publish模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动Subscribe模式： 如果您打开自动Subscribe模式，加入频道之后，SDK将会自动订阅当前频道内其他用户的音视频流；如果关闭自动Subscribe模式，则需要您调用subscribe接口之后才会订阅其他用户的音视频流。
        ``` {#codeblock_nia_cfc_akw}
        /*
        设置自动发布和订阅，只能在joinChannel之前配置
        autoPublish: YES表示自动发布，NO表示手动发布
        autoSubscribe: YES表示自动订阅，NO表示手动订阅
        */ 
        [self.engine setAutoPublish:YES withAutoSubscribe:YES];          
        ```

2.  加入频道。 

    **说明：** AliRtcAuthInfo的各项参数均需要App Server通过API来获取，然后App Server下发至客户端，客户端将各项参数赋值后，就可以加入频道。

    -   name：无需APP Server下发。
    -   channelID 、userID、name命名要求：字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节，非法命名系统将拒绝提供服务。
    ``` {#codeblock_o07_39d_hez}
    AliRtcAuthInfo *authinfo = [[AliRtcAuthInfo alloc]init];
    authinfo.channel   = /* 您的channelId */;
    authinfo.appid     = /* 您的Appid */;
    authinfo.token     = /* 您的token */;
    authinfo.nonce     = /* 您的nonce */;
    authinfo.user_id   = /* 您的userId */;
    authinfo.token     = /* 您的token */;
    authinfo.timestamp = /* 您的timestamp */;
    authinfo.gslb      = /* 您的gslb地址 */;
    [self.engine joinChannel:authinfo name:/* userName */ onResult:^(NSInteger errCode){
        // 加入频道UI处理
    }]; 
    ```

3.  发布或取消发布本地流。 

    发布本地流。

    -   自动pub模式下：加入频道成功后，即可发布本地流，无需再次调用publish接口。
    -   非自动pub模式下：加入成功后，可通过以下接口发布本地流。
    如果publish过程中需要变更配置或者停止publish，需要按如下流程先重新设置配置参数，然后再调用publish接口。

    ``` {#codeblock_boc_b1y_jjb}
    //YES表示允许发布音频流，NO表示不允许
    [self.engine configLocalAudioPublish:YES];
    //YES表示允许发布相机流，NO表示不允许
    [self.engine configLocalCameraPublish:YES];
    //YES表示允许发布次要视频流；NO表示不允许
    [self.engine configLocalSimulcast:YES forTrack:AliRtcVideoTrackCamera];
    [self.engine publish:^(int err) {
        // publish相关UI操作
    }];           
    ```

    取消发布本地流。

    ``` {#codeblock_rmi_ec5_uaq}
    [self.engine configLocalAudioPublish:NO];
    [self.engine configLocalCameraPublish:NO];
    [self.engine configLocalSimulcast:NO forTrack:AliRtcVideoTrackCamera];
    [self.engine publish:^(int err) {
        // publish取消相关UI操作
    }];          
    ```

4.  订阅或取消订阅远程流。 

    订阅远程流。

    -   自动sub模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
    -   非自动sub模式下：加入频道成功后，可通过以下接口订阅远端流。
    如果subscribe过程中需要变更配置或者停止subscribe，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

    ``` {#codeblock_0yx_n6p_bee}
    //YES表示允许订阅音频流，NO表示不允许
    [self.engine configRemoteAudio:/* remoteUserID */ enable:YES];
    //YES表示允许订阅屏幕流，NO表示不允许
    [self.engine configRemoteScreenTrack:/* remoteUserID */ enable:YES];
    //第二个参数：YES表示优先拉取大流
    //第三个参数：YES表示允许订阅相机流，NO表示不允许
    [self.engine configRemoteCameraTrack:/* remoteUserID */ preferMaster:YES enable:YES];
    [self.engine subscribe:/* remoteUserID */ onResult:^(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
    }];          
    ```

    无论是自动模式还是非自动模式，当您订阅成功后，通过delegate可以获取订阅的callback，然后您可以进行相关UI操作或逻辑处理。

    ``` {#codeblock_ue0_e5y_yy5}
    - (void)onSubscribeChangedNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack {
        dispatch_async(dispatch_get_main_queue(), ^{
            // UI或者逻辑处理，例如渲染远端视频流的操作如下
            if(videoTrack & AliRtcVideoTrackCamera) {
            // camera track
            AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
            canvas.renderMode = /* renderMode */;
            canvas.view = (AliRenderView *)view;/* 渲染view */
            [self.engine setRemoteViewConfig:canvas uid:uid forTrack:AliRtcVideoTrackCamera];
          }
        });
    }           
    ```

    您可以通过下述delegate回调监听远端用户的流状态变更。例如，手动模式下，收到此回调后，可以获取到远端用户的发布状态，然后相应做出订阅（subscribe）操作，或者更新UI等。

    ``` {#codeblock_dfh_pn2_4v4}
    - (void)onRemoteTrackAvailableNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack {
    }           
    ```

    取消订阅远程流。

    ``` {#codeblock_kxu_gc3_tez}
    [self.engine configRemoteAudio:/* remoteUserID */ enable:NO];
    [self.engine configRemoteScreenTrack:/* remoteUserID */ enable:NO];
    [self.engine configRemoteCameraTrack:/* remoteUserID */ preferMaster:YES enable:NO];
    [self.engine subscribe:/* remoteUserID */ onResult:^(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
    }];            
    ```

5.  离开频道。 

    ``` {#codeblock_eli_2vb_pvu}
    [self.engine leaveChannel];           
    ```

     您可以下载示例代码，快速跑通Demo，实现频道内和其他用户进行实时音视频通话，详情请参见[iOS Demo](../../../../cn.zh-CN/Demo/iOS Demo.md#)。


