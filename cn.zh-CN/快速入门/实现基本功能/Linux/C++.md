---
keyword: [rtc, Linux, C++]
---

# C++

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、录制和离开频道等。

1.  下载最新的SDK，更多信息，请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  初始化SDK。

    ```
    //初始化SDK
    AliRTCSdk::Linux::EngineEventHandlerInterface *linuxEventHandler = new AliRTCSdk::Linux::FakeLinuxEventHandler();
    AliRTCSdk::Linux::AliRTCEngineInterface *linuxEngine = (AliRTCSdk::Linux::AliRTCEngineInterface*)CreateAliRTCEngineInstance(linuxEventHandler, 42000, 45000, nullptr, nullptr);
    
    // 如果创建失败，需要销毁EventHandler实例
    if (linuxEngine == nullptr) {
        delete linuxEventHandler;
        linuxEventHandler = nullptr;
        return;
    }
    ```

    **注意：**

    -   创建一个SDK实例需要占用一个系统端口进行音视频数据传输，建议端口范围设置为42000～45000，并保证其他服务不会占用此范围的端口。
    -   log：示例代码中传入的第四个参数，表示log存放的路径，设置为nullptr，会默认放在/tmp路径下。
    -   AliRtcCoreService：示例代码中传入的第五个参数，表示AliRtcCoreService可执行程序存放的绝对路径，设置为nullptr，会默认在当前路径下寻找。
3.  获得加入频道必须的频道鉴权令牌（Token）。

    -   您可以在控制台生成临时Token校验加入频道是否成功，详情请参见[控制台生成Token](/cn.zh-CN/常用功能/生成Token.md)。
    -   在安全要求更高的场景下，建议您在服务端生成Token，详情请参见[服务端生成Token](/cn.zh-CN/常用功能/生成Token.md)。
