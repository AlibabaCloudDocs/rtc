# Android集成

您可以阅读本文，了解Android端超级小班课的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|系统版本|支持Android 4.1及以上。|
|API版本|不低于16。|
|CPU架构|支持真机架构armeabi、armeabi-v7a、arm64-v8a （不支持模拟器x86架构）。|
|Android Studio版本支持|支持Android Studio3.0及以上。下载[Android Studio](https://developer.android.google.cn/studio/)。|

您需要集成并启动Web端，具体操作，请参见[Web集成](/cn.zh-CN/解决方案/超级小班课/Web集成.md)。

## Demo运行指引

**说明：** 您在集成Android端时，如果遇到Demo体验过程中出现无法创建房间或通话等问题，请参见[Android端运行常见问题]()。

1.  获取应用ID和AppKey。

    **说明：**

    应用ID和AppKey需要对应，不同的应用ID有不同的AppKey。

    在后续开发中会使用应用ID和AppKey，建议记录到本地文档中，妥善保存。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  获取应用ID和查询AppKey。

        -   应用ID：可在**应用ID/名称**列表下直接获取。
        -   AppKey：单击**查询AppKey**获取AppKey。
        如果您还未有应用，您可以单击**创建应用**创建。

        ![获取AppKey和应用ID](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2758773061/p176303.png)

2.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcSuperClass-demo)并解压。

    解压成功之后如下图所示：

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p214008.png)

    **说明：**

    -   Demo源码中已经集成AliRTC SDK。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
3.  在Android Studio打开Android端工程。

    打开**Android Studio**，单击**Open an existing Android Studio project**并选择android目录下的RtcSolutionSuperClassRoom文件夹。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180032.png)

4.  修改配置文件。

    打开Android Studio，在Demo中找到RTCSuperClassRoom/RTCSuperClassRoom\_Demo/src/main/java/com/aliyun/rtc/superclassroom/utils/MockAliRtcAuthInfo.java文件。填写AppId和AppKey。

    ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3505260161/p214188.png)

    **说明：**

    本Demo中在客户端代码配置AppId和AppKey的方式，很容易被反编译逆向破解，一旦AppId和AppKey泄露，攻击者就可以盗用您的阿里云流量，因此该配置方式仅适合用于本地Demo的运行和功能调试。

    正确的Token签发方式是将Token的计算代码集成到您的服务端，并提供面向App的接口，在需要Token时由您的App接口向业务服务器发起请求获取动态Token。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

5.  选择一台已连接的真机设备。（暂不支持模拟器运行）

    将一台Android真机设备（需在系统设置中开启开发者模式和USB调试功能）使用数据线与电脑连接，在手机端同意调试后在Android Studio中选择接入的真机设备。

6.  单击**build and run**编译，Android真机会安装并启动超级小班课App。

    ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3505260161/p214194.png)

7.  开启超级小班课。

    Android端主要为学生听课场景。

    1.  教师由Web端输入姓名进入教室，为助教和学生发送教室码。

    2.  助教由Web端输入姓名和教室码进入教室，选择需要管理的小组进行管理。

    3.  学生由Web端或移动端（Android或iOS）输入姓名和教室码进行教室听课学习，还可以进行连麦互动。


## Demo源码解析

1.  项目结构说明

    -   RTCSuperClassRoom：超级小班课功能实现库。
    -   RTCSolutionCommon：公共组建库。
    -   RTCViewCommon：公共UI库。
    -   app：程序入口。
    -   thirdparty-lib：第三方库的引用。
    ![目录1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7445760161/p224679.png)

    -   activity：activity类。
    -   adapter：列表控件adapter。
    -   api：网络请求。
    -   bean：实体类。
    -   constants：常量数据管理类，在这配置Server端请求域名和分享链接的域名。
    -   rtc：RTC。
    -   ui：放的互动界面和登录界面。
    -   util：工具类。
    -   view：自定义view。
    ![目录2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7445760161/p224680.png)

