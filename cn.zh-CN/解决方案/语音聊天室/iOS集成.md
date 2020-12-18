# iOS集成

您可以阅读本文，了解iOS端语音聊天室的集成操作。

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

您需要集成并启动服务端，具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/语音聊天室/服务端集成.md)。

**说明：** 您需要持有Apple开发证书或个人账号。

## Demo运行指引

**说明：**

您在集成iOS端时，如果遇到问题，或者Demo体验过程中出现无法创建房间或通话等问题，请参见[iOS端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcAudioLiveRoom-Demo)并解压。

    解压成功之后如下图所示：

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3640208061/p189742.png)

    **说明：**

    -   Demo源码中没有集成iOS AliRTC SDK，需要手动进行集成。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  下载[SDK](https://alivc-demo-cms.alicdn.com/html-demo/SDK/ios/iOS1.18.2.2009075_Publish.zip)并解压。

3.  打开终端，定位到Podfile文件所在的目录，执行`pod install`命令。

    安装成功如下图所示。安装后生成的Pods文件夹已在iOS目录下。

    ![Pod下载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200137.png)

4.  替换SDK。

    将[步骤二](#step_kg2_0qg_psy)解压的AliRTCSdk.framework文件，替换掉[步骤三](#step_w14_2jd_9d2)安装后生成的Pods/AliRTCSdk/AliRTCSdk.framework文件。

    ![替换AliRTCSdk](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200429.png)

5.  修改配置文件。

    1.  打开解压后的Demo文件夹alibabacloud-AliRtcAudioLiveRoom-Demo-master，找到iOS/RTCCommon/⁨AppConfig.h⁩文件。

    2.  修改文件中的`kBaseUrl`变量，如：`http://<服务器IP> :8080/`，部署到正式环境上建议绑定域名并使用：`http://<域名>/`。

        示例

        假设本地IP为192.0.2.1，那么`kBaseUrl="http://192.0.2.1:8080/"`。本地IP查询，请参见[查询IP地址]()。

        ![配置路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200643.png)

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机和电脑的浏览器验证。

        输入正确的URL（`http://<服务器IP> :8080/chatroom`）地址，即可在浏览器中打开并看到：`Hello RTC!`。电脑端浏览器正确访问说明IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200442.png)

6.  导入Demo源码。

    打开**Xcode**，单击**Open a project or file**，双击打开iOS目录下的RTCSolution.xcworkspace文件。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200473.png)

7.  选择运行Target为RTCSolution，将一台IOS真机设备使用数据线与电脑链接，在**Xcode**中选择相应的真机设备，真机在设置中打开开发者模式。（暂不支持模拟器运行）

    ![选择Target](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9122208061/p200474.png)

8.  修改Bundle Identifier。

    **说明：** Bundle Identifier改成为`com.<公司名>.<项目名>`，避免由于Bundle已被注册从而运行失败。

    **General**选项卡中修改Bundle Identifier。

    ![General修改Bundle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200478.png)

    **Sign & Capabilities**选项卡中修改Bundle Identifier。

    ![Signing修改Bundle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200477.png)

9.  在**Sign & Capabilities**选项卡，勾选**Automatically manage signing**，在下方选择自己的**Team**。

    1.  选择**Team**。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

    2.  若以前没添加过账号，单击**Add an Account**添加。

        ![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184855.png)

    3.  完成账号添加。

        ![添加Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3457036061/p184858.png)

    4.  在Team里选择新创建的账号即可，并且在完成签名后确保下方没有报错提示。

10. 单击**build and run**按钮编译。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9122208061/p200645.png)

11. 加入语音聊天室。

    1.  将2台或2台以上真机移动端设备（Android或iOS）装上Demo App。

    2.  将设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台真机上输入任意房间号和昵称，选择角色进入语聊房并等待他人加入。

    4.  在其余真机上输入相同房间号和任意昵称（可同名，不做限制），选择角色加入房间并进行聊天。


## Demo源码解析

1.  项目结构说明

    Demo是以cocoapods本地库的方式集成到项目中的。

    为了方便把语聊房的代码移植到您的项目中，我们把代码封装为名称为RTCAudioLiveRoom的本地库当中。

    您只需在Podfile中指定RTCAudioLiveRoom.podspec的路径即可。

    ```
    #基础组件 :path 的路径为podfile 和 RTCCommon.podspec 的相对路径
    pod 'RTCCommon', :path => 'RTCCommon/'
     
    #基础UI组件 :path 的路径为podfile 和 RTCCommonView.podspec 的相对路径 
    pod 'RTCCommonView', :path => 'RTCCommonView/'
     
    #语聊房 :path 的路径为podfile 和 RTCAudioLiveRoom.podspec 的相对路径
    pod 'RTCAudioLiveRoom', :path => 'RTCAudioLiveRoom/'
    ```

    ![路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6489148951/p142331.png)