4.  加入频道。

    ```
    AliRTCSdk::Linux::AuthInfo authInfo;
    authInfo.appid = "";              //应用ID
    authInfo.channel = room.c_str();  //频道ID
    authInfo.userid = "";             //用户ID
    authInfo.username = "";           //用户名称
    authInfo.nonce = "";              //随机码     
    authInfo.token = "";              //频道鉴权令牌
    authInfo.timestamp = 1591430980;  //频道过期时间戳
    
    int gslbCount = 1;
    authInfo.gslb_count = gslbCount;
    const char *gslbArray[gslbCount];
    if (gslbCount > 0)
    {
      for(int i = 0; i < gslbCount; i++)
      {
        gslbArray[i] = "*****";
      }
      authInfo.gslb = gslbArray;
    }
    
    int agentCount = 0;
    authInfo.agent_count = agentCount;
    const char *agentArray[agentCount];
    if (agentCount > 0)
    {
      for (int i = 0; i < agentCount; i++)
      {
        agentArray[i] = "";
      }
      authInfo.agent = agentArray;
    }
    
    // 初始化入会的设置
    AliRTCSdk::Linux::JoinChannelConfig joinConfig;
    // 关闭自动录制
    joinConfig.recordingMode = AliRTCSdk::Linux::RecordingManually;
    // 关闭自动推流
    joinConfig.publishMode = AliRTCSdk::Linux::PublishManually;
    
    // 入会
    linuxEngine->JoinChannel(authInfo, joinConfig);
    ```

    |参数|描述|
    |--|--|
    |appid|应用ID，在控制台应用管理页面创建和查看。|
    |channel|频道ID。1~64位，支持大小写字母、数字、下划线（\_）、短划线（-）。|
    |userid|用户ID。1~64位，支持大小写字母、数字、下划线（\_）、短划线（-）。 **说明：** 同一个用户ID在其他端登录，先入会的端会被后入会的端踢出频道。 |
    |username|用户名。|
    |nonce|随机码。需要加上前缀AK-，由字母\[a-zA-Z\]和数字\[0-9\]组成，不包含特殊字符，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |timestamp|频道过期时间戳。代表令牌有效时间为当前时间+所选择小时数。|
    |token|频道鉴权令牌，计算方法：`token = sha256(appId + appKey + channel + userId + nonce + timestamp)`。|
    |gslb|gslb服务地址，该参数是数组类型，当前请使用：`["https://****"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|
    |agent|agent服务地址，该参数是数组类型，当前请使用：`["https://****"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

5.  发布或取消发布本地流。

    -   自动发布模式：加入频道成功后，即可发布本地流，无需再次调用publish接口。
    -   手动发布模式：加入频道成功后，可通过以下接口发布本地流。
    在发布Yuv和Pcm数据之前，需要设置推流的音视频参数。

    ```
    // 开启Yuv输入，使用视频流（原相机流）进行推送
    // 注意：第二个参数useTexture目前只能设置为false
    linuxEngine->SetExternalVideoSource(true, false, AliRTCSdk::Linux::VideoSourceCamera);
    
    // 开启Pcm输入
    // 第二个参数为pcm的采样率，请根据实际情况设置
    // 第三个参数为pcm的channel数，请根据实际情况设置
    linuxEngine->SetExternalAudioSource(true, 16000, 2);
    ```

    如果发布过程中需要变更配置或者停止发布，需要按如下流程先重新设置配置参数，然后再调用publish接口。

    **说明：** Linux SDK通过原相机流和屏幕流通道传递视频流，Linux SDK不支持摄像头采集视频。

    ```
    //设置是否推视频流（原相机流）。true表示允许发布，false表示不允许。
    linuxEngine->ConfigLocalCameraPublish(true);
    
    //设置是否推音频流。true表示允许发布，false表示不允许。 
    linuxEngine->ConfigLocalAudioPublish(true);
    
    //设置是否推视频流（原屏幕流）。true表示允许发布，false表示不允许。
    linuxEngine->ConfigLocalScreenPublish(true);
    
    //设置是否推次要视频流。true表示允许发布，false表示不允许。
    linuxEngine->ConfigLocalSimulcast(true, AliRTCSdk::Linux::VideoSourceCamera);
    
    linuxEngine->publish();
    
    
    while (true) {
        ...
    
       // 推Yuv数据
       linuxEngine->PushExternalVideoFrame(&sample, AliRTCSdk::Linux::VideoSourceCamera);
    
       // 推Pcm数据
       linuxEngine->PushExternalAudioFrameRawData(cache_buf, frame_length, 0);
    }
    ```

    取消发布本地流。

    ```
    // 设置是否推视频流（原相机流）
    linuxEngine->ConfigLocalCameraPublish(false);
    
    // 设置是否推音频流
    linuxEngine->ConfigLocalAudioPublish(false);
    
    // 设置是否推视频流（原屏幕流）
    linuxEngine->ConfigLocalScreenPublish(false);
    
    // 设置是否推次要视频流
    linuxEngine->ConfigLocalSimulcast(false, AliRTCSdk::Linux::VideoSourceCamera);
    
    linuxEngine->publish();
    ```

    发布和取消发布本地流回调代码如下所示。

    ```
    /**
    * @brief 推流结果回调
    * @param result 返回0表示成功，返回其他表示失败
    * @param isPublished true表示推流成功，false表示停止推流
    */
    virtual void OnPublishChangedNotify(int result, bool isPublished) = 0;
    ```

6.  录制和取消录制。

    -   自动录制模式：加入频道成功后，无需调用以下接口，即可开始录制。
    -   手动录制模式：加入频道成功后，可通过以下接口进行录制操作。
    开始录制。

    ```
    linuxEngine->StartRecording();
    ```

    取消录制。

    ```
    linuxEngine->StopRecording();
    ```

    录制回调示例代码如下所示。

    ```
    /**
    * @brief 远端用户上线回调
    * @param uid 远端用户ID
    */
    virtual void OnRemoteUserOnLineNotify(const char * uid) = 0;
    
    /**
    * @brief 远端用户下线回调
    * @param uid 远端用户ID
    */
    virtual void OnRemoteUserOffLineNotify(const char * uid) = 0;
    
    /**
    * @brief 音频原始数据的回调
    * @param frame 音频原始数据
    */
    virtual void OnAudioFrameReceived(const AliRTCSdk::Linux::AudioFrame * frame) = 0;
    
    /**
    * @brief 视频原始数据的回调
    * @param uid 远端用户ID
    * @param frame 视频原始数据
    */
    virtual void OnVideoFrameReceived(const char * uid, const AliRTCSdk::Linux::VideoFrame * frame) = 0;
    ```

7.  离开频道。

    ```
    linuxEngine->LeaveChannel();
    ```

8.  销毁SDK。

    ```
    linuxEngine->Release();
    linuxEngine = nullptr;
    ```


接口详情请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Linux SDK/Java/AliRtcEngine接口.md)。

