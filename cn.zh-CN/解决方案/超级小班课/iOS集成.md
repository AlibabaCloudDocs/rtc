# iOS集成

您可以阅读本文，了解iOS端超级小班课的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|iPhone设备|支持iPhone5及以上。|
|系统版本|支持iOS 8.0及以上。|
|CPU架构|支持真机架构armv7+arm64，不支持模拟器i386、x86架构。|
|Xcode版本|支持Xcode9.0及以上。下载[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。|
|CocoaPods版本|支持1.5.0及以上。具体操作，请参见[安装CocoaPods]()。|
|其他|不支持Bitcode，不支持屏幕旋转。|

您需要集成并启动Web端，具体操作，请参见[Web集成](/cn.zh-CN/解决方案/超级小班课/Web集成.md)。

**说明：** 您需要持有Apple开发证书或个人账号。

## Demo运行指引

**说明：**

您在集成iOS端时，如果遇到问题，或者Demo体验过程中出现无法创建房间或通话等问题，请参见[iOS端运行常见问题]()。

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

    -   Demo源码中未集成AliRTC SDK。需要手动进行集成。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
3.  打开终端，定位到iOS文件夹下Podfile文件所在的目录，执行`pod install`命令。

    安装后生成的Pods文件夹已在iOS目录下。

4.  修改配置文件。

    打开解压后的Demo文件夹alibabacloud-AliRtcSuperClass-demo，找到iOS/RTCSmallClass/RTCSmallClass/RTC/RTCSmallClass.m⁩文件。在文件的第339行和340行填写AppId和AppKey。

    ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217478.png)

    **说明：**

    本Demo中在客户端代码配置AppId和AppKey的方式，很容易被反编译逆向破解，一旦AppId和AppKey泄露，攻击者就可以盗用您的阿里云流量，因此该配置方式仅适合用于本地Demo的运行和功能调试。

    正确的Token签发方式是将Token的计算代码集成到您的服务端，并提供面向App的接口，在需要Token时由您的App接口向业务服务器发起请求获取动态Token。具体操作，请参见[生成Token](/cn.zh-CN/常用功能/生成Token.md)。

5.  导入Demo源码。

    打开**Xcode**，单击**Open a project or file**，双击打开iOS目录下的RTCSolution.xcworkspace文件。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217495.png)

6.  选择运行Target为RTCSolution，将一台IOS真机设备使用数据线与电脑链接，在**Xcode**中选择相应的真机设备，真机在设置中打开开发者模式。（暂不支持模拟器运行）

    ![选择Target](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217496.png)

7.  修改Bundle Identifier。

    **说明：** Bundle Identifier改成为`com.<公司名>.<项目名>`，避免由于Bundle已被注册从而运行失败。

    **General**选项卡中修改Bundle Identifier。

    ![General](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217499.png)

    **Sign & Capabilities**选项卡中修改Bundle Identifier。

    ![Sign](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1119850161/p217500.png)

8.  在**Sign & Capabilities**选项卡，勾选**Automatically manage signing**，在下方选择自己的**Team**。

    1.  选择**Team**。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

    2.  若以前没添加过账号，单击**Add an Account**添加。

        ![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184855.png)

    3.  完成账号添加。

        ![添加Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3457036061/p184858.png)

    4.  在Team里选择新创建的账号即可，并且在完成签名后确保下方没有报错提示。

9.  单击**build and run**按钮编译。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1119850161/p217509.png)

10. 开启超级小班课。

    iOS端主要为学生听课场景。

    1.  教师由Web端输入姓名进入教室，为助教和学生发送教室码。

    2.  助教由Web端输入姓名和教室码进入教室，选择需要管理的小组进行管理。

    3.  学生由Web端或移动端（Android或iOS）输入姓名和教室码进行教室听课学习，还可以进行连麦互动。


## Demo源码解析

1.  项目结构说明

    Demo是以Cocoapods Lib的方式集成到项目中的。

    RTC把开发的业务代码封装到名称为RTCSmallClass的库当中，这样RTCSmallClass就可以像一个本地的第三方库一样。可以随便移植到其他项目中。

    您只需在Podfile中指定RTCSmallClass库的路径即可。

    ```
     pod 'RTCSmallClass', :path => '../RTCSmallClass'
        ##   pod 'RTCSmallClass'  表示项目依赖RTCSmallClass库
        ##   path => './RTCSmallClass'  表示RTCSmallClass库的位置(相对于Podfile文件)
    ```

    livcVoiceCallSolo组件库目录说明，如下表所示。

    |文件名|说明|
    |---|--|
    |RTCSmallClass.podspec|组件的描述文件|
    |RTCSmallClass.bundle|存放资源的bundle|
    |SmallClassLogin|登录页|
    |SmallClassMainController|通话页|
    |SmallClassGroupMemberController|小组成员页|

