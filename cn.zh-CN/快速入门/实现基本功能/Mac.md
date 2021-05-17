---
keyword: [基本功能, Mac]
---

# Mac

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、订阅远端和离开频道等。通过阅读本文，您可以了解阿里云RTC的基本功能。

-   您已下载并集成最新版本的SDK。具体操作，请参见[Mac端集成SDK](/cn.zh-CN/快速入门/集成客户端SDK/Mac.md)。
-   您已获取加入频道必需的频道鉴权令牌（Token）。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 操作步骤

**说明：** 本文中的实现方法仅供参考，您可以根据实际业务需求进行开发。

1.  初始化SDK。

    您需要创建AliRtcEngine实例，并注册AliRtcEngineDelegate监听相关回调。如果您在ViewController中持有AliRtcEngine实例，请声明属性。

    ```
    @interface ViewController () <AliRtcEngineDelegate>
    @property (nonatomic, strong) AliRtcEngine *engine;
    @end          
    ```

    Mac回调详情请参见[回调及监听](/cn.zh-CN/SDK参考/iOS和Mac SDK/iOS和Mac SDK（v1.17）/回调及监听.md)。

    ```
    self.engine = [AliRtcEngine sharedInstance:self extras:@""];            
    ```

    **说明：** 目前暂不支持多实例。

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas布局进行本地预览视频。

        ```
        AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
        canvas.renderMode = AliRtcRenderModeAuto;
        canvas.view = (AliRenderView *)view; /* 预览窗口view */
        canvas.mirrorMode = AliRtcRenderMirrorModeOnlyFrontCameraPreviewEnabled;
        [self.engine setLocalViewConfig:canvas forTrack:AliRtcVideoTrackCamera];
        [self.engine startPreview];           
        ```

        **说明：**

        -   AliRtcRenderMode提供四种渲染模式。
            -   （推荐）AliRtcRenderModeAuto：自动模式。
            -   AliRtcRenderModeStretch：拉伸填充视图，不保持视频比例。
            -   AliRtcRenderModeFill：在保持视频宽高比的同时缩放，填充黑边。
            -   AliRtcRenderModeCrop：在保持视频宽高比的同时缩放，并裁剪以适合视图。
        -   view必须是AliRenderView或者其子类。
        -   AliRtcRenderMirrorMode在本地或远端均可设置镜像模式，并提供三种镜像模式。
            -   AliRtcRenderMirrorModeOnlyFrontCameraPreviewEnabled：只有前置摄像头预览镜像，其余不镜像。
            -   AliRtcRenderMirrorModeAllEnabled：全部镜像。
            -   AliRtcRenderMirrorModeAllDisabled：全部不镜像。
        您也可以取消本地预览。

        ```
        [self.engine stopPreview];           
        ```

    2.  设置自动或者手动模式。

        **说明：** 默认实现自动发布和订阅，您也可以通过代码手动发布和订阅。

        -   自动发布模式： 如果您打开自动发布模式，加入频道之后，SDK将自动开始发布音视频流；如果关闭自动发布模式，则需要您调用publish接口之后才会发布音视频流。
        -   自动订阅模式： 如果您打开自动订阅模式，加入频道之后，SDK将会自动订阅当前频道内其他人的音视频流；如果关闭自动订阅模式，则需要您调用subscribe接口之后才会订阅其他人的音视频流。
        ```
        /*
        设置自动发布和订阅，只能在加入频道之前配置。
        autoPublish：是否自动发布。取值：YES|NO。
        autoSubscribe：是否自动订阅。取值：YES|NO。
        */ 
        [self.engine setAutoPublish:YES withAutoSubscribe:YES];          
        ```

2.  加入频道。

    ```
    AliRtcAuthInfo *authinfo = [[AliRtcAuthInfo alloc]init];
    authinfo.channel   = /* 您的channelId */;
    authinfo.appid     = /* 您的Appid */;
    authinfo.nonce     = /* 您的nonce */;
    authinfo.user_id   = /* 您的userId */;
    authinfo.token     = /* 您的token */;
    authinfo.timestamp = /* 您的timestamp */;
    authinfo.gslb      = /* 您的gslb地址 */;
    [self.engine joinChannel:authinfo name:/* userName */ onResult:^(NSInteger errCode){
        // 加入频道UI处理
    }]; 
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
        //YES表示允许发布音频流，NO表示不允许。
        [self.engine configLocalAudioPublish:YES];
        //YES表示允许发布相机流，NO表示不允许。
        [self.engine configLocalCameraPublish:YES];
        //YES表示允许发布次要视频流；NO表示不允许。
        [self.engine configLocalSimulcast:YES forTrack:AliRtcVideoTrackCamera];
        [self.engine publish:^(int err) {
        }];           
        ```

    -   取消发布本地流

        ```
        [self.engine configLocalAudioPublish:NO];
        [self.engine configLocalCameraPublish:NO];
        [self.engine configLocalSimulcast:NO forTrack:AliRtcVideoTrackCamera];
        [self.engine publish:^(int err) {
        }];          
        ```

4.  订阅或取消订阅远程流。

    -   订阅远程流

        -   自动订阅模式下：加入频道成功后，即可订阅远端流，无需再次调用subscribe接口。
        -   手动订阅模式下：加入频道成功后，可通过以下接口订阅远端流。
        如果订阅过程中需要变更配置或者停止订阅，需要按如下流程先重新设置配置参数，然后再调用subscribe接口。

        ```
        //YES表示允许订阅音频流，NO表示不允许。
        [self.engine configRemoteAudio:/* remoteUserID */ enable:YES];
        //YES表示允许订阅屏幕流，NO表示不允许。
        [self.engine configRemoteScreenTrack:/* remoteUserID */ enable:YES];
        //第二个参数：YES表示优先拉取大流。
        //第三个参数：YES表示允许订阅相机流，NO表示不允许。
        [self.engine configRemoteCameraTrack:/* remoteUserID */ preferMaster:YES enable:YES];
        [self.engine subscribe:/* remoteUserID */ onResult:^(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
        }];          
        ```

        无论是自动模式还是非自动模式，当您订阅成功后，通过delegate可以获取订阅的callback，然后您可以进行相关UI操作或逻辑处理。

        ```
        - (void)onSubscribeChangedNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack {
            dispatch_async(dispatch_get_main_queue(), ^{
                // UI或者逻辑处理，例如渲染远端视频流的操作如下。
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

        ```
        - (void)onRemoteTrackAvailableNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack {
        }           
        ```

    -   取消订阅远程流

        ```
        [self.engine configRemoteAudio:/* remoteUserID */ enable:NO];
        [self.engine configRemoteScreenTrack:/* remoteUserID */ enable:NO];
        [self.engine configRemoteCameraTrack:/* remoteUserID */ preferMaster:YES enable:NO];
        [self.engine subscribe:/* remoteUserID */ onResult:^(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at) {
        }];            
        ```

5.  离开频道。

    ```
    [self.engine leaveChannel];           
    ```


您可以下载示例代码，快速运行Demo，实现频道内和其他人进行实时音视频通话，详情请参见[运行Mac Demo](/cn.zh-CN/快速入门/运行Demo示例/运行Mac Demo.md)。