2.  接口与回调

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_hy5_w1p_wc3)|获取单例对象|
    |[destroySharedInstance](#li_yyv_xig_vc5)|销毁实例对象|
    |[login](#li_9di_hn2_1p4)|加入频道|
    |[logout](#li_0qb_dj2_vj1)|退出频道|
    |[enterSeat](#li_q0i_ttv_rww)|上麦|
    |[leavelSeat](#li_xjl_087_fry)|下麦|
    |[renotifySeatsInfo](#li_6cm_gwj_8zs)|重新通过回调通知座位信息|
    |[muteLocalMic](#li_ldr_8uu_otv)|静音/取消静音|
    |[muteAllRemoteAudioPlaying](#li_cpn_zcy_8ft)|关闭/开启远端声音|
    |[startAudioAccompanyWithFile](#li_4lp_asj_128)|播放背景音乐|
    |[stopAudioAccompany](#li_fw8_b3z_fmb)|停止播放背景音乐|
    |[setAudioAccompanyVolume](#li_ukf_6qv_kw0)|设置伴奏音量|
    |[playEffectSoundtWithSoundId](#li_w05_1sg_7hz)|播放音效|
    |[stopAudioEffectWithSoundId](#li_l66_eo5_70y)|停止播放音效|
    |[setAudioEffectPlayoutVolumeWithSoundId](#li_wd2_bzj_jn1)|设置音效的音量|
    |[enableEarBack](#li_041_79y_tqu)|设置耳返|
    |[setAudioEffectReverbMode](#li_ws8_hf5_5my)|设置混响模式|
    |[setAudioEffectVoiceChangerMode](#li_iu7_rgo_pbb)|设置音效混响模式|

    事件回调

    |API|描述|
    |---|--|
    |[onEnterSeat](#li_m7y_zrd_5f4)|远端用户上麦通知|
    |[onLeaveSeat](#li_f1x_4pb_rm8)|远端用户下线通知|
    |[onRoomDestory](#li_7tf_wdm_fv5)|房间被销毁通知|
    |[onSeatVolumeChanged](#li_iop_u2q_3rq)|音量变化通知|
    |[onSeatMutedChanged](#li_79m_a3g_0ub)|静音/取消静音变化通知|

    接口示例

    -   获取单例对象

        ```
        // 单例模式 初始化RTCAudioliveRoom
        RTCAudioliveRoom *manager = [RTCAudioliveRoom sharedInstance];
        //设置代理对象
        manager.delegate = vc
        ```

    -   销毁实例对象

        ```
        [self.manager destroySharedInstance];
        ```

    -   加入频道

        ```
        /// 加入频道
        /// @param channelId   频道名称
        /// @param name    任意用于显示的用户名称。不是User ID
        /// @param role   角色
        /// @param handler   回调
        
         [self.manager login:@"频道名称"
                           name:@"用户昵称"
                           role:@"角色"
                       complete:^(AliRtcAuthInfo * _Nonnull authInfo, NSInteger errorCode) {
                if (authInfo)
                {
                    //加入房间成功
                    // ....
                    return;
                }
                //加入房间失败
            }];
        ```

    -   退出频道

        ```
        [self.manager logout];
        ```

    -   上麦

        ```
        [self.manager enterSeat];
        ```

    -   下麦

        ```
        [self.manager leavelSeat];
        ```

    -   重新通过回调通知座位信息

        ```
        [self.manager renotifySeatsInfo];
        ```

    -   静音/取消静音

        ```
        //静音
        [self.manager muteLocalMic:YES];
        
        //取消静音
        [self.manager muteLocalMic:NO];
        ```

    -   关闭/开启远端声音

        ```
        //关闭远端声音
        [self.manager muteAllRemoteAudioPlaying:YES];
        
        //开启远端声音
        [self.manager muteAllRemoteAudioPlaying:NO];
        ```

    -   播放背景音乐

        ```
        /// 播放背景音乐
        /// @param filePath 文件路径
        /// @param publish 是否推送远端
        
        [self.manager startAudioAccompanyWithFile:@"文件url" publish:YES];
        ```

    -   停止播放背景音乐

        ```
        [self.manager stopAudioAccompany];
        ```

    -   设置伴奏音量

        ```
        /// 设置背景音乐音量
        /// @param volume 音量 0~100
        
        [self.manager setAudioAccompanyVolume:100];
        ```

    -   播放音效

        ```
        /// 播放音效
        /// @param soundId 音效id
        /// @param filePath 资源路径
        /// @param publish 是否推送远端
        
        [self.manager playEffectSoundtWithSoundId:111
                                      filePath:@"文件url"
                                      publish:YES];
        ```

    -   停止播放音效

        ```
        [self.manager stopAudioEffectWithSoundId:111];
        ```

    -   设置音效的音量

        ```
        [self.manager setAudioEffectPlayoutVolumeWithSoundId:111 volume:100];
        ```

    -   设置耳返

        ```
        //开启耳返
        [self.manager enableEarBack:YES]; 
        //关闭耳返
        [self.manager enableEarBack:NO];
        ```

    -   设置混响模式

        ```
        [self.manager setAudioEffectReverbMode:AliRtcAudioEffectReverb_Off];
        ```

    -   设置音效混响模式

        ```
        [self.manager setAudioEffectVoiceChangerMode:AliRtcAudioEffectvVoiceChanger_OFF];
        ```

    回调示例

    -   远端用户上麦通知

        ```
        /// 远端用户上麦通知
        /// @param seat 麦序
        - (void)onEnterSeat:(SeatInfo *)seat;
        ```

    -   远端用户下线通知

        ```
        /// 远端用户下线通知
        /// @param seat 麦序
        - (void)onLeaveSeat:(SeatInfo *)seat;
        ```

    -   房间被销毁通知

        ```
        /// 房间被销毁通知
        - (void)onRoomDestory;
        ```

    -   音量变化通知

        ```
        /// 音量变化通知
        /// @param seatIndex 麦序
        /// @param isSpeaking 是否在说话
        - (void)onSeatVolumeChanged:(NSInteger)seatIndex isSpeaking:(BOOL)isSpeaking;
        ```

    -   静音/取消静音变化通知

        ```
        /// 静音/取消静音变化通知
        /// @param seatIndex 麦序
        /// @param mute 是否静音
        - (void)onSeatMutedChanged:(NSInteger)seatIndex mute:(BOOL)mute;
        ```