2.  接口与回调

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_ssd_56h_tos)|获取单例对象|
    |[destorySharedInstance](#li_1vb_0lp_au8)|销毁实例对象|
    |[login](#li_und_e7o_8cy)|加入房间|
    |[logout](#li_2co_2z7_5sp)|退出房间|
    |[muteLocalCamera](#li_jhk_gx4_k7g)|切换是否停止发布本地视频麦|
    |[muteLocalMic](#li_2ek_z5g_3o5)|切换是否停止发布本地音频|
    |[switchCamera](#li_8f6_v6q_yx9)|切换摄像头|
    |[getUserInfo](#li_xvg_453_y1f)|获取用户信息|
    |[startPreview](#li_in3_n9f_u5w)|开始预览|
    |[stopPreview](#li_4o2_i7b_g72)|停止预览|
    |[startPublish](#li_x9l_s6r_bm0)|开始推流|
    |[stopPublish](#li_a5y_vvp_wdt)|停止推流|
    |[getRemoteUserList](#li_m93_quk_i6y)|获取远端用户列表|

    事件回调

    |API|描述|
    |---|--|
    |[onJoin](#li_qqq_l02_7t3)|用户上线通知|
    |[onLeave](#li_xl2_vzq_29r)|用户下线通知|
    |[onOccurError](#li_vni_vh4_jr2)|SDK报错|
    |[onOccurWarning](#li_uvv_9bg_u9t)|SDK警告|
    |[onRoomDestroy](#li_fk6_ren_f5z)|房间被销毁的回调|
    |[onSDKError](#li_do9_q16_ae0)|SDK报错，需要销毁实例|
    |[onJoinChannelResult](#li_um7_ox8_436)|加入房间通知|
    |[onLeaveChannelResult](#li_fnu_mo8_ec2)|离开房间通知|
    |[onNetworkQualityChanged](#li_eku_ny7_ca9)|网络状态回调|
    |[onUserVideoMuted](#li_shb_ka4_hpm)|用户muteVideo通知|
    |[onUserAudioMuted](#li_ltf_b5s_hit)|用户muteAudio通知|
    |[onSubscribeResult](#li_63z_k67_v28)|订阅成功回调|
    |[onUserSpeaking](#li_th9_ue4_fzp)|判断用户是否在说话|
    |[onRemoteTraceAvaliable](#li_lfn_z9r_671)|当订阅情况发生变化时的回调|

    接口示例

    -   获取单例对象

        接口名称：sharedInstance。

        ```
        /**
             * 获取单例
             */
           [RTCSmallClass sharedInstance];
        ```

    -   毁单例对象

        接口名称：destorySharedInstance。

        ```
        /// 销毁RTCSDK
        - (void)destroySharedInstance;
        ```

    -   加入房间

        接口名称：login。

        ```
        /// 加入频道
        /// @param channel 频道
        /// @param userName 用户昵称
        - (void)login:(NSString *)channel userName:(NSString *)userName;
        ```

    -   退出房间

        接口名称：logout。

        ```
        /// 离开所有频道
        - (void)logout;
        ```

    -   切换是否停止发布本地视频

        接口名称：muteLocalCamera。

        ```
        /// 禁用摄像头
        /// @param mute 是否禁用
        /// @param channel 频道
        - (int)muteLocalCamera:(BOOL)mute channel:(NSString *)channel;
        ```

    -   切换是否停止发布本地音频

        接口名称：muteLocalMic。

        ```
        /// 静音
        /// @param mute 是否静音
        /// @param channel 频道
        - (int)muteLocalMic:(BOOL)mute channel:(NSString *)channel;
        ```

    -   设置摄像头

        接口名称：switchCamera。

        ```
        /// 旋转摄像头
        - (int)switchCamera;
        ```

    -   获取用户信息

        接口名称：getUserInfo。

        ```
         /// 获取用户信息
        /// @param uid 用户id
        /// @param channel 频道
        - (NSDictionary *)getUserInfo:(NSString *)uid channel:(NSString *)channel;
        ```

    -   开始预览

        接口名称：startPreview。

        ```
        /// 开始本地预览
        /// @param preview 预览的view
        - (void)startPreview:(UIView *)preview;
        ```

    -   停止预览

        接口名称：stopPreview。

        ```
        /// 停止本地预览
        - (void)stopPreview;
        ```

    -   开始推流

        接口名称：startPublish。

        ```
          /// 开始推流
        /// @param channel 频道
        - (void)startPublish:(NSString *)channel;
        ```

    -   停止推流

        接口名称：stopPublish。

        ```
          
        /// 停止推流
        /// @param channel 频道
        - (void)stopPublish:(NSString *)channel;
        ```

    -   获取远端用户列表

        接口名称：getRemoteUserList。

        ```
        /// 获取某个频道远端用户列表
        /// @param channel 频道
        - (NSArray *)getRemoteUserList:(NSString *)channel;
        ```

    回调示例

    -   用户上线通知

        回调名称：onJoin。

        ```
          /// 远端用户加入频道
        /// @param channel 频道
        /// @param uid 用户id
        - (void)channel:(NSString *)channel onJoin:(NSString *)uid;
        ```

    -   用户下线通知

        回调名称：onLeave。

        ```
        /// 远端用户离开频道
        /// @param channel 频道
        /// @param uid 用户id
        - (void)channel:(NSString *)channel onLeave:(NSString *)uid;
        ```

    -   SDK报错

        回调名称：onOccurError。

        ```
        /// 错误码
        /// @param channel 频道
        /// @param error 错误码
        - (void)channel:(NSString *)channel onOccurError:(int)error;
        ```

    -   SDK警告

        回调名称：onOccurWarning。

        ```
        /// 警告
        /// @param channel 频道
        /// @param warn 警告码
        - (void)channel:(NSString *)channel onOccurWarning:(int)warn;
        ```

    -   房间被销毁的回调

        回调名称：onRoomDestroy。

        ```
           /// 房间被销毁通知
        - (void)onRoomdestroy;
        ```

    -   SDK报错，需要销毁实例

        回调名称：onSDKError。

        ```
        /// sdk严重错误 需要销毁引擎
        /// @param channel 频道
        /// @param error 错误码
        - (void)channel:(NSString *)channel onSDKError:(int)error;
        ```

    -   加入房间通知

        回调名称：onJoinChannelResult。

        ```
          /// 加入频道
        /// @param channel 频道
        /// @param result 结果
        - (void)channel:(NSString *)channel onJoinChannelResult:(int)result;
        ```

    -   离开房间通知

        回调名称：onLeaveChannelResult。

        ```
        /// 离开频道
        /// @param channel 频道
        /// @param result 结果
        - (void)channel:(NSString *)channel onLeaveChannelResult:(int)result ;
        ```

    -   网络状态

        回调名称：onNetworkQualityChanged。

        ```
        /// 网络变化判断
        /// @param uid 用户id
        /// @param upQuality 上行网络质量
        /// @param downQuality 下行网络质量
        - (void)onNetworkQualityChanged:(NSString *)uid
                       upNetworkQuality:(AliRtcNetworkQuality)upQuality
                     downNetworkQuality:(AliRtcNetworkQuality)downQuality;
        ```

    -   用户muteVideo通知

        回调名称：onUserVideoMuted。

        ```
        /// 用户是否禁用摄像头
        /// @param channel 频道
        /// @param uid 用户id
        /// @param isMute 是否禁用
        - (void)channel:(NSString *)channel onUserVideoMuted:(NSString *)uid videoMuted:(BOOL)isMute;
        ```

    -   用户muteAudio通知

        回调名称：onUserAudioMuted。

        ```
        /// 用户是否静音
        /// @param channel 频道
        /// @param uid 用户id
        /// @param isMute 用户是否静音
        - (void)channel:(NSString *)channel onUserAudioMuted:(NSString *)uid audioMuted:(BOOL)isMute;
        ```

    -   订阅成功

        回调名称：onSubscribeResult。

        ```
        /// 订阅成功
        /// @param channel 频道
        /// @param uid 用户id
        /// @param result 结果
        - (void)channel:(NSString *)channel onSubscribe:(NSString *)uid result:(BOOL)result;
        ```

    -   判断用户是否在说话

        回调名称：onUserSpeaking。

        ```
        /// 用户说话状态改变
        /// @param channel 频道
        /// @param uid 用户id
        /// @param speaking 是否正在说话
        /// @param name 用户昵称
        - (void)channel:(NSString *)channel onUserSpeaking:(NSString *)uid speaking:(BOOL) speaking displayName:(NSString *)name;
        ```

    -   当订阅情况发生变化时的回调

        回调名称：onRemoteTraceAvaliable。

        ```
        /// 远端流变化
        /// @param channel 频道
        /// @param uid 用户id
        /// @param abaliable 是否可用
        - (void)channel:(NSString *)channel onRemoteTrace:(NSString *)uid avaliable:(BOOL)abaliable;
        ```


