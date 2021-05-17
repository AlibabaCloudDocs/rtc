# Android媒体播放器集成与实现

媒体播放器组件（AliRtcPlayerExtension）是基于阿里云播放器开发的播放组件，支持播放主流的在线流媒体及本地资源。通过集成媒体播放器组件，您可以在本地播放或发布媒体资源给指定频道内的远端用户。

环境中已安装Android Studio 3.0或以上版本，更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 环境要求

|类别|要求|
|--|--|
|系统版本|支持Android 4.1或以上版本。|
|API版本|支持16及以上版本。|
|CPU架构|支持实体设备架构armeabi-v7a、arm64-v8a。|
|其他|不支持视频采集旋转，不支持USB外接摄像头。|

## 功能说明

-   目前支持播放的媒体格式有视频格式（MP4、M3U8、FLV、MKV）和音频格式（MP3），并且支持H.264、H.265视频编码和AAC音频编码。
-   使用[阿里云播放器](/cn.zh-CN/播放器SDK/产品说明.md)（AliyunPlayer）可实现本地播放媒体资源；阿里云RTC SDK实现实时音视频通信；AliRtcPlayerExtension支持将播放的媒体流发布给同频道中的远端用户，远端用户可以订阅并播放。
-   发布播放器画面到远端时，支持使用屏幕流通道，远端用户可通过订阅相机流和屏幕流，同时看到主播和播放器的画面。

## 集成开发环境

