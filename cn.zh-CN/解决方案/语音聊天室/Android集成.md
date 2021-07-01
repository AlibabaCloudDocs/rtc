# Android集成

通过阅读本文，您可以了解语音聊天室Android端的集成操作。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   服务端已集成并开启。具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/语音聊天室/服务端集成.md)。
-   环境中已安装Android Studio 3.0或以上版本。更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已通过Maven方式集成AliRTC Android SDK（1.18版本）。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
2.  配置Demo工程。

    1.  打开Android Studio，单击**Open an Existing Project**，选择android文件夹。

    2.  打开android/RTCAudioLiveRoom/RTCAudioLiveRoom\_Demo/src/main/java/com/aliyun/rtc/audiochatroom/constant/Constant.java文件。

        ![打开配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200493.png)

    3.  修改文件中的`BASE_URL`值。

        例如本地服务端IP地址为192.0.2.1，则`BASE_URL`的值为`http://192.0.2.1:8080/chatroom`，即`BASE_URL="http://192.0.2.1:8080/chatroom"`。本地服务端IP地址查询，请参见[查询IP地址]()。

        ![修改BASE_URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200495.png)

        **说明：**

        -   服务端IP地址禁止使用127.0.0.1。
        -   移动端和服务端处于同一局域网中。
        -   如果需要部署到正式环境，请绑定域名即`BASE_URL="http://<域名>/chatroom"`。
    4.  验证移动端和服务端。

        分别在移动端和服务端浏览器中访问`BASE_URL`地址，如果显示如下图所示，表示移动端访问服务端正常。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200442.png)

3.  运行Demo。

    将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5950208061/p200584.png)

    **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。

4.  加入语音聊天室。

    1.  将2台或2台以上移动端设备安装Demo App。

    2.  将设备连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间号和昵称，选择角色进入语聊房并等待他人加入。

    4.  在其余设备上输入相同房间号和任意昵称（可同名，不做限制），选择角色加入房间并进行聊天。


## Demo目录结构说明

项目结构如下所示：

