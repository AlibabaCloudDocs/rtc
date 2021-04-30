---
keyword: [iOS SDK, Mac SDK, AliRtcEngine]
---

# AliRtcEngine接口

通过阅读本文，您可以了解到iOS SDK和Mac SDK的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setH5CompatibleMode](#li_001)|设置H5兼容模式。|1.1|
|[getH5CompatibleMode](#li_002)|检查是否设置了H5兼容模式。|1.1|
|[sharedInstance](#li_003)|创建AliRtcEngine实例。|1.17|
|[destroy](#li_004)|释放SDK实例。|1.1|
|[uploadLog](#li_005)|上传日志。|1.1|
|[setLogDirPath](#li_006)|设置SDK日志文件保存路径。|1.17|
|[setLogLevel](#li_007)|设置日志级别。|1.17|

频道相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[joinChannel](#li_008)|加入频道。|1.1|
|[leaveChannel](#li_009)|离开频道。|1.1|
|[switchChannel](#li_010)|切换频道。|2.1|
|[isInCall](#li_011)|检查当前是否在频道中。|1.1|
|[setChannelProfile](#li_012)|设置频道模式。|1.15|
|[createChannelWithDelegate](#li_013)|创建AliRtcEngine子频道实例。|2.1|
|[destroyChannel](#li_014)|销毁[createChannelWithDelegate](#li_013)创建的子频道。|2.1|

发布相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[publishLocalVideoStream](#li_015)|设置是否允许发布视频流。|2.1|
|[isLocalVideoStreamPublished](#li_016)|查询当前是否允许发布视频流。|1.1|
|[isScreenSharePublished](#li_017)|查询当前是否允许发布屏幕流。|1.1|
|[publishLocalAudioStream](#li_018)|设置是否允许发布音频流。|2.1|
|[isLocalAudioStreamPublished](#li_019)|查询当前是否允许推音频流。|1.1|
|[publishLocalDualStream](#li_020)|设置是否允许发布次要视频流。|2.1|
|[isDualStreamPublished](#li_021)|查询当前是否允许发布次要视频流。|2.1|

订阅相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setRemoteVideoStreamType](#li_022)|设置订阅的相机流格式，大流或小流。|2.1|
|[setRemoteDefaultVideoStreamType](#li_023)|设置默认订阅的相机流格式，大流或小流。|2.1|
|[setDefaultSubscribeAllRemoteAudioStreams](#li_024)|设置是否默认接收音频流。|2.1|
|[subscribeAllRemoteAudioStreams](#li_025)|停止或恢复接收所有远端音频流。|2.1|
|[subscribeRemoteAudioStream](#li_026)|停止或恢复特定远端用户的音频流拉取。|2.1|
|[setDefaultSubscribeAllRemoteVideoStreams](#li_027)|设置是否默认接收视频流。|2.1|
|[subscribeAllRemoteVideoStreams](#li_028)|停止或恢复接收所有远端视频流。|2.1|
|[subscribeRemoteVideoStream](#li_029)|停止或恢复特定远端用户的视频流拉取。|2.1|

视频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setScreenShareEncoderConfiguration](#li_030)|设置屏幕共享编码属性。|2.1|
|[setLocalViewConfig](#li_031)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[setCameraCapturerConfiguration](#li_032)|设置摄像头采集偏好。|2.1|
|[setDeviceOrientationMode](#li_033)|设置设备方向。|2.1|
|[enableLocalVideo](#li_034)|禁用或重新启用本地视频采集。|2.1|
|[muteLocalCamera](#li_035)|停止或恢复本地视频数据数据发送。|1.1|
|[muteAllRemoteVideoRendering](#li_036)|停止或恢复远端所有的视频渲染。|2.1|
|[setRemoteViewConfig](#li_037)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[isCameraOn](#li_038)|检查摄像头是否打开。|1.1|
|[stopRecord](#li_039)|停止录制。|1.17|
|[startRecord](#li_040)|开始录制（非布局录制）。|1.17|
|[setBeautyEffect](#li_041)|设置是否启用基础美颜。|1.17.9|
|[setVideoEncoderConfiguration](#li_042)|设置视频编码属性。|2.1|
|[addVideoWatermark](#li_043)|添加水印。|2.1|
|[clearVideoWatermark](#li_044)|清理对应数据流水印信息。|2.1|
|[snapshotVideo](#li_045)|截图。|2.1|
|[switchCamera](#li_046)|切换前后摄像头。|1.1|
|[getCurrentCameraDirection](#li_047)|获取当前摄像头方向，默认前置摄像头。|1.1|
|[setCameraZoom](#li_048)|设置摄像头缩放比例。|1.1|
|[setCameraFlash](#li_049)|设置摄像头闪光灯是否打开。|1.14|
|[isCameraFocusPointSupported](#li_050)|摄像头是否支持手动聚焦。|1.14|
|[isCameraExposurePointSupported](#li_051)|摄像头是否支持设置曝光区域。|1.14|
|[setCameraFocusPoint](#li_052)|设置摄像头手动聚焦。|1.14|
|[setCameraExposurePoint](#li_053)|设置摄像头曝光点。|1.14|
|[isCameraAutoFocusFaceModeSupported](#li_054)|摄像头是否支持人脸聚焦。|2.1|
|[setCameraAutoFocusFaceModeEnabled](#li_055)|设置摄像头人脸对焦。|2.1|

共享视频接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startScreenShare](#li_056)|开始屏幕分享。|2.1|
|[stopScreenShare](#li_057)|停止屏幕分享。|2.1|

音频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[setAudioOnlyMode](#li_058)|设置为纯音频模式还是音视频模式。|1.1|
|[isAudioOnly](#li_059)|查询当前是否为纯音频模式。|1.1|
|[muteLocalMic](#li_060)|停止或恢复本地音频数据发送。|1.1|
|[muteRemoteAudioPlaying](#li_061)|停止或恢复远端的音频播放。|1.1|
|[muteAllRemoteAudioPlaying](#li_062)|停止或恢复远端所有的音频播放。|1.16.2|
|[startAudioCapture](#li_063)|开启音频采集。|1.11|
|[stopAudioCapture](#li_064)|关闭音频采集。|1.11|
|[startAudioPlayer](#li_065)|开启音频播放设备。|1.11|
|[stopAudioPlayer](#li_066)|关闭音频播放。|1.11|
|[setRemoteAudioVolume](#li_067)|设置本地播放的指定远端用户音量。|2.1|
|[enableSpeakerphone](#li_068)|设置音频输出为听筒或扬声器。|2.1|
|[isEnableSpeakerphone](#li_069)|获取当前音频输出为听筒或扬声器。|2.1|
|[setRecordingVolume](#li_070)|设置录音音量。|1.16.2|
|[setPlayoutVolume](#li_071)|设置播放音量。|1.16.2|
|[enableAudioVolumeIndication](#li_072)|设置音量回调频率和平滑系数。|1.17.9|
|[setAudioProfile](#li_073)|设置音频Profile。|2.1|
|[setAudioSessionOperationRestriction](#li_074)|设置SDK对AVAudioSession的控制权限。|2.1|
|[setDeviceVolumeType](#li_075)|设置SDK设备音量类型。|2.1|
|[enableAudioDTX](#li_076)|开启本地音频流量控制（语音）。|2.1|
|[enableAudioAMD](#li_077)|开启本地音频流量控制（麦克风）。|2.1|
|[setAudioEffectVoiceChangerMode](#li_079)|设置变声音效模式。|2.1|
|[setAudioEffectPitchValue](#li_080)|设置变调参数。|2.1|
|[setAudioEffectReverbMode](#li_081)|设置混响音效模式。|2.1|
|[setAudioEffectReverbParamType](#li_082)|设置混响音效类型和具体参数。|2.1|
|[startAudioAccompany](#li_083)|开始混音。|1.15|
|[stopAudioAccompany](#li_084)|停止混音。|1.15|
|[setAudioAccompanyVolume](#li_085)|设置混音音量。|1.15|
|[setAudioAccompanyPublishVolume](#li_086)|设置混音之后推流出去的音量。|1.15|
|[getAudioAccompanyPublishVolume](#li_087)|获取推流出去的混音音量。|1.15|
|[setAudioAccompanyPlayoutVolume](#li_088)|设置混音之后本地播放的音量。|1.15|
|[getAudioAccompanyPlayoutVolume](#li_089)|获取混音本地播放的音量。|1.15|
|[pauseAudioAccompany](#li_090)|暂停混音。|1.15|
|[resumeAudioAccompany](#li_091)|重新开始混音。|1.15|
|[getAudioAccompanyDuration](#li_092)|获取伴奏文件时长。|1.17.30|
|[getAudioAccompanyCurrentPosition](#li_093)|获取音乐文件播放进度。|1.17.30|
|[setAudioAccompanyPosition](#li_094)|设置音频文件的播放位置。|1.17.30|
|[preloadAudioEffect](#li_095)|预加载音效文件。|1.15|
|[unloadAudioEffect](#li_096)|删除预加载的音效文件。|1.15|
|[playAudioEffect](#li_097)|开始播放音效。|1.15|
|[stopAudioEffect](#li_098)|停止播放音效。|1.15|
|[stopAllAudioEffects](#li_099)|停止播放所有音效。|1.15|
|[setAudioEffectPublishVolume](#li_100)|设置音效推流音量。|1.15|
|[getAudioEffectPublishVolume](#li_101)|获取推流音效音量。|1.15|
|[setAudioEffectPlayoutVolume](#li_102)|设置音效本地播放音量。|1.15|
|[getAudioEffectPlayoutVolume](#li_103)|获取音效本地播放音量。|1.15|
|[setAllAudioEffectsPublishVolume](#li_104)|设置所有音效本地播放音量。|1.15|
|[setAllAudioEffectsPlayoutVolume](#li_105)|设置所有音效推流音量。|1.15|
|[pauseAudioEffect](#li_106)|暂停音效。|1.15|
|[pauseAllAudioEffects](#li_107)|暂停所有音效。|1.15|
|[resumeAudioEffect](#li_108)|重新开始播放音效。|1.15|
|[resumeAllAudioEffects](#li_109)|重新开始播放所有音效。|1.15|
|[enableEarBack](#li_110)|启用耳返。|1.15|
|[setEarBackVolume](#li_111)|设置耳返音量。|1.15|

媒体引擎接口

|API|描述|支持的最低版本|
|---|--|-------|
|[registerVideoSampleObserver](#li_112)|订阅视频数据输出。|1.17|
|[unRegisterVideoSampleObserver](#li_113)|取消订阅视频数据输出。|1.17|
|[registerLocalVideoTexture](#li_114)|订阅本地视频纹理数据。|1.15|
|[unregisterLocalVideoTexture](#li_115)|取消本地视频纹理数据输出。|1.15|
|[subscribeAudioData](#li_116)|订阅音频数据输出。|1.17|
|[unSubscribeAudioData](#li_117)|取消音频数据输出。|1.17|
|[setSubscribeAudioNumChannel](#li_118)|设置输出音频声道数（混音前数据不支持该参数设置）。|2.1|
|[setSubscribeAudioSampleRate](#li_119)|设置输出音频采样率（混音前数据不支持该参数设置）。|2.1|
|[setExternalVideoSource](#li_120)|启用外部视频输入源。|2.1|
|[pushExternalVideoFrame](#li_121)|输入视频数据。|2.1|
|[setExternalAudioSource](#li_122)|设置是否启用外部音频输入源。|1.17.9|
|[pushExternalAudioFrameRawData](#li_123)|输入音频数据。|1.17.9|
|[setExternalAudioVolume](#li_124)|设置混音音量。|1.17.9|
|[getExternalAudioVolume](#li_125)|获取混音音量。|1.17.9|
|[setMixedWithMic](#li_126)|设置是否与麦克风采集音频混合。|1.17.9|
|[setExteranlAudioRender](#li_127)|设置是否启用外部输入音频播放。|1.17.9|
|[pushExternalAudioRenderRawData](#li_128)|输入外部音频播放数据。|1.17.9|

直播旁路接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startLiveStreaming](#li_129)|开始直播拉流。|2.1|
|[stopLiveStreaming](#li_130)|停止直播拉流。|2.1|
|[startPublishLiveStream](#li_131)|开启旁路直播。|2.1|
|[updatePublishLiveStream](#li_132)|更新旁路直播相关参数。|2.1|
|[stopPublishLiveStream](#li_133)|停止旁路直播。|2.1|
|[setLiveStreamingViewConfig](#li_134)|设置直播拉流窗口及渲染参数。|2.1|

跨频道连麦接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startChannelRelay](#li_135)|开启跨频道连麦。|2.1|
|[updateChannelRelay](#li_136)|更新跨频道连麦。|2.1|
|[stopChannelRelay](#li_137)|停止跨频道连麦。|2.1|

预览接口

|API|描述|支持的最低版本|
|---|--|-------|
|[startPreview](#li_138)|开始本地预览。|1.1|
|[stopPreview](#li_139)|停止本地预览。|1.1|

远端用户查询接口

|API|描述|支持的最低版本|
|---|--|-------|
|[getOnlineRemoteUsers](#li_140)|获取远端在线用户列表。|1.1|
|[getUserInfo](#li_141)|查询远端用户信息。|1.1|
|[isUserOnline](#li_142)|查询用户是否在线。|1.1|

其他接口

|API|描述|支持的最低版本|
|---|--|-------|
|[getSDKVersion](#li_143)|获取SDK版本号。|1.1|
|[getErrorDescription](#li_144)|获取错误码描述。|2.1|
|[setClientRole](#li_145)|设置用户角色。|1.16|
|[getCurrentClientRole](#li_146)|获取用户角色。|1.17.19|
|[startLastmileDetect](#li_147)|开始网络质量探测。|1.16.2|
|[stopLastmileDetect](#li_148)|停止网络质量探测。|1.16.2|
|[postFeedbackWithUid](#li_149)|SDK问题反馈。|1.17.12|
|[sendMediaExtensionMsg](#li_150)|发送媒体扩展信息。|1.17.1|
|[startIntelligentDenoise](#li_151)|开启智能降噪。|1.17.19|
|[stopIntelligentDenoise](#li_152)|关闭智能降噪。|1.17.19|
|[refreshAuthInfo](#li_153)|刷新鉴权信息。|1.17.41|
|[getCurrentConnectionStatus](#li_154)|获取当前网络链接状态。|2.1|
|[enableDelegateMainQueue](#li_155)|是否分发回调到主线程。|2.1|
|[setDelegateQueue](#li_156)|指定回调线程队列。|2.1|

## 接口详情

-   setH5CompatibleMode：设置是否兼容H5。

    ```
    + (void)setH5CompatibleMode:(BOOL)comp;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |comp|BOOL|YES表示兼容H5，NO表示不兼容H5。默认不兼容H5。|

    **说明：** 当前版本不支持在创建AliRtcEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此方法。

-   getH5CompatibleMode：检查是否设置了H5兼容模式。

    ```
    + (BOOL)getH5CompatibleMode;
    ```

    返回说明

    YES表示兼容H5，NO表示不兼容H5。

-   sharedInstance：创建AliRtcEngine实例。

    ```
    + (instancetype _Nonnull )sharedInstance:(id<AliRtcEngineDelegate>_Nullable)delegate extras:(NSString *_Nullable)extras;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |delegate|id<AliRtcEngineDelegate\>\_Nullable|监听回调的代理。|
    |extras|NSString \*\_Nullable|通过JSON配置SDK的特别功能，详情请参见[extras功能说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。无需特别功能，可填空字符：@""。|

    **说明：** 同一时间只会存在一个主实例。

-   destroy：释放SDK实例。

    ```
    + (void)destroy;
    ```

    **说明：** 在所有操作结束之后调用。

-   uploadLog：上传日志。默认离会自动上传。

    ```
    + (void)uploadLog;
    ```

-   setLogDirPath：设置SDK日志文件保存路径。

    ```
    + (int)setLogDirPath:(NSString *_Nullable)logDirPath;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logDirPath|NSString \*\_Nullable|日志文件保存绝对路径。iOS端日志默认存储路径为Library/Caches/Ali\_RTC\_Log。Mac端日志默认存储路径为/Users/xxx/Documents（文稿）/Ali\_RTC\_Log。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 请在调用所有SDK接口前调用此接口，避免日志出现丢失，同时App必须保证指定的目录已存在且可写入。

-   setLogLevel：设置日志等级。

    ```
    - (void)setLogLevel:(AliRtcLogLevel)logLevel;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logLevel|AliRtcLogLevel[AliRtcLogLevel](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|Log级别。|

-   joinChannel：加入频道。

    ```
    - (int)joinChannel:(AliRtcAuthInfo *_Nonnull)authInfo name:(NSString *_Nullable)userName onResult:(void(^_Nullable)(NSInteger errCode,NSString * _Nonnull channel,NSInteger elapsed))onResult;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|鉴权信息。|
    |userName|String|用户的显示名称（不是用户ID）。|
    |onResult|void\(^\_Nullable\)\(NSInteger errCode,NSString \* \_Nonnull channel,NSInteger elapsed\)|当此接口执行结束后调用此回调。|

    **说明：** 加入频道成功后，如果中途需要加入其他频道，必须先调用[leaveChannel](#li_009)离开当前频道，如果加入频道失败，需要重试时，无需先调用[leaveChannel](#li_009)。

-   leaveChannel：离开频道。

    ```
    - (int)leaveChannel;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   1.15及以上版本：销毁引擎只能通过[destroy](#li_004)方法。
    -   1.15以下版本：离开频道时，AliRtcEngine实例会被销毁，如需继续加入频道等操作，需要重新调用getInstance初始化AliRtcEngine实例。
    -   如果当前不在频道内，调用[leaveChannel](#li_009)不会对实例产生任何影响，但会产生消息，通知频道内其他用户。
-   switchChannel：切换频道。

    ```
    - (int)switchChannel:(AliRtcAuthInfo *_Nonnull)authInfo;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|鉴权信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    -   返回ERR\_SDK\_INVALID\_STATE，请确认是否频道模式或角色不匹配，或当前未加入任何频道中。
    -   返回ERR\_INVALID\_ARGUMENTS，请确认鉴权信息是否合法，或是否加入相同频道。
    -   返回ERR\_INNER为SDK内部状态错误。
    **说明：**

    -   本方法只允许在直播模式AliRtcInteractiveLive下，观看角色AliRtcClientRoleLive使用。
    -   该接口是异步接口，调用此方法成功切换频道后，SDK会先触发离开原频道的[onLeaveChannelResult](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)回调，再返回加入新频道的onJoinChannelResult回调。
-   isInCall：检查当前是否在频道中。

    ```
    - (BOOL)isInCall;
    ```

    返回说明

    YES表示在频道中，NO表示不在频道中。

-   setChannelProfile：设置频道模式。

    ```
    - (int)setChannelProfile:(AliRtcChannelProfile)profile;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |profile|[AliRtcChannelProfile](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|频道类型，默认为AliRtcCommunication。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

-   createChannelWithDelegate：创建AliRtcEngine子频道实例。

    ```
    - (AliRtcEngine *_Nullable)createChannelWithDelegate:(id<AliRtcEngineDelegate>_Nonnull)delegate extras:(NSString *_Nullable)extras;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |delegate|id<AliRtcEngineDelegate\>\_Nonnull|返回的SDK实例对象的代理。|
    |extras|NSString \*\_Nullable|通过JSON配置SDK的特别功能，详情请参见[extras功能说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。无需特别功能，可填空字符：@""。|

    返回说明

    成功返回子频道实例，失败返回nil。

-   destroyChannel：销毁[createChannelWithDelegate](#li_013)创建的子频道。

    ```
    - (void)destroyChannel;
    ```

-   publishLocalVideoStream：设置是否允许发布相机流。

    ```
    - (int)publishLocalVideoStream:(BOOL)enabled;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enabled|boolean|YES表示发送视频，NO表示停止发送，默认YES。|

-   isLocalVideoStreamPublished：查询当前是否允许发布视频流。

    ```
    - (BOOL)isLocalVideoStreamPublished;
    ```

    返回说明

    YES表示发布相机流，NO表示发布相机流。

-   isScreenSharePublished：查询当前是否允许发布屏幕流。

    ```
    - (BOOL)isScreenSharePublished;
    ```

    返回说明

    YES表示发布屏幕流，NO表示未发布屏幕流。

-   publishLocalAudioStream：设置是否允许发布音频流。

    ```
    - (int)publishLocalAudioStream:(BOOL)enabled;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|boolean|YES表示发送本地音频流，NO表示停止推流，默认YES。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isLocalAudioStreamPublished：查询当前是否允许推音频流。

    ```
    - (BOOL)isLocalAudioStreamPublished;
    ```

    返回说明

    YES表示允许推送，NO表示不允许推送。

-   publishLocalDualStream：设置是否允许发布次要视频流。

    ```
    - (int)publishLocalDualStream:(BOOL)enabled;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示需要推送次流，NO表示不推送次流，默认NO。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isDualStreamPublished：查询当前是否允许发布次要视频流。

    ```
    - (BOOL)isDualStreamPublished;
    ```

    返回说明

    YES表示允许推送，NO表示不允许推送。

-   setRemoteVideoStreamType：设置订阅的相机流格式，大流或小流。

    ```
    - (int)setRemoteVideoStreamType:(NSString *_Nonnull)uid type:(AliRtcVideoStreamType)streamType;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|远端用户ID。|
    |streamType|[AliRtcVideoStreamType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|相机流格式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setRemoteDefaultVideoStreamType：设置默认订阅的相机流格式，大流或小流。

    ```
    - (int)setRemoteDefaultVideoStreamType:(AliRtcVideoStreamType)streamType;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamType|[AliRtcVideoStreamType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|相机流格式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDefaultSubscribeAllRemoteAudioStreams：设置是否默认接收音频流。

    ```
    - (int)setDefaultSubscribeAllRemoteAudioStreams:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|BOOL|YES表示接收用户的音频流，NO表示停止接收用户的音频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   入会前、后均可调用。如果在加入频道后调用setDefaultSubscribeAllRemoteAudioStreams:NO，会接收不到设置后加入频道的用户的音频流。
    -   停止接收音频流后，如果想要恢复接收，请调用[subscribeRemoteAudioStream](#li_026):uid sub:YES，并指定你想要接收的远端用户UID。
    -   如果想恢复接收多个用户的音频流，则需要多次调用[subscribeRemoteAudioStream](#li_026)。setDefaultSubscribeAllRemoteAudioStreams:YES只能恢复接收后面加入频道的用户的音频流。
-   subscribeAllRemoteAudioStreams：停止或恢复接收所有远端音频流。

    ```
    - (int)subscribeAllRemoteAudioStreams:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|BOOL|YES表示接收所有用户的音频流，NO表示停止接收所有用户的音频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口作为订阅远端音频流的总开关，如果设置为NO，则不仅当前会议中所有远端音频流都会停止订阅，后续入会的新用户也将不再订阅（即使设置了[setDefaultSubscribeAllRemoteAudioStreams](#li_024):YES）。

-   subscribeRemoteAudioStream：停止或恢复特定远端用户的音频流拉取。

    ```
    - (int)subscribeRemoteAudioStream:(NSString *_Nonnull)uid sub:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|远端用户ID。|
    |sub|BOOL|YES表示接收指定用户的音频流，NO表示停止接收指定用户的音频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 如果之前有调用过[subscribeAllRemoteAudioStreams](#li_025):NO对所有远端音频进行静音，在调用本API之前请确保你已调用[subscribeAllRemoteAudioStreams](#li_025):YES。[subscribeAllRemoteAudioStreams](#li_025)是全局控制，[subscribeRemoteAudioStream](#li_026)是精细控制。

-   setDefaultSubscribeAllRemoteVideoStreams：设置是否默认接收视频流。

    ```
    - (int)setDefaultSubscribeAllRemoteVideoStreams:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|boolean|YES表示接收用户的视频流，NO表示不接收用户的视频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   入会前、后均可调用。如果在加入频道后调用setDefaultSubscribeAllRemoteVideoStreams:NO，会接收不到设置后加入频道的用户的视频流。
    -   停止接收视频流后，如果想要恢复接收，请调用[subscribeRemoteVideoStream](#li_029):uid track:track sub:YES，并指定你想要接收的远端用户UID。
    -   如果想恢复接收多个用户的视频流，则需要多次调用[subscribeRemoteVideoStream](#li_029)，setDefaultSubscribeAllRemoteVideoStreams:YES 只能恢复接收后面加入频道的用户的视频流。
-   subscribeAllRemoteVideoStreams：停止或恢复接收所有远端视频流。

    ```
    - (int)subscribeAllRemoteVideoStreams:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|BOOL|YES表示接收所有用户的视频流，NO表示停止允许接收所有用户的视频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口作为订阅远端视频流的总开关，如果设置为NO，则不仅当前会议中所有远端视频流都会停止订阅，后续入会的新用户也将不再订阅（即使设置了[setDefaultSubscribeAllRemoteVideoStreams](#li_027):YES）。

-   subscribeRemoteVideoStream：停止或恢复特定远端用户的视频流拉取。

    ```
    - (int)subscribeRemoteVideoStream:(NSString *_Nonnull)uid track:(AliRtcVideoTrack)track sub:(BOOL)sub;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|远端用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流类型。|
    |sub|BOOL|YES表示接收指定用户的视频流，NO表示停止接收指定用户的视频流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   如果之前有调用过[subscribeAllRemoteVideoStreams](#li_028):NO暂停接收所有远端视频，在调用此接口之前请确保已调用[subscribeAllRemoteVideoStreams](#li_028):YES。
    -   [subscribeAllRemoteVideoStreams](#li_028)是全局控制，subscribeRemoteVideoStream是精细控制。
-   setScreenShareEncoderConfiguration：设置屏幕共享编码属性。

    ```
    - (void)setScreenShareEncoderConfiguration:(AliRtcScreenShareEncoderConfiguration* _Nonnull)config;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|[AliRtcScreenShareEncoderConfiguration](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)\* \_Nonnull|预定义的屏幕共享编码属性。|

-   setLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    ```
    - (int)setLocalViewConfig:(AliVideoCanvas *_Nullable)viewConfig forTrack:(AliRtcVideoTrack)track;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |viewConfig|[AliVideoCanvas](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nullable|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频Track的类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   支持[joinChannel](#li_008)之前和之后切换窗口。如果canvas或者canvas中的view为nil，则停止渲染。
    -   如果在播放过程中需要重新设置render mode，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   如果在播放过程中需要重新设置mirror mode，请保持canvas中其他成员变量不变，仅修改mirrorMode。
-   setCameraCapturerConfiguration：设置摄像头采集偏好。

    ```
    - (int)setCameraCapturerConfiguration:(AliRtcCameraCapturerConfiguration* _Nonnull)config;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|[AliRtcCameraCapturerConfiguration](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)\* \_Nonnull|摄像头采集偏好。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDeviceOrientationMode：设置设备方向。

    ```
    - (int)setDeviceOrientationMode:(AliRtcOrientationMode)mode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|设备方向。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableLocalVideo：禁用或重新启用本地视频采集。

    ```
    - (int)enableLocalVideo:(BOOL)enabled;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enabled|BOOL|YES表示恢复正常，NO表示停止视频采集，默认YES。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   muteLocalCamera：停止或恢复本地视频数据数据发送。

    ```
    - (int)muteLocalCamera:(BOOL)mute forTrack:(AliRtcVideoTrack)track;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示视频数据发送黑帧，NO表示恢复正常。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要改变发布状态的视频Track类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口只是控制指定视频流上是否发送黑帧，采集和数据发送不会停止，如果需要关闭采集请使用[enableLocalVideo](#li_034)接口，如果需要中止视频数据发送请使用[publishLocalVideoStream](#li_015)接口。

-   muteAllRemoteVideoRendering：停止或恢复远端所有的视频渲染。

    ```
    - (int)muteAllRemoteVideoRendering:(BOOL)mute;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止渲染，NO表示恢复渲染，默认为NO。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 拉流和解码不受影响，支持[joinChannel](#li_008)之前和之后设置。

-   setRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    ```
    - (int)setRemoteViewConfig:(AliVideoCanvas *_Nullable)canvas uid:(NSString *_Nonnull)uid forTrack:(AliRtcVideoTrack)track;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nullable|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|NSString \*\_Nonnull|用户ID。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要设置的视频Track类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   支持[joinChannel](#li_008)之前和之后切换窗口。如果canvas为nil或者view为nil，则停止渲染相应的流。
    -   如果在播放过程中需要重新设置render mode，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   如果在播放过程中需要重新设置mirror mode，请保持canvas中其他成员变量不变，仅修改mirrorMode。
-   isCameraOn：检查摄像头是否打开。

    ```
    - (BOOL)isCameraOn;
    ```

    返回说明

    YES表示摄像头已打开，NO表示摄像头没有打开。

-   stopRecord：停止录制。

    ```
    - (void)stopRecord;
    ```

-   startRecord：开始录制（非布局录制）。

    ```
    - (BOOL)startRecord:(AliRtcRecordType)recordType recordFormat:(AliRtcRecordFormat)recordFormat filePath:(NSString*_Nonnull)filePath audioConfig:(AliRtcRecordAudioConfig*_Nullable)audioConfig videoConfig:(AliRtcRecordVideoConfig*_Nullable)videoConfig;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |recordType|[AliRtcRecordType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制类型。|
    |recordFormat|[AliRtcRecordFormat](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|录制格式。|
    |filePath|NSString\*\_Nonnull|文件路径。|
    |audioConfig|AliRtcRecordAudioConfig\*\_Nullable|录制音频设置。|
    |videoConfig|[AliRtcRecordVideoConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)\*\_Nullable|视频设置，移动端不支持录制视频。|

    返回说明

    YES表示方法调用成功，NO方法调用失败。

-   setBeautyEffect：设置是否启用基础美颜（目前只支持美白和磨皮。）。

    ```
    - (int)setBeautyEffect:(BOOL)enable config:(AliRtcBeautyConfig *_Nullable)config;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示启用，NO表示关闭，默认为NO。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nullable|基础美颜参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setVideoEncoderConfiguration：设置视频编码属性。

    ```
    - (void)setVideoEncoderConfiguration:(AliRtcVideoEncoderConfiguration* _Nonnull)config;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|[AliRtcVideoEncoderConfiguration](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)\* \_Nonnull|预定义的编码属性。|

-   addVideoWatermark：添加水印。

    ```
    - (int)addVideoWatermark:(AliRtcVideoTrack)track image:(NSString*_Nonnull)imageUrl config:(AliRtcWatermarkConfig *_Nullable)config;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|数据流类型。|
    |imageUrl|NSString\*\_Nonnull|水印图片路径。|
    |config|[AliRtcWatermarkConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nullable|水印配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   clearVideoWatermark：清理对应数据流水印信息。

    ```
    - (int)clearVideoWatermark:(AliRtcVideoTrack)track;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|数据流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   snapshotVideo：截图（截图结果通过OnSnapshotComplete回调返回）。

    ```
    - (int)snapshotVideo:(NSString*_Nullable)userId type:(AliRtcVideoTrack)type;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|NSString\*\_Nullable|用户ID。|
    |trackType|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   switchCamera：切换前后摄像头。

    ```
    - (int)switchCamera;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentCameraDirection：获取当前摄像头方向，默认前置摄像头。

    ```
    - (AliRtcCameraDirection)getCurrentCameraDirection;
    ```

    返回说明

    返回camera方向枚举值。

-   setCameraZoom：设置摄像头缩放比例。

    ```
    - (int)setCameraZoom:(float)zoom;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |zoom|float|zoom的级别。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setCameraFlash：设置摄像头闪光灯是否打开。

    ```
    - (int)setCameraFlash:(BOOL)flash;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |flash|BOOL|是否允许闪光灯。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isCameraFocusPointSupported：摄像头是否支持手动聚焦。

    ```
    - (BOOL)isCameraFocusPointSupported;
    ```

    返回说明

    YES表示支持，NO表示不支持。

-   isCameraExposurePointSupported：摄像头是否支持设置曝光区域。

    ```
    - (BOOL)isCameraExposurePointSupported;
    ```

    返回说明

    YES表示支持，NO表示不支持。

-   setCameraFocusPoint：设置摄像头手动聚焦。

    ```
    - (int)setCameraFocusPoint:(CGPoint)point;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |point|CGPoint|聚焦点的坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setCameraExposurePoint：设置摄像头曝光点。

    ```
    - (int)setCameraExposurePoint:(CGPoint)point;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |point|CGPoint|曝光点的坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isCameraAutoFocusFaceModeSupported：摄像头是否支持人脸聚焦。

    ```
    - (BOOL)isCameraAutoFocusFaceModeSupported;
    ```

    返回说明

    YES表示支持，NO表示不支持。

-   setCameraAutoFocusFaceModeEnabled：设置摄像头人脸对焦。

    ```
    - (BOOL)setCameraAutoFocusFaceModeEnabled:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启人脸对焦，NO表示关闭人脸对焦。|

    返回说明

    YES表示方法调用成功，NO表示方法调用失败。

-   startScreenShar：开始屏幕分享。

    ```
    - (int)startScreenShare;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopScreenShare：停止屏幕分享。

    ```
    - (int)stopScreenShare;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioOnlyMode：设置为纯音频模式还是音视频模式。

    ```
    - (int)setAudioOnlyMode:(BOOL)audioOnly;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioOnly|BOOL|YES表示只有音频推流和拉流，NO表示音视频都支持。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isAudioOnly：检查当前是否纯音频模式。

    ```
    - (BOOL)isAudioOnly;
    ```

    返回说明

    YES表示纯音频模式，NO表示音视频模式。

-   muteLocalMic：停止或恢复本地音频数据发送。

    ```
    - (int)muteLocalMic:(BOOL)mute mode:(AliRtcMuteLocalAudioMode)mode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示本地音频发送空帧，NO表示恢复正常。|
    |mode|[AliRtcMuteLocalAudioMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|静音模式，默认麦克风静音模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** mute只是发送音频数据为静音帧，采集和编码模块仍然在工作。

-   muteRemoteAudioPlaying：停止或恢复远端的音频播放。

    ```
    - (int)muteRemoteAudioPlaying:(NSString *_Nonnull)uid mute:(BOOL)mute;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|用户ID。|
    |mute|BOOL|YES表示停止播放，NO表示恢复播放。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   muteAllRemoteAudioPlaying：停止或恢复远端所有的音频播放。

    ```
    - (int)muteAllRemoteAudioPlaying:(BOOL)mute;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|BOOL|YES表示停止播放，NO表示恢复播放。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 拉流和解码不受影响。支持[joinChannel](#li_008)之前和之后设置。

-   startAudioCapture：开启音频采集。

    ```
    - (void)startAudioCapture;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口可以控制提前打开音频采集，如果不设置，则SDK会在合适的时机在打开音频采集。

-   stopAudioCapture：关闭音频采集。

    ```
    - (void)stopAudioCapture;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口可以控制关闭音频采集，与startAudioCapture对应。

-   startAudioPlayer：开启音频播放设备。

    ```
    - (void)startAudioPlayer;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口可以控制提前打开音频播放，如果不设置，则SDK会在合适的时机在打开音频播放。

-   stopAudioPlayer：关闭音频播放。

    ```
    - (void)stopAudioPlayer;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口可以控制关闭音频播放，与stopAudioPlayer对应。

-   setRemoteAudioVolume：设置本地播放的指定远端用户音量。

    ```
    - (int)setRemoteAudioVolume:(NSString *_Nonnull)uid volume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|用户ID。|
    |volume|NSInteger|播放音量，取值范围：\[0,100\]，其中0表示静音，100表示原始音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableSpeakerphone：设置音频输出为听筒或扬声器。

    ```
    - (int)enableSpeakerphone:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示扬声器模式，NO表示听筒模式，默认为YES。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   isEnableSpeakerphone：获取当前音频输出为听筒或扬声器。

    ```
    - (BOOL)isEnableSpeakerphone;
    ```

    返回说明

    YES表示扬声器模式，NO表示听筒模式。

-   setRecordingVolume：设置录音音量。

    ```
    - (int)setRecordingVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|取值范围：\[0,400\]，其中0表示静音，大于100表示放大音量，小于100表示减小音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setPlayoutVolume：设置播放音量。

    ```
    - (int)setPlayoutVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|取值范围：\[0,400\]，其中0表示静音，大于100表示放大音量，小于100表示减小音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableAudioVolumeIndication：设置音量回调频率和平滑系数。

    ```
    - (int)enableAudioVolumeIndication:(NSInteger)interval smooth:(NSInteger)smooth reportVad:(NSInteger)reportVad;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |interval|NSInteger|时间间隔，单位为毫秒，最小值不得小于10ms，建议设置300~500ms，小于等于0表示不启用音量提示和说话人提示功能。|
    |smooth|NSInteger|平滑系数，取值范围：\[0,9\]，数值越大平滑程度越高，反之越低，实时性越好，建议设置3。|
    |reportVad|NSInteger|说话人检测开关，取值：     -   1：开启，通过[onAudioVolumeCallback](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)接口回调每一个说话人的状态。
    -   0：关闭。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioProfile：设置音频Profile。

    ```
    - (int)setAudioProfile:(AliRtcAudioProfile)audio_profile audio_scene:(AliRtcAudioScenario)audio_scene;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audio\_profile|[AliRtcAudioProfile](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频采集或编码模式参数。|
    |audio\_scene|[AliRtcAudioScenario](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频场景模式参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioSessionOperationRestriction：设置SDK对AVAudioSession的控制权限。

    ```
    - (int)setAudioSessionOperationRestriction:(AliRtcAudioSessionOperationRestriction)restriction;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |restriction|[AliRtcAudioSessionOperationRestriction](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|控制权限。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDeviceVolumeType：设置SDK设备音量类型。

    ```
    - (int)setDeviceVolumeType:(AliRtcDeviceVolumeType)type;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |type|[AliRtcDeviceVolumeType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音量类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableAudioDTX：开启本地音频流量控制（语音）。

    ```
    - (int)enableAudioDTX:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启，NO表示关闭。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 推流之前调用有效。开启语音活动检测可以在检测到没有语音的情况下，发送字节数减少，节省用户流量。

-   enableAudioAMD：开启本地音频流量控制（麦克风）。

    ```
    - (int)enableAudioAMD:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启，NO表示关闭。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 推流之前调用有效。开启语音活动检测可以在检测到麦克风静音或者关闭麦克风时停止发送音频包。

-   setAudioEffectVoiceChangerMode：设置变声音效模式。

    ```
    - (int)setAudioEffectVoiceChangerMode:(AliRtcAudioEffectVoiceChangerMode)mode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliRtcAudioEffectVoiceChangerMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|模式值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPitchValue：设置变调参数。

    ```
    - (int)setAudioEffectPitchValue:(double)value;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |value|double|取值范围：\[0.5,2.0\]，默认为1.0，表示音调不变。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectReverbMode：设置混响音效模式。

    ```
    - (int)setAudioEffectReverbMode:(AliRtcAudioEffectReverbMode)mode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliRtcAudioEffectReverbMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音效模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectReverbParamType：设置混响音效类型和具体参数。

    ```
    - (int)setAudioEffectReverbParamType:(AliRtcAudioEffectReverbParamType)type value:(float)value;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |type|[AliRtcAudioEffectReverbParamType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音效混响模式。|
    |value|float|具体参数值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startAudioAccompany：开始混音。

    ```
    - (int)startAudioAccompanyWithFile:(NSString *_Nonnull)filePath onlyLocalPlay:(BOOL)onlyLocalPlay replaceMic:(BOOL)replaceMic loopCycles:(NSInteger)loopCycles;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |filePath|NSString \*\_Nonnull|混音文件路径。|
    |onlyLocalPlay|BOOL|是否只本地播放。|
    |replaceMic|BOOL|是否替换掉MIC。|
    |loopCycles|NSInteger|循环次数（可以设置-1或者正整数）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioAccompany：停止混音。

    ```
    - (int)stopAudioAccompany;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioAccompanyVolume：设置混音音量（需要在[startAudioAccompany](#li_083)后才能生效\)。

    ```
    - (int)setAudioAccompanyVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioAccompanyPublishVolume：设置混音之后推流出去的音量（需要在[startAudioAccompany](#li_083)后才能生效）。

    ```
    - (int)setAudioAccompanyPublishVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioAccompanyPublishVolume：获取推流出去的混音音量。

    ```
    - (int)getAudioAccompanyPublishVolume;
    ```

    返回说明

    返回推流出的混音音量，返回0~100为成功，其他为返回的错误码。

-   setAudioAccompanyPlayoutVolume：设置混音之后本地播放的音量（需要在[startAudioAccompany](#li_083)后才能生效）。

    ```
    - (int)setAudioAccompanyPlayoutVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioAccompanyPlayoutVolume：获取混音本地播放的音量。

    ```
    - (int)getAudioAccompanyPlayoutVolume;
    ```

    返回说明

    返回混音本地播放的音量，返回0~100为成功，其他为返回的错误码。

-   pauseAudioAccompany：暂停混音。

    ```
    public abstract int pauseAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAudioAccompany：重新开始混音。

    ```
    - (int)pauseAudioAccompany;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioAccompanyDuration：获取伴奏文件时长。

    ```
    - (int)getAudioAccompanyDuration;
    ```

    返回说明

    返回伴奏文件时长（单位：ms），小于0表示错误码。

-   getAudioAccompanyCurrentPosition：获取音乐文件播放进度。

    ```
    - (int)getAudioAccompanyCurrentPosition;
    ```

    返回说明

    返回音乐文件播放进度（单位：ms），小于0表示错误码。

-   setAudioAccompanyPosition：设置音频文件的播放位置。

    ```
    - (int)setAudioAccompanyPosition:(int)pos;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |pos|int|进度条位置，单位为毫秒。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PreloadAudioEffect：预加载音效文件。

    ```
    - (int)preloadAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *_Nonnull)filePath;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*\_Nonnull|音效文件路径。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   unloadAudioEffect：删除预加载的音效文件。

    ```
    - (int)unloadAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   playAudioEffect：开始播放音效。

    ```
    - (int)playAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *_Nonnull)filePath cycles:(NSInteger)cycles publish:(BOOL)publish;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*\_Nonnull|音效文件路径。|
    |cycles|NSInteger|循环次数（可以设置-1或者正整数）。|
    |publish|BOOL|是否发布。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAudioEffect：停止播放音效。

    ```
    - (int)stopAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopAllAudioEffects：停止播放所有音效。

    ```
    - (int)stopAllAudioEffects;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPublishVolume：设置音效推流音量。

    ```
    - (int)setAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioEffectPublishVolume：获取推流音效音量。

    ```
    - (int)getAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAudioEffectPlayoutVolume：设置音效本地播放音量。

    ```
    - (int)setAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getAudioEffectPlayoutVolume：获取音效本地播放音量。

    ```
    - (int)getAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAllAudioEffectsPublishVolume：设置所有音效本地播放音量。

    ```
    - (int)setAllAudioEffectsPublishVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setAllAudioEffectsPlayoutVolume：设置所有音效推流音量。

    ```
    - (int)setAllAudioEffectsPlayoutVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pauseAudioEffect：暂停音效。

    ```
    - (int)pauseAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pauseAllAudioEffects：暂停所有音效。

    ```
    - (int)pauseAllAudioEffects;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAudioEffect：重新开始播放音效。

    ```
    - (int)resumeAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   resumeAllAudioEffects：重新开始播放所有音效。

    ```
    - (int)resumeAllAudioEffects;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   enableEarBack：启用耳返。

    ```
    - (int)enableEarBack:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|是否启用耳返。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setEarBackVolume：设置耳返音量。

    ```
    - (int)setEarBackVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|取值范围：\[0,100\]，默认100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   registerVideoSampleObserver：订阅视频数据输出。

    ```
    - (void)registerVideoSampleObserver;
    ```

-   unRegisterVideoSampleObserver：取消订阅视频数据输出。

    ```
    - (void)unregisterVideoSampleObserver;
    ```

-   registerLocalVideoTexture：订阅本地视频纹理数据。

    ```
    - (void)registerLocalVideoTexture;
    ```

-   unregisterLocalVideoTexture：取消本地视频纹理数据输出。

    ```
    - (void)unregisterLocalVideoTexture;
    ```

-   subscribeAudioData：订阅音频数据输出。

    ```
    - (void)subscribeAudioData:(AliRtcAudioSource)audioSource;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliRtcAudioSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|数据类型。|

-   unSubscribeAudioData：取消音频数据输出。

    ```
    - (void)unSubscribeAudioData:(AliRtcAudioSource)audioSource;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliRtcAudioSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|数据类型。|

-   setSubscribeAudioNumChannel：设置输出音频声道数（混音前数据不支持该参数设置）。

    ```
    - (void)setSubscribeAudioNumChannel:(AliRtcAudioNumChannel)audioNumChannel;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioNumChannel|[AliRtcAudioNumChannel](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|声道数，默认单声道。|

-   setSubscribeAudioSampleRate：设置输出音频采样率（混音前数据不支持该参数设置）。

    ```
    - (void)setSubscribeAudioSampleRate:(AliRtcAudioSampleRate)audioSampleRate;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSampleRate|[AliRtcAudioSampleRate](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|采样率，默认44.1kHz。|

-   setExternalVideoSource：启用外部视频输入源。

    ```
    - (int)setExternalVideoSource:(BOOL)enable useTexture:(BOOL)useTexture sourceType:(AliRtcVideoSource)type renderMode:(AliRtcRenderMode)renderMode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启，NO表示关闭。|
    |useTexture|BOOL|是否使用Texture模式。|
    |type|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|流类型。|
    |renderMode|[AliRtcRenderMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|渲染模式。|

-   pushExternalVideoFrame：输入视频数据。

    ```
    - (int)pushExternalVideoFrame:(AliRtcVideoDataSample *_Nonnull)frame sourceType:(AliRtcVideoSource)type;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |frame|[AliRtcVideoDataSample](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|帧数据。|
    |type|[AliRtcVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setExternalAudioSource：设置是否启用外部音频输入源。

    ```
    - (int)setExternalAudioSource:(BOOL)enable withSampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启，NO表示关闭。|
    |sampleRate|NSUInteger|采样率，例如16000Hz、48000Hz等。|
    |channelsPerFrame|NSUInteger|声道数，例如1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pushExternalAudioFrameRawData：输入音频数据。

    ```
    - (int)pushExternalAudioFrameRawData:(void *_Nonnull)data samples:(NSUInteger)samples timestamp:(NSTimeInterval)timestamp;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |data|void \*\_Nonnull|音频数据，不建议超过40ms数据。|
    |samples|NSUInteger|采样率，例如16kHz、48kHz等。|
    |timestamp|NSTimeInterval|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setExternalAudioVolume：设置混音音量。

    ```
    - (int)setExternalAudioVolume:(int)vol;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |vol|int|混音音量，取值范围：\[1,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getExternalAudioVolume：获取混音音量。

    ```
    - (int)getExternalAudioVolume;
    ```

    返回说明

    返回当前混音音量。

-   setMixedWithMic：设置是否与麦克风采集音频混合。

    ```
    - (int)setMixedWithMic:(BOOL)mixed;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mixed|BOOL|YES表示混音，NO表示完全替换麦克风采集数据。|

    返回说明

    返回当前混音音量。

-   setExteranlAudioRender：设置是否启用外部输入音频播放。

    ```
    - (int)setExteranlAudioRender:(BOOL)enable sampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES表示开启，NO表示关闭。|
    |sampleRate|NSUInteger|采样率，例如16kHz、48kHz等。|
    |channelsPerFrame|NSUInteger|声道数，例如1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   pushExternalAudioRenderRawData：输入外部音频播放数据。

    ```
    - (int)pushExternalAudioRenderRawData:(const void* _Nullable)audioSamples sampleLength:(NSUInteger)sampleLength sampleRate:(NSUInteger)sampleRate channelsPerFrame:(NSUInteger)channelsPerFrame timestamp:(long long)timestamp;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSamples|constvoid\* \_Nullable|音频数据。|
    |sampleLength|NSUInteger|音频数据长度。|
    |sampleRate|NSUInteger|音频采样率。|
    |channelsPerFrame|NSUInteger|音频声道数。|
    |timestamp|long long|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startLiveStreaming：开始直播拉流。

    ```
    - (void)startLiveStreamingWithAuthInfo:(AliRtcAuthInfo *_Nonnull)authInfo onResult:(void(^_Nullable)(int errCode))onResult;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|入会鉴权信息。|
    |onResult|void\(^\_Nullable\)\(int errCode\)|拉流结果回调，当错误码为0时表示拉流成功，其他表示拉流失败。|

-   stopLiveStreaming：停止直播拉流。

    ```
    - (int)stopLiveStreaming;
    ```

-   startPublishLiveStream：开启旁路直播。

    ```
    - (int)startPublishLiveStreamWithURL:(NSString *_Nonnull)streamURL liveTranscoding:(AliRtcLiveTranscoding *_Nonnull)trancoding;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamUrl|NSString \*\_Nonnull|推流地址。|
    |transcoding|[AliRtcLiveTranscoding](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   updatePublishLiveStream：更新旁路直播相关参数。

    ```
    - (int)updatePublishLiveStreamWithURL:(NSString *_Nonnull)streamURL liveTranscoding:(AliRtcLiveTranscoding *_Nonnull)trancoding;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamUrl|NSString \*\_Nonnull|推流地址。|
    |transcoding|[AliRtcLiveTranscoding](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopPublishLiveStream：停止旁路直播。

    ```
    - (int)stopPublishLiveStreamWithURL:(NSString *_Nonnull)streamURL;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamUrl|NSString \*\_Nonnull|推流地址。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setLiveStreamingViewConfig：设置直播拉流窗口及渲染参数。

    ```
    - (int)setLiveStreamingViewConfig:(AliVideoCanvas *_Nullable)canvas;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |canvas|[AliVideoCanvas](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nullable|canvas包含了窗口以及渲染方式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startChannelRelay：开启跨频道连麦。

    ```
    - (int)startChannelRelay:(AliRtcChannelRelayConfiguration *_Nonnull)configuration;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |configuration|[AliRtcChannelRelayConfiguration](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   updateChannelRelay：更新跨频道连麦。

    ```
    - (int)updateChannelRelay:(AliRtcChannelRelayConfiguration *_Nonnull)configuration;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |configuration|[AliRtcChannelRelayConfiguration](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   stopChannelRelay：停止跨频道连麦。

    ```
    - (int)stopChannelRelay;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   startPreview：开始本地预览（会自动打开摄像头）。

    ```
    - (int)startPreview;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 如果没有设置view，则无法预览。可以在[joinChannel](#li_008)之前就开启预览。

-   stopPreview：停止本地预览。

    ```
    - (int)stopPreview;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** leaveChannel会自动停止本地预览，且会自动关闭摄像头（如果正在推camera流，则不会关闭摄像头）。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    - (NSArray<NSString *> *_Nullable)getOnlineRemoteUsers;
    ```

    返回说明

    返回用户列表（保存的是用户ID）。

-   getUserInfo：查询远端用户信息。

    ```
    - (NSDictionary *_Nullable)getUserInfo:(NSString *_Nonnull)uid;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|要获取的目标用户ID。|

    返回说明

    返回一个字典，其中key关键字含义如下所示：

    |key关键字|含义|
    |------|--|
    |userID|远端用户的ID。|
    |displayName|远端用户的名称。|
    |sessionID|远端用户的会话ID。|
    |isOnline|远端用户是否在线。|
    |isCameraMirror|远端用户是否开启了相机流镜像。|
    |isScreenMirror|远端用户是否开启了屏幕流镜像。|
    |muteAudioPlaying|本端是否静音了此远端用户。|
    |preferCameraMaster|远端用户是否开启了大流优先。|
    |hasCameraView|本端是否设置了此远端用户相机流的view。|
    |hasScreenView|本端是否设置了此远端用户屏幕流的view。|
    |hasAudio|远端用户是否推送了音频流。|
    |hasCameraMaster|远端用户是否推送了相机大流。|
    |hasCameraSlave|远端用户是否推送了相机小流。|
    |hasScreenSharing|远端用户是否推送了屏幕流。|
    |requestAudio|本端是否订阅了此远端用户的音频流。|
    |requestCameraMaster|本端是否订阅了此远端用户的相机大流。|
    |requestCameraSlave|本端是否订阅了此远端用户的相机小流。|
    |requestScreenSharing|本端是否订阅了此远端用户的屏幕流。|
    |subScribedAudio|本端是否拉到了此远端用户的音频流。|
    |subScribedCameraMaster|本端是否拉到了此远端用户的相机大流。|
    |subScribedCamearSlave|本端是否拉到了此远端用户的相机小流。|
    |subScribedScreenSharing|本端是否拉到了此远端用户的屏幕流。|

-   isUserOnline：查询用户是否在线。

    ```
    - (BOOL)isUserOnline:(NSString *_Nonnull)uid;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nonnull|用户ID。从App server分配的唯一标示符。|

    返回说明

    YES表示在线，NO表示离线。

-   getSdkVersion：获取SKD版本号。

    ```
    + (NSString *_Nonnull)getSdkVersion;
    ```

    返回说明

    返回SDK版本号。

-   getErrorDescription：获取错误码描述。

    ```
    + (NSString *_Nullable)getErrorDescription:(NSInteger)errCode;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |errorCode|NSInteger|错误码。|

    返回说明

    返回错误码描述字符串。

-   setClientRole：设置用户角色。

    ```
    - (int)setClientRole:(AliRtcClientRole)role;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |role|[AliRtcClientRole](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|用户角色类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentClientRole：获取用户角色。

    ```
    - (AliRtcClientRole)getCurrentClientRole;
    ```

    返回说明

    返回当前用户角色。

-   startLastmileDetect：开始网络质量探测。

    ```
    - (int)startLastmileDetect;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 请在[joinChannel](#li_008)之前调用，探测结果在[onLastmileDetectResultWithQuality](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)回调。

-   stopLastmileDetect：停止网络质量探测。

    ```
    - (int)stopLastmileDetect;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   postFeedbackWithUid：SDK问题反馈。

    ```
    - (void)postFeedbackWithUid:(NSString *_Nullable)uid channleId:(NSString *_Nullable)channelId description:(NSString *_Nonnull)description type:(AliRtcFeedbackType)type timeStamp:(NSTimeInterval)timeStamp;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*\_Nullable|当前UID（允许为空）。|
    |channelId|NSString \*\_Nullable|当前频道ID（允许为空）。|
    |description|NSString \*\_Nullable|问题描述（支持中英文，不允许为空）。|
    |type|[AliRtcFeedbackType](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|问题类型。|
    |timeStamp|NSTimeInterval|问题发生的时间戳（Unix时间戳，可以为大致时间，无需特别精确，也可以为0）。|

-   sendMediaExtensionMsg：发送媒体扩展信息。

    ```
    - (int)sendMediaExtensionMsg:(NSData *_Nonnull)data repeatCount:(int)repeatCount;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |data|NSData \*\_Nonnull|扩展信息。|
    |repeatCount|int|重复次数。|

    返回说明

    -   0：成功。
    -   -1：未推流。
    -   -2：参数错误。
    -   -3：发送过于频繁，建议稍后再发送。
-   startIntelligentDenoise：开启智能降噪。

    ```
    - (int)startIntelligentDenoise;
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   此接口可以通话过程中控制打开智能降噪功能。
    -   此功能默认关闭，开启后可能导致功耗增加，智能降噪适合于会议，教育等语音通讯为主的场景，不适合有背景音乐的场景。
-   stopIntelligentDenoise：关闭智能降噪。

    ```
    - (void)stopIntelligentDenoise;
    ```

    **说明：** 此接口可以通话过程中控制关闭智能降噪功能。

-   refreshAuthInfo：刷新鉴权信息。

    ```
    - (int)refreshAuthInfo:(AliRtcAuthInfo *_Nonnull)authInfo;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|[AliRtcAuthInfo](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md) \*\_Nonnull|鉴权信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   getCurrentConnectionStatus：获取当前网络连接状态。

    ```
    - (AliRtcConnectionStatus)getCurrentConnectionStatus;
    ```

    返回说明

    返回当前网络连接状态。

-   enableDelegateMainQueue：是否分发回调到主线程。

    ```
    - (int)enableDelegateMainQueue:(BOOL)enabled;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enabled|BOOL|YES表示回调分发至主线程队列，NO表示回调不分发至主线程队列，默认为YES。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   setDelegateQueue：指定回调线程队列。

    ```
    - (int)setDelegateQueue:(NSOperationQueue *_Nullable)queue;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |queue|NSOperationQueue \*\_Nullable|回调队列。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   如果调用[enableDelegateMainQueue](#li_155):YES时，此接口设置无效，回调线程为主线程。
    -   如果调用[enableDelegateMainQueue](#li_155):NO时，可通过此接口指定回调线程，若不设置，则使用SDK的默认子线程。

