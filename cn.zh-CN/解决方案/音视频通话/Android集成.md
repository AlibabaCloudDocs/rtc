# Android集成

通过阅读本文，您可以了解到Android端音视频通话的集成方法。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

环境中已安装Android Studio 3.0或以上版本，更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。更多信息，请参见[应用管理](/cn.zh-CN/控制台指南/管理应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已经集成AliRTC Android SDK。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  配置Demo工程。

    根据[步骤1](#step1)中获取的AppID和AppKey修改Android/app/src/main/java/com/aliyun/apsaravideo/sophon/utils/MockAliRtcAuthInfo.java文件中`appID`和`appKey`的值。

    ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3201134161/p243310.png)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

4.  运行Demo。如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。

    1.  打开Android Studio，单击**Open an Existing Project**，选择Android文件夹。

    2.  单击![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228848.png)，同步工程。

        ![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3201134161/p243312.png)

    3.  将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。

        ![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3201134161/p243313.png)

        **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。


## Demo目录结构说明

app程序入口目录说明：

|文件名|说明|
|---|--|
|base|activity基础类。|
|bean|实体类。|
|listener|监听回调类。|
|login|登录页。|
|network|网络请求。|
|adapter|列表控件adapter。|
|rtc|RTC。|
|util|工具类。|
|videocall|通话页面。|
|widget|控件。|

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_001)|获取RTCBeaconTowerImpl的实例对象，初始化RTC SDK。|
|[destorySharedInstance](#li_002)|销毁RTCBeaconTowerImpl的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。|
|[joinChannel](#li_003)|加入RTC频道。|
|[logout](#li_004)|退出RTC频道。|
|[muteLocalMic](#li_005)|是否停止本地音频采集。|
|[muteLocalCamera](#li_006)|是否停止本地视频采集。|
|[switchCamera](#li_007)|切换前后摄像头。|
|[setLocalViewConfig](#li_008)|为本地预览设置参数及绘制窗口。|
|[startPreview](#li_009)|开始本地预览。|
|[stopPreview](#li_010)|停止本地预览。|
|[configRemoteCameraTrack](#li_011)|设置是否拉取相机、屏幕、音频流，必须调用[subscribe](#li_012)才能生效。|
|[subscribe](#li_012)|手动拉视频和音频流。|
|[setRemoteViewConfig](#li_013)|为远端的视频设置参数及绘制窗口。|
|[setDelegate](#li_014)|设置监听。|
|[getUserInfo](#li_015)|获取用户信息。|

|API|描述|
|---|--|
|[onJoinChannelResult](#li_016)|加入房间的通知。|
|[onRemoteTrackAvailableNotify](#li_017)|远端用户音视频流发生变化时的回调。|
|[onSubscribeChangedNotify](#li_018)|订阅情况发生变化时的回调。|
|[onNetworkQualityChanged](#li_019)|网络质量变化时的回调。|
|[onRemoteUserOnLineNotify](#li_020)|远端用户上线的通知。|
|[onRemoteUserOffLineNotify](#li_021)|远端用户下线的通知。|

功能实现接口

-   sharedInstance：获取RTCBeaconTowerImpl的实例对象，初始化RTC SDK。

    ```
        /**
         * 获取单例
         */
        public static RTCBeaconTowerImpl sharedInstance() {
            return RTCBeaconTowerImpl.sharedInstance();
        }
    ```

-   destorySharedInstance：销毁RTCBeaconTowerImpl的实例对象，销毁后需要再调用[sharedInstance](#li_001)接口再次初始化实例。

    ```
     /**
         * 销毁实例
         */
        public abstract void destorySharedInstance();
    ```

-   joinChannel：加入RTC频道。

    ```
        /**
         * 加入房间
         */
        public abstract void joinChannel(AliRtcAuthInfo authInfo, String displayName);
    ```

-   logout：退出RTC频道。

    ```
        /**
         * 登出
         */
        public abstract void logout();
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

-   switchCamera：切换前后摄像头。

    ```
      /**
         * 切换摄像头
         */
        public abstract int switchCamera();
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

-   configRemoteCameraTrack：设置是否拉取相机、屏幕、音频流，必须调用[subscribe](#li_012)才能生效。

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

-   getUserInfo：获取用户信息。

    ```
        /**
         * 获取用户信息
         */
          public abstract AliRtcRemoteUserInfo getUserInfo(String s);
    ```


回调接口

-   onJoinChannelResult：加入房间的通知。

    ```
        /**
         * 加入房间通知
         * @param result 0为成功，反之失败
         */
        void onJoinChannelResult(int result);
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


