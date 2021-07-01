# iOS集成

通过阅读本文，您可以了解超级小班课iOS端的集成操作。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   Web端服务已集成并开启。具体操作，请参见[Web集成](/cn.zh-CN/解决方案/超级小班课/Web集成.md)。
-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。具体操作，请参见[创建应用](/cn.zh-CN/快速入门/创建应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中未集成AliRTC SDK，需要手动进行集成。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  打开终端，定位到iOS文件夹下Podfile文件所在的目录，执行pod install命令。

    安装后生成的Pods文件夹已在iOS目录下。

4.  配置Demo工程。

    根据[步骤1](#step_knx_fmc_0md)中获取的AppID和AppKey修改iOS/RTCSmallClass/RTCSmallClass/RTC/RTCSmallClass.m⁩文件中`AppId`和`AppKey`的值。

    ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217478.png)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

5.  运行Demo。

    1.  使用Xcode打开iOS目录下的RTCSolution.xcworkspace文件。

    2.  选择运行的Target为RTCSolution，然后将iOS设备与电脑有线连接，并在Xcode中选择相对应的设备（暂不支持模拟器运行）。

        ![选择Target](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217496.png)

    3.  单击**General**页签，修改**Bundle Identifier**，建议将Bundle Identifier改成com.<公司名\>.<项目名\>，避免由于Bundle已被注册从而运行失败。

        ![General](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p217499.png)

    4.  单击**Signing & Capabilities**页签，选中**Automatically manage signing**，然后单击**Team**下拉框，根据实际情况选择Team。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

        **说明：** 如果之前没有添加过账号，可以选择**Add an Account...**，根据提示添加账号，然后在此处选择新添加的账号。

    5.  单击![004](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2963821161/p228524.png)，编译并运行。如果在编译过程中出现问题或无法正常通话，请参见[iOS端运行常见问题]()。

        ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1119850161/p217509.png)

6.  开启超级小班课。

    1.  教师由Web端输入姓名进入教室，为助教和学生发送教室码。

    2.  助教由Web端输入姓名和教室码进入教室，选择需要管理的小组进行管理。

    3.  学生由Web端或移动端输入姓名和教室码进行教室听课学习，还可以进行连麦互动。


## Demo目录结构说明

RTC把业务代码封装到RTCSmallClass的库中，因此只需在Podfile中指定RTCSmallClass库的路径，RTCSmallClass就可以以本地第三方库的形式移植到其他项目中。如下所示：

```
 pod 'RTCSmallClass', :path => '../RTCSmallClass'
    ##   pod 'RTCSmallClass'  表示项目依赖RTCSmallClass库
    ##   path => './RTCSmallClass'  表示RTCSmallClass库的位置(相对于Podfile文件)
```

RTCSmallClass组件库目录说明，如下所示：

