# Android集成

您可以阅读本文，了解Android端语音聊天室的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|系统版本|支持Android 4.1及以上。|
|API版本|不低于16。|
|CPU架构|支持真机架构armeabi、armeabi-v7a、arm64-v8a （不支持模拟器x86架构）。|
|Android Studio版本支持|支持Android Studio3.0及以上。下载[Android Studio](https://developer.android.google.cn/studio/)。|

您需要集成并启动服务端，具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/语音聊天室/服务端集成.md)。

## Demo运行指引

**说明：** 您在集成Android端时，如果遇到Demo体验过程中出现无法创建房间或通话等问题，请参见[Android端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcAudioLiveRoom-Demo)并解压。

    解压成功之后如下图所示：

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3640208061/p189742.png)

    **说明：**

    -   Demo源码中已经集成AliRTC SDK（版本：1.18）。SDK集成方式通过Maven集成。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  在Android Studio打开Android端工程。

    打开**Android Studio**，单击**Open an existing Android Studio project**并选择alibabacloud-AliRtcAudioLiveRoom-Demo-master目录下的android文件夹。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180032.png)

3.  修改配置文件。

    1.  打开Android Studio，在Demo中找到android/RTCAudioLiveRoom/RTCAudioLiveRoom\_Demo/src/main/java/com/aliyun/rtc/audiochatroom/constant/Constant.java文件。

        ![打开配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200493.png)

    2.  修改文件中的`BASE_URL`变量，如：`http://<服务器IP> :端口:8080/chatroom`，部署到正式环境上建议绑定域名并使用：`http://<域名>/chatroom`。

        示例

        假设本地IP为192.0.2.1，那么`BASE_URL="http://192.0.2.1:8080/chatroom"`。本地IP查询，请参见[查询IP地址]()。

        ![修改BASE_URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200495.png)

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机端和电脑端浏览器验证。

        输入正确的URL（`BASE_URL`变量）地址，即可在浏览器中打开并看到：Hello RTC!。电脑端浏览器正确访问说明IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200442.png)

4.  选择一台已连接的真机设备。（暂不支持模拟器运行）

    将一台Android真机设备（需在系统设置中开启开发者模式和USB调试功能）使用数据线与电脑连接，在手机端同意调试后在Android Studio中选择接入的真机设备。

5.  单击**build and run**编译，Android真机会安装并启动语音聊天室App。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200584.png)

6.  加入语音聊天室。

    1.  将2台或2台以上真机移动端设备（Android或iOS）装上Demo App。

    2.  将设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台真机上输入任意房间号和昵称，选择角色进入语聊房并等待他人加入。

    4.  在其余真机上输入相同房间号和任意昵称（可同名，不做限制），选择角色加入房间并进行聊天。


## Demo源码解析

1.  项目结构说明

    -   RTCAudioLiveRoom：语聊房功能实现库。
    -   RTCSolutionCommon：公共组建库。
    -   RTCViewCommon：公共UI库。
    -   app：程序入口。
    -   thirdparty-lib：第三方库的引用。
    ![目录结构1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9881129951/p142817.png)

    -   adapter：列表控件adapter。
    -   bean：实体类。
    -   Constant：常量数据管理类，在这配置Server端请求域名和分享链接的域名。
    -   api：网络请求。
    -   rtc：RTC。
    -   ui：放的互动界面和登录界面。
    -   util：工具类。
    -   view：自定义view。
    ![目录结构2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0981129951/p142820.png)

