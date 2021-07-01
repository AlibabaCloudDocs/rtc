# Android集成

通过阅读本文，您可以了解Android端超级小班课的集成操作。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   Web端服务已集成并开启。具体操作，请参见[Web集成](/cn.zh-CN/解决方案/超级小班课/Web集成.md)。
-   环境中已安装Android Studio 3.0或以上版本。更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。具体操作，请参见[创建应用](/cn.zh-CN/快速入门/创建应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已经集成AliRTC Android SDK。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  配置Demo工程。

    根据[步骤1](#step_wiy_brc_zt8)中获取的AppID和AppKey修改RTCSuperClassRoom/RTCSuperClassRoom\_Demo/src/main/java/com/aliyun/rtc/superclassroom/utils/MockAliRtcAuthInfo.java文件中`appID`和`appKey`的值。

    ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3505260161/p214188.png)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

4.  运行Demo。

    1.  打开Android Studio，单击**Open an Existing Project**，选择android目录下的RtcSolutionSuperClassRoom文件夹。

    2.  单击![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228848.png)，同步工程。

    3.  将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。

        ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3505260161/p214194.png)

        **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。

5.  开启超级小班课。

    1.  教师由Web端输入姓名进入教室，为助教和学生发送教室码。

    2.  助教由Web端输入姓名和教室码进入教室，选择需要管理的小组进行管理。

    3.  学生由Web端或移动端输入姓名和教室码进行教室听课学习，还可以进行连麦互动。


## Demo目录结构说明

项目结构如下所示：