|文件名|说明|
|---|--|
|RTCAudioLiveRoom|语音聊天室功能实现库。更多信息，请参见[RTCAudioLiveRoom组件库目录说明](#p_csu_l5b_mmw)。|
|RTCSolutionCommon|公共组建库。|
|RTCViewCommon|公共UI库。|
|app|程序入口。|
|thirdparty-lib|第三方库的引用。|

RTCAudioLiveRoom组件库目录说明，如下所示：

|文件名|说明|
|---|--|
|adapter|列表控件adapter。|
|bean|实体类。|
|constant|常量数据管理类，在此配置服务端请求域名和分享链接的域名。|
|api|网络请求。|
|rtc|RTC。|
|ui|互动界面和登录界面。|
|util|工具类。|
|view|自定义view。|

## API说明

|API|描述|
|---|--|
|[sharedInstance](#li_n7p_k2s_uer)|获取单例对象。|
|[destorySharedInstance](#li_nft_wmt_5zn)|毁单例对象。|
|[login](#li_p7g_28q_vms)|加入房间。|
|[logout](#li_m4c_sja_kye)|退出房间。|
|[setAudioEffectVolume](#li_x3q_9po_mm3)|设置音效音量。|
|[setAudioAccompanyVolume](#li_66k_o3c_cd7)|设置伴奏音量。|
|[enterSeat](#li_j1l_npk_vtf)|上麦。|
|[leavelSeat](#li_qm7_00y_2ob)|下麦。|
|[setRTCAudioLiveRoomDelegate](#li_d3d_b96_ztn)|设置监听回调。|
|[muteLocalMic](#li_xry_0fu_u6z)|设置是否静音。|
|[muteRomteAudioPlaying](#li_a33_n3s_d1n)|设置是否本地静音。|
|[enableEarBack](#li_i1z_vg6_nhg)|是否开启耳返。|
|[startAudioAccompany](#li_f6k_xmd_0e1)|播放伴奏。|
|[stopAudioAccompany](#li_fdu_xah_7ry)|停止伴奏。|
|[playAudioEffect](#li_hgz_grj_ecr)|播放音效。|
|[stopAudioEffect](#li_5v0_4op_stx)|停止音效。|
|[setAudioEffectReverbMode](#li_gy8_s2e_14z)|设置音效场景（混音模式）。|
|[setAudioEffectVoiceChangerMode](#li_ieg_tax_wku)|设置变声音效模式。|

|API|描述|
|---|--|
|[onEnterSeat](#li_gg1_u4j_ufe)|用户上麦通知。|
|[onLeaveSeat](#li_adk_6tx_2rv)|用户下麦通知。|
|[onOccurError](#li_uzm_4cb_995)|错误信息通知。|
|[onUpdateRoleNotify](#li_mj9_qfv_0pz)|切换用户角色回调。|
|[onPublishChangedNotify](#li_ptq_9kt_bg5)|推流回调。|
|[onJoinChannelResult](#li_d9d_pxa_yby)|加入频道结果回调。|
|[onLeaveChannelResult](#li_l3w_7ts_m8o)|离开频道结果回调。|
|[onSeatVolumeChanged](#li_gkr_auk_7x7)|音量大小提示。|
|[onAudioPlayingStateChanged](#li_4sg_tq8_xf2)|伴奏播放回调。|
|[onUserAudioMuted](#li_z2g_g8j_jgs)|用户muteAudio通知回调。|
|[onRoomDestroy](#li_ebp_tpu_fqi)|房间被销毁回调。|
|[onNetworkQualityChanged](#li_dne_r13_nx5)|网络状态回调。|

功能实现接口

-   sharedInstance：获取单例对象。

    获取BaseRTCAudioLiveRoom的实例对象，初始化RTC SDK。

    ```
        /**
         * 获取单例
         */
        public static BaseRTCAudioLiveRoom sharedInstance() {
            return RTCAudioLiveRoomImpl.sharedInstance();
        }
    ```

-   destorySharedInstance：毁单例对象。

    销毁BaseRTCAudioLiveRoom的实例对象，销毁后需要再调用sharedInstance接口再次初始化实例。

    ```
        /**
         * 销毁实例
         */
        public abstract void destorySharedInstance();
    ```

-   login：加入房间。

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

-   logout：退出房间。

    退出RTC频道。

    ```
        /**
         * 退出房间
         */
        public abstract void logout();
    ```

-   setAudioEffectVolume：设置音效音量。

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

-   setAudioAccompanyVolume：设置伴奏音量。

    同时设置播放和推流的音量。

    ```
        /**
         * 设置伴奏音量
         * @param volume 音量 区间0-100
         */
        public abstract void setAudioAccompanyVolume(int volume);
    ```

-   enterSeat：上麦。

    切换互动角色。

    ```
        /**
         * 上麦
         */
        public abstract void enterSeat();
    ```

-   leavelSeat：下麦。

    切换观众角色。

    ```
        /**
         * 下麦
         */
        public abstract void leaveSeat();
    ```

-   setRTCAudioLiveRoomDelegate：设置监听回调。

    ```
            /**
         * 设置监听
         *
         * @param audioLiveRoomDelegate 监听
         */
        public abstract void setRTCAudioLiveRoomDelegate(RTCAudioLiveRoomDelegate audioLiveRoomDelegate);        
    ```

-   muteLocalMic：设置是否静音。

    ```
        /**
         * 是否开启静音模式
         *
         * @param mute true为静音 false不静音
         * @return 0表示设置成功，反之失败
         */
        public abstract int muteLocalMic(boolean mute);
    ```

-   muteRomteAudioPlaying：设置是否本地静音。

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

-   enableEarBack：是否开启耳返。

    ```
        /**
         * 是否耳返
         *
         * @param enableEarBack 是否开启耳返 true为开启 false关闭
         * @return 0表示设置成功，反之失败
         */
        public abstract int enableEarBack(boolean enableEarBack);
    ```

-   startAudioAccompany：播放伴奏。

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

-   stopAudioAccompany：停止伴奏。

    ```
        /**
         * 停止伴奏
         */
        public abstract void stopAudioAccompany();
    ```

-   playAudioEffect：播放音效。

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

-   stopAudioEffect：停止音效。

    ```
        /**
         * 停止音效
         *
         * @param soundId 音效ID
         */
        public abstract void stopAudioEffect(int soundId);
    ```

-   setAudioEffectReverbMode：设置音效场景（混音模式）。

    ```
        /**
         * 设置音效场景
         * @param aliRtcAudioEffectReverbMode 音效场景枚举
         */
        public abstract void setAudioEffectReverbMode(AliRtcEngine.AliRtcAudioEffectReverbMode aliRtcAudioEffectReverbMode);
    ```

-   setAudioEffectVoiceChangerMode：设置变声音效模式。

    ```
        /**
         * 设置变声音效模式
         *
         * @param mode 模式
         * @return int 结果码 0为成功
         */
        public abstract int setAudioEffectVoiceChangerMode(AliRtcEngine.AliRtcAudioEffectVoiceChangerMode mode);
    ```


回调接口

-   onEnterSeat：用户上麦通知。

    ```
        /**
         * 上麦通知回调
         *
         * @param seatInfo 麦位信息
         */
        void onEnterSeat(SeatInfo seatInfo);
    ```

-   onLeaveSeat：用户下麦通知。

    ```
        /**
         * 下麦通知回调
         *
         * @param seatInfo 麦位信息
         */
        void onLeaveSeat(SeatInfo seatInfo);
    ```

-   onOccurError：错误信息通知。

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

-   onUpdateRoleNotify：切换用户角色回调。

    ```
        /**
         * 角色切换成功
         *
         * @param oldRole 旧的用户角色
         * @param newRole 新的用户角色
         */
        void onUpdateRoleNotify(AliRtcEngine.AliRTCSDK_Client_Role oldRole, AliRtcEngine.AliRTCSDK_Client_Role newRole);
    ```

-   onPublishChangedNotify：推流回调。

    ```
        /**
         * 推流结果回调
         * @param result 返回码 0表示推流成功，反之失败
         * @param isPublished 是否再推流
         */
        void onPublishChangedNotify(int result, boolean isPublished);
    ```

-   onJoinChannelResult：加入频道结果回调。

    result为0表示加入房间成功，反之失败。

    ```
        /**
         * 登录回调
         *
         * @param result 状态码
         * @param uid 自己的uid
         */
        void onJoinChannelResult(int result, String uid);
    ```

-   onLeaveChannelResult：离开频道结果回调。

    ```
        /**
         * 退出房间回调
         * @param result 退出房间回调 0表示成功 反之失败
         */
        void onLeaveChannelResult(int result);
    ```

-   onSeatVolumeChanged：音量大小提示。

    当某个用户说话状态改变是才会回调（从说话到不说话，或者从不说话到说话）。

    ```
        /**
         * 用户音量更新回调
         * @param seatIndex 麦序
         * @param isSpeaking 是否正在说话
         */
        void onSeatVolumeChanged(int seatIndex, boolean isSpeaking);
    ```

-   onAudioPlayingStateChanged：伴奏播放回调。

    背景音乐播放状态的回调。

    ```
        /**
         * 播放状态更新回调
         *
         * @param audioPlayingStatus 当前播放状态
         */
        void onAudioPlayingStateChanged(AliRtcEngine.AliRtcAudioPlayingStateCode audioPlayingStatus);
    ```

-   onUserAudioMuted：用户muteAudio通知回调。

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

-   onRoomDestroy：房间被销毁回调。

    ```
        /**
         * 房间被销毁回调
         */
        void onRoomDestroy();
    ```

-   onNetworkQualityChanged：网络状态回调。

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