2.  功能实现流程

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_n7p_k2s_uer)|获取单例对象|
    |[destorySharedInstance](#li_nft_wmt_5zn)|毁单例对象|
    |[login](#li_p7g_28q_vms)|加入房间|
    |[logout](#li_m4c_sja_kye)|退出房间|
    |[setAudioEffectVolume](#li_x3q_9po_mm3)|设置音效音量|
    |[setAudioAccompanyVolume](#li_66k_o3c_cd7)|设置伴奏音量|
    |[enterSeat](#li_j1l_npk_vtf)|上麦|
    |[leavelSeat](#li_qm7_00y_2ob)|下麦|
    |[setRTCAudioLiveRoomDelegate](#li_d3d_b96_ztn)|设置监听回调|
    |[muteLocalMic](#li_xry_0fu_u6z)|设置是否静音|
    |[muteRomteAudioPlaying](#li_a33_n3s_d1n)|设置是否本地静音|
    |[enableEarBack](#li_i1z_vg6_nhg)|是否开启耳返|
    |[startAudioAccompany](#li_f6k_xmd_0e1)|播放伴奏|
    |[stopAudioAccompany](#li_fdu_xah_7ry)|停止伴奏|
    |[playAudioEffect](#li_hgz_grj_ecr)|播放音效|
    |[stopAudioEffect](#li_5v0_4op_stx)|停止音效|
    |[setAudioEffectReverbMode](#li_gy8_s2e_14z)|设置音效场景（混音模式）|
    |[setAudioEffectVoiceChangerMode](#li_ieg_tax_wku)|设置变声音效模式|

    事件回调

    |API|描述|
    |---|--|
    |[onEnterSeat](#li_gg1_u4j_ufe)|用户上麦通知|
    |[onLeaveSeat](#li_adk_6tx_2rv)|用户下麦通知|
    |[onOccurError](#li_uzm_4cb_995)|错误信息通知|
    |[onUpdateRoleNotify](#li_mj9_qfv_0pz)|切换用户角色回调|
    |[onPublishChangedNotify](#li_ptq_9kt_bg5)|推流回调|
    |[onJoinChannelResult](#li_d9d_pxa_yby)|加入频道结果回调|
    |[onLeaveChannelResult](#li_l3w_7ts_m8o)|离开频道结果回调|
    |[onSeatVolumeChanged](#li_gkr_auk_7x7)|音量大小提示|
    |[onAudioPlayingStateChanged](#li_4sg_tq8_xf2)|伴奏播放回调|
    |[onUserAudioMuted](#li_z2g_g8j_jgs)|用户muteAudio通知回调|
    |[onRoomDestroy](#li_ebp_tpu_fqi)|房间被销毁回调|
    |[onNetworkQualityChanged](#li_dne_r13_nx5)|网络状态回调|

    接口示例

    -   获取单例对象

        接口名称：sharedInstance。

        获取BaseRTCAudioLiveRoom的实例对象，初始化RTC SDK。

        ```
            /**
             * 获取单例
             */
            public static BaseRTCAudioLiveRoom sharedInstance() {
                return RTCAudioLiveRoomImpl.sharedInstance();
            }
        ```

    -   毁单例对象

        接口名称：destorySharedInstance。

        销毁BaseRTCAudioLiveRoom的实例对象，销毁后需要再调用sharedInstance接口再次初始化实例。

        ```
            /**
             * 销毁实例
             */
            public abstract void destorySharedInstance();
        ```

    -   加入房间

        接口名称：login。

        根据选中的角色类型、房间号、用户名加入RTC频道。

        ```
         /**
             * 加入房间
             *
             * @param role           角色类型
             * @param channelId      房间号
             * @param userName       用户名
             */
            public abstract void login(String channelId, String userName, AliRtcEngine.AliRTCSDK_Client_Role role);
        ```

    -   退出房间

        接口名称：logout。

        退出RTC频道。

        ```
            /**
             * 退出房间
             */
            public abstract void logout();
        ```

    -   设置音效音量

        接口名称：setAudioEffectVolume。

        同时设置播放和推流的音量。

        ```
            /**
             * 设置音效音量
             * 
             * @param soundId 音效文件的sourceId
             * @param volume 音量 区间0-100
             *
             */
            public abstract void setAudioEffectVolume(int soundId, int volume);
        ```

    -   设置伴奏音量

        接口名称：setAudioAccompanyVolume。

        同时设置播放和推流的音量。

        ```
            /**
             * 设置伴奏音量
             * @param volume 音量 区间0-100
             */
            public abstract void setAudioAccompanyVolume(int volume);
        ```

    -   上麦

        接口名称：enterSeat。

        切换互动角色。

        ```
            /**
             * 上麦
             */
            public abstract void enterSeat();
        ```

    -   下麦

        接口名称：leavelSeat。

        切换观众角色。

        ```
            /**
             * 下麦
             */
            public abstract void leaveSeat();
        ```

    -   设置监听回调

        接口名称：setRTCAudioLiveRoomDelegate。

        ```
                /**
             * 设置监听
             *
             * @param audioLiveRoomDelegate 监听
             */
            public abstract void setRTCAudioLiveRoomDelegate(RTCAudioLiveRoomDelegate audioLiveRoomDelegate);        
        ```

    -   设置是否静音

        接口名称：muteLocalMic。

        ```
            /**
             * 是否开启静音模式
             *
             * @param mute true为静音 false不静音
             * @return 0表示设置成功，反之失败
             */
            public abstract int muteLocalMic(boolean mute);
        ```

    -   设置是否本地静音

        接口名称：muteRomteAudioPlaying。

        true表示本地听不到远端的声音，false表示本地可以听到远端声音。

        ```
            /**
             * 停止远端的所有音频流的播放。返回0为成功，其他返回错误码。
             *
             * @param enableSpeakerPhone true为开启 false关闭
             * @return 0表示设置成功，反之失败
             */
            public abstract int muteAllRemoteAudioPlaying(boolean enableSpeakerPhone);
        ```

    -   是否开启耳返

        接口名称：enableEarBack。

        ```
            /**
             * 是否耳返
             *
             * @param enableEarBack 是否开启耳返 true为开启 false关闭
             * @return 0表示设置成功，反之失败
             */
            public abstract int enableEarBack(boolean enableEarBack);
        ```

    -   播放伴奏

        接口名称：startAudioAccompany。

        ```
            /**
             * 开始伴奏
             *
             * @param fileName      伴奏文件路径，支持本地文件和网络url
             * @param onlyLocalPlay 是否仅本地播放，true表示仅仅本地播放，false表示本地播放且推流到远端
             * @param replaceMic    是否替换mic的音频流，true表示伴奏音频流替换本地mic音频流，false表示伴奏音频流和mic音频流同时推
             * @param loopCycles    循环播放次数，-1表示一直循环
             */
            public abstract void startAudioAccompany(String fileName, boolean onlyLocalPlay, boolean replaceMic, int loopCycles);
        ```

    -   停止伴奏

        接口名称：stopAudioAccompany。

        ```
            /**
             * 停止伴奏
             */
            public abstract void stopAudioAccompany();
        ```

    -   播放音效

        接口名称：playAudioEffect。

        ```
            /**
             * 播放音效
             *
             * @param soundId  音效ID
             * @param filePath 音效文件路径，支持本地文件和网络url
             * @param cycles   循环播放次数。-1表示一直循环
             * @param publish  是否将音效音频流推到远端
             */
            public abstract void playAudioEffect(int soundId, String filePath, int cycles, boolean publish);
        ```

    -   停止音效

        接口名称：stopAudioEffect。

        ```
            /**
             * 停止音效
             *
             * @param soundId 音效ID
             */
            public abstract void stopAudioEffect(int soundId);
        ```

    -   设置音效场景（混音模式）

        接口名称：setAudioEffectReverbMode。

        ```
            /**
             * 设置音效场景
             * @param aliRtcAudioEffectReverbMode 音效场景枚举
             */
            public abstract void setAudioEffectReverbMode(AliRtcEngine.AliRtcAudioEffectReverbMode aliRtcAudioEffectReverbMode);
        ```

    -   设置变声音效模式

        接口名称：setAudioEffectVoiceChangerMode。

        ```
            /**
             * 设置变声音效模式
             *
             * @param mode 模式
             * @return int 结果码 0为成功
             */
            public abstract int setAudioEffectVoiceChangerMode(AliRtcEngine.AliRtcAudioEffectVoiceChangerMode mode);
        ```

    回调通知

    -   用户上麦通知

        回调名称：onEnterSeat。

        ```
            /**
             * 上麦通知回调
             *
             * @param seatInfo 麦位信息
             */
            void onEnterSeat(SeatInfo seatInfo);
        ```

    -   用户下麦通知

        回调名称：onLeaveSeat

        ```
            /**
             * 下麦通知回调
             *
             * @param seatInfo 麦位信息
             */
            void onLeaveSeat(SeatInfo seatInfo);
        ```

    -   错误信息通知

        回调名称：onOccurError。

        当错误码是以下几种情况时，需要销毁SDK实例：

        -   ErrorCodeEnum.ERR\_ICE\_CONNECTION\_HEARTBEAT\_TIMEOUT
        -   ErrorCodeEnum.ERR\_SDK\_INVALID\_STATE
        -   ErrorCodeEnum.ERR\_SESSION\_REMOVED
        ```
            /**
             * sdk报错
             * @param error 错误码
             */
            void onOccurError(int error);
        ```

    -   切换用户角色回调

        回调名称：onUpdateRoleNotify。

        ```
            /**
             * 角色切换成功
             *
             * @param oldRole 旧的用户角色
             * @param newRole 新的用户角色
             */
            void onUpdateRoleNotify(AliRtcEngine.AliRTCSDK_Client_Role oldRole, AliRtcEngine.AliRTCSDK_Client_Role newRole);
        ```

    -   推流回调

        回调名称：onPublishChangedNotify。

        ```
            /**
             * 推流结果回调
             * @param result 返回码 0表示推流成功，反之失败
             * @param isPublished 是否再推流
             */
            void onPublishChangedNotify(int result, boolean isPublished);
        ```

    -   加入频道结果回调

        回调名称：onJoinChannelResult。

        result为0表示加入房间成功，反之失败。

        ```
            /**
             * 登陆回调
             *
             * @param result 状态码
             * @param uid 自己的uid
             */
            void onJoinChannelResult(int result, String uid);
        ```

    -   离开频道结果回调

        回调名称：onLeaveChannelResult。

        ```
            /**
             * 退出房间回调
             * @param result 退出房间回调 0表示成功 反之失败
             */
            void onLeaveChannelResult(int result);
        ```

    -   音量大小提示

        回调名称：onSeatVolumeChanged。

        当某个用户说话状态改变是才会回调（从说话到不说话，或者从不说话到说话）。

        ```
            /**
             * 用户音量更新回调
             * @param seatIndex 麦序
             * @param isSpeaking 是否正在说话
             */
            void onSeatVolumeChanged(int seatIndex, boolean isSpeaking);
        ```

    -   伴奏播放回调

        回调名称：onAudioPlayingStateChanged。

        背景音乐播放状态的回调。

        ```
            /**
             * 播放状态更新回调
             *
             * @param audioPlayingStatus 当前播放状态
             */
            void onAudioPlayingStateChanged(AliRtcEngine.AliRtcAudioPlayingStateCode audioPlayingStatus);
        ```

    -   用户muteAudio通知回调

        回调名称：onUserAudioMuted。

        某个用户静音时回调该用户当前的麦序和静音状态。

        ```
            /**
             * 用户静音回调
             *
             * @param seatIndex 麦序
             * @param mute      是否静音
             */
            void onSeatMutedChanged(int seatIndex, boolean mute);
        ```

    -   房间被销毁回调

        回调名称：onRoomDestroy。

        ```
            /**
             * 房间被销毁回调
             */
            void onRoomDestroy();
        ```

    -   网络状态回调

        回调名称：onNetworkQualityChanged。

        ```
            /**
             * 网络状态回调
             *
             * @param aliRtcNetworkQuality1 下行网络质量
             * @param aliRtcNetworkQuality  上行网络质量
             * @param s                     String  用户ID
             */
            void onNetworkQualityChanged(String s, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality, AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality1);
        ```