|文件名|说明|
|---|--|
|RTCSuperClassRoom|超级小班课功能实现库。更多信息，请参见[RTCSuperClassRoom组件库目录说明](#p_b89_v9p_urv)。|
|RTCSolutionCommon|公共组建库。|
|RTCViewCommo|公共UI库。|
|app|程序入口。|
|thirdparty-lib|第三方库的引用。|

RTCSuperClassRoom组件库目录说明，如下所示：

|文件名|说明|
|---|--|
|activity|activity类。|
|adapter|列表控件adapter。|
|api|网络请求。|
|bean|实体类。|
|constant|常量数据管理类，在此配置服务端请求域名和分享链接的域名。|
|rtc|RTC。|
|ui|互动界面和登录界面。|
|util|工具类。|
|view|自定义view。|

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_jox_e4t_etu)|获取单例对象。|
|[destorySharedInstance](#li_yv2_ack_684)|毁单例对象。|
|[login](#li_pe9_sd6_ttg)|加入房间。|
|[logout](#li_xld_k3q_cc0)|退出房间。|
|[muteLocalCamera](#li_y1w_vtg_qlu)|切换是否停止发布本地视频。|
|[muteLocalMic](#li_t5u_vqp_koz)|切换是否停止发布本地音频。|
|[switchCamera](#li_203_wn5_vbw)|切换摄像头。|
|[getUserInfo](#li_qgr_ml7_3qo)|获取用户信息。|
|[registerCallBack](#li_ut6_vk2_vmo)|注册回调。|
|[startPreview](#li_vhw_eqw_6t5)|开始预览。|
|[stopPreview](#li_qu3_ukg_j92)|停止预览。|
|[startPublish](#li_4ue_x22_mhj)|开始推流。|
|[stopPublish](#li_d38_zf3_s7h)|停止推流。|
|[setRemoteViewConfig](#li_4u2_vui_gtt)|设置远端画面。|
|[getRemoteUserList](#li_bjy_rgx_im6)|获取远端用户列表。|
|[isInCall](#li_pah_zjw_gq9)|是否入会。|
|[isPreview](#li_tym_i9c_ya0)|是否预览。|

|API|描述|
|---|--|
|[onJoin](#li_yia_s1o_0bk)|用户上线通知。|
|[onLeave](#li_jjd_wig_acd)|用户下线通知。|
|[onOccurError](#li_erp_26i_fo3)|SDK报错。|
|[onOccurWarning](#li_u1p_lj8_34n)|SDK警告。|
|[onRoomDestroy](#li_hnc_93y_ob2)|房间被销毁的回调。|
|[onSDKError](#li_qxp_og6_mps)|SDK报错，需要销毁实例。|
|[onJoinChannelResult](#li_0jh_66l_613)|加入房间通知。|
|[onLeaveChannelResult](#li_0hb_4p7_bhe)|离开房间通知。|
|[onNetworkQualityChanged](#li_t3n_guy_up4)|网络状态回调。|
|[onUserVideoMuted](#li_xmy_a5e_bxd)|用户muteVideo通知。|
|[onUserAudioMuted](#li_qh3_3wl_0xx)|用户muteAudio通知。|
|[onSubscribeResult](#li_y6h_t3w_xy8)|订阅成功回调。|
|[onUserSpeaking](#li_my5_sjx_epl)|判断用户是否在说话。|
|[onRemoteTraceAvaliable](#li_eja_2v0_4ig)|当订阅情况发生变化时回调。|

功能实现接口

-   sharedInstance：获取单例对象。

    获取RTCSuperClassImpl的实例对象，初始化RTC SDK。

    ```
    /**
         * 获取单例
         */
        public static BaseRTCSuperClass sharedInstance() {
            return RTCSuperClassImpl.sharedInstance();
        }
    ```

-   destorySharedInstance：毁单例对象。

    销毁RTCSuperClassImpl的实例对象，销毁后需要再调用sharedInstance接口再次初始化实例。

    ```
        /**
         * 销毁实例
         */
        public abstract void destorySharedInstance();
    ```

-   login：加入房间。

    根据输入的房间号、用户名加入RTC频道。

    ```
    /**
         * 登录
         *
         * @param channelId 房间号
         * @param userName 昵称
         */
        public abstract void login(String channelId,  String userName);
    ```

-   logout：退出房间。

    退出RTC频道。

    ```
        /**
         * 登出
         */
        public abstract void logout();
    ```

-   muteLocalCamera：切换是否停止发布本地视频。

    ```
        /**
         * 切换是否停止发布本地视频
         * @param channelId  频道号
         * @param isMute 是否停止发布
         */
        public abstract void muteLocalCamera(String channelId,boolean isMute); 
    ```

-   muteLocalMic：切换是否停止发布本地音频。

    ```
    /**
         * 切换是否停止发布本地音频
         *  @param channelId  频道号
         *  @param isMute 是否停止发布
         */
        public abstract void muteLocalMic(String channelId,boolean isMute);
    ```

-   switchCamera：设置摄像头接口。

    ```
        /**
         * 设置摄像头
         */
        public abstract void switchCamera();
    ```

-   getUserInfo：获取用户信息。

    ```
     /**
         * 获取用户信息
         * @param channelId  频道号
         * @param userId 用户id
         */
        public abstract AliRtcRemoteUserInfo getUserInfo(String channelId, String userId);
    ```

-   registerCallBack：注册回调。

    ```
     /**
         * 注册回调
         */
        public abstract void registerCallBack(RTCSuperClassCallback rtcSuperClassCallback);
    ```

-   startPreview：开始预览。

    ```
    /**
         * 开始预览
         * @param viewGroup  显示画面的view
         */
        public abstract void startPreview(ViewGroup viewGroup);
    ```

-   stopPreview：停止预览。

    ```
        /**
         * 停止预览
         */
        public abstract void stopPreview();
    ```

-   startPublish：开始推流。

    ```
        /**
         * 开始推流
         * @param channelId  频道号
         */
        public abstract void startPublish(String channelId);
    ```

-   stopPublish：停止推流。

    ```
       /**
         * 停止推流
         * @param channelId  频道号
         */
        public abstract void stopPublish(String channelId);
    ```

-   setRemoteViewConfig：设置远端画面。

    ```
    /**
         * 设置远端画面
         * @param channelId  频道号
         * @param canvas canvas对象
         * @param track track对象
         */
        public abstract void setRemoteViewConfig(String channelId, AliRtcEngine.AliVideoCanvas canvas, String uid, AliRtcEngine.AliRtcVideoTrack track);
    ```

-   getRemoteUserList：获取远端用户列表。

    ```
     /**
         * 获取远端用户列表
         * @param channelId  频道号
         */
        public abstract List<RTCUserInfo> getRemoteUserList(String channelId);
    ```

-   isInCall：是否入会。

    ```
      /**
         * 是否入会
         * @param channelId  频道号
         */
        public abstract boolean isInCall(String channelId);
    ```

-   isPreview：是否预览。

    ```
     /**
         * 是否预览
         * @param channelId  频道号
         */
        public abstract boolean isPreview(String channelId);
    ```


回调接口

-   onJoin：用户上线通知。

    ```
       /**
         * 用户上线通知
         *
         * @param userId 用户id
         */
        void onJoin(String channelId,String userId);
    ```

-   onLeave：用户下线。

    ```
     /**
         * 用户下线通知
         * @param channelId  频道号
         * @param userId 用户id
         */
        void onLeave(String channelId,String userId);
    ```

-   onOccurError：SDK报错通知。

    ```
        /**
         * sdk报错
         *
         * @param channelId  频道号
         */
        void onOccurError(String channelId,int error);
    ```

-   onOccurWarning：SDK警告。

    ```
        /**
         * sdk警告
         *
         * @param channelId  频道号
         */
        void onOccurWarning(String channelId,int error);
    ```

-   onRoomDestroy：房间被销毁的回调。

    ```
        /**
         * 房间被销毁的回调
         * @param channelId  频道号
         */
        void onRoomDestroy(String channelId);
    ```

-   onSDKError：SDK报错，需要销毁实例。

    ```
        /**
         * sdk报错,需要销毁实例
         * @param channelId  频道号
         */
        void onSDKError(String channelId,int error);
    ```

-   onJoinChannelResult：加入房间通知。

    ```
        /**
         * 加入房间通知
         * @param channelId  频道号
         * @param result 0为成功 反之失败
         */
        void onJoinChannelResult(String channelId,int result);
    ```

-   onLeaveChannelResult：离开房间通知。

    ```
        /**
         * 离开房间通知
         * @param channelId  频道号
         */
        void onLeaveChannelResult(String channelId,int result);
    ```

-   onNetworkQualityChanged：网络状态。

    ```
     /**
          * 网络状态回调
          *
          * @param channelId  频道号
          * @param aliRtcNetworkQuality1 下行网络质量
          * @param aliRtcNetworkQuality  上行网络质量
          * @param userId                     String  用户ID
          */
        void onNetworkQualityChanged(String channelId,String userId, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality1);
    ```

-   onUserVideoMuted：用户muteVideo通知。

    ```
    /**
         * 用户muteVideo通知
         * @param channelId  频道号
         */
        void onUserVideoMuted(String channelId,String userId, boolean mute);
    ```

-   onUserAudioMuted：用户muteAudio通知。

    ```
     /**
         * 用户muteAudio通知
         * @param channelId  频道号
         */
        void onUserAudioMuted(String channelId,String userId, boolean mute);
    ```

-   onSubscribeResult：订阅成功。

    ```
     /**
         *
         * 订阅成功
         * @param channelId  频道号
         * @param userId  用户ID
         * @param result  0表示订阅成功，非0表示失败
         * @param videoTrack     订阅成功的视频流
         * @param audioTrack     订阅成功的音频流
         */
        void onSubscribeResult(String channelId,String userId, int result, AliRtcEngine.AliRtcVideoTrack videoTrack, AliRtcEngine.AliRtcAudioTrack audioTrack);
    ```

-   onUserSpeaking：判断用户是否在说话。

    ```
     /**
         *
         * 用户是否在说话
         * @param channelId  频道号
         * @param userId  用户ID
         * @param isSpeaking 是否正在说话
         */
        void onUserSpeaking(String channelId,String userId, boolean isSpeaking);
    ```

-   onRemoteTraceAvaliable：当订阅情况发生变化时的回调。

    ```
      /**
          *
          * 当订阅情况发生变化时，返回这个消息 onSubscribeChangedNotify
          * @param channelId  频道号
          * @param userId  用户ID
          * @param videoTrack     订阅成功的视频流
          * @param audioTrack     订阅成功的音频流
          */
        void onRemoteTraceAvaliable(String channelId,String userId, AliRtcEngine.AliRtcAudioTrack audioTrack, AliRtcEngine.AliRtcVideoTrack videoTrack);
    ```


