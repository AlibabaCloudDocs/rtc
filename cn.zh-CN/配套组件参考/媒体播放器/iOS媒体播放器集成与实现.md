# iOS媒体播放器集成与实现

媒体播放器组件（AliRtcPlayerExtension）是基于阿里云播放器开发的播放组件，支持播放主流的在线流媒体及本地资源。通过集成媒体播放器组件，您可以在本地播放或发布媒体资源给指定频道内的远端用户。

-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 环境要求

|类别|要求|
|--|--|
|系统版本|支持iOS 8.0及以上版本。|
|硬件设备|-   iPhone：支持iPhone5及之后的设备。
-   iPad：均支持。 |
|CPU架构|支持实体设备架构armv7+arm64（模拟器i386、x86架构仅支持编译）。|
|其他|不支持bitcode，不支持屏幕旋转。|

## 功能说明

-   目前支持播放的媒体格式有视频格式（MP4、M3U8、FLV、MKV）和音频格式（MP3），并且支持H.264、H.265视频编码和AAC音频编码。
-   使用[阿里云播放器](/cn.zh-CN/播放器SDK/产品说明.md)（AliyunPlayer）可实现本地播放媒体资源；阿里云RTC SDK实现实时音视频通信；AliRtcPlayerExtension支持将播放的媒体流发布给同频道中的远端用户，远端用户可以订阅并播放。
-   发布播放器画面到远端时，支持使用屏幕流通道，远端用户可通过订阅相机流和屏幕流，同时看到主播和播放器的画面。

## 集成开发环境

