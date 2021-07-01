# iOS集成

通过阅读本文，您可以了解语音聊天室iOS端的集成操作。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   服务端已集成并开启。具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/语音聊天室/服务端集成.md)。
-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 操作步骤

1.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    解压成功之后如下图所示：

    **说明：**

    -   Demo源码中没有集成iOS AliRTC SDK，需要手动进行集成。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
2.  下载并解压[SDK](https://alivc-demo-cms.alicdn.com/html-demo/SDK/ios/iOS1.18.2.2009075_Publish.zip)。

3.  打开终端，定位到Podfile文件所在的目录，执行pod install命令。

    安装成功如下图所示。安装后生成的Pods文件夹已在iOS目录下。

    ![Pod下载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200137.png)

4.  替换SDK。

    将[步骤二](#step_kg2_0qg_psy)解压的AliRTCSdk.framework文件，替换掉[步骤三](#step_w14_2jd_9d2)安装后生成的Pods/AliRTCSdk/AliRTCSdk.framework文件。

    ![替换AliRTCSdk](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200429.png)

5.  配置Demo工程。

    1.  打开iOS/RTCCommon/⁨AppConfig.h⁩文件。

    2.  修改文件中的`kBaseUrl`值。

        例如本地服务端IP地址为192.0.2.1，则`kBaseUrl`的值为`http://192.0.2.1:8080/`。本地服务端IP地址查询，请参见[查询IP地址]()。

        ![配置路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200643.png)

        **说明：**

        -   服务端IP地址禁止使用127.0.0.1。
        -   移动端和服务端处于同一局域网中。
        -   如果需要部署到正式环境，请绑定域名即`kBaseUrl`的值为`http://<域名>/`。
    3.  验证移动端和服务端。

        分别在移动端和服务端浏览器中访问`http://<服务器IP> :8080/chatroom`地址，如果显示如下图所示，表示移动端访问服务端正常。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200442.png)

6.  运行Demo。

    1.  使用Xcode打开iOS目录下的RTCSolution.xcworkspace工程文件。

    2.  选择运行的Target为RTCSolution，然后将iOS设备与电脑有线连接，并在Xcode中选择相对应的设备（暂不支持模拟器运行）。

        ![选择Target](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9122208061/p200474.png)

    3.  单击**General**页签，修改**Bundle Identifier**，建议将Bundle Identifier改成com.<公司名\>.<项目名\>，避免由于Bundle已被注册从而运行失败。

        ![General修改Bundle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8122208061/p200478.png)

    4.  单击**Signing & Capabilities**页签，选中**Automatically manage signing**，然后单击**Team**下拉框，根据实际情况选择Team。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

        **说明：** 如果之前没有添加过账号，可以选择**Add an Account...**，根据提示添加账号，然后在此处选择新添加的账号。

    5.  单击![004](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2963821161/p228524.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[iOS端运行常见问题]()。

        ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9122208061/p200645.png)

7.  加入语音聊天室。

    1.  将2台或2台以上移动端设备安装Demo App。

    2.  将设备连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间号和昵称，选择角色进入语聊房并等待他人加入。

    4.  在其余设备上输入相同房间号和任意昵称（可同名，不做限制），选择角色加入房间并进行聊天。


## Demo目录结构说明

RTC把开发的业务代码封装到RTCAudioLiveRoom库中，因此只需在Podfile中指定RTCAudioLiveRoom库的路径，RTCAudioLiveRoom就可以以本地第三方库的形式移植到其他项目中。如下所示：

```
#基础组件 :path 的路径为podfile 和 RTCCommon.podspec 的相对路径
pod 'RTCCommon', :path => 'RTCCommon/'
 
#基础UI组件 :path 的路径为podfile 和 RTCCommonView.podspec 的相对路径 
pod 'RTCCommonView', :path => 'RTCCommonView/'
 
#语聊房 :path 的路径为podfile 和 RTCAudioLiveRoom.podspec 的相对路径
pod 'RTCAudioLiveRoom', :path => 'RTCAudioLiveRoom/'
```

RTCAudioLiveRoom组件库目录说明，如下所示：

![路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6489148951/p142331.png)

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_hy5_w1p_wc3)|获取单例对象。|
|[destroySharedInstance](#li_yyv_xig_vc5)|销毁实例对象。|
|[login](#li_9di_hn2_1p4)|加入频道。|
|[logout](#li_0qb_dj2_vj1)|退出频道。|
|[enterSeat](#li_q0i_ttv_rww)|上麦。|
|[leavelSeat](#li_xjl_087_fry)|下麦。|
|[renotifySeatsInfo](#li_6cm_gwj_8zs)|重新通过回调通知座位信息。|
|[muteLocalMic](#li_ldr_8uu_otv)|静音或取消静音。|
|[muteAllRemoteAudioPlaying](#li_cpn_zcy_8ft)|关闭或开启远端声音。|
|[startAudioAccompanyWithFile](#li_4lp_asj_128)|播放背景音乐。|
|[stopAudioAccompany](#li_fw8_b3z_fmb)|停止播放背景音乐。|
|[setAudioAccompanyVolume](#li_ukf_6qv_kw0)|设置伴奏音量。|
|[playEffectSoundtWithSoundId](#li_w05_1sg_7hz)|播放音效。|
|[stopAudioEffectWithSoundId](#li_l66_eo5_70y)|停止播放音效。|
|[setAudioEffectPlayoutVolumeWithSoundId](#li_wd2_bzj_jn1)|设置音效的音量。|
|[enableEarBack](#li_041_79y_tqu)|设置耳返。|
|[setAudioEffectReverbMode](#li_ws8_hf5_5my)|设置混响模式。|
|[setAudioEffectVoiceChangerMode](#li_iu7_rgo_pbb)|设置音效混响模式。|

|API|描述|
|---|--|
|[onEnterSeat](#li_m7y_zrd_5f4)|远端用户上麦通知。|
|[onLeaveSeat](#li_f1x_4pb_rm8)|远端用户下线通知。|
|[onRoomDestory](#li_7tf_wdm_fv5)|房间被销毁通知。|
|[onSeatVolumeChanged](#li_iop_u2q_3rq)|音量变化通知。|
|[onSeatMutedChanged](#li_79m_a3g_0ub)|静音或取消静音变化通知。|

功能实现接口

-   获取单例对象。

    ```
    // 单例模式 初始化RTCAudioliveRoom
    RTCAudioliveRoom *manager = [RTCAudioliveRoom sharedInstance];
    //设置代理对象
    manager.delegate = vc
    ```

-   销毁实例对象。

    ```
    [self.manager destroySharedInstance];
    ```

-   加入频道。

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

-   退出频道。

    ```
    [self.manager logout];
    ```

-   上麦。

    ```
    [self.manager enterSeat];
    ```

-   下麦。

    ```
    [self.manager leavelSeat];
    ```

-   重新通过回调通知座位信息。

    ```
    [self.manager renotifySeatsInfo];
    ```

-   静音或取消静音。

    ```
    //静音
    [self.manager muteLocalMic:YES];
    
    //取消静音
    [self.manager muteLocalMic:NO];
    ```

-   关闭或开启远端声音。

    ```
    //关闭远端声音
    [self.manager muteAllRemoteAudioPlaying:YES];
    
    //开启远端声音
    [self.manager muteAllRemoteAudioPlaying:NO];
    ```

-   播放背景音乐。

    ```
    /// 播放背景音乐
    /// @param filePath 文件路径
    /// @param publish 是否推送远端
    
    [self.manager startAudioAccompanyWithFile:@"文件url" publish:YES];
    ```

-   停止播放背景音乐。

    ```
    [self.manager stopAudioAccompany];
    ```

-   设置伴奏音量。

    ```
    /// 设置背景音乐音量
    /// @param volume 音量 0~100
    
    [self.manager setAudioAccompanyVolume:100];
    ```

-   播放音效。

    ```
    /// 播放音效
    /// @param soundId 音效id
    /// @param filePath 资源路径
    /// @param publish 是否推送远端
    
    [self.manager playEffectSoundtWithSoundId:111
                                  filePath:@"文件url"
                                  publish:YES];
    ```

-   停止播放音效。

    ```
    [self.manager stopAudioEffectWithSoundId:111];
    ```

-   设置音效的音量。

    ```
    [self.manager setAudioEffectPlayoutVolumeWithSoundId:111 volume:100];
    ```

-   设置耳返。

    ```
    //开启耳返
    [self.manager enableEarBack:YES]; 
    //关闭耳返
    [self.manager enableEarBack:NO];
    ```

-   设置混响模式。

    ```
    [self.manager setAudioEffectReverbMode:AliRtcAudioEffectReverb_Off];
    ```

-   设置音效混响模式。

    ```
    [self.manager setAudioEffectVoiceChangerMode:AliRtcAudioEffectvVoiceChanger_OFF];
    ```


回调接口

-   远端用户上麦通知。

    ```
    /// 远端用户上麦通知
    /// @param seat 麦序
    - (void)onEnterSeat:(SeatInfo *)seat;
    ```

-   远端用户下线通知。

    ```
    /// 远端用户下线通知
    /// @param seat 麦序
    - (void)onLeaveSeat:(SeatInfo *)seat;
    ```

-   房间被销毁通知。

    ```
    /// 房间被销毁通知
    - (void)onRoomDestory;
    ```

-   音量变化通知。

    ```
    /// 音量变化通知
    /// @param seatIndex 麦序
    /// @param isSpeaking 是否在说话
    - (void)onSeatVolumeChanged:(NSInteger)seatIndex isSpeaking:(BOOL)isSpeaking;
    ```

-   静音或取消静音变化通知。

    ```
    /// 静音/取消静音变化通知
    /// @param seatIndex 麦序
    /// @param mute 是否静音
    - (void)onSeatMutedChanged:(NSInteger)seatIndex mute:(BOOL)mute;
    ```


