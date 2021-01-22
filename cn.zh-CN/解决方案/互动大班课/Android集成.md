# Android集成

通过阅读本文，您可以了解到Android端互动大班课的集成方法。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   Web端服务已集成并开启，具体操作，请参见[Web集成](/cn.zh-CN/解决方案/互动大班课/Web集成.md)。
-   环境中已安装Android Studio 3.0或以上版本，更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。更多信息，请参见[应用管理](/cn.zh-CN/控制台指南/管理应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/Demo/Demo体验.md)。

    **说明：**

    -   Demo源码中已经集成AliRTC Android SDK。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  配置Demo工程。

    根据[步骤1](#step1)中获取的AppID和AppKey修改android/ApsaraVideoInteractiveClass/RTCInteractiveClass\_RTC/RTCInteractiveClass\_demo/src/main/java/com/aliyun/rtc/rtcinteractiveclassplayer/utils/MockAliRtcAuthInfo.java文件中`appID`和`appKey`的值。

    ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1352221161/p227422.png)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/常用功能/生成Token.md)。

4.  运行Demo。

    1.  打开Android Studio，单击**Open an Existing Project**，选择android目录下的ApsaraVideoInteractiveClass文件夹。

    2.  单击![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228848.png)，同步工程。

        ![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228852.png)

    3.  将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。

        ![005](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228920.png)

        **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。

    **说明：** 如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。


## Demo目录结构说明

项目结构如下所示：

