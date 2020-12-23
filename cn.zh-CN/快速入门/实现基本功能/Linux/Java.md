---
keyword: [Linux, rtc, Java]
---

# Java

阿里云RTC的基本功能包含创建实例、加入频道、本地发布、录制和离开频道等。

在实现基本功能前，请您确保下载最新SDK，请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

获得加入频道必须的频道鉴权令牌（Token）：

-   您可以在控制台生成临时Token校验加入频道是否成功，详情请参见[控制台生成Token](/cn.zh-CN/常用功能/生成Token.md)。
-   在安全要求更高的场景下，建议您在服务端生成Token，详情请参见[服务端生成Token](/cn.zh-CN/常用功能/生成Token.md)。

**说明：** 本文中的实现方法为主要功能方法，仅供参考，您可以根据业务需求进行实际开发。

1.  初始化SDK。

    ```
    AliRTCLinuxEngineListener engineEventHandler = new EngineListener();
    AliRTCLinuxEngine linuxEngine = AliRTCLinuxEngine.createInstance(engineEventHandler, 42000, 45000, null, CORE_SERVICE_PATH);
    ```

    **注意：**

    -   创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。
    -   logPath：示例代码中传入的第四个参数，表示logPath存放的路径，设置为null，会默认放在/tmp路径下。
    -   AliRtcCoreService：示例代码中传入的第五个参数，表示AliRtcCoreService可执行程序存放的绝对路径，设置为null，会默认在当前路径下寻找。