2.  功能实现流程

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_jox_e4t_etu)|获取单例对象|
    |[destorySharedInstance](#li_yv2_ack_684)|毁单例对象|
    |[login](#li_pe9_sd6_ttg)|加入房间|
    |[logout](#li_xld_k3q_cc0)|退出房间|
    |[muteLocalCamera](#li_y1w_vtg_qlu)|切换是否停止发布本地视频|
    |[muteLocalMic](#li_t5u_vqp_koz)|切换是否停止发布本地音频|
    |[switchCamera](#li_203_wn5_vbw)|切换摄像头|
    |[getUserInfo](#li_qgr_ml7_3qo)|获取用户信息|
    |[registerCallBack](#li_ut6_vk2_vmo)|注册回调|
    |[startPreview](#li_vhw_eqw_6t5)|开始预览|
    |[stopPreview](#li_qu3_ukg_j92)|停止预览|
    |[startPublish](#li_4ue_x22_mhj)|开始推流|
    |[stopPublish](#li_d38_zf3_s7h)|停止推流|
    |[setRemoteViewConfig](#li_4u2_vui_gtt)|设置远端画面|
    |[getRemoteUserList](#li_bjy_rgx_im6)|获取远端用户列表|
    |[isInCall](#li_pah_zjw_gq9)|是否入会|
    |[isPreview](#li_tym_i9c_ya0)|是否预览|

    事件回调

    |API|描述|
    |---|--|
    |[onJoin](#li_yia_s1o_0bk)|用户上线通知|
    |[onLeave](#li_jjd_wig_acd)|用户下线通知|
    |[onOccurError](#li_erp_26i_fo3)|SDK报错|
    |[onOccurWarning](#li_u1p_lj8_34n)|SDK警告|
    |[onRoomDestroy](#li_hnc_93y_ob2)|房间被销毁的回调|
    |[onSDKError](#li_qxp_og6_mps)|SDK报错，需要销毁实例|
    |[onJoinChannelResult](#li_0jh_66l_613)|加入房间通知|
    |[onLeaveChannelResult](#li_0hb_4p7_bhe)|离开房间通知|
    |[onNetworkQualityChanged](#li_t3n_guy_up4)|网络状态回调|
    |[onUserVideoMuted](#li_xmy_a5e_bxd)|用户muteVideo通知|
    |[onUserAudioMuted](#li_qh3_3wl_0xx)|用户muteAudio通知|
    |[onSubscribeResult](#li_y6h_t3w_xy8)|订阅成功回调|
    |[onUserSpeaking](#li_my5_sjx_epl)|判断用户是否在说话|
    |[onRemoteTraceAvaliable](#li_eja_2v0_4ig)|当订阅情况发生变化时回调|

    接口示例

    -   获取单例对象

        接口名称：sharedInstance。

        获取RTCSuperClassImpl的实例对象，初始化RTC SDK。

        ```
        /**
             * 获取单例
             */
            public static BaseRTCSuperClass sharedInstance() {
                return RTCSuperClassImpl.sharedInstance();
            }
        ```

    -   毁单例对象

        接口名称：destorySharedInstance。

        销毁RTCSuperClassImpl的实例对象，销毁后需要再调用sharedInstance接口再次初始化实例。

        ```
            /**
             * 销毁实例
             */
            public abstract void destorySharedInstance();
        ```

    -   加入房间

        接口名称：login。

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

    -   退出房间

        接口名称：logout。

        退出RTC频道。

        ```
            /**
             * 登出
             */
            public abstract void logout();
        ```

    -   切换是否停止发布本地视频

        接口名称：muteLocalCamera。

        ```
            /**
             * 切换是否停止发布本地视频
             * @param channelId  频道号
             * @param isMute 是否停止发布
             */
            public abstract void muteLocalCamera(String channelId,boolean isMute); 
        ```

    -   切换是否停止发布本地音频

        接口名称：muteLocalMic。

        ```
        /**
             * 切换是否停止发布本地音频
             *  @param channelId  频道号
             *  @param isMute 是否停止发布
             */
            public abstract void muteLocalMic(String channelId,boolean isMute);
        ```

    -   设置摄像头接口

        名称：switchCamera。

        ```
            /**
             * 设置摄像头
             */
            public abstract void switchCamera();
        ```

    -   获取用户信息

        接口名称：getUserInfo。

        ```
         /**
             * 获取用户信息
             * @param channelId  频道号
             * @param userId 用户id
             */
            public abstract AliRtcRemoteUserInfo getUserInfo(String channelId, String userId);
        ```

    -   注册回调

        接口名称：registerCallBack。

        ```
         /**
             * 注册回调
             */
            public abstract void registerCallBack(RTCSuperClassCallback rtcSuperClassCallback);
        ```

    -   开始预览

        接口名称：startPreview。

        ```
        /**
             * 开始预览
             * @param viewGroup  显示画面的view
             */
            public abstract void startPreview(ViewGroup viewGroup);
        ```

    -   停止预览

        接口名称：stopPreview。

        ```
            /**
             * 停止预览
             */
            public abstract void stopPreview();
        ```

    -   开始推流

        接口名称：startPublish。

        ```
            /**
             * 开始推流
             * @param channelId  频道号
             */
            public abstract void startPublish(String channelId);
        ```

    -   停止推流

        接口名称：stopPublish。

        ```
           /**
             * 停止推流
             * @param channelId  频道号
             */
            public abstract void stopPublish(String channelId);
        ```

    -   设置远端画面

        接口名称：setRemoteViewConfig。

        ```
        /**
             * 设置远端画面
             * @param channelId  频道号
             * @param canvas canvas对象
             * @param track track对象
             */
            public abstract void setRemoteViewConfig(String channelId, AliRtcEngine.AliVideoCanvas canvas, String uid, AliRtcEngine.AliRtcVideoTrack track);
        ```

    -   获取远端用户列表

        接口名称：getRemoteUserList。

        ```
         /**
             * 获取远端用户列表
             * @param channelId  频道号
             */
            public abstract List<RTCUserInfo> getRemoteUserList(String channelId);
        ```

    -   是否入会

        接口名称：isInCall。

        ```
          /**
             * 是否入会
             * @param channelId  频道号
             */
            public abstract boolean isInCall(String channelId);
        ```

    -   是否预览

        接口名称：isPreview。

        ```
         /**
             * 是否预览
             * @param channelId  频道号
             */
            public abstract boolean isPreview(String channelId);
        ```

    回调通知

    -   用户上线通知

        回调名称：onJoin。

        ```
           /**
             * 用户上线通知
             *
             * @param userId 用户id
             */
            void onJoin(String channelId,String userId);
        ```

    -   用户下线

        通知调名称：onLeave。

        ```
         /**
             * 用户下线通知
             * @param channelId  频道号
             * @param userId 用户id
             */
            void onLeave(String channelId,String userId);
        ```

    -   SDK报错通知

        回调名称：onOccurError。

        ```
            /**
             * sdk报错
             *
             * @param channelId  频道号
             */
            void onOccurError(String channelId,int error);
        ```

    -   SDK警告

        回调名称：onOccurWarning。

        ```
            /**
             * sdk警告
             *
             * @param channelId  频道号
             */
            void onOccurWarning(String channelId,int error);
        ```

    -   房间被销毁的回调

        回调名称：onRoomDestroy。

        ```
            /**
             * 房间被销毁的回调
             * @param channelId  频道号
             */
            void onRoomDestroy(String channelId);
        ```

    -   SDK报错，需要销毁实例

        回调名称：onSDKError。

        ```
            /**
             * sdk报错,需要销毁实例
             * @param channelId  频道号
             */
            void onSDKError(String channelId,int error);
        ```

    -   加入房间通知

        回调名称：onJoinChannelResult。

        ```
            /**
             * 加入房间通知
             * @param channelId  频道号
             * @param result 0为成功 反之失败
             */
            void onJoinChannelResult(String channelId,int result);
        ```

    -   离开房间通知

        回调名称：onLeaveChannelResult。

        ```
            /**
             * 离开房间通知
             * @param channelId  频道号
             */
            void onLeaveChannelResult(String channelId,int result);
        ```

    -   网络状态

        回调名称：onNetworkQualityChanged。

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

    -   用户muteVideo通知

        回调名称：onUserVideoMuted。

        ```
        /**
             * 用户muteVideo通知
             * @param channelId  频道号
             */
            void onUserVideoMuted(String channelId,String userId, boolean mute);
        ```

    -   用户muteAudio通知

        回调名称：onUserAudioMuted。

        ```
         /**
             * 用户muteAudio通知
             * @param channelId  频道号
             */
            void onUserAudioMuted(String channelId,String userId, boolean mute);
        ```

    -   订阅成功

        回调名称：onSubscribeResult。

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

    -   判断用户是否在说话

        回调名称：onUserSpeaking。

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

    -   当订阅情况发生变化时的回调

        回调名称：onRemoteTraceAvaliable。

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


