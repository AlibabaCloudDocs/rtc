# iOS集成

通过阅读本文，您可以了解到iOS端音视频通话的集成方法。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。更多信息，请参见[应用管理](/cn.zh-CN/控制台指南/管理应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/Demo/Demo体验.md)。

    **说明：**

    -   Demo源码中已经集成AliRTC iOS SDK。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  配置Demo工程。

    根据[步骤1](#step1)中获取的AppID和AppKey修改iOS\\RTCSolution\\RTCBeaconTower\\RTCBeaconTower\\ChatRoomViewController.m文件中`appID`和`appKey`的值。

    ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2623514161/p243046.jpg)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/常用功能/生成Token.md)。

4.  运行Demo。

    1.  使用Xcode打开ios\\RTCSolution\\RTCSolution.xcworkspace工程文件。

    2.  选择运行的Target为RTCSolution，然后将iOS设备与电脑有线连接，并在Xcode中选择相对应的设备（暂不支持模拟器运行）。

        ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0389911161/p228448.png)

    3.  单击**General**页签，修改**Bundle Identifier**，建议将Bundle Identifier改成com.<公司名\>.<项目名\>，避免由于Bundle已被注册从而运行失败。

        ![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4575031161/p230707.png)

    4.  单击**Signing & Capabilities**页签，选中**Automatically manage signing**，然后单击**Team**下拉框，根据实际情况选择Team。

        ![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3326121161/p228517.png)

        **说明：** 如果之前没有添加过账号，可以选择**Add an Account...**，根据提示添加账号，然后在此处选择新添加的账号。

    5.  单击![004](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2963821161/p228524.png)，编译并运行。

        ![005](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3963821161/p228530.png)

    **说明：** 如果在签名、编译过程中出现问题或无法正常通话，请参见[iOS端运行常见问题]()。


## Demo目录结构说明

RTC把业务代码封装到RTCBeaconTower的库中，因此只需在Podfile中指定RTCBeaconTower库的路径，RTCBeaconTower就可以以本地第三方库的形式移植到其他项目中。如下所示：