2.  加入频道。

    ```
    // TODO by user, need authinfo
    AliRTCLinuxEngine.AuthInfo authInfo = new AliRTCLinuxEngine.AuthInfo();
    authInfo.appid = "";     //应用ID
    authInfo.channel = "";   //频道ID
    authInfo.userid = "";    //用户ID
    authInfo.username = "";  //用户名称
    authInfo.nonce = "";     //随机码
    authInfo.token = "";     //频道鉴权令牌
    authInfo.timestamp = 0;  //频道过期时间戳
    
    int gslbCount = 1;
    authInfo.gslb_count = gslbCount;
    String[] gslbArray = new String[gslbCount];
    if (gslbCount > 0) {
        for (int i = 0; i < gslbCount; i++) {
            gslbArray[i] = "https://********.com";
        }
        authInfo.gslb = gslbArray;
    }
    
    int agentCount = 0;
    authInfo.agent_count = agentCount;
    String[] agentArray = new String[agentCount];
    if (agentCount > 0) {
        for (int i = 0; i < agentCount; i++) {
            agentArray[i] = "https://********.com";
        }
        authInfo.agent = agentArray;
    }
    // 初始化入会的设置
    AliRTCLinuxEngine.JoinChannelConfig joinConfig = new AliRTCLinuxEngine.JoinChannelConfig();
    // 关闭录制功能
    joinConfig.recordingMode = AliRTCLinuxEngine.RecordingMode.RecordingManually;
    // 关闭自动推流
    joinConfig.publishMode = AliRTCLinuxEngine.PublishMode.PublishManually;
    
    // 入会
    linuxEngine.joinChannel(authInfo, joinConfig);                     
    ```

    |参数|描述|
    |--|--|
    |appid|应用ID，在控制台应用管理页面创建和查看。|
    |channel|频道ID。1~64位，支持大小写字母、数字、下划线（\_）、中划线（-）。|
    |userid|用户ID。1~64位，支持大小写字母、数字、下划线（\_）、中划线（-）。 **说明：** 同一个用户ID在其他端登录，先入会的端会被后入会的端踢出频道。 |
    |username|用户名。|
    |nonce|随机码。需要加上前缀AK-，由字母\[a-zA-Z\]和数字\[0-9\]组成，不包含特殊字符，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |timestamp|频道过期时间戳。代表令牌有效时间为当前时间+所选择小时数。|
    |token|频道鉴权令牌，计算方法：`token = sha256(appId + appKey + channelId + userId + nonce + timestamp)`。|
    |gslb|gslb服务地址，该参数是数组类型，当前请使用：`["https://****"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|
    |agent|agent服务地址，该参数是数组类型，当前请使用：`["https://****"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

3.  发布或取消发布本地流。

    -   自动发布模式：加入频道成功后，即可发布本地流，无需再次调用publish接口。
    -   手动发布模式：加入频道成功后，可通过以下接口发布本地流。
    在发布Yuv和Pcm数据之前，需要设置推流的音视频参数。

    ```
    // 开启Yuv输入，使用相机流进行推送
    // 注意：第二个参数useTexture目前只能设置为false
    linuxEngine.setExternalVideoSource(true, false, AliRTCLinuxEngine.VideoSource.VideoSourceCamera, AliRTCLinuxEngine.RenderMode.RenderModeAuto);
    
    // 开启Pcm输入
    // 第二个参数为pcm的采样率，请根据实际情况设置
    // 第三个参数为pcm的channel数，请根据实际情况设置
    linuxEngine.setExternalAudioSource(true, 16000, 2);
    ```

    如果发布过程中需要变更配置或者停止发布，需要按如下流程先重新设置配置参数，然后再调用publish接口。

    ```
    // 设置是否推相机流。true表示允许发布相机流，false表示不允许。
    linuxEngine.configLocalCameraPublish(true);
    
    // 设置是否推音频流。true表示允许发布音频流，false表示不允许。
    linuxEngine.configLocalAudioPublish(true);
    
    //设置是否推屏幕流。true表示允许发布屏幕流，false表示不允许。
    linuxEngine.configLocalScreenPublish(true);
    
    //设置是否推次要视频流。true表示允许发布次要视频流，false表示不允许。
    linuxEngine.configLocalSimulcast(true);
    
    linuxEngine.publish();
    
    
    while (true) {
        ...
    
        // 推Yuv数据
        linuxEngine.pushExternalVideoFrame(sample, AliRTCLinuxEngine.VideoSource.VideoSourceCamera);
    
        // 推Pcm数据
        linuxEngine.pushExternalAudioFrameRawData(buf, frame_length, 0);
    }
    ```

    取消发布本地流。

    ```
    // 设置是否推相机流。
    linuxEngine.configLocalCameraPublish(false);
    
    // 设置是否推音频流
    linuxEngine.configLocalAudioPublish(false);
    
    // 设置是否推屏幕流
    linuxEngine.configLocalScreenPublish(false);
    
    // 设置是否推次要视频流。
    linuxEngine.configLocalSimulcast(false, VideoTrackCamera);
    
    linuxEngine.publish();
    ```

    发布和取消发布本地流回调代码如下所示。

    ```
    /**
    * @brief 推流结果回调
    * @param result 返回0表示成功，返回其他表示失败
    * @param isPublished true表示推流成功，false表示停止推流
    */
    void onPublishChangedNotify(int result, boolean isPublished);
    ```

4.  录制和取消录制。

    -   自动录制模式：加入频道成功后，无需调用以下接口，即可开始录制。
    -   手动录制模式：加入频道成功后，可通过以下接口进行录制操作。
    开始录制。

    ```
    linuxEngine.startRecording();
    ```

    取消录制。

    ```
    linuxEngine.stopRecording();
    ```

    录制回调示例代码如下所示。

    ```
    /**
    * @brief 远端用户上线回调
    * @param uid 远端用户ID
    */
    void onRemoteUserOnLineNotify(String uid);
    
    /**
    * @brief 远端用户下线回调
    * @param uid 远端用户ID
    */
    void onRemoteUserOffLineNotify(String uid);
    
    /**
    * @brief 音频原始数据的回调
    * @param frame 音频原始数据
    */
    void onAudioFrameReceived(AliRTCLinuxEngine.AudioFrame frame);
    
    /**
    * @brief 视频原始数据的回调
    * @param uid 远端用户ID，
    * @param frame 视频原始数据
    */
    void onVideoFrameReceived(String uid, AliRTCLinuxEngine.VideoFrame frame);
                                
    ```

5.  离开频道。

    ```
    linuxEngine.eaveChannel();
    ```

6.  销毁SDK。

    ```
    linuxEngine.destroy();
    linuxEngine = null;
    ```


接口详情请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Linux SDK/Java/AliRtcEngine接口.md)