|文件名|说明|
|---|--|
|RTCSmallClass.podspec|组件的描述文件。|
|RTCSmallClass.bundle|存放资源的bundle。|
|SmallClassLogin|登录页。|
|SmallClassMainController|通话页。|
|SmallClassGroupMemberController|小组成员页。|

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_ssd_56h_tos)|获取单例对象。|
|[destorySharedInstance](#li_1vb_0lp_au8)|销毁实例对象。|
|[login](#li_und_e7o_8cy)|加入房间。|
|[logout](#li_2co_2z7_5sp)|退出房间。|
|[muteLocalCamera](#li_jhk_gx4_k7g)|切换是否停止发布本地视频麦。|
|[muteLocalMic](#li_2ek_z5g_3o5)|切换是否停止发布本地音频。|
|[switchCamera](#li_8f6_v6q_yx9)|切换摄像头。|
|[getUserInfo](#li_xvg_453_y1f)|获取用户信息。|
|[startPreview](#li_in3_n9f_u5w)|开始预览。|
|[stopPreview](#li_4o2_i7b_g72)|停止预览。|
|[startPublish](#li_x9l_s6r_bm0)|开始推流。|
|[stopPublish](#li_a5y_vvp_wdt)|停止推流。|
|[getRemoteUserList](#li_m93_quk_i6y)|获取远端用户列表。|

|API|描述|
|---|--|
|[onJoin](#li_qqq_l02_7t3)|用户上线通知。|
|[onLeave](#li_xl2_vzq_29r)|用户下线通知。|
|[onOccurError](#li_vni_vh4_jr2)|SDK报错。|
|[onOccurWarning](#li_uvv_9bg_u9t)|SDK警告。|
|[onRoomDestroy](#li_fk6_ren_f5z)|房间被销毁的回调。|
|[onSDKError](#li_do9_q16_ae0)|SDK报错，需要销毁实例。|
|[onJoinChannelResult](#li_um7_ox8_436)|加入房间通知。|
|[onLeaveChannelResult](#li_fnu_mo8_ec2)|离开房间通知。|
|[onNetworkQualityChanged](#li_eku_ny7_ca9)|网络状态回调。|
|[onUserVideoMuted](#li_shb_ka4_hpm)|用户muteVideo通知。|
|[onUserAudioMuted](#li_ltf_b5s_hit)|用户muteAudio通知。|
|[onSubscribeResult](#li_63z_k67_v28)|订阅成功回调。|
|[onUserSpeaking](#li_th9_ue4_fzp)|判断用户是否在说话。|
|[onRemoteTraceAvaliable](#li_lfn_z9r_671)|当订阅情况发生变化时的回调。|

功能实现接口

-   sharedInstance：获取单例对象。

    ```
    /**
         * 获取单例
         */
       [RTCSmallClass sharedInstance];
    ```

-   destorySharedInstance：毁单例对象。

    ```
    /// 销毁RTCSDK
    - (void)destroySharedInstance;
    ```

-   login：加入房间。

    ```
    /// 加入频道
    /// @param channel 频道
    /// @param userName 用户昵称
    - (void)login:(NSString *)channel userName:(NSString *)userName;
    ```

-   logout：退出房间。

    ```
    /// 离开所有频道
    - (void)logout;
    ```

-   muteLocalCamera：切换是否停止发布本地视频。

    ```
    /// 禁用摄像头
    /// @param mute 是否禁用
    /// @param channel 频道
    - (int)muteLocalCamera:(BOOL)mute channel:(NSString *)channel;
    ```

-   muteLocalMic：切换是否停止发布本地音频。

    ```
    /// 静音
    /// @param mute 是否静音
    /// @param channel 频道
    - (int)muteLocalMic:(BOOL)mute channel:(NSString *)channel;
    ```

-   switchCamera：设置摄像头。

    ```
    /// 旋转摄像头
    - (int)switchCamera;
    ```

-   getUserInfo：获取用户信息。

    ```
     /// 获取用户信息
    /// @param uid 用户id
    /// @param channel 频道
    - (NSDictionary *)getUserInfo:(NSString *)uid channel:(NSString *)channel;
    ```

-   startPreview：开始预览。

    ```
    /// 开始本地预览
    /// @param preview 预览的view
    - (void)startPreview:(UIView *)preview;
    ```

-   stopPreview：停止预览。

    ```
    /// 停止本地预览
    - (void)stopPreview;
    ```

-   startPublish：开始推流。

    ```
      /// 开始推流
    /// @param channel 频道
    - (void)startPublish:(NSString *)channel;
    ```

-   stopPublish：停止推流。

    ```
      
    /// 停止推流
    /// @param channel 频道
    - (void)stopPublish:(NSString *)channel;
    ```

-   getRemoteUserList：获取远端用户列表。

    ```
    /// 获取某个频道远端用户列表
    /// @param channel 频道
    - (NSArray *)getRemoteUserList:(NSString *)channel;
    ```


回调接口

-   onJoin：用户上线通知。

    ```
      /// 远端用户加入频道
    /// @param channel 频道
    /// @param uid 用户id
    - (void)channel:(NSString *)channel onJoin:(NSString *)uid;
    ```

-   onLeave：用户下线通知。

    ```
    /// 远端用户离开频道
    /// @param channel 频道
    /// @param uid 用户id
    - (void)channel:(NSString *)channel onLeave:(NSString *)uid;
    ```

-   onOccurError：SDK报错。

    ```
    /// 错误码
    /// @param channel 频道
    /// @param error 错误码
    - (void)channel:(NSString *)channel onOccurError:(int)error;
    ```

-   onOccurWarning：SDK警告。

    ```
    /// 警告
    /// @param channel 频道
    /// @param warn 警告码
    - (void)channel:(NSString *)channel onOccurWarning:(int)warn;
    ```

-   onRoomDestroy：房间被销毁的回调。

    ```
       /// 房间被销毁通知
    - (void)onRoomdestroy;
    ```

-   onSDKError：SDK报错，需要销毁实例。

    ```
    /// sdk严重错误 需要销毁引擎
    /// @param channel 频道
    /// @param error 错误码
    - (void)channel:(NSString *)channel onSDKError:(int)error;
    ```

-   onJoinChannelResult：加入房间通知。

    ```
      /// 加入频道
    /// @param channel 频道
    /// @param result 结果
    - (void)channel:(NSString *)channel onJoinChannelResult:(int)result;
    ```

-   onLeaveChannelResult：离开房间通知。

    ```
    /// 离开频道
    /// @param channel 频道
    /// @param result 结果
    - (void)channel:(NSString *)channel onLeaveChannelResult:(int)result ;
    ```

-   onNetworkQualityChanged：网络状态。

    ```
    /// 网络变化判断
    /// @param uid 用户id
    /// @param upQuality 上行网络质量
    /// @param downQuality 下行网络质量
    - (void)onNetworkQualityChanged:(NSString *)uid
                   upNetworkQuality:(AliRtcNetworkQuality)upQuality
                 downNetworkQuality:(AliRtcNetworkQuality)downQuality;
    ```

-   onUserVideoMuted：用户muteVideo通知。

    ```
    /// 用户是否禁用摄像头
    /// @param channel 频道
    /// @param uid 用户id
    /// @param isMute 是否禁用
    - (void)channel:(NSString *)channel onUserVideoMuted:(NSString *)uid videoMuted:(BOOL)isMute;
    ```

-   onUserAudioMuted：用户muteAudio通知。

    ```
    /// 用户是否静音
    /// @param channel 频道
    /// @param uid 用户id
    /// @param isMute 用户是否静音
    - (void)channel:(NSString *)channel onUserAudioMuted:(NSString *)uid audioMuted:(BOOL)isMute;
    ```

-   onSubscribeResult：订阅成功。

    ```
    /// 订阅成功
    /// @param channel 频道
    /// @param uid 用户id
    /// @param result 结果
    - (void)channel:(NSString *)channel onSubscribe:(NSString *)uid result:(BOOL)result;
    ```

-   onUserSpeaking：判断用户是否在说话。

    ```
    /// 用户说话状态改变
    /// @param channel 频道
    /// @param uid 用户id
    /// @param speaking 是否正在说话
    /// @param name 用户昵称
    - (void)channel:(NSString *)channel onUserSpeaking:(NSString *)uid speaking:(BOOL) speaking displayName:(NSString *)name;
    ```

-   onRemoteTraceAvaliable：当订阅情况发生变化时的回调。

    ```
    /// 远端流变化
    /// @param channel 频道
    /// @param uid 用户id
    /// @param abaliable 是否可用
    - (void)channel:(NSString *)channel onRemoteTrace:(NSString *)uid avaliable:(BOOL)abaliable;
    ```