```
 pod 'RTCBeaconTower', :path => 'RTCBeaconTower'
    ##   pod 'RTCBeaconTower'  说明项目依赖RTCBeaconTower库
    ##   path => 'RTCBeaconTower'  指明RTCBeaconTower库的位置(相对于Podfile)
```

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_001)|获取AliRTCBeaconTower的实例对象，初始化RTC SDK。|
|[destorySharedInstance](#li_002)|销毁AliRTCBeaconTower的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。|
|[login](#li_003)|根据输入的房间号、用户名加入RTC频道。|
|[logout](#li_004)|退出RTC频道。|
|[setDelegate](#li_005)|设置监听。|
|[enterSeat](#li_006)|连麦。|
|[leavelSeat](#li_007)|断开连麦。|
|[switchCamera](#li_008)|切换前后摄像头。|
|[muteLocalCamera](#li_009)|是否停止本地视频采集。|
|[muteLocalMic](#li_010)|是否停止本地音频采集。|
|[setLocalViewConfig](#li_011)|为本地预览设置参数及绘制窗口。|
|[setRemoteViewConfig](#li_012)|为远端的视频设置参数及绘制窗口。|
|[startPreview](#li_013)|开始本地预览。|
|[stopPreview](#li_014)|停止本地预览。|
|[configRemoteAudio](#li_015)|设置是否拉取音频流。|
|[configRemoteCameraTrack](#li_016)|设置是否拉取camera视频流。|
|[configRemoteScreenTrack](#li_017)|设置是否拉取screen视频流。|
|[displayName](#li_018)|获取用户名。|
|[enableSpeakPhone](#li_019)|设置是否开启扬声器。|
|[subscribe](#li_020)|手动拉视频和音频流。|

|API|描述|
|---|--|
|[onRemoteUserOffLineNotify](#li_021)|远端用户下线的通知。|
|[onRemoteUserOnLineNotify](#li_022)|远端用户上线的通知。|
|[onEnterSeatResult](#li_023)|用户上麦的通知。|
|[onLeaveSeatResult](#li_024)|用户下麦的通知。|
|[onRoomDestroy](#li_025)|房间被销毁的回调。|
|[onOccurError](#li_026)|错误信息的通知。|
|[onOccurWarning](#li_027)|警告信息的通知。|
|[onSDKError](#li_028)|SDK发生异常需要销毁实例。|
|[onJoinChannelResult](#li_029)|加入房间的通知。|
|[onLeaveChannelResult](#li_030)|离开房间的通知。|
|[onRemoteTrackAvailableNotify](#li_031)|远端用户音视频流发生变化时的回调。|
|[onSubscribeChangedNotify](#li_032)|订阅情况发生变化时的回调。|
|[onUserAudioMuted](#li_033)|用户取消音频的通知。|
|[onUserVideoMuted](#li_034)|用户取消视频的通知。|
|[onNetworkQualityChanged](#li_035)|网络质量变化时的回调。|
|[onUpdateRoleNotifyWithOldRole](#li_036)|角色切换成功的通知。|

功能实现接口

-   sharedInstance：获取AliRTCBeaconTower的实例对象，初始化RTC SDK。

    ```
    /**
    * @brief 获取单例
    * @return AliRTCBeaconTower 单例对象
    */
    + (AliRTCBeaconTower *) sharedInstance;
    ```

-   destorySharedInstance：销毁AliRTCBeaconTower的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。

    ```
    /// 销毁RTC SDK
    - (void)destroySharedInstance;
    ```

-   login：根据输入的房间号、用户名加入RTC频道。

    ```
    /**
    * @brief 加入频道
    * @param authInfo   频道号
    * @param name    任意用于显示的用户名称，不是User ID
    */
    - (void)login:(AliRtcAuthInfo *)authInfo name:(NSString *)name;
    ```

-   logout：退出RTC频道。

    ```
    /// 离开频道
    - (void)logout;
    ```

-   setDelegate：设置监听。

    ```
    - (void)setDelegate:(id<RTCVideoliveRoomDelegate> _Nullable)delegate;
    ```

-   enterSeat：连麦。

    ```
    /// 连麦
    - (int)enterSeat;
    ```

-   leavelSeat：断开连麦。

    ```
    //断开连麦
    - (void)leaveSeat;
    ```

-   switchCamera：切换前后摄像头。

    ```
    /**
    * @brief 切换前后摄像头
    * @return 0表示Success 非0表示Failure
    * @note 只有iOS和android提供这个接口
    */
    - (int)switchCamera;
    ```

-   muteLocalCamera：是否停止本地视频采集。

    ```
    /**
    * @brief 是否将停止本地视频采集
    * @param mute     YES表示停止视频采集；NO表示恢复正常
    * @param track    需要停止采集的track
    * @return 0表示Success 非0表示Failure
    * @note 发送黑色的视频帧。本地预览也呈现黑色。采集，编码，发送模块仍然工作，只是视频内容是黑色帧
    */
    - (int)muteLocalCamera:(BOOL)mute forTrack:(AliRtcVideoTrack)track;
    ```

-   muteLocalMic：是否停止本地音频采集。

    ```
    /**
    * @brief mute或unmute本地音频采集
    * @param mute  YES表示本地音频采集空帧；NO表示恢复正常
    * @note mute是指采集和发送静音帧。采集和编码模块仍然在工作
    * @return 0表示成功放入队列，-1表示被拒绝
    */
    - (int)muteLocalMic:(BOOL)mute;
    ```

-   setLocalViewConfig：为本地预览设置参数及绘制窗口。

    ```
    /**
    * @brief 为本地预览设置参数以及绘制窗口
    * @param viewConfig 包含了窗口以及渲染方式
    * @param track      must be AliVideoTrackCamera
    * @return 0表示Success，非0表示Failure
    * @note 支持joinChannel之前和之后切换窗口。如果viewConfig或者viewConfig中的view为nil，则停止渲染
    * 如果在播放过程中需要重新设置render mode，请保持canvas中其他成员变量不变，仅修改renderMode
    * 如果在播放过程中需要重新设置mirror mode，请保持canvas中其他成员变量不变，仅修改mirrorMode
    */
    - (int)setLocalViewConfig:(AliVideoCanvas *_Nullable)viewConfig forTrack:(AliRtcVideoTrack)track;
    ```

-   setRemoteViewConfig：为远端的视频设置参数及绘制窗口。

    ```
    /**
    * @brief 为远端的视频设置参数及绘制窗口
    * @param canvas canvas包含了窗口以及渲染方式
    * @param uid    User ID。从App server分配的唯一标示符
    * @param track  需要设置的track
    * @return 0表示Success，非0表示Failure
    * @note 支持joinChannel之前和之后切换窗口。如果canvas为nil或者view为nil，则停止渲染相应的流
    *       如果在播放过程中需要重新设置render mode，请保持canvas中其他成员变量不变，仅修改renderMode
    *       如果在播放过程中需要重新设置mirror mode，请保持canvas中其他成员变量不变，仅修改mirrorMode
    */
    - (int)setRemoteViewConfig:(AliVideoCanvas *)canvas uid:(NSString *)uid forTrack:(AliRtcVideoTrack)track;
    ```

-   startPreview：开始本地预览。

    ```
    /**
    * @brief 开始本地预览
    * @return 0表示Success 非0表示Failure
    * @note 如果没有设置view，则无法预览。可以在joinChannel之前就开启预览
    *       会自动打开摄像头
    */
    - (int)startPreview;
    ```

-   stopPreview：停止本地预览。

    ```
    /**
    * @brief 停止本地预览
    * @return 0表示Success 非0表示Failure
    * @note leaveChannel会自动停止本地预览
    *       会自动关闭摄像头 (如果正在publish camera流，则不会关闭摄像头)
    */
    - (int)stopPreview;
    ```

-   configRemoteAudio：设置是否拉取音频流。

    ```
    /**
     * @brief 设置是否拉取音频流
     * @param uid userId 从App server分配的唯一标示符
     * @param enable  YES: 拉取; NO: 不拉取
     * @note 可以在joinChannel之前或者之后设置。如果已经订阅该用户的流，需要调用subscribe:(NSString *)uid onResult:才生效
     */
    - (void)configRemoteAudio:(NSString *)uid enable:(BOOL)enable;
    ```

-   configRemoteCameraTrack：设置是否拉取camera视频流。

    ```
    /**
     * @brief 设置是否拉取camera视频流
     * @param uid userId 从App server分配的唯一标示符。
     * @param master  是否优先拉取大流
     * @param enable  YES: 拉取; NO: 不拉取
     * @note 可以在joinChannel之前或者之后设置。如果已经订阅该用户的流，需要调用subscribe:(NSString *)uid onResult:才生效
     */
    - (void)configRemoteCameraTrack:(NSString *)uid preferMaster:(BOOL)master enable:(BOOL)enable;
    ```

-   configRemoteScreenTrack：设置是否拉取screen视频流。

    ```
    /**
     * @brief 设置是否拉取screen视频流
     * @param uid  uerId从App server分配的唯一标示符
     * @param enable  YES: 拉取; NO: 不拉取
     * @note 可以在joinChannel之前或者之后设置。如果已经订阅该用户的流，需要调用subscribe:(NSString *)uid onResult:才生效
     */
    
    - (void)configRemoteScreenTrack:(NSString *)uid enable:(BOOL)enable;
    ```

-   displayName：获取用户名。

    ```
    /// 获取用户名
    /// @param userid userId
    - (NSString *)displayName:(NSString *)userid;
    ```

-   enableSpeakPhone：设置是否开启扬声器。

    ```
    - (int)enableSpeakPhone:(BOOL)enable;
    ```

-   subscribe：手动拉视频和音频流。

    ```
    /**
    * @brief 手动拉视频和音频流
    * @param uid        User ID。不允许为nil
    * @param onResult   当subscribe执行结束后调用这个回调
    * @note 如果需要手动选择拉取的流，调用configRemoteAudio, configRemoteTrack,
    *       configRemoteScreenTrack来设置。缺省是拉取audio和camera track
    *       如果需要unsub所有的流，先通过configRemoteAudio, configRemoteTrack,
    *       configRemoteScreenTrack来清除设置，然后调用subscribe
    */
    - (void)subscribe:(NSString *)uid onResult:(void (^)(NSString *uid, AliRtcVideoTrack vt, AliRtcAudioTrack at))onResult;
    ```


回调接口

-   onRemoteUserOffLineNotify：远端用户下线的通知。

    ```
    /// 远端用户下线通知
    /// @param uid 用户id
    - (void)onRemoteUserOffLineNotify:(NSString *)uid;
    ```

-   onRemoteUserOnLineNotify：远端用户上线的通知。

    ```
    /// 远端用户上线通知
    /// @param uid 用户id
    - (void)onRemoteUserOnLineNotify:(NSString *)uid;
    ```

-   onEnterSeatResult：用户上麦的通知。

    ```
    /// 自己上麦通知
    /// @param errorCode 结果
    - (void)onEnterSeatResult:(int)errorCode;
    ```

-   onLeaveSeatResult：用户下麦的通知。

    ```
    /// 自己下线通知
    /// @param errorCode 结果
    - (void)onLeaveSeatResult:(int)errorCode;
    ```

-   onRoomDestroy：房间被销毁的回调。

    ```
    /// 房间被销毁通知
    - (void)onRoomdestroy;
    ```

-   onOccurError：错误信息的通知。

    ```
    /**
     * @brief 如果engine出现error，通过这个回调通知app
     * @param error  Error type
     */
    - (void)onOccurError:(int)error;
    ```

-   onOccurWarning：警告信息的通知。

    ```
    /**
    * @brief 如果engine出现warning，通过这个回调通知app
    * @param warn  Warning type
    */
    - (void)onOccurWarning:(int)warn;
    ```

-   onSDKError：SDK发生异常需要销毁实例。

    ```
    /**
    * @brief 如果engine出现严重error，通过这个回调通知app
    * @param error  错误类型 
    */
    - (void)onSDKError:(int)error;
    ```

-   onJoinChannelResult：加入房间的通知。

    ```
    /**
    * @brief 加入频道结果
    * @param result 加入频道结果，成功返回0，失败返回错误码
    * @note 此回调等同于joinChannel接口的block，二者择一处理即可
    */
    - (void)onJoinChannelResult:(int)result authInfo:(AliRtcAuthInfo *)authInfo;
    ```

-   onLeaveChannelResult：离开房间的通知。

    ```
    /**
    * @brief 离开频道结果
    * @param result 离开频道结果，成功返回0，失败返回错误码
    * @note 调用leaveChannel接口后返回，如果leaveChannel后直接调用destroy，将不会收到此回调
    */
    - (void)onLeaveChannelResult:(int)result;
    ```

-   onRemoteTrackAvailableNotify：远端用户音视频流发生变化时的回调。

    ```
    /**
    * @brief 当远端用户的流发生变化时，返回这个消息
    * @note 远方用户停止推流，也会发送这个消息
    */
    - (void)onRemoteTrackAvailableNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack;
    ```

-   onSubscribeChangedNotify：当订阅情况发生变化时的回调。

    ```
    /**
     * @brief 当订阅情况发生变化时，返回这个消息
     */
    - (void)onSubscribeChangedNotify:(NSString *)uid audioTrack:(AliRtcAudioTrack)audioTrack videoTrack:(AliRtcVideoTrack)videoTrack;
    ```

-   onUserAudioMuted：用户取消音频的通知

    ```
    /**
     * @brief 用户muteAudio通知
     * @param uid 执行muteAudio的用户
     * @param isMute YES:静音 NO:未静音
     */
    - (void)onUserAudioMuted:(NSString *)uid onUserAudioMuted:(BOOL)isMute;
    ```

-   onUserVideoMuted：用户取消视频通知。

    ```
    /**
     * @brief 用户muteVideo通知
     * @param uid 执行muteVideo的用户
     * @param isMute YES:推流黑帧 NO:正常推流
     */
    - (void)onUserVideoMuted:(NSString *)uid videoMuted:(BOOL)isMute;
    ```

-   onNetworkQualityChanged：网络质量变化时的回调。

    ```
    /**
     * @brief 网络质量变化时发出的消息
     * @param uid 网络质量发生变化的uid
     * @param upQuality  上行网络质量
     * @param downQuality  下行网络质量
     * @note 当网络质量发生变化时触发，uid为@""时代表self的网络质量变化
     */
    - (void)onNetworkQualityChanged:(NSString *)uid
                   onNetworkQualityChanged:(AliRtcNetworkQuality)upQuality
                 downNetworkQuality:(AliRtcNetworkQuality)downQuality;
    ```

-   onUpdateRoleNotifyWithOldRole：角色切换成功的通知。

    ```
    /**
     * @brief 当用户角色发生变化化时通知
     * @param oldRole 变化前角色类型
     * @param newRole 变化后角色类型
     * @note 调用setClientRole方法切换角色成功时触发此回调
     */
    - (void)onUpdateRoleNotifyWithOldRole:(AliRtcClientRole)oldRole newRole:(AliRtcClientRole)newRole;
    ```