|文件名|说明|
|---|--|
|RTCInteractiveClass\_RTC|互动大班课功能实现库。更多信息，请参见[RTCInteractiveClass\_RTC组件库目录说明](#p_bfx_igl_lri)。|
|RTCSolutionCommon|公共组建库。|
|RTCViewCommo|公共UI库。|
|app|程序入口。|
|thirdparty-lib|第三方库的引用。|

RTCInteractiveClass\_RTC组件库目录说明，如下所示：

|文件名|说明|
|---|--|
|adapter|列表控件adapter。|
|bean|实体类。|
|constant|常量数据管理类，在此配置服务端请求域名和分享链接的域名。|
|network|网络请求。|
|rtc|RTC。|
|ui|互动界面和登录界面。|
|util|工具类。|
|view|自定义view。|

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_001)|获取RTCInteractiveClassImpl的实例对象，初始化RTC SDK。|
|[destorySharedInstance](#li_002)|销毁RTCSuperClassImpl的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。|
|[login](#li_003)|根据输入的房间号、用户名加入RTC频道。|
|[logout](#li_004)|退出RTC频道。|
|[enterSeat](#li_005)|连麦。|
|[leavelSeat](#li_006)|断开连麦。|
|[muteLocalMic](#li_007)|是否停止本地音频采集。|
|[muteLocalCamera](#li_008)|是否停止本地视频采集。|
|[setLocalViewConfig](#li_009)|为本地预览设置参数及绘制窗口。|
|[startPreview](#li_010)|开始本地预览。|
|[stopPreview](#li_011)|停止本地预览。|
|[configRemoteCameraTrack](#li_012)|设置是否拉取相机、屏幕、音频流，必须调用[subscribe](#li_013)才能生效。|
|[subscribe](#li_013)|手动拉视频和音频流。|
|[setRemoteViewConfig](#li_014)|为远端的视频设置参数及绘制窗口。|
|[setDelegate](#li_015)|设置监听。|
|[switchCamera](#li_016)|切换前后摄像头。|

|API|描述|
|---|--|
|[onEnterSeatResult](#li_017)|用户上麦的通知。|
|[onLeaveSeatResult](#li_018)|用户下麦的通知。|
|[onOccurError](#li_019)|错误信息的通知。|
|[onOccurWarning](#li_020)|警告信息的通知。|
|[onRoomDestroy](#li_021)|房间被销毁的回调。|
|[onSDKError](#li_022)|SDK发生异常需要销毁实例。|
|[onJoinChannelResult](#li_023)|加入房间的通知。|
|[onLeaveChannelResult](#li_024)|离开房间的通知。|
|[onRemoteTrackAvailableNotify](#li_025)|远端用户音视频流发生变化时的回调。|
|[onSubscribeChangedNotify](#li_026)|订阅情况发生变化时的回调。|
|[onUserAudioMuted](#li_027)|用户取消音频的通知。|
|[onUserVideoMuted](#li_028)|用户取消视频的通知。|
|[onNetworkQualityChanged](#li_029)|网络质量变化时的回调。|
|[onUpdateRoleNotify](#li_030)|角色切换成功的通知。|
|[onRemoteUserOnLineNotify](#li_031)|远端用户上线的通知。|
|[onRemoteUserOffLineNotify](#li_032)|远端用户下线的通知。|

功能实现接口

-   sharedInstance：获取RTCInteractiveClassImpl的实例对象，初始化RTC SDK。

    ```
        /**
         * 获取单例
         */
        public static RTCInteractiveClassImpl sharedInstance() {
            return RTCInteractiveClassImpl.sharedInstance();
        }
    ```

-   destorySharedInstance：销毁RTCSuperClassImpl的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。

    ```
    /**
         * 销毁实例
         */
        public abstract void destorySharedInstance();
    ```

-   login：根据输入的房间号、用户名加入RTC频道。

    ```
        /**
         * 登录
         *
         * @param channelId 房间号
         * @param userName 昵称
         */
        public abstract void login(String channelId,  String userName);
    ```

-   logout：退出RTC频道。

    ```
        /**
         * 登出
         */
        public abstract void logout();
    ```

-   enterSeat：连麦。

    ```
     /**
         * 上麦
         */
        public abstract void enterSeat();
    ```

-   leavelSeat：断开连麦。

    ```
    /**
         * 下麦
         */
        public abstract void leavelSeat();
    ```

-   muteLocalMic：是否停止本地音频采集。

    ```
        /**
         * 停止发布音频
         */
        public abstract int muteLocalMic(boolean isMute);
    ```

-   muteLocalCamera：是否停止本地视频采集。

    ```
      /**
         * 停止发布视频
         */
        public abstract int muteLocalCamera(boolean isMute);
    ```

-   setLocalViewConfig：为本地预览设置参数及绘制窗口。

    ```
      /**
         * 设置本地预览渲染参数
         */
        public abstract void setLocalViewConfig(AliRtcEngine.AliVideoCanvas localAliVideoCanvas, AliRtcEngine.AliRtcVideoTrack aliRtcVideoTrackCamera);
    ```

-   startPreview：开始本地预览。

    ```
     /**
         * 开启预览
         */
        public abstract void startPreview();
    ```

-   stopPreview：停止本地预览。

    ```
       /**
         * 停止预览
         */
        public abstract void stopPreview();
    ```

-   configRemoteCameraTrack：设置是否拉取相机、屏幕、音频流，必须调用[subscribe](#li_013)才能生效。

    ```
        /**
         * 设置是否订阅远端相机流。默认为订阅大流。当对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效
         */
        public abstract void configRemoteCameraTrack(String userId, boolean master, boolean enable);
    ```

-   subscribe：手动拉视频和音频流。

    ```
      /**
         * 订阅
         */
        public abstract void subscribe(String userId);
    ```

-   setRemoteViewConfig：为远端的视频设置参数及绘制窗口。

    ```
     /**
         * 设置远端渲染参数
         */
        public abstract void setRemoteViewConfig(AliRtcEngine.AliVideoCanvas aliVideoCanvas, String uid, AliRtcEngine.AliRtcVideoTrack aliRtcVideoTrack);
    ```

-   setDelegate：设置监听。

    ```
      /**
         * 设置监听
         */
        public abstract void setDelegate(RTCInteractiveClassDelegate callback);
    ```

-   switchCamera：切换前后摄像头。

    ```
      /**
         * 切换摄像头
         */
        public abstract int switchCamera();
    ```


回调接口

-   onEnterSeatResult：用户上麦的通知。

    ```
       /**
        * 自己上麦结果通知
        * @param result 0为成功，反之失败
        */
       void onEnterSeatResult(int result);
    ```

-   onLeaveSeatResult：用户下麦的通知。

    ```
       /**
        * 自己下麦结果通知
        */
       void onLeaveSeatResult(int result);
    ```

-   onOccurError：错误信息的通知，当错误码是以下几种情况时，需要销毁SDK实例。

    -   ErrorCodeEnum.ERR\_ICE\_CONNECTION\_HEARTBEAT\_TIMEOUT
    -   ErrorCodeEnum.ERR\_SDK\_INVALID\_STATE
    -   ErrorCodeEnum.ERR\_SESSION\_REMOVED
    ```
       /**
        * SDK报错
        *
        */
       void onOccurError(int error);
    ```

-   onOccurWarning：警告信息的通知。

    ```
     /**
        * SDK警告
        *
        */
       void onOccurWarning( int error);
    ```

-   onRoomDestroy：房间被销毁的回调。

    ```
      /**
        * 房间被销毁的回调
        */
       void onRoomDestroy(int i);
    ```

-   onSDKError：SDK发生异常需要销毁实例。

    ```
       /**
        * SDK报错，需要销毁实例
        */
       void onSDKError( int error);
    ```

-   onJoinChannelResult：加入房间的通知。

    ```
        /**
         * 加入房间通知
         * @param result 0为成功，反之失败
         */
        void onJoinChannelResult(int result);
    ```

-   onLeaveChannelResult：离开房间的通知。

    ```
        /**
         * 离开房间通知
         */
        void onLeaveChannelResult(int result);
    ```

-   onRemoteTrackAvailableNotify：远端用户音视频流发生变化时的回调。

    ```
       /**
        *
        * 当订阅情况发生变化时，返回这个消息onSubscribeChangedNotify
        * @param userId  用户ID
        * @param videoTrack     订阅成功的视频流
        * @param audioTrack     订阅成功的音频流
        */
       void onRemoteTrackAvailableNotify(String userId, AliRtcEngine.AliRtcAudioTrack audioTrack, AliRtcEngine.AliRtcVideoTrack videoTrack);
    ```

-   onSubscribeChangedNotify：当订阅情况发生变化时的回调。

    ```
    /**
        *
        * 订阅结果回调
        * @param userId  用户ID
        * @param videoTrack     订阅成功的视频流
        * @param audioTrack     订阅成功的音频流
        */
       void onSubscribeChangedNotify(String userId, AliRtcEngine.AliRtcAudioTrack audioTrack, AliRtcEngine.AliRtcVideoTrack videoTrack);
    ```

-   onUserAudioMuted：用户取消音频的通知

    ```
      /**
         * 用户取消音频的通知
         */
        void onUserAudioMuted(String userId, boolean mute);
    ```

-   onUserVideoMuted：用户取消视频通知。

    ```
     /**
         * 用户取消视频通知
         */
        void onUserVideoMuted(String userId, boolean mute);
    ```

-   onNetworkQualityChanged：网络质量变化时的回调。

    ```
    /**
         * 网络状态回调
         *
         * @param aliRtcNetworkQuality1 下行网络质量
         * @param aliRtcNetworkQuality  上行网络质量
         * @param s                     用户ID
         */
        void onNetworkQualityChanged(String s, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality1);
    ```

-   onUpdateRoleNotify：角色切换成功的通知。

    ```
     /**
        *
        * 角色切换成功通知
        */
       void onUpdateRoleNotify(AliRtcEngine.AliRTCSDK_Client_Role oldRole, AliRtcEngine.AliRTCSDK_Client_Role newRole);
    ```

-   onRemoteUserOnLineNotify：远端用户上线的通知。

    ```
       /**
        * 用户上线通知
        *
        * @param userId 用户ID
        */
       void onRemoteUserOnLineNotify(String userId);
    ```

-   onRemoteUserOffLineNotify：远端用户下线的通知。

    ```
       /**
        * 用户下线通知
        * @param userId 用户ID
        */
       void onRemoteUserOffLineNotify(String userId);
    ```