1.  创建Xcode项目，具体操作，请参见[Create a project](https://help.apple.com/xcode/mac/current/#/dev07db0e578)。

2.  集成阿里云RTC SDK，具体操作，请参见[集成客户端SDK](/cn.zh-CN/快速入门/集成客户端SDK/iOS.md)。

    **说明：** 需要集成RTC SDK 1.17.48及以上版本，目前暂不支持RTC SDK 2.1版本，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  集成阿里云播放器SDK，具体操作，请参见[iOS端集成](/cn.zh-CN/播放器SDK/iOS播放器/集成文档.md)。

    需要集成阿里云播放器SDK 5.3.4版本，建议使用pod方式集成，如下所示：

    ```
    target 'Your App' do
        pod 'AliPlayerSDK_iOS', '~> version', '5.3.4'
    end
    ```

4.  集成媒体播放器组件。

    1.  下载并解压媒体播放器组件，下载地址，请参见[组件下载](/cn.zh-CN/配套组件参考/组件下载.md)。

    2.  将解压后的媒体播放器组件文件复制到工程中。

    3.  在业务代码中导入头文件。

        ```
        #import "AliRtcPlayerExtension.h"
        ```


## 功能实现——本地播放媒体资源

集成阿里云播放器SDK后，您可以实现本地播放功能，步骤如下：

1.  创建播放器实例。

    ```
    self.player = [[AliPlayer alloc] init];
    ```

2.  设置播放器监听事件。

    播放器提供了多种监听事件，通过监听这些事件，您可以更好地掌握播放过程，如果播放发生异常，您可以根据这些事件排查问题。回调详细说明请参见[接口说明](/cn.zh-CN/播放器SDK/iOS播放器/接口说明.md)。示例如下所示：

    ```
    @interface SimplePlayerViewController ()<AVPDelegate>
    @end
    - (void)viewDidLoad {
        self.player = [[AliPlayer alloc] init];
        self.player.playerView = self.avpPlayerView.playerView;
        self.player.delegate = self;
        //...
    }
    /**
     @brief 错误代理回调
     @param player 播放器player指针
     @param errorModel 播放器错误描述，参考AliVcPlayerErrorModel
     */
    - (void)onError:(AliPlayer*)player errorModel:(AVPErrorModel *)errorModel {
        //提示错误，及stop播放
    }
    /**
     @brief 播放器事件回调
     @param player 播放器player指针
     @param eventType 播放器事件类型，@see AVPEventType
     */
    -(void)onPlayerEvent:(AliPlayer*)player eventType:(AVPEventType)eventType {
        switch (eventType) {
            case AVPEventPrepareDone: {
                // 准备完成
            }
                break;
            case AVPEventAutoPlayStart:
                // 自动播放开始事件
                break;
            case AVPEventFirstRenderedStart:
                // 首帧显示
                break;
            case AVPEventCompletion:
                // 播放完成
                break;
            case AVPEventLoadingStart:
                // 缓冲开始
                break;
            case AVPEventLoadingEnd:
                // 缓冲完成
                break;
            case AVPEventSeekEnd:
                // 跳转完成
                break;
            case AVPEventLoopingStart:
                // 循环播放开始
                break;
            default:
                break;
        }
    }
    /**
     @brief 视频当前播放位置回调
     @param player 播放器player指针
     @param position 视频当前播放位置
     */
    - (void)onCurrentPositionUpdate:(AliPlayer*)player position:(int64_t)position {
        // 更新进度条
    }
    //...
    ```

3.  准备播放。

    1.  创建DataSource。

        此处以AVPUrlSource为例，调用AliPlayer接口的prepare准备播放，支持网络路径或本地路径。如下所示：

        ```
        AVPUrlSource *source = [[AVPUrlSource alloc] urlWithString:@"播放地址"];
        [self.player setUrlSource:source];
        [self.player prepare];
        ```

        **说明：** 请确保收到`onPlayerEvent`回调播放状态为AVPEventPrepareDone后再进行下一步操作。

    2.  设置显示的view及播放控制。

        ```
        //设置view
        self.player.playerView = self.avpPlayerView.playerView;//用户显示的view
        // 开始播放
        [self.player start];
        //暂停播放
        [self.player pause];
        //停止播放
        [self.player stop];
        // 跳转到，目前只支持不精准
        [self.player seekToTime:position seekMode:AVP_SEEKMODE_INACCURATE];
        // 重置
        [self.player reset];
        //释放，释放后播放器将不可再被使用
        [self.player destroy];
        self.player = nil;
        ```

        **说明：** 本地screen流不预览，不需要设置view给RtcEngine。

    更多功能使用方式，请参见[功能使用](/cn.zh-CN/播放器SDK/iOS播放器/功能使用.md)。


## 功能实现——发布媒体资源到远端

集成完阿里云RTC SDK、阿里云播放器SDK、媒体播放器组件后，您可以发布媒体资源供频道内的远端用户订阅，步骤如下：

1.  初始化RTC SDK并加入频道。

    创建AliRtcEngine实例，实现本地用户以主播身份加入互动模式频道。

    ```
    // 创建RtcEngine
    self.engine = [AliRtcEngine sharedInstance:selfextras:@""];
    //设置频道模式为互动模式
    [self.engine setChannelProfile:AliRtcInteractivelive];
    //设置角色为AliRTCSDK_Interactive
    [self.engine setClientRole:AliRtcClientRoleInteractive];
    //加入频道
    [self.engine joinChannel:authInfo name:name onResult:^(NSInteger errCode){
        if (errCode == 0) {
        //加入频道成功
        } else {
        //加入频道失败
        }
    }];
    ```

    **说明：** 请确保收到[onJoinChannelResult](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)回调后再进行下一步操作。

2.  创建播放器并绑定指定频道。

    ```
    //创建播放器对象
    self.player = [[AliPlayer alloc]init];
    self.player.delegate = self;
    self.player.playerView = self.containerView;
    
    //如果业务层未单独保存播放器相关日志，建议将播放器关键日志绑定到RTC，方便问题分析
    [AliRtcPlayerExtension enablePlayerLogger:YES];
    //创建AliRtcPlayerExtension对象并绑定AliRtcEngine对象
    self.playerExtension = [AliRtcPlayerExtension shareInstance];
    [self.playerExtension bindPlayerToRtcEngine:self.player engine:self.engine]
    ```

3.  发布媒体资源。

    ```
    //使用屏幕流时，需调用configLocalScreenPublish打开屏幕流
    [self.engine configLocalScreenPublish:YES];
    
    // 使用播放器播放本地或在线资源（参考本地播放媒体资源）。
    
    // 分享播放器媒体流给远端用户
    [self.playerExtension publishAudio:NO];
    [self.playerExtension publishVideo:AliRtcVideosourceScreenShareType renderMode:AliRtcRenderModeAuto];
    ```

    **说明：** AliRtcPlayerExtension会设置播放器音频为mute状态，当调用publishAudio后，通过RtcEngine进行音频播放，实现回声消除等功能。

    您可以调用`setExternalAudioPublishVolume`方法调节远端用户听到的音量，或者调用`setExternalAudioPlayoutVolume`方法调节本地用户的播放音量。

4.  取消发布媒体资源并解绑定频道。

    ```
    [self.engine configLocalScreenPublish:NO];
    [self.playerExtension unpublishVideo];
    [self.playerExtension unpublishAudio];
    
    // 取消播放器和RtcEngine的绑定
    [self.playerExtension unbindPlayerFromRtcEngine];
    ```