1.  创建Android studio项目，具体操作，请参见[Android Developers](https://developer.android.com/studio/projects/create-project)。

2.  集成阿里云RTC SDK，具体操作，请参见[集成客户端SDK](/cn.zh-CN/快速入门/集成客户端SDK/Android.md)。

    **说明：** 需要集成RTC SDK 1.17.46版本，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  集成阿里云播放器SDK，具体操作，请参见[Android端集成](/cn.zh-CN/播放器SDK/Android播放器/集成文档.md)。

    需要集成阿里云播放器SDK 5.3.4版本，如下所示：

    ```
    dependencies {
        implementation 'com.aliyun.sdk.android:AliyunPlayer:5.3.4-full-14838371'
    }
    ```

4.  集成媒体播放器组件。

    1.  下载并解压媒体播放器组件，下载地址，请参见[媒体播放器组件](/cn.zh-CN/SDK参考/SDK下载.mdsection_9a0_e3m_v6o)。

    2.  复制AliRtcPlayerExtension.aar文件至App模块下的libs文件夹中。

    3.  在项目的/app/build.gradle文件中，添加以下依赖：

        ```
         dependencies {
            implementation fileTree(include: ['*.jar','*.aar'], dir: 'libs')
        }
        ```


## 功能实现——本地播放媒体资源

集成阿里云播放器SDK后，您可以实现本地播放功能，步骤如下：

1.  创建播放器实例。

    通过AliPlayerFactory类创建播放器AliPlayer，创建方法如下所示：

    ```
    AliPlayer aliyunVodPlayer;
    .....
    aliyunVodPlayer = AliPlayerFactory.createAliPlayer(getApplicationContext());
    ```

2.  设置播放器监听事件。

    播放器提供了多种监听事件，通过监听这些事件，您可以更好地掌握播放过程，如果播放发生异常，您可以根据这些事件排查问题。回调详细说明请参见[接口说明](/cn.zh-CN/播放器SDK/Android播放器/接口说明.md)。示例如下所示：

    ```
    aliyunVodPlayer.setOnCompletionListener(new IPlayer.OnCompletionListener() {
        @Override
        public void onCompletion() {
            //播放完成事件
        }
    });
    aliyunVodPlayer.setOnErrorListener(new IPlayer.OnErrorListener() {
        @Override
        public void onError(ErrorInfo errorInfo) {
            //出错事件
        }
    });
    aliyunVodPlayer.setOnPreparedListener(new IPlayer.OnPreparedListener() {
        @Override
        public void onPrepared() {
            //准备成功事件
        }
    });
    aliyunVodPlayer.setOnVideoSizeChangedListener(new IPlayer.OnVideoSizeChangedListener() {
        @Override
        public void onVideoSizeChanged(int width, int height) {
            //视频分辨率变化回调
        }
    });
    aliyunVodPlayer.setOnRenderingStartListener(new IPlayer.OnRenderingStartListener() {
        @Override
        public void onRenderingStart() {
            //首帧渲染显示事件
        }
    });
    aliyunVodPlayer.setOnInfoListener(new IPlayer.OnInfoListener() {
        @Override
        public void onInfo(int type, long extra) {
            //其他信息的事件，type包括了：循环播放开始，缓冲位置，当前播放位置，自动播放开始等
        }
    });
    aliyunVodPlayer.setOnLoadingStatusListener(new IPlayer.OnLoadingStatusListener() {
        @Override
        public void onLoadingBegin() {
            //缓冲开始
        }
        @Override
        public void onLoadingProgress(int percent, float kbps) {
            //缓冲进度
        }
        @Override
        public void onLoadingEnd() {
            //缓冲结束
        }
    });
    aliyunVodPlayer.setOnSeekCompleteListener(new IPlayer.OnSeekCompleteListener() {
        @Override
        public void onSeekComplete() {
            //拖动结束
        }
    });
    aliyunVodPlayer.setOnSubtitleDisplayListener(new IPlayer.OnSubtitleDisplayListener() {
        @Override
        public void onSubtitleShow(long id, String data) {
            //显示字幕
        }
        @Override
        public void onSubtitleHide(long id) {
            //隐藏字幕
        }
    });
    aliyunVodPlayer.setOnTrackChangedListener(new IPlayer.OnTrackChangedListener() {
        @Override
        public void onChangedSuccess(TrackInfo trackInfo) {
            //切换音视频流或者清晰度成功
        }
        @Override
        public void onChangedFail(TrackInfo trackInfo, ErrorInfo errorInfo) {
            //切换音视频流或者清晰度失败
        }
    });
    aliyunVodPlayer.setOnStateChangedListener(new IPlayer.OnStateChangedListener() {
        @Override
        public void onStateChanged(int newState) {
            //播放器状态改变事件
        }
    });
    ```

3.  准备播放。

    1.  创建DataSource。

        此处以UrlSource为例，如下所示：

        ```
        UrlSource urlSource = new UrlSource();
        urlSource.setUri(播放资源地址);
        aliyunVodPlayer.setDataSource(urlSource);
         ......
         //准备播放
         aliyunVodPlayer.prepare();
        ```

    2.  设置显示的view。

        如果播放源有画面，需要将显示的view设置到播放器中用来显示画面，支持SurfaceView和TextureView。此处以SurfaceView为例，如下所示：

        ```
        surfaceView = (SurfaceView) findViewById(R.id.playview);
        surfaceView.getHolder().addCallback(new SurfaceHolder.Callback() {
            @Override
            public void surfaceCreated(SurfaceHolder holder) {
                aliyunVodPlayer.setDisplay(holder);
            }
            @Override
            public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {
                //调用播放器的redraw方法，用来刷新视频画面的。如果view的大小变化了，调用此方法将会更新画面大小，保证视频画面与View的变化一致
                aliyunVodPlayer.redraw();
            }
            @Override
            public void surfaceDestroyed(SurfaceHolder holder) {
                aliyunVodPlayer.setDisplay(null);
            }
        });
        ```

        **说明：** 本地screen流不预览，不需要设置view给RtcEngine。

    3.  创建播放器的播放控制按钮，在按钮事件里面实现播放器控制接口。

        基本的控制功能如下所示：

        ```
        //开始播放
        aliyunVodPlayer.start();
        //暂停播放
        aliyunVodPlayer.pause();
        //停止播放
        aliyunVodPlayer.stop();
        //跳转到，不精准
        aliyunVodPlayer.seekTo(long position);
        //重置
        aliyunVodPlayer.reset();
        //释放，释放后播放器将不可再被使用
        aliyunVodPlayer.release();
        ```

    更多功能使用方式，请参见[功能使用](/cn.zh-CN/播放器SDK/Android播放器/功能使用.md)。


## 功能实现——发布媒体资源到远端

集成完阿里云RTC SDK、阿里云播放器SDK、媒体播放器组件后，您可以发布媒体资源供频道内的远端用户订阅，步骤如下：

1.  初始化RTC SDK并加入频道。

    创建AliRtcEngine实例，实现本地用户以主播身份加入互动模式频道。

    ```
    RtcEngine aliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
    //设置频道模式为互动模式
    aliRtcEngine.setChannelProfile(AliRTCSDK_Channel_Profile.AliRTCSDK_Interactive_live);
    //加入频道之前设置角色为AliRTCSDK_Interactive
    aliRtcEngine.setClientRole(AliRTCSDK_Client_Role.AliRTCSDK_Interactive);
    //加入频道
    aliRtcEngine.joinChannel(aliRtcAuthInfo, userName);
    ```

    **说明：** 请确保收到[onJoinChannelResult](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)回调后再进行下一步操作。

2.  创建播放器并绑定指定频道。

    ```
    // 创建播放器实例
    AliPlayer aliyunVodPlayer = AliPlayerFactory.createAliPlayer(getApplicationContext());
    // RTC默认使用通话模式，建议将播放器设置成一致的模式，防止出现双音量条的现象
    AliPlayerGlobalSettings.setAudioStreamType(AliPlayerGlobalSettings.StreamType.STREAM_VOICE_CALL);
    // 播放器使用软解播放（目前Android播放器转推yuv，需使用软解播放，需业务层调用enableHardwareDecoder为false，在后续版本将支持硬解转推）
    aliyunVodPlayer.enableHardwareDecoder(false);
    
    //如果业务层未单独保存播放器相关日志，建议将播放器关键日志绑定到RTC，方便问题分析
    AliRtcPlayerExtension.enablePlayerLogger(view.getContext().getApplicationContext(), true);
    // 获取AliRtcPlayerExtension实例，并绑定播放器和RtcEngine
    AliRtcPlayerExtension rtcPlayerExtension = AliRtcPlayerExtension.getInstance();
    rtcPlayerExtension.bindPlayerToRtcEngine(aliyunVodPlayer, aliRtcEngine);
    ```

3.  发布媒体资源。

    ```
    //使用屏幕流时，需调用configLocalScreenPublish打开屏幕流
    aliRtcEngine.configLocalScreenPublish(true);
    
    // 使用播放器播放本地或在线资源（参见本地播放媒体资源）
    
    // 发布播放器媒体流
    rtcPlayerExtension.publishVideo(AliRtcEngine.AliRtcVideoTrack.AliRtcVideoTrackScreen, AliRtcEngine.AliRtcRenderMode.AliRtcRenderModeAuto);
    rtcPlayerExtension.publishAudio(false);
    ```

    **说明：** AliRtcPlayerExtension会设置播放器音频为mute状态，当调用publishAudio后，通过RtcEngine进行音频播放，实现回声消除等功能。

    您可以调用`setExternalAudioPublishVolume`方法调节远端用户听到的音量，或者调用`setExternalAudioPlayoutVolume`方法调节本地用户的播放音量。

4.  取消发布媒体资源并解绑定频道。

    ```
    aliRtcEngine.configLocalScreenPublish(false);
    rtcPlayerExtension.unpublishVideo();
    rtcPlayerExtension.unpublishAudio();
    
    // 取消播放器和RtcEngine的绑定
    rtcPlayerExtension.unbindPlayerFromRtcEngine();
    ```


