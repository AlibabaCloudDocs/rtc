---
keyword: [基本功能, iOS]
---

# iOS

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、订阅远端和离开频道等。通过阅读本文，您可以了解阿里云RTC的基本功能。

-   您已下载并集成最新版本的SDK。具体操作，请参见[iOS端集成SDK](/cn.zh-CN/快速入门/集成客户端SDK/iOS.md)。
-   您已获取加入频道必需的频道鉴权令牌（Token）。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 使用限制

本文仅供SDK 2.1及以上版本使用，如果您需要SDK 1.17版本对应的文档，请[提交工单](https://selfservice.console.aliyun.com/ticket/createIndex.htm)获取。

## 操作步骤

**说明：** 本文中的实现方法仅供参考，您可以根据实际业务需求进行开发。

1.  初始化SDK。

    您需要创建AliRtcEngine实例，并注册回调。如果您在ViewController中持有AliRtcEngine实例，请声明属性。具体回调接口请参见[回调及监听](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)。

    ```
    @interface ViewController () <AliRtcEngineDelegate>
    @property (nonatomic, strong) AliRtcEngine *engine;
    @end
    ```

    ```
    self.engine = [AliRtcEngine sharedInstance:self extras:@""]; 
    ```

    1.  本地预览。在创建完AliRtcEngine实例后，您可以创建canvas布局进行本地预览视频。

        ```
        AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
        canvas.renderMode = AliRtcRenderModeAuto;
        canvas.view = view; /* 预览窗口view，iOS为UIView对象，Mac为NSView对象*/
        canvas.mirrorMode = AliRtcRenderMirrorModeOnlyFrontCameraPreviewEnabled;
        [self.engine setLocalViewConfig:canvas forTrack:AliRtcVideoTrackCamera];
        [self.engine startPreview];  
        ```

        **说明：**

        -   AliRtcRenderMode提供四种渲染模式：
            -   AliRtcRenderModeAuto（推荐）：自动。
            -   AliRtcRenderModeStretch：拉伸填充视图，不保持视频比例。
            -   AliRtcRenderModeFill：在保持视频宽高比的同时缩放，填充黑边。
            -   AliRtcRenderModeCrop：在保持视频宽高比的同时缩放，并裁剪以适合视图。
        -   AliRtcRenderMirrorMode在本地或远端均可设置镜像模式，并提供三种镜像模式：
            -   AliRtcRenderMirrorModeOnlyFrontCameraPreviewEnabled：只有前置摄像头预览镜像，其余不镜像。
            -   AliRtcRenderMirrorModeAllEnabled：全部镜像。
            -   AliRtcRenderMirrorModeAllDisabled：全部不镜像。
    2.  取消本地预览。

        ```
        [self.engine stopPreview];  
        ```

    3.  设置发布与订阅。

        -   SDK默认入会后自动发布音频流与视频流，如果您不希望自动发布音频和视频，可以在入会前通过以下接口设置：

            ```
            [self.engine publishLocalAudioStream:NO];//默认不发布音频流
            [self.engine publishLocalVideoStream:NO];//默认不发布视频流
            ```

        -   SDK默认入会后自动订阅远端的音频流与视频流，如果您不希望自动订阅音频与视频，可以在入会前通过以下接口设置：

            ```
            [self.engine setDefaultSubscribeAllRemoteAudioStreams:NO];//默认不订阅音频流
            [self.engine setDefaultSubscribeAllRemoteVideoStreams:NO];//默认不订阅视频流
            ```

2.  加入频道。

    ```
    AliRtcAuthInfo *authinfo = [[AliRtcAuthInfo alloc]init];
    authinfo.channelId   = /* 您的channelId */;
    authinfo.appId     = /* 您的Appid */;
    authinfo.nonce     = /* 您的nonce */;
    authinfo.userId   = /* 您的userId */;
    authinfo.token     = /* 您的token */;
    authinfo.timestamp = /* 您的timestamp */;
    authinfo.gslb      = /* 您的gslb地址 */;
    [self.engine joinChannel:authinfo name:@"userName" onResult:^(NSInteger errCode,NSString * _Nonnull channel,NSInteger elapsed){
         // 加入频道UI处理
    }];
    ```

    |参数|描述|
    |--|--|
    |appId|应用ID，在控制台**应用管理**页面创建和查看。|
    |channelId|频道ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。|
    |userId|用户ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。 **说明：** 同一个用户ID在其他端登录，先入会的端会被后入会的端踢出频道。 |
    |nonce|随机码。以前缀AK-开头，由大小写字母、数字组成，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |timestamp|过期时间戳。可以选择12小时、24小时、3天和7天，代表令牌有效时间。|
    |token|频道鉴权令牌，计算方法：`token = sha256(appId + appKey + channelId + userId + nonce + timestamp)`。|
    |gslb|服务地址，该参数是数组类型，当前请使用：`["https://rgslb.rtc.aliyuncs.com"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

3.  发布或取消发布本地流。

    -   发布本地音频流和视频流

        如果您在入会前没有设置发布音频流和视频流，则入会后会自动发布本地的音频流和视频流；如果您在入会前设置取消发布音频流和视频流，则入会后需要调用以下接口进行手动发布：

        ```
        [self.engine publishLocalAudioStream:YES];//发布音频流
        [self.engine publishLocalVideoStream:YES];//发布视频流
        ```

    -   发布小流

        SDK默认不发布小流，如果您需要推送小流，请调用以下接口（入会前、后均可调用）：

        ```
        [self.engine publishLocalDualStream:YES];
        ```

    -   取消发布本地音频流和视频流

        如果您需要取消发布本地的音频流和视频流，请调用以下接口：

        ```
        [self.engine publishLocalAudioStream:NO];//取消发布音频流
        [self.engine publishLocalVideoStream:NO];//取消发布视频流
        ```

4.  订阅或取消订阅远程流。

    -   订阅远端音频流和视频流

        如果您在入会前没有设置订阅音频流和视频流，则入会后会自动订阅远端的音频流和视频流；如果您在入会前设置取消订阅音频流和视频流，则入会后需要调用以下接口进行手动订阅：

        ```
        [self.engine setDefaultSubscribeAllRemoteAudioStreams:YES];//订阅全部的远端音频流
        [self.engine setDefaultSubscribeAllRemoteVideoStreams:YES];//订阅全部的远端视频流
        ```

        **说明：** 此接口作用于后续入会的远端用户，对于调用此接口之前已经入会的远端用户，此接口不产生影响。

        订阅成功后，您可以在onRemoteTrackAvailableNotify回调里渲染远端的视频画面：

        ```
        - (void)onRemoteTrackAvailableNotify:(NSString *_Nonnull)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack {
            dispatch_async(dispatch_get_main_queue(), ^{
                // UI或者逻辑处理，例如渲染远端视频流的操作如下。
                if(videoTrack == AliRtcVideoTrackCamera) {
                // camera track
                AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
                canvas.renderMode = /* renderMode */;
                canvas.view = view;/* 渲染view */
                [self.engine setRemoteViewConfig:canvas uid:uid forTrack:AliRtcVideoTrackCamera];
              }
            });
        }  
        ```

    -   取消订阅远端音频流和视频流

        如果您需要取消订阅远端的音频流和视频流，请调用以下接口：

        ```
        [self.engine setDefaultSubscribeAllRemoteAudioStreams:NO];//订阅全部的远端音频流
        [self.engine setDefaultSubscribeAllRemoteVideoStreams:NO];//订阅全部的远端视频流
        ```

        **说明：** 此接口作用于后续入会的远端用户，对于调用此接口之前已经入会的远端用户，此接口不产生影响。

    -   订阅特定用户的音频流和视频流

        当已取消订阅所有的音频流和视频流之后，如果您需要订阅某个远端用户的音频流和视频流，可以通过调用以下接口实现（如果需要取消订阅此远端用户的音频流和视频流，参数sub传入NO即可）：

        ```
        [self.engine subscribeRemoteAudioStream:uid sub:YES];//订阅特定用户的音频流
        [self.engine subscribeRemoteVideoStream:uid track:AliRtcVideoTrackCamera sub:YES];//订阅特定用户的视频流
        ```

    -   订阅小流

        如果您需要订阅小流，请调用以下接口：

        ```
        [self.engine setRemoteDefaultVideoStreamType:AliRtcVideoStreamTypeLow];
        ```

        **说明：** 此接口作用于后续入会的远端用户，对于调用此接口之前已经入会的远端用户，此接口不产生影响。

    -   取消订阅所有远端用户音频流和视频流

        如果您希望当前会议中及后续入会的用户全部取消订阅，请调用以下接口：

        ```
        [self.engine subscribeAllRemoteAudioStreams:NO];
        [self.engine subscribeAllRemoteVideoStreams:NO];
        ```

        **说明：**

        -   当以上接口设置为NO时，优先级最高，即使setDefaultSubscribeAllRemoteAudioStreams和setDefaultSubscribeAllRemoteVideoStreams设置为YES时也不生效。
        -   当以上接口设置为YES时，是否订阅以setDefaultSubscribeAllRemoteAudioStreams和setDefaultSubscribeAllRemoteVideoStreams设置为准。
5.  离开频道。

    ```
    [self.engine leaveChannel]; 
    ```


您可以下载示例代码，快速运行Demo，实现频道内和其他人进行实时音视频通话，详情请参见[运行iOS Demo](/cn.zh-CN/快速入门/运行Demo示例/运行iOS Demo.md)。

