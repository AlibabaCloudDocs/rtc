---
keyword: [Windows SDK, AliEngine]
---

# AliEngine接口

通过阅读本文，您可以了解到Windows SDK的AliEngine接口详情。

## 目录

基础接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetH5CompatibleMode](#li_001)|设置H5兼容模式。|1.1|
|[GetH5CompatibleMode](#li_002)|检查当前是否兼容H5。|1.1|
|[Create](#li_003)|创建一个AliEngine实例。|2.1|
|[Destroy](#li_004)|SDK资源释放。|1.1|
|[UploadLog](#li_005)|上传日志。|1.15|
|[SetLogDirPath](#li_006)|设置SDK日志文件保存路径。|1.16.2|
|[SetEngineEventListener](#li_007)|设置回调。|2.1|
|[QueryInterface](#li_008)|获取功能接口实例。|2.1|

频道相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[JoinChannel](#li_009)|加入频道。|1.1|
|[LeaveChannel](#li_010)|离开频道。|1.1|
|[SwitchChannel](#li_011)|切换频道。|2.1|
|[IsInCall](#li_012)|检查当前是否在频道中。|1.1|
|[SetChannelProfile](#li_013)|设置频道模式。|1.15|
|[CreateChannel](#li_014)|创建一个AliEngine子频道实例。|2.1|
|[DestroyChannel](#li_015)|销毁[CreateChannel](#li_014)创建的子频道。|2.1|

发布相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[PublishLocalVideoStream](#li_016)|设置是否允许推视频流。|2.1|
|[IsLocalVideoStreamPublished](#li_017)|查询当前是否允许推视频流。|1.1|
|[IsScreenSharePublished](#li_018)|查询当前是否允许推屏幕流。|1.1|
|[PublishLocalAudioStream](#li_019)|设置是否允许推音频流。|2.1|
|[IsLocalAudioStreamPublished](#li_020)|查询当前是否允许推音频流。|1.1|
|[PublishLocalDualStream](#li_021)|设置是否允许推次要视频流。|2.1|
|[IsDualStreamPublished](#li_022)|查询当前是否允许推次要视频流。|2.1|

订阅相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetRemoteVideoStreamType](#li_023)|设置订阅的相机流格式。|2.1|
|[SetRemoteDefaultVideoStreamType](#li_024)|设置默认订阅的相机流格式。|2.1|
|[SetDefaultSubscribeAllRemoteAudioStreams](#li_025)|设置是否默认拉音频流。|2.1|
|[SubscribeAllRemoteAudioStreams](#li_026)|停止或恢复拉所有远端音频流。|2.1|
|[SubscribeRemoteAudioStream](#li_027)|停止或恢复特定远端用户的音频流拉取。|2.1|
|[SetDefaultSubscribeAllRemoteVideoStreams](#li_028)|设置是否默认拉视频流。|2.1|
|[SubscribeAllRemoteVideoStreams](#li_029)|停止或恢复拉所有远端视频流。|2.1|
|[SubscribeRemoteVideoStream](#li_030)|停止或恢复特定远端用户的视频流拉取。|2.1|

视频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetScreenShareEncoderConfiguration](#li_031)|设置屏幕共享编码属性。|2.1|
|[SetLocalViewConfig](#li_032)|为本地预览设置渲染窗口以及绘制参数。|1.1|
|[SetCameraCapturerConfiguration](#li_033)|设置摄像头采集偏好。|2.1|
|[SetDeviceOrientationMode](#li_034)|设置设备方向（适用于Android或iOS端）。|2.1|
|[EnableLocalVideo](#li_035)|禁用或重新启用本地视频采集。|2.1|
|[MuteLocalCamera](#li_036)|设置是否停止推本地视频流。|1.1|
|[MuteAllRemoteVideo](#li_037)|停止或恢复远端所有的视频渲染。|2.1|
|[SetRemoteViewConfig](#li_038)|为远端的视频设置渲染窗口以及绘制参数。|1.1|
|[UpdateViewConfig](#li_039)|更新渲染配置。|2.1|
|[IsCameraOn](#li_040)|检查摄像头是否打开。|1.1|
|[StopRecord](#li_041)|停止录制。|1.17|
|[StartRecord](#li_042)|开始录制（非布局录制）。|1.17|
|[StartRecord](#li_043)|开始录制（窗口布局录制）。|2.1|
|[UpdateRecordLayout](#li_044)|更新录制内容信息。|2.1|
|[AddRecordTemplate](#li_045)|添加录制模板。|2.1|
|[PauseRecord](#li_046)|暂停录制。|2.1|
|[ResumeRecord](#li_047)|重新开始录制。|2.1|
|[SetBeautyEffect](#li_048)|设置基础美颜。|1.17.9|
|[SetVideoEncoderConfiguration](#li_049)|设置视频编码属性。|2.1|
|[AddVideoWatermark](#li_050)|添加水印。|2.1|
|[ClearVideoWatermark](#li_051)|清理对应数据流水印信息。|2.1|
|[SnapshotVideo](#li_052)|截图。|2.1|
|[SwitchCamera](#li_053)|切换前后摄像头（适用于Android或iOS端）。|2.1|
|[GetCurrentCameraDirection](#li_054)|获取当前摄像头方向（适用于Android或iOS端）。|2.1|
|[SetCameraZoom](#li_055)|设置摄像头缩放比例（适用于Android或iOS端）。|2.1|
|[SetCameraFlash](#li_056)|设置摄像头闪光灯是否打开（适用于Android或iOS端）。|2.1|
|[IsCameraFocusPointSupported](#li_057)|摄像头是否支持手动聚焦（适用于Android或iOS端）。|2.1|
|[IsCameraExposurePointSupported](#li_058)|摄像头是否支持设置曝光区域（适用于Android或iOS端）。|2.1|
|[SetCameraFocusPoint](#li_059)|设置摄像头手动聚焦（适用于Android或iOS端）。|2.1|
|[SetCameraExposurePoint](#li_060)|设置摄像头曝光点（适用于Android或iOS端）。|2.1|
|[IsCameraAutoFocusFaceModeSupported](#li_061)|摄像头是否支持人脸聚焦（适用于Android或iOS端）。|2.1|
|[SetCameraAutoFocusFaceModeEnabled](#li_062)|设置摄像头人脸对焦（适用于Android或iOS端）。|2.1|

共享视频接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartScreenShareByDesktopId](#li_063)|根据桌面ID进行屏幕分享。|2.1|
|[StartScreenShareByScreenRegion](#li_064)|根据屏幕区域进行屏幕分享。|2.1|
|[StartScreenShareByWindowId](#li_065)|根据窗口ID进行屏幕分享。|2.1|
|[StartScreenShare](#li_066)|开始屏幕分享（适用于Android或iOS端）。|2.1|
|[StopScreenShare](#li_067)|停止屏幕分享。|2.1|
|[UpdateScreenShareConfig](#li_068)|更新屏幕分享配置。|2.1|
|[GetScreenShareConfig](#li_069)|获取屏幕共享配置。|2.1|
|[GetScreenShareSourceInfo](#li_070)|获取屏幕分享源信息。|2.1|
|[GetCurrentScreenShareSourceId](#li_071)|获取当前屏幕共享源ID。|2.1|
|[GetCurrentScreenShareSourceType](#li_072)|获取当前屏幕共享源类型。|2.1|
|[GetDesktopRegion](#li_073)|获取屏幕分享桌面区域。|2.1|

音频相关接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetAudioOnlyMode](#li_075)|设置为纯音频模式还是音视频模式。|1.1|
|[IsAudioOnlyMode](#li_076)|查询当前是否为纯音频模式。|1.1|
|[MuteLocalMic](#li_077)|设置是否停止推本地音频。|1.1|
|[MuteRemoteAudio](#li_078)|设置是否停止播放远端音频流。|1.1|
|[MuteAllRemoteAudio](#li_079)|停止或恢复远端所有的音频播放。|1.16.2|
|[StartAudioCapture](#li_080)|开启音频采集。|1.11|
|[StopAudioCapture](#li_081)|关闭音频采集。|1.11|
|[StartAudioPlayer](#li_082)|开启音频播放设备。|1.11|
|[StopAudioPlayer](#li_083)|关闭音频播放。|1.11|
|[SetRemoteAudioVolume](#li_084)|设置本地播放的指定远端用户音量。|2.1|
|[SetDefaultAudioRouteToSpeakerphone](#li_085)|设置默认音频输出为听筒或扬声器（适用于Android或iOS端）。|2.1|
|[EnableSpeakerphone](#li_086)|设置音频输出为听筒或扬声器（适用于Android或iOS端）。|2.1|
|[IsEnableSpeakerphone](#li_087)|获取当前音频输出为听筒还是扬声器（适用于Android或iOS端）。|2.1|
|[SetRecordingVolume](#li_088)|设置录音音量。|1.16.2|
|[SetPlayoutVolume](#li_089)|设置播放音量。|1.16.2|
|[EnableAudioVolumeIndication](#li_090)|设置音量回调频率和平滑系数。|1.17.9|
|[SetAudioProfile](#li_091)|设置音频Profile。|2.1|
|[SetDeviceVolumeType](#li_092)|设置音量类型（适用于iOS端）。|2.1|
|[EnableAudioDTX](#li_093)|开启本地音频流量控制（检测语音）。|2.1|
|[EnableAudioAMD](#li_094)|开启本地音频流量控制（检测麦克风）。|2.1|
|[SetAudioEffectVoiceChangerMode](#li_096)|设置变声音效模式。|2.1|
|[SetAudioEffectPitchValue](#li_097)|设置变调参数。|2.1|
|[SetAudioEffectReverbMode](#li_098)|设置混响音效模式。|2.1|
|[SetAudioEffectReverbParamType](#li_099)|设置混响音效类型和具体参数。|2.1|
|[StartAudioAccompany](#li_100)|开始混音（适用于Android或iOS端）。|2.1|
|[StopAudioAccompany](#li_101)|停止混音（适用于Android或iOS端）。|2.1|
|[SetAudioAccompanyVolume](#li_102)|设置混音音量（适用于Android或iOS端）。|2.1|
|[SetAudioAccompanyPublishVolume](#li_103)|设置混音之后推流出去的音量（适用于Android或iOS端）。|2.1|
|[GetAudioAccompanyPublishVolume](#li_104)|获取推流出去的混音音量（适用于Android或iOS端）。|2.1|
|[SetAudioAccompanyPlayoutVolume](#li_105)|设置混音之后本地播放的音量（适用于Android或iOS端）。|2.1|
|[GetAudioAccompanyPlayoutVolume](#li_106)|获取混音本地播放的音量（适用于Android或iOS端）。|2.1|
|[PauseAudioAccompany](#li_107)|暂停混音（适用于Android或iOS端）。|2.1|
|[ResumeAudioAccompany](#li_108)|重新开始混音（适用于Android或iOS端）。|2.1|
|[GetAudioAccompanyDuration](#li_109)|获取伴奏文件时长（适用于Android或iOS端）。|2.1|
|[GetAudioAccompanyCurrentPosition](#li_110)|获取音乐文件播放进度（适用于Android或iOS端）。|2.1|
|[SetAudioAccompanyPosition](#li_111)|设置音频文件的播放位置（适用于Android或iOS端）。|2.1|
|[PreloadAudioEffect](#li_112)|预加载音效文件（适用于Android或iOS端）。|2.1|
|[UnloadAudioEffect](#li_113)|删除预加载的音效文件（适用于Android或iOS端）。|2.1|
|[PlayAudioEffect](#li_114)|开始播放音效（适用于Android或iOS端）。|2.1|
|[StopAudioEffect](#li_115)|停止播放音效（适用于Android或iOS端）。|2.1|
|[StopAllAudioEffects](#li_116)|停止播放所有音效（适用于Android或iOS端）。|2.1|
|[SetAudioEffectPublishVolume](#li_117)|设置音效推流音量（适用于Android或iOS端）。|2.1|
|[GetAudioEffectPublishVolume](#li_118)|获取推流音效音量（适用于Android或iOS端）。|2.1|
|[SetAudioEffectPlayoutVolume](#li_119)|设置音效本地播放音量（适用于Android或iOS端）。|2.1|
|[GetAudioEffectPlayoutVolume](#li_120)|获取音效本地播放音量（适用于Android或iOS端）。|2.1|
|[SetAllAudioEffectsPublishVolume](#li_121)|设置所有音效本地播放音量（适用于Android或iOS端）。|2.1|
|[SetAllAudioEffectsPlayoutVolume](#li_122)|设置所有音效推流音量（适用于Android或iOS端）。|2.1|
|[PauseAudioEffect](#li_123)|暂停音效（适用于Android或iOS端）。|2.1|
|[PauseAllAudioEffects](#li_124)|暂停所有音效（适用于Android或iOS端）。|2.1|
|[ResumeAudioEffect](#li_125)|重新开始播放音效（适用于Android或iOS端）。|2.1|
|[ResumeAllAudioEffects](#li_126)|重新开始播放所有音效（适用于Android或iOS端）。|2.1|
|[EnableEarBack](#li_127)|启用耳返（适用于Android或iOS端）。|2.1|
|[SetEarBackVolume](#li_128)|设置耳返音量（适用于Android或iOS端）。|2.1|
|[EnableSystemAudioRecording](#li_129)|设置是否开启系统声音采集推送。|2.1|
|[IsSystemAudioRecording](#li_130)|当前是否开启系统声音采集推送。|2.1|
|[SetSystemAudioRecordingVolume](#li_131)|设置系统声音采集推送音量。|2.1|
|[GetSystemAudioRecordingVolume](#li_132)|获取当前设置系统声音采集推送音量。|2.1|

音频设备管理接口

|API|描述|支持的最低版本|
|---|--|-------|
|[GetAudioCaptureList](#li_133)|获取系统中的录音设备列表。|2.1|
|[GetCurrentAudioCaptureName](#li_134)|获取使用的录音设备名称。|2.1|
|[GetCurrentAudioCaptureID](#li_135)|获取使用的录音设备ID。|2.1|
|[SetCurrentAudioCaptureName](#li_136)|选择录音设备名称。|2.1|
|[SetCurrentAudioCaptureID](#li_137)|选择录音设备ID。|2.1|
|[GetAudioPlayerList](#li_138)|获取系统中的扬声器列表。|2.1|
|[GetCurrentAudioPlayerName](#li_139)|获取当前使用的扬声器名称。|2.1|
|[GetCurrentAudioPlayerID](#li_140)|获取当前使用的扬声器ID。|2.1|
|[SetCurrentAudioPlayerName](#li_141)|选择扬声器名称。|2.1|
|[SetCurrentAudioPlayerID](#li_142)|选择扬声器ID。|2.1|
|[SetRecordingDeviceVolume](#li_143)|设置音频采集设备音量。|2.1|
|[GetRecordingDeviceVolume](#li_144)|获取音频采集设备音量。|2.1|
|[SetPlaybackDeviceVolume](#li_145)|设置音频播放设备音量。|2.1|
|[GetPlaybackDeviceVolume](#li_146)|获取音频播放设备音量。|2.1|
|[StartTestAudioRecordByName](#li_147)|开始测试音频采集设备。|2.1|
|[StartTestAudioRecordById](#li_148)|开启麦克风设备测试（按设备ID）。|2.1|
|[StopTestAudioRecord](#li_149)|停止测试音频采集设备。|2.1|
|[StartTestAudioPlayoutByName](#li_150)|开始测试音频播放设备。|2.1|
|[StartTestAudioPlayoutById](#li_151)|开启扬声器设备测试（按设备ID）。|2.1|
|[StopTestAudioPlayout](#li_152)|停止测试音频播放设备。|2.1|

视频设备管理接口

|API|描述|支持的最低版本|
|---|--|-------|
|[GetCameraList](#li_153)|获取摄像头列表。|2.1|
|[GetCurrentCameraName](#li_154)|获取当前使用的摄像头名称。|2.1|
|[GetCurrentCameraID](#li_155)|获取当前使用的摄像头ID。|2.1|
|[SetCurrentCameraName](#li_156)|选择摄像头名称。|2.1|
|[SetCurrentCameraID](#li_157)|选择摄像头ID。|2.1|

媒体引擎接口

|API|描述|支持的最低版本|
|---|--|-------|
|[RegisterVideoSampleObserver](#li_158)|订阅视频数据输出。|2.1|
|[UnRegisterVideoSampleObserver](#li_159)|取消订阅视频数据输出。|2.1|
|[RegisterLocalVideoTextureObserver](#li_160)|订阅本地视频纹理数据。|2.1|
|[UnRegisterLocalVideoTextureObserver](#li_161)|取消本地视频纹理数据输出。|2.1|
|[RegisterAudioFrameObserver](#li_162)|订阅音频数据输出。|2.1|
|[UnRegisterAudioFrameObserver](#li_163)|取消音频数据输出。|2.1|
|[RegisterAudioEventObserver](#li_164)|订阅音频事件（默认订阅）。|2.1|
|[UnRegisterAudioEventObserver](#li_165)|取消订阅音频事件。|2.1|
|[SetSubscribeAudioNumChannel](#li_166)|设置输出音频声道数（混音前数据不支持该参数设置）。|2.1|
|[SetSubscribeAudioSampleRate](#li_167)|设置输出音频采样率（混音前数据不支持该参数设置）。|2.1|
|[SubscribeAudioData](#li_168)|订阅音频数据。|2.1|
|[UnsubscribeAudioData](#li_169)|取消订阅音频数据。|2.1|
|[SetExternalVideoSource](#li_170)|启用外部视频输入源。|2.1|
|[PushExternalVideoFrame](#li_171)|输入视频数据。|2.1|
|[SetExternalAudioSource](#li_172)|设置是否启用外部音频输入源。|2.1|
|[PushExternalAudioFrameRawData](#li_173)|输入音频数据。|2.1|
|[SetExternalAudioPublishVolume](#li_174)|设置混音音量。|2.1|
|[GetExternalAudioPublishVolume](#li_175)|获取混音音量。|2.1|
|[SetMixedWithMic](#li_176)|设置是否与麦克风采集音频混合。|2.1|
|[SetExteranlAudioRender](#li_177)|设置是否启用外部输入音频播放。|2.1|
|[PushExternalAudioRenderRawData](#li_178)|输入外部音频播放数据。|2.1|
|[SetExternalAudioRenderVolume](#li_179)|设置音频外部播放源音量。|2.1|
|[GetExternalAudioRenderVolume](#li_180)|获取音频外部播放源音量。|2.1|

直播旁路接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartLiveStreaming](#li_181)|开始直播拉流。|2.1|
|[StopLiveStreaming](#li_182)|停止直播拉流。|2.1|
|[StartPublishLiveStream](#li_183)|开启旁路直播。|2.1|
|[UpdatePublishLiveStream](#li_184)|更新旁路直播相关参数。|2.1|
|[StopPublishLiveStream](#li_185)|停止旁路直播。|2.1|
|[SetLiveStreamingViewConfig](#li_186)|设置直播拉流窗口及渲染参数。|2.1|
|[UpdateLiveStreamingViewConfig](#li_187)|更新直播拉流窗口及渲染参数。|2.1|

跨频道连麦接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartChannelRelay](#li_188)|开启跨频道连麦。|2.1|
|[UpdateChannelRelay](#li_189)|更新跨频道连麦。|2.1|
|[StopChannelRelay](#li_190)|停止跨频道连麦。|2.1|

预览接口

|API|描述|支持的最低版本|
|---|--|-------|
|[StartPreview](#li_191)|开始本地预览。|1.1|
|[StopPreview](#li_192)|停止本地预览。|1.1|

远端用户查询接口

|API|描述|支持的最低版本|
|---|--|-------|
|[GetOnlineRemoteUsers](#li_193)|获取远端在线用户列表。|1.1|
|[GetUserInfo](#li_194)|查询远端用户信息。|1.1|
|[IsUserOnline](#li_195)|查询用户是否在线。|1.1|

其他接口

|API|描述|支持的最低版本|
|---|--|-------|
|[SetLogLevel](#li_196)|设置日志级别。|1.1|
|[GetSDKVersion](#li_197)|获取SDK版本号。|1.1|
|[GetErrorDescription](#li_198)|获取错误码描述|2.1|
|[GetEncodeParam](#li_199)|获取编码分辨率|2.1|
|[SetClientRole](#li_200)|设置用户角色。|1.16|
|[GetClientRole](#li_201)|获取用户角色。|1.17.19|
|[StartLastmileDetect](#li_202)|开始网络质量探测。|1.16.2|
|[StopLastmileDetect](#li_203)|停止网络质量探测。|1.16.2|
|[PostFeedback](#li_204)|SDK问题反馈。|1.17.12|
|[SendMediaExtensionMsg](#li_205)|发送媒体扩展信息。|1.17.1|
|[StartIntelligentDenoise](#li_206)|开启智能降噪。|1.17.19|
|[StopIntelligentDenoise](#li_207)|关闭智能降噪。|1.17.19|
|[RefreshAuthInfo](#li_208)|刷新令牌。|1.17.41|
|[SetAudioSessionOperationRestriction](#li_209)|设置SDK对AVAudioSession的控制权限（适用于iOS端）。|2.1|
|[GetCurrentConnectionStatus](#li_210)|获取当前网络链接状态。|2.1|

## 接口详情

-   SetH5CompatibleMode：设置是否兼容H5。

    ```
    static void SetH5CompatibleMode(bool comp);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |comp|bool|是否兼容H5。取值：     -   true：兼容H5。
    -   false（默认值）：不兼容H5。 |

    **说明：** 当前版本不支持在创建AliEngine实例之后更改H5兼容模式，必须在创建实例之前就调用此方法。

-   GetH5CompatibleMode：检查当前是否兼容H5。

    ```
    static bool GetH5CompatibleMode();
    ```

    返回说明

    true表示兼容H5，false表示不兼容H5。

-   Create：获取一个AliEngine实例。

    ```
    static AliEngine *Create(const char *extras);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |extras|const char \*|通过JSON配置SDK的特别功能，详情请参见[extras功能说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。|

    **说明：** 同一时间只会存在一个主实例。

-   Destroy：SDK资源释放。

    ```
    static AliEngine::Destroy();
    ```

    **说明：** 在所有操作结束之后调用。

-   UploadLog：上传日志。默认会自动上传。

    ```
    static void UploadLog();
    ```

-   SetLogDirPath：设置SDK日志文件保存路径。

    ```
    static int SetLogDirPath(const char *logDirPath);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logDirPath|const char \*|日志文件保存绝对路径。默认路径：%appdata%目录下。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 如需调用此接口，请在调用所有SDK接口前进行设置，避免日志出现丢失，同时App必须保证指定的目录已存在且可写入。

-   SetEngineEventListener：设置回调。

    ```
    int SetEngineEventListener(AliEngineEventListener *listener);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |listener|AliEngineEventListener \*|回调类指针。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   QueryInterface：获取功能接口实例。

    ```
    int QueryInterface(AliEngineInterfaceIdType iid, void** pInterface);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |iid|[AliEngineInterfaceIdType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|功能接口类型。|
    |pInterface|void\*\*|设备管理或媒体引擎的二级指针。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   JoinChannel：加入频道。

    ```
    int JoinChannel(const AliEngineAuthInfo &authInfo,const char *userName);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|const [AliEngineAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|鉴权信息。|
    |userName|const char \*|用户的显示名称（不是用户ID）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   加入频道成功后，如果中途需要加入其他频道，必须先调用[LeaveChannel](#li_010)离开当前频道，如果加入频道失败，需要重试时，无需先调用[LeaveChannel](#li_010)。
    -   该接口是异步接口，是否成功加入频道，通过[OnJoinChannelResult](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)判断。
-   LeaveChannel：离开频道。

    ```
    int LeaveChannel();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   1.15及以上版本：销毁引擎只能通过[Destroy](#li_004)方法。
    -   1.15以下版本：离开频道时，AliEngine实例会被销毁，如需继续加入频道等操作，需要重新调用[Create](#li_003)初始化AliEngine实例。
    -   如果当前不在频道内，调用[LeaveChannel](#li_010)不会对实例产生任何影响，但会产生消息，通知频道内其他用户。
-   SwitchChannel：切换频道。

    ```
    int SwitchChannel(const AliEngineAuthInfo &authInfo);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|const [AliEngineAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|鉴权信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    -   返回AliEngineErrorInvaildState，请确认是否频道模式或角色不匹配，或当前未加入任何频道中。
    -   返回AliEngineErrorInvaildArgument，请确认鉴权信息是否合法，或是否加入相同频道。
    -   返回AliEngineErrorInner为SDK内部状态错误。
    **说明：**

    -   本方法只允许在直播模式AliEngineInteractiveLive下，观看角色AliEngineClientRoleLive使用。
    -   该接口是异步接口，调用此方法成功切换频道后，SDK会先触发离开原频道的[OnLeaveChannelResult](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调，再返回加入新频道的[OnJoinChannelResult](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调。
-   IsInCall：检查当前是否在频道中。

    ```
    bool IsInCall();
    ```

    返回说明

    true表示在频道中，false表示不在频道中。

-   SetChannelProfile：设置频道模式。

    ```
    int SetChannelProfile(const AliEngineChannelProfile channelProfile);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |channelProfile|[AliEngineChannelProfile](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|频道类型，默认为AliEngineCommunication。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口只可以在加入频道之前调用，会议中不可以重新设置，离开频道后可以重新设置。

-   CreateChannel：创建一个AliEngine子频道实例。

    ```
    AliEngine * CreateChannel(const char* extras);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |extras|const char\*|接收来自客户灰度下发的参数。|

    返回说明

    成功返回子频道实例，失败返回空指针。

-   DestroyChannel：销毁[CreateChannel](#li_014)创建的子频道。

    ```
    void DestroyChannel();
    ```

-   PublishLocalVideoStream：设置是否允许推视频流。

    ```
    int PublishLocalVideoStream(bool enabled);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否允许推视频流。取值：     -   true（默认值）：允许推视频流。
    -   false：不允许推视频流。 |

-   IsLocalVideoStreamPublished：查询当前是否允许推视频流。

    ```
    bool IsLocalVideoStreamPublished();
    ```

    返回说明

    true表示允许推相机流，false表示不允许推相机流。

-   IsScreenSharePublished：查询当前是否允许推屏幕流。

    ```
    bool IsScreenSharePublished();
    ```

    返回说明

    true表示允许推相机流，false表示不允许推相机流。

-   PublishLocalAudioStream：设置是否允许推音频流。

    ```
    int PublishLocalAudioStream(bool enabled);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否允许推音频流。取值：     -   true（默认值）：允许推音频流。
    -   false：不允许推音频流。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsLocalAudioStreamPublished：查询当前是否允许推音频流。

    ```
    bool IsLocalAudioStreamPublished();
    ```

    返回说明

    true表示允许推音频流，false表示不允许推音频流。

-   PublishLocalDualStream：设置是否允许推次要视频流。

    ```
    int PublishLocalDualStream(bool enabled);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否允许推次要视频流。取值：     -   true（默认值）：允许推次要视频流。
    -   false：不允许推次要视频流。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsDualStreamPublished：查询当前是否允许推次要视频流。

    ```
    bool IsDualStreamPublished();
    ```

    返回说明

    true表示允许推次要视频流，false表示不允许推次要视频流。

-   SetRemoteVideoStreamType：设置订阅的相机流格式。

    ```
    int SetRemoteVideoStreamType(const char* uid,AliEngineVideoStreamType streamType);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char\*|远端用户ID。|
    |streamType|[AliEngineVideoStreamType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|相机流格式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetRemoteDefaultVideoStreamType：设置默认订阅的相机流格式。

    ```
    int SetRemoteDefaultVideoStreamType(AliEngineVideoStreamType streamType);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamType|[AliEngineVideoStreamType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|相机流格式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetDefaultSubscribeAllRemoteAudioStreams：设置是否默认拉音频流。

    ```
    int SetDefaultSubscribeAllRemoteAudioStreams(bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SubscribeAllRemoteAudioStreams：停止或恢复拉所有远端音频流。

    ```
    int SubscribeAllRemoteAudioStreams(bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SubscribeRemoteAudioStream：停止或恢复特定远端用户的音频流拉取。

    ```
    int SubscribeRemoteAudioStream(const char* uid, bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char\*|远端用户ID。|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetDefaultSubscribeAllRemoteVideoStreams：设置是否默认拉视频流。

    ```
    int SetDefaultSubscribeAllRemoteVideoStreams(bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SubscribeAllRemoteVideoStreams：停止或恢复拉所有远端视频流。

    ```
    int SubscribeAllRemoteVideoStreams(bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SubscribeRemoteVideoStream：停止或恢复特定远端用户的视频流拉取。

    ```
    int SubscribeRemoteVideoStream(const char* uid, AliEngineVideoTrack track, bool sub);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char\*|远端用户ID。|
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|视频流类型。|
    |sub|bool|是否订阅。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetScreenShareEncoderConfiguration：设置屏幕共享编码属性。

    ```
    void SetScreenShareEncoderConfiguration(const AliEngineScreenShareEncoderConfiguration& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|const [AliEngineScreenShareEncoderConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕共享编码属性。|

-   SetLocalViewConfig：为本地预览设置渲染窗口以及绘制参数。

    ```
    int SetLocalViewConfig(AliEngineVideoCanvas renderConfig,AliEngineVideoTrack track);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderConfig|[AliEngineVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|视频流的类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   支持加入频道之前和之后切换窗口。如果canvas中的hWnd为NULL，则停止渲染。
    -   如果在播放过程中需要重新设置渲染方式，请保持canvas中其他成员变量不变，仅修改renderMode。
    -   canvas中渲染方式默认为AliEngineRenderModeAuto。
-   SetCameraCapturerConfiguration：设置摄像头采集偏好。

    ```
    int SetCameraCapturerConfiguration(const AliEngineCameraCapturerConfiguration& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|const [AliEngineCameraCapturerConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|采集偏好。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetDeviceOrientationMode：设置设备方向（适用于Android或iOS端）。

    ```
    int SetDeviceOrientationMode(AliEngineOrientationMode mode);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|[AliEngineOrientationMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|设备方向。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableLocalVideo：禁用或重新启用本地视频采集。

    ```
    int EnableLocalVideo(bool enabled);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enabled|bool|禁用或重新启用本地视频采集。取值：     -   true（默认值）：重新启用视频采集。
    -   false：停止视频采集。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   MuteLocalCamera：停止或恢复本地视频数据数据发送。

    ```
    int MuteLocalCamera(bool mute, AliEngineVideoTrack track);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|停止或恢复推视频流。取值：     -   true：停止推视频流。
    -   false（默认值）：恢复推视频流。 |
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|需要改变推流状态的视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口只是控制指定视频流上是否发送黑帧，采集和数据发送不会停止，如果需要关闭采集请使用[EnableLocalVideo](#li_035)接口，如果需要中止视频数据发送请使用[PublishLocalVideoStream](#li_016)接口。

-   MuteAllRemoteVideo：停止或恢复远端所有的视频渲染。

    ```
    int MuteLocalCamera(bool mute, AliEngineVideoTrack track);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|停止或恢复渲染。取值：     -   true：停止渲染，所有视频为黑帧。
    -   false（默认值）：恢复渲染。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetRemoteViewConfig：为远端的视频设置渲染窗口以及绘制参数。

    ```
    int SetRemoteViewConfig(AliEngineVideoCanvas renderConfig,const char *uid,AliEngineVideoTrack track);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderConfig|[AliEngineVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|渲染参数，包含渲染窗口以及渲染方式。|
    |uid|const char \*|用户ID。|
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|需要设置的视频流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdateViewConfig：更新渲染配置。

    ```
    int UpdateViewConfig(AliEngineVideoCanvas renderConfig);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderConfig|[AliEngineVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|窗口以及渲染方式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsCameraOn：检查摄像头是否打开。

    ```
    bool IsCameraOn();
    ```

    返回说明

    true表示摄像头已打开，false表示摄像头未打开。

-   StopRecord：停止录制。

    ```
    bool StopRecord();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   StartRecord：开始录制（非布局录制）。

    ```
    bool StartRecord(AliEngineRecordType recordType, AliEngineRecordFormat recordFormat, const char * filePath, AliEngineRecordAudioConfig& audioConfig, AliEngineRecordVideoConfig& videoConfig, bool isFragment);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |recordType|[AliEngineRecordType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制类型。|
    |recordFormat|[AliEngineRecordFormat](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|录制格式。|
    |filePath|const char \*|文件路径。|
    |audioConfig|[AliEngineRecordAudioConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|录制音频设置。|
    |videoConfig|[AliEngineRecordVideoConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|录制视频设置。|
    |isFragment|bool|是否支持mp4内部分段，只在录制mp4时有效。|

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   StartRecord：开始录制（窗口布局录制）。

    ```
    int StartRecord(const char* filePath, const AliEngineRecordVideoLayout& layout);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |filePath|const char \*|文件路径。|
    |layout|const [AliEngineRecordVideoLayout](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|视频窗口布局设置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdateRecordLayout：更新录制内容信息。

    ```
    bool UpdateRecordLayout(AliEngineRecordVideoLayout& layout);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |layout|[AliEngineRecordVideoLayout](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|录制视频内容及布局。|

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   AddRecordTemplate：添加录制模板。

    ```
    int AddRecordTemplate(const AliEngineRecordTemplate& rTemplate);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |rTemplate|const [AliEngineRecordTemplate](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|录制模板。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PauseRecord：暂停录制。

    ```
    bool PauseRecord();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   ResumeRecord：重新开始录制。

    ```
    bool ResumeRecord();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   SetBeautyEffect：设置是否启用基础美颜。

    ```
    int SetBeautyEffect(bool enable, const AliEngineBeautyConfig &config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否启用基础美颜。取值：     -   true：开启。
    -   false（默认值）：关闭。 |
    |config|const [AliEngineBeautyConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|基础美颜参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 该接口目前只支持美白和磨皮。

-   SetVideoEncoderConfiguration：设置视频编码属性。

    ```
    void SetVideoEncoderConfiguration(const AliEngineVideoEncoderConfiguration& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|const [AliEngineVideoEncoderConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|预定义的编码属性。|

-   AddVideoWatermark：添加水印。

    ```
    int AddVideoWatermark(AliEngineVideoTrack track, const char* image_url, const AliEngineWaterMarkConfig &options);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|数据流类型。|
    |image\_url|const char\*|水印图片路径。|
    |options|const [AliEngineWaterMarkConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|水印配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   ClearVideoWatermark：清理对应数据流水印信息。

    ```
    int ClearVideoWatermark(AliEngineVideoTrack track);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |track|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|数据流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SnapshotVideo：截图。

    ```
    int SnapshotVideo(const String& userId, const AliEngineVideoTrack &trackType);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|const String &|用户ID。|
    |trackType|const [AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 截图结果通过[OnSnapshotComplete](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调返回。

-   SwitchCamera：切换前后摄像头（适用于Android或iOS端）。

    ```
    int SwitchCamera();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetCurrentCameraDirection：获取当前摄像头方向（适用于Android或iOS端）。

    ```
    AliEngineCameraDirection GetCurrentCameraDirection();
    ```

    返回说明

    返回camera方向枚举值。

-   SetCameraZoom：设置摄像头缩放比例（适用于Android或iOS端）。

    ```
    int SetCameraZoom(float zoom);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |zoom|float|zoom的级别。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetCameraFlash：设置摄像头闪光灯是否打开（适用于Android或iOS端）。

    ```
    int SetCameraFlash(bool flash);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |flash|bool|是否允许闪光灯。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsCameraFocusPointSupported：摄像头是否支持手动聚焦（适用于Android或iOS端）。

    ```
    bool IsCameraFocusPointSupported();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   IsCameraExposurePointSupported：摄像头是否支持设置曝光区域（适用于Android或iOS端）。

    ```
    bool IsCameraExposurePointSupported();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   SetCameraFocusPoint：设置摄像头手动聚焦（适用于Android或iOS端）。

    ```
    int SetCameraFocusPoint(float pointX, float pointY);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |pointX|float|聚焦点x坐标。|
    |pointY|float|聚焦点y坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetCameraExposurePoint：设置摄像头曝光点（适用于Android或iOS端）。

    ```
    int SetCameraExposurePoint(float pointX, float pointY);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |pointX|float|聚焦点x坐标。|
    |pointY|float|聚焦点y坐标。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsCameraAutoFocusFaceModeSupported：摄像头是否支持人脸聚焦（适用于Android或iOS端）。

    ```
    bool IsCameraAutoFocusFaceModeSupported();
    ```

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   SetCameraAutoFocusFaceModeEnabled：设置摄像头人脸对焦（适用于Android或iOS端）。

    ```
    bool SetCameraAutoFocusFaceModeEnabled(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否开启摄像头人脸对焦。取值：     -   true：开启。
    -   false：关闭。 |

    返回说明

    true表示方法调用成功，false表示方法调用失败。

-   StartScreenShareByDesktopId：根据桌面ID进行屏幕分享。

    ```
    int StartScreenShareByDesktopId(unsigned int desktopId, const AliEngineScreenShareConfig& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |desktopId|unsigned int|桌面ID（可通过[GetScreenShareSourceInfo](#li_070)接口获取）。|
    |config|const [AliEngineScreenShareConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕分享配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 配置指定区域分享时，分享区域最小分辨率为16 x 16，设置区域小于最小分辨率时重置为最小分辨率；设置分享区域超过实际桌面分辨率时，将分享整个桌面。

-   StartScreenShareByScreenRegion：根据屏幕区域进行屏幕分享。

    ```
    int StartScreenShareByScreenRegion(const AliEngineScreenShareRegion& screenRegion, const AliEngineScreenShareConfig& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |screenRegion|const [AliEngineScreenShareRegion](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|指定要共享的屏幕相对于虚拟屏幕的位置。|
    |config|const [AliEngineScreenShareConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕分享配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：**

    -   本方法仅适用于桌面共享，设置窗口共享请使用StartScreenShareByWindowId接口。
    -   配置指定区域分享时，分享区域最小分辨率为16 x 16，设置区域小于最小分辨率时重置为最小分辨率；设置分享区域超过实际桌面分辨率时，将分享整个桌面。
    -   关于虚拟屏幕坐标，请参见[The Virtual Screen](https://docs.microsoft.com/en-us/windows/win32/gdi/the-virtual-screen)。
-   StartScreenShareByWindowId：根据窗口ID进行屏幕分享。

    ```
    int StartScreenShareByWindowId(unsigned int windowId, const AliEngineScreenShareConfig& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |windowId|unsigned int|窗口ID（可通过GetScreenShareSourceInfo接口获取）|
    |config|const [AliEngineScreenShareConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕分享配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartScreenShare：开始屏幕分享（适用于Android或iOS端）。

    ```
    int StartScreenShare();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopScreenShare：停止屏幕分享。

    ```
    int StopScreenShare();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdateScreenShareConfig：更新屏幕分享配置。

    ```
    int UpdateScreenShareConfig(const AliEngineScreenShareConfig& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|const [AliEngineScreenShareConfig](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕分享配置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetScreenShareConfig：获取屏幕共享配置。

    ```
    AliEngineScreenShareConfig GetScreenShareConfig();
    ```

    返回说明

    返回屏幕共享配置信息。

-   GetScreenShareSourceInfo：获取屏幕分享源信息。

    ```
    AliEngineScreenSourceList* GetScreenShareSourceInfo(AliEngineScreenShareType sourceType);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sourceType|[AliEngineScreenShareType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|屏幕分享类型。|

    返回说明

    返回屏幕共享源列表。

    **说明：** 请在遍历完屏幕共享源列表后调用其release成员方法，由SDK内部释放相关资源。

-   GetCurrentScreenShareSourceId：获取当前屏幕共享源ID。

    ```
    unsigned int GetCurrentScreenShareSourceId();
    ```

    返回说明

    返回当前屏幕共享源ID。

-   GetCurrentScreenShareSourceType：获取当前屏幕共享源类型。

    ```
    AliEngineScreenShareType GetCurrentScreenShareSourceType();
    ```

    返回说明

    返回当前屏幕共享源类型。

-   GetDesktopRegion：获取屏幕分享桌面区域。

    ```
    int GetDesktopRegion(const String& sourceId, const String& sourceTitle, AliEngineScreenShareRegion& region);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |sourceId|const String&|屏幕分享数据源ID。|
    |sourceTitle|const String&|屏幕分享数据源名称。|
    |region|[AliEngineScreenShareRegion](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|屏幕区域信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioOnlyMode：设置音频模式或音视频模式。

    ```
    int SetAudioOnlyMode(bool audioOnly);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioOnly|bool|音频模式或音视频模式。取值：     -   true：只有音频推流和拉流。
    -   false：音视频推流和拉流。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsAudioOnlyMode：检查当前是否纯音频模式。

    ```
    bool IsAudioOnlyMode();
    ```

    返回说明

    true表示纯音频模式，false表示音视频模式。

-   MuteLocalMic：停止或恢复本地音频数据发送。

    ```
    int MuteLocalMic(bool mute, AliEngineMuteLocalAudioMode mode = AliEngineMuteLocalAudioModeDefault);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|停止或恢复本地音频数据发送。取值：     -   true：本地音频发送静音帧。
    -   false：恢复正常。 |
    |mode|[AliEngineMuteLocalAudioMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|静音模式，默认麦克风静音模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** mute只是发送音频数据为静音帧，采集和编码模块仍然在工作。

-   MuteRemoteAudio：停止或恢复远端的音频播放。

    ```
    int MuteRemoteAudio(const char *uid,bool mute);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char \*|用户ID。|
    |bool|mute|停止或恢复远端的音频播放。取值：     -   true：停止播放。
    -   false：恢复播放。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   MuteAllRemoteAudio：停止或恢复远端所有的音频播放。

    ```
    int MuteAllRemoteAudio(bool mute);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|bool|停止或恢复远端所有的音频播放。取值：     -   true：停止播放。
    -   false：恢复播放。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartAudioCapture：开启音频采集。

    ```
    int StartAudioCapture();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopAudioCapture：关闭音频采集。

    ```
    int StopAudioCapture();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartAudioPlayer：开启音频播放设备。

    ```
    int StartAudioPlayer();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopAudioPlayer：关闭音频播放。

    ```
    int StopAudioPlayer();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetRemoteAudioVolume：设置本地播放的指定远端用户音量。

    ```
    int SetRemoteAudioVolume(const char *uid,int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char \*|用户ID。|
    |int|volume|播放音量，取值范围：\[0,100\]。其中，0表示静音，100表示原始音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetDefaultAudioRouteToSpeakerphone：设置默认音频输出为听筒或扬声器（适用于Android或iOS端）。

    ```
    int SetDefaultAudioRouteToSpeakerphone(bool defaultToSpeakerphone);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |defaultToSpeakerphone|bool|默认音频输出为听筒或扬声器。取值：     -   true（默认值）：扬声器模式。
    -   false：听筒模式。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableSpeakerphone：设置音频输出为听筒或扬声器（适用于Android或iOS端）。

    ```
    int EnableSpeakerphone(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|音频输出为听筒或扬声器。取值：     -   true：扬声器模式。
    -   false（默认值）：听筒模式。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsEnableSpeakerphone：获取当前音频输出为听筒还是扬声器（适用于Android或iOS端）。

    ```
    bool IsEnableSpeakerphone();
    ```

    返回说明

    true表示听筒，false表示扬声器。

-   SetRecordingVolume：设置录音音量。

    ```
    int SetRecordingVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|取值范围：\[0,400\]。其中0表示静音；大于100表示放大音量；小于100表示减小音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetPlayoutVolume：设置播放音量。

    ```
    int SetPlayoutVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|取值范围：\[0,400\]。其中0表示静音；大于100表示放大音量；小于100表示减小音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableAudioVolumeIndication：设置音量回调频率和平滑系数。

    ```
    int EnableAudioVolumeIndication(int interval, int smooth, int reportVad);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |interval|int|时间间隔，单位为毫秒，最小值不得小于10ms，建议设置300~500ms；小于等于0表示不启用音量提示和说话人提示功能。|
    |smooth|int|平滑系数，数值越大平滑程度越高，反之越低，实时性越好，取值范围：\[0,9\]，建议设置3。|
    |reportVad|int|说话人检测开关。取值：     -   0：关闭。
    -   1：开启，通过onAudioVolumeCallback接口回调每一个说话人的状态。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioProfile：设置音频Profile。

    ```
    int SetAudioProfile(int audio_profile, int audio_scene);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audio\_profile|int|音频采集或编码模式参数，详情请参见[AliEngineAudioProfile](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)。|
    |audio\_scene|int|音频场景模式参数，详情请参见[AliEngineAudioScenario](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetDeviceVolumeType：设置音量类型。

    ```
    int SetDeviceVolumeType(int type);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |type|int|音量类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableAudioDTX：开启本地音频流量控制（检测语音）。

    ```
    int EnableAudioDTX(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否开启本地音频流量控制。取值：     -   true：开启。
    -   false：关闭。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 推流之前调用有效。开启语音活动检测可以在检测到没有语音的情况下，发送字节数减少，节省用户流量。

-   EnableAudioAMD：开启本地音频流量控制（检测麦克风）。

    ```
    int EnableAudioAMD(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否开启本地音频流量控制。取值：     -   true：开启。
    -   false：关闭。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 推流之前调用有效。开启语音活动检测可以在检测到麦克风静音或者关闭麦克风时停止发送音频包。

-   SetAudioEffectVoiceChangerMode：设置变声音效模式。

    ```
    int SetAudioEffectVoiceChangerMode(const AliEngineAudioEffectVoiceChangerMode &mode);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|const [AliEngineAudioEffectVoiceChangerMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|变声音效模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioEffectPitchValue：设置变调参数。

    ```
    int SetAudioEffectPitchValue(double value);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |value|double|取值范围：\[0.5,2.0\]，默认1.0，表示音调不变。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioEffectReverbMode：设置混响音效模式。

    ```
    int SetAudioEffectReverbMode(const AliEngineAudioEffectReverbMode& mode);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mode|const [AliEngineAudioEffectReverbMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|音效模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioEffectReverbParamType：设置混响音效类型和具体参数。

    ```
    int SetAudioEffectReverbParamType(const AliEngineAudioEffectReverbParamType& type, float value);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |type|const [AliEngineAudioEffectReverbParamType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|音效混响模式。|
    |value|float|具体参数值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartAudioAccompany：开始混音（适用于Android或iOS端）。

    ```
    int StartAudioAccompany(const char *filePath, bool onlyLocalPlay, bool replaceMic, int loopCycles);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |filePath|const char \*|混音文件路径。|
    |onlyLocalPlay|bool|是否只本地播放。|
    |replaceMic|bool|是否替换掉MIC。|
    |loopCycles|int|循环次数（可以设置-1或者正整数）。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopAudioAccompany：停止混音（适用于Android或iOS端）。

    ```
    int StopAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioAccompanyVolume：设置混音音量（适用于Android或iOS端）。

    ```
    int SetAudioAccompanyVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 设置音量需要在startAudioAccompany后才能生效。

-   SetAudioAccompanyPublishVolume：设置混音之后推流出去的音量（适用于Android或iOS端）。

    ```
    int SetAudioAccompanyPublishVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 设置音量需要在startAudioAccompany后才能生效。

-   GetAudioAccompanyPublishVolume：获取推流出去的混音音量（适用于Android或iOS端）。

    ```
    int GetAudioAccompanyPublishVolume();
    ```

    返回说明

    返回推流出去的混音音量。

-   SetAudioAccompanyPlayoutVolume：设置混音之后本地播放的音量（适用于Android或iOS端）。

    ```
    int SetAudioAccompanyPlayoutVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 设置音量需要在[StartAudioAccompany](#li_100)后才能生效。

-   GetAudioAccompanyPlayoutVolume：获取混音本地播放的音量（适用于Android或iOS端）。

    ```
    int GetAudioAccompanyPlayoutVolume();
    ```

    返回说明

    当前混音本地播放的音量大小。

-   PauseAudioAccompany：暂停混音（适用于Android或iOS端）。

    ```
    int PauseAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   ResumeAudioAccompany：重新开始混音（适用于Android或iOS端）。

    ```
    int ResumeAudioAccompany();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetAudioAccompanyDuration：获取伴奏文件时长（适用于Android或iOS端）。

    ```
    int GetAudioAccompanyDuration();
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|const [AliEngineCameraCapturerConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)&|采集偏好。|

    返回说明

    返回当前伴奏文件时长，单位为毫秒。

-   GetAudioAccompanyCurrentPosition：获取音乐文件播放进度（适用于Android或iOS端）。

    ```
    int GetAudioAccompanyCurrentPosition();
    ```

    返回说明

    当前音乐文件播放进度，单位为毫秒。

-   SetAudioAccompanyPosition：设置音频文件的播放位置（适用于Android或iOS端）。

    ```
    int SetAudioAccompanyPosition(int pos_ms);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |pos\_ms|int|进度条位置，单位为毫秒。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PreloadAudioEffect：预加载音效文件（适用于Android或iOS端）。

    ```
    int PreloadAudioEffect(unsigned int soundId, const char *filePath);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|
    |filePath|const char \*|音效文件路径。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UnloadAudioEffect：删除预加载的音效文件（适用于Android或iOS端）。

    ```
    int UnloadAudioEffect(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PlayAudioEffect：开始播放音效（适用于Android或iOS端）。

    ```
    int PlayAudioEffect(unsigned int soundId, const char *filePath, int cycles, bool publish);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|
    |filePath|const char \*|音效文件路径。|
    |cycles|int|循环次数（可以设置-1或者正整数）。|
    |publish|bool|是否推流。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopAudioEffect：停止播放音效（适用于Android或iOS端）。

    ```
    int StopAudioEffect(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopAllAudioEffects：停止播放所有音效（适用于Android或iOS端）。

    ```
    int StopAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioEffectPublishVolume：设置音效推流音量（适用于Android或iOS端）。

    ```
    int SetAudioEffectPublishVolume(unsigned int soundId, int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetAudioEffectPublishVolume：获取推流音效音量（适用于Android或iOS端）。

    ```
    int GetAudioEffectPublishVolume(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioEffectPlayoutVolume：设置音效本地播放音量（适用于Android或iOS端）。

    ```
    int SetAudioEffectPlayoutVolume(unsigned int soundId, int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetAudioEffectPlayoutVolume：获取音效本地播放音量（适用于Android或iOS端）。

    ```
    int GetAudioEffectPlayoutVolume(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAllAudioEffectsPublishVolume：设置所有音效本地播放音量（适用于Android或iOS端）。

    ```
    int SetAllAudioEffectsPublishVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAllAudioEffectsPlayoutVolume：设置所有音效推流音量（适用于Android或iOS端）。

    ```
    int SetAllAudioEffectsPlayoutVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|混音音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PauseAudioEffect：暂停音效（适用于Android或iOS端）。

    ```
    int PauseAudioEffect(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PauseAllAudioEffects：暂停所有音效（适用于Android或iOS端）。

    ```
    int PauseAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   ResumeAudioEffect：重新开始播放音效（适用于Android或iOS端）。

    ```
    int ResumeAudioEffect(unsigned int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|unsigned int|用户给该音效文件分配的ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   ResumeAllAudioEffects：重新开始播放所有音效（适用于Android或iOS端）。

    ```
    int ResumeAllAudioEffects();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableEarBack：启用耳返（适用于Android或iOS端）。

    ```
    int EnableEarBack(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否启用耳返。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetEarBackVolume：设置耳返音量（适用于Android或iOS端）。

    ```
    int SetEarBackVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量，取值范围：\[0,100\]，默认值100。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   EnableSystemAudioRecording：设置是否开启系统声音采集推送。

    ```
    int EnableSystemAudioRecording(bool enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否开启系统声音采集推送。取值：     -   true：开启。
    -   false：关闭。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsSystemAudioRecording：当前是否开启系统声音采集推送。

    ```
    bool IsSystemAudioRecording();
    ```

    返回说明

    true表示开启状态， false表示关闭状态。

-   SetSystemAudioRecordingVolume：设置系统声音采集推送音量。

    ```
    int SetSystemAudioRecordingVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|设置音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetSystemAudioRecordingVolume：获取当前设置系统声音采集推送音量。

    ```
    int GetSystemAudioRecordingVolume();
    ```

    返回说明

    返回系统音量。

    **说明：** 需要开启系统声音采集推送后才能设置，否则设置失败。

-   GetAudioCaptureList：获取系统中的录音设备列表。

    ```
    AliEngineDeviceInfoList* GetAudioCaptureList();
    ```

    返回说明

    返回系统中的录音设备列表。

-   GetCurrentAudioCaptureName：获取使用的录音设备名称。

    ```
    String GetCurrentAudioCaptureName();
    ```

    返回说明

    返回当前音频采集设备名。

-   GetCurrentAudioCaptureID：获取使用的录音设备ID。

    ```
    String GetCurrentAudioCaptureID();
    ```

    返回说明

    返回当前音频采集设备ID。

-   SetCurrentAudioCaptureName：选择录音设备名称。

    ```
    int SetCurrentAudioCaptureName(const char* captureName);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |captureName|const char\*|音频采集设备名称。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetCurrentAudioCaptureID：选择录音设备ID。

    ```
    int SetCurrentAudioCaptureID(const char* captureID);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |captureID|const char\*|音频采集设备名称。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetAudioPlayerList：获取系统中的扬声器列表。

    ```
    AliEngineDeviceInfoList* GetAudioPlayerList();
    ```

    返回说明

    返回音频播放设备列表。

-   GetCurrentAudioPlayerName：获取当前使用的扬声器名称。

    ```
    String GetCurrentAudioPlayerName();
    ```

    返回说明

    返回当前音频播放设备名。

-   GetCurrentAudioPlayerID：获取当前使用的扬声器ID。

    ```
    String GetCurrentAudioPlayerID();
    ```

    返回说明

    返回当前音频播放设备ID。

-   SetCurrentAudioPlayerName：选择扬声器名称。

    ```
    int SetCurrentAudioPlayerName(const char* playerName);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |playerName|const char\*|音频播放设备名称。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetCurrentAudioPlayerID：选择扬声器ID。

    ```
    int SetCurrentAudioPlayerID(const char* playerID);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |playerID|const char\*|音频播放设备ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetRecordingDeviceVolume：设置音频采集设备音量。

    ```
    int SetRecordingDeviceVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetRecordingDeviceVolume：获取音频采集设备音量。

    ```
    int GetRecordingDeviceVolume();
    ```

    返回说明

    返回音频采集设备音量。

-   SetPlaybackDeviceVolume：设置音频播放设备音量。

    ```
    int SetPlaybackDeviceVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|音量值。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetPlaybackDeviceVolume：获取音频播放设备音量。

    ```
    int GetPlaybackDeviceVolume();
    ```

    返回说明

    返回设备音量。

-   StartTestAudioRecordByName：开始测试音频采集设备。

    ```
    int StartTestAudioRecordByName(const char *deviceName, int callbackInterval = 0);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceName|const char \*|音频采集设备名称。|
    |callbackInterval|int|音量回调频率，单位：毫秒，默认值200毫秒。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 开始测试后音量信息通过onAudioDeviceRecordLevel回调返回。

-   StartTestAudioRecordById：开启麦克风设备测试（按设备ID）。

    ```
    int StartTestAudioRecordById(const char * deviceId, int callbackInterval = 0);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceId|const char \*|设备ID。|
    |callbackInterval|int|音量回调频率，单位：毫秒，默认值200毫秒。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 开始测试后音量信息通过onAudioDeviceRecordLevel回调返回。

-   StopTestAudioRecord：停止测试音频采集设备。

    ```
    int StopTestAudioRecord();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartTestAudioPlayoutByName：开始测试音频播放设备。

    ```
    int StartTestAudioPlayoutByName(const char* deviceName, const char* filePath, int callbackInterval = 0, int loopCycles = 0);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceName|const char\*|音频播放设备名称。|
    |filePath|const char\*|音频文件路径。|
    |callbackInterval|int|音量回调频率，单位：毫秒，默认值200毫秒。|
    |loopCycles|int|重复播放次数，-1表示循环播放。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartTestAudioPlayoutById：开启扬声器设备测试（按设备ID）。

    ```
    int StartTestAudioPlayoutById(const char* deviceId, const char* filePath, int callbackInterval = 0, int loopCycles = 0);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceId|const char\*|设备ID。|
    |filePath|const char\*|音频文件路径。|
    |callbackInterval|int|音量回调频率，单位：毫秒，默认值200毫秒。|
    |loopCycles|int|重复播放次数，-1表示循环播放。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 开始测试后音量信息通过onAudioDevicePlayoutLevel回调返回。

-   StopTestAudioPlayout：停止测试音频播放设备。

    ```
    int StopTestAudioPlayout();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetCameraList：获取摄像头列表。

    ```
    AliEngineDeviceInfoList* GetCameraList();
    ```

    返回说明

    返回摄像头列表。

-   GetCurrentCameraName：获取当前使用的摄像头名称。

    ```
    String GetCurrentCameraName();
    ```

    返回说明

    返回当前使用的摄像头名称。

-   GetCurrentCameraID：获取当前使用的摄像头ID。

    ```
    String GetCurrentCameraID();
    ```

    返回说明

    返回当前使用的摄像头ID。

-   SetCurrentCameraName：选择摄像头名称。

    ```
    int SetCurrentCameraName(const char* cameraName);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |cameraName|const char\*|摄像头名称。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetCurrentCameraID：选择摄像头ID。

    ```
    int SetCurrentCameraID(const char* cameraID);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |cameraID|const char\*|摄像头ID。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   RegisterVideoSampleObserver：订阅视频数据输出。

    ```
    void RegisterVideoSampleObserver(IVideoFrameObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IVideoFrameObserver\*|视频数据接收对象。|

    **说明：** 输出数据将通过IVideoFrameObserver回调返回。

-   UnRegisterVideoSampleObserver：取消订阅视频数据输出。

    ```
    void UnRegisterVideoSampleObserver(IVideoFrameObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IVideoFrameObserver\*|视频数据接收对象。|

-   RegisterLocalVideoTextureObserver：订阅本地视频纹理数据。

    ```
    void RegisterLocalVideoTextureObserver(IVideoTextureObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IVideoTextureObserver\*|视频数据接收对象。|

    **说明：** 输出数据将通过IVideoTextureObserver回调返回。

-   UnRegisterLocalVideoTextureObserver：取消本地视频纹理数据输出。

    ```
    void UnRegisterLocalVideoTextureObserver(IVideoTextureObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IVideoTextureObserver\*|视频数据接收对象。|

-   RegisterAudioFrameObserver：订阅音频数据输出。

    ```
    int RegisterAudioFrameObserver(IAudioFrameObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IAudioFrameObserver\*|音频数据接收对象。|

-   UnRegisterAudioFrameObserver：取消音频数据输出。

    ```
    void UnRegisterAudioFrameObserver(IAudioFrameObserver* observer);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |observer|IAudioFrameObserver\*|音频数据接收对象。|

-   RegisterAudioEventObserver：订阅音频事件（默认订阅）, 如音频啸叫。

    ```
    int RegisterAudioEventObserver();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UnRegisterAudioEventObserver：取消订阅音频事件。

    ```
    void UnRegisterAudioEventObserver();
    ```

-   SetSubscribeAudioNumChannel：设置输出音频声道数（混音前数据不支持该参数设置）。

    ```
    void SetSubscribeAudioNumChannel(AliEngineAudioNumChannelType audioNumChannel);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioNumChannel|[AliEngineAudioNumChannelType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|声道数，默认单声道。|

-   SetSubscribeAudioSampleRate：设置输出音频采样率（混音前数据不支持该参数设置）。

    ```
    void SetSubscribeAudioSampleRate(AliEngineAudioSampleRate audioSampleRate);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSampleRate|[AliEngineAudioSampleRate](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|采样率，默认44.1kHz。|

-   SubscribeAudioData：订阅音频数据。

    ```
    void SubscribeAudioData(AliEngineAudioSource audioSource);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliEngineAudioSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频数据源。|

    **说明：** 订阅音频数据输出前，需先通过[SetSubscribeAudioNumChannel](#li_166)与[SetSubscribeAudioSampleRate](#li_167)设置输出音频数据参数。

-   UnsubscribeAudioData：取消订阅音频数据。

    ```
    void UnsubscribeAudioData(AliEngineAudioSource audioSource);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSource|[AliEngineAudioSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频数据源。|

-   SetExternalVideoSource：启用外部视频输入源。

    ```
    int SetExternalVideoSource(bool enable, bool useTexture, AliEngineVideoTrack type, AliEngineRenderMode renderMode);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否启用外部视频输入源。取值：     -   true：开启。
    -   false：关闭。 |
    |useTexture|bool|是否使用texture模式。|
    |type|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|流类型。|
    |renderMode|[AliEngineRenderMode](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|渲染模式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PushExternalVideoFrame：输入视频数据。

    ```
    int PushExternalVideoFrame(const AliEngineVideoRawData &frame, AliEngineVideoTrack type);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |frame|const [AliEngineVideoRawData](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|帧数据。|
    |type|[AliEngineVideoTrack](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|流类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetExternalAudioSource：设置是否启用外部音频输入源。

    ```
    int SetExternalAudioSource(bool enable, unsigned int sampleRate, unsigned int channelsPerFrame);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否启用外部音频输入源。取值：     -   true：开启。
    -   false：关闭。 |
    |sampleRate|unsigned int|采样率，例如16000Hz、48000Hz等。|
    |channelsPerFrame|unsigned int|声道数，例如1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PushExternalAudioFrameRawData：输入音频数据。

    ```
    int PushExternalAudioFrameRawData(const void * data, unsigned int sampleLen, double timestamp);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |data|const void \*|音频数据，不建议超过40ms数据。|
    |sampleLen|unsigned int|采样。|
    |timestamp|double|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetExternalAudioPublishVolume：设置混音音量。

    ```
    int SetExternalAudioPublishVolume(int vol);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |vol|int|音量，取值范围：\[0,100\]。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetExternalAudioPublishVolume：获取混音音量。

    ```
    int GetExternalAudioPublishVolume();
    ```

    返回说明

    返回当前混音音量。

-   SetMixedWithMic：设置是否与麦克风采集音频混合。

    ```
    int SetMixedWithMic(bool mixed);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mixed|bool|是否与麦克风采集音频混合。取值：     -   true：混音。
    -   false：完全替换麦克风采集数据。 |

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetExteranlAudioRender：设置是否启用外部输入音频播放。

    ```
    int SetExteranlAudioRender(bool enable, unsigned int sampleRate, unsigned int channelsPerFrame);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|bool|是否启用外部输入音频播放。取值：     -   true：开启。
    -   false：关闭。 |
    |sampleRate|unsigned int|采样率，例如16kHz、48kHz等。|
    |channelsPerFrame|unsigned int|声道数，例如1或2。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PushExternalAudioRenderRawData：输入外部音频播放数据。

    ```
    int PushExternalAudioRenderRawData(const void* audioSamples, unsigned int sampleLength, unsigned int sampleRate, unsigned int channelsPerFrame, long long timestamp);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioSamples|const void\*|音频数据。|
    |sampleLength|unsigned int|音频数据长度。|
    |sampleRate|unsigned int|音频采样率。|
    |channelsPerFrame|unsigned int|音频声道数。|
    |timestamp|long long|时间戳。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetExternalAudioRenderVolume：设置音频外部播放源音量。

    ```
    int SetExternalAudioRenderVolume(int volScal);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volScal|int|音量。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetExternalAudioRenderVolume：获取音频外部播放源音量。

    ```
    int GetExternalAudioRenderVolume();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartLiveStreaming：开始直播拉流。

    ```
    void StartLiveStreaming(const AliEngineAuthInfo &authInfo);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|const [AliEngineAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|鉴权信息。|

    **说明：** [OnStartLiveStreamingResult](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调反馈直播拉流是否成功。

-   StopLiveStreaming：停止直播拉流。

    ```
    int StopLiveStreaming();
    ```

-   StartPublishLiveStream：开启旁路直播。

    ```
    int StartPublishLiveStream(const String& streamURL, const AliEngineLiveTranscoding &transcoding);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamURL|const String&|推流地址。|
    |transcoding|const [AliEngineLiveTranscoding](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdatePublishLiveStream：更新旁路直播相关参数。

    ```
    int UpdatePublishLiveStream(const String& streamURL, const AliEngineLiveTranscoding &transcoding);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamURL|const String&|推流地址。|
    |transcoding|const [AliEngineLiveTranscoding](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|推流所需参数。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopPublishLiveStream：停止旁路直播。

    ```
    int StopPublishLiveStream(const String& streamURL);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |streamURL|const String&|推流地址。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetLiveStreamingViewConfig：设置直播拉流窗口及渲染参数。

    ```
    int SetLiveStreamingViewConfig(AliEngineVideoCanvas& config);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|[AliEngineVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|包含了窗口以及渲染方式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdateLiveStreamingViewConfig：更新直播拉流窗口及渲染参数。

    ```
    int UpdateLiveStreamingViewConfig(AliEngineVideoCanvas& renderConfig);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |renderConfig|[AliEngineVideoCanvas](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|包含了窗口以及渲染方式。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartChannelRelay：开启跨频道连麦。

    ```
    int StartChannelRelay(const AliEngineChannelRelayConfiguration &configuration);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |configuration|const [AliEngineChannelRelayConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   UpdateChannelRelay：更新跨频道连麦。

    ```
    int UpdateChannelRelay(const AliEngineChannelRelayConfiguration &configuration);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |configuration|const [AliEngineChannelRelayConfiguration](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|配置信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopChannelRelay：停止跨频道连麦。

    ```
    int StopChannelRelay();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StartPreview：开始本地预览。

    ```
    int StartPreview();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   StopPreview：停止本地预览。

    ```
    int StopPreview();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetOnlineRemoteUsers：获取远端在线用户列表。

    ```
    void GetOnlineRemoteUsers(StringArray &userList);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userList|StringArray &|用户列表（保存的是用户ID）。|

-   GetUserInfo：查询远端用户的各种状态。

    ```
    int GetUserInfo(const char *uid,Dictionary &dict);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char \*|用户ID。从App server分配的唯一标示符。|
    |dict|Dictionary &|App提供的容器，用于存放用户数据。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   IsUserOnline：判断用户是否在线。

    ```
    bool IsUserOnline(const char *uid);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char \*|用户ID。从App server分配的唯一标示符。|

    返回说明

    true表示在线， false表示离线。

-   SetLogLevel：设置日志等级。

    ```
    static void SetLogLevel(AliEngineLogLevel logLevel);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |logLevel|[AliEngineLogLevel](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|Log级别，详情请参见AliEngineLogLevel。|

-   GetSDKVersion：获取SDK版本号。

    ```
    static const char *GetSDKVersion();
    ```

    返回说明

    返回SDK版本号。

-   GetErrorDescription：获取错误码描述。

    ```
    static const char* GetErrorDescription(int errorCode);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |errorCode|int|获取错误码描述。|

    返回说明

    返回错误码描述字符串。

-   GetEncodeParam：获取编码分辨率。

    ```
    static void GetEncodeParam(int *width, int *height);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |width|int \*|宽度。|
    |height|int \*|高度。|

-   SetClientRole：设置用户角色。

    ```
    int SetClientRole(const AliEngineClientRole clientRole);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |clientRole|const [AliEngineClientRole](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|用户角色类型。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetClientRole：获取用户角色。

    ```
    AliEngineClientRole GetClientRole();
    ```

    返回说明

    返回当前用户角色。

-   StartLastmileDetect：开始网络质量探测。

    ```
    int StartLastmileDetect();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口需在[JoinChannel](#li_009)之前调用，探测结果在[OnLastmileDetectResultWithQuality](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调。

-   StopLastmileDetect：停止网络质量探测。

    ```
    int StopLastmileDetect();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   PostFeedback：SDK问题反馈。

    ```
    void PostFeedback(const char *uid, const char *channelId, const char *description, const AliEngineFeedbackType type, long long timeStamp);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const char \*|当前uid（允许为空）。|
    |channelId|const char \*|当前频道ID（允许为空）。|
    |description|const char \*|问题描述（支持中英文，不允许为空）。|
    |type|const [AliEngineFeedbackType](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|问题类型。|
    |timeStamp|long long|问题发生的时间戳（Unix时间戳，可以为大致时间，无需特别精确，也可以为0）。|

-   SendMediaExtensionMsg：发送媒体扩展信息。

    ```
    int SendMediaExtensionMsg(unsigned char *message, unsigned int length, int repeatCount);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |message|unsigned char \*|扩展信息。|
    |length|unsigned int|扩展信息长度。|
    |repeatCount|int|重复次数。|

    返回说明

    -   0：成功。
    -   -1：未推流。
    -   -2：参数错误。
    -   -3：发送过于频繁，建议稍后再发送。
-   StartIntelligentDenoise：开启智能降噪。

    ```
    int StartIntelligentDenoise();
    ```

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

    **说明：** 此接口可以通话过程中控制打开智能降噪功能 。

-   StopIntelligentDenoise：关闭智能降噪。

    ```
    void StopIntelligentDenoise();
    ```

-   RefreshAuthInfo：刷新鉴权信息。

    ```
    int RefreshAuthInfo(const AliEngineAuthInfo &authInfo);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|const [AliEngineAuthInfo](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md) &|鉴权信息。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   SetAudioSessionOperationRestriction：设置SDK对AVAudioSession的控制权限（适用于iOS端）。

    ```
    int SetAudioSessionOperationRestriction(AliEngineAudioSessionOperationRestriction restriction);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |restriction|[AliEngineAudioSessionOperationRestriction](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|AVAudioSession控制权限设置。|

    返回说明

    0表示方法调用成功，其他表示方法调用失败。

-   GetCurrentConnectionStatus：获取当前网络连接状态。

    ```
    AliEngineConnectionStatus GetCurrentConnectionStatus();
    ```

    返回说明

    返回当前网络连接状态。


