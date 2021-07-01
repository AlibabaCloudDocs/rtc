# Android集成

通过阅读本文，您可以了解视频互动直播Android端的集成操作。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   服务端已集成并开启。具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/视频互动直播/服务端集成.md)。
-   环境中已安装Android Studio 3.0或以上版本。更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已集成AliRTC Android SDK。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
2.  配置Demo工程。

    1.  打开Android Studio，单击**Open an Existing Project**，选择android目录下的RtcSolutionVideoLiveRoom文件夹。

    2.  打开RtcSolutionVideoLiveRoom/RTCVideoLiveRoom/RTCVideoLiveRoom\_Demo/src/main/java/com/aliyun/rtc/videoliveroom/constant/Constant.java文件。

        ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204677.png)

    3.  修改文件中的`API_URL`值。

        例如本地服务端IP地址为192.0.2.1，则`API_URL`的值为`http://192.0.2.1:8080/videoliveRoom`，即`API_URL="http://192.0.2.1:8080/videoliveRoom"`。本地服务端IP地址查询，请参见[查询IP地址]()。

        ![修改API_URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204852.png)

        **说明：**

        -   服务端IP地址禁止使用127.0.0.1。
        -   移动端和服务端处于同一局域网中。
        -   如果需要部署到正式环境，请绑定域名即`API_URL="http://<域名>/videoliveRoom"`。
    4.  验证移动端和服务端。

        分别在移动端和服务端浏览器中访问`API_URL`地址，如果显示如下图所示，表示移动端访问服务端正常。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204853.png)

3.  运行Demo。

    将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204857.png)

    **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。

4.  开启视频互动直播。

    1.  将2台或2台以上移动设备安装Demo App。

    2.  将设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间标题开始直播。

    4.  其余设备可在视频直播区看到该房间后，进入直播间观看。


## Demo目录结构说明

项目结构如下所示：

|文件名|说明|
|---|--|
|RTCVideoLiveRoom|视频互动直播功能实现库。更多信息，请参见[RTCVideoLiveRoom组件库目录说明](#section_gn1_ohk_7rv)。|
|RTCSolutionCommon|公共组建库。|
|RTCViewCommon|公共UI库。|
|app|程序入口。|
|thirdparty-lib|第三方库的引用。|

RTCVideoLiveRoom组件库目录说明，如下所示：

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
|[sharedInstance](#li_07a_57l_to9)|获取单例对象。|
|[destorySharedInstance](#li_n61_vcr_0yy)|毁单例对象。|
|[joinRoom](#li_gof_yks_tlp)|加入直播。|
|[leaveRoom](#li_lb6_c3d_5h2)|退出直播。|
|[setAudioEffectVolume](#li_suo_g8s_8pg)|设置音效音量。|
|[setAudioAccompanyVolume](#li_u5h_p3b_w3b)|设置伴奏音量。|
|[enterSeat](#li_zst_ghz_arl)|上麦。|
|[leavelSeat](#li_53z_598_92x)|下麦。|
|[enableEarBack](#li_vxt_isw_wst)|设置耳返。|
|[startAudioAccompany](#li_8ju_j0g_gek)|播放伴奏。|
|[stopAudioAccompany](#li_yby_0fy_ygs)|停止伴奏。|
|[playAudioEffect](#li_yfp_vny_61j)|播放音效。|
|[stopAudioEffect](#li_0sx_9k6_5oe)|停止音效。|
|[setAudioEffectReverbMode](#li_f73_mzx_ywk)|设置音效场景（混音模式）。|
|[setDelegate](#li_z5d_tp9_x3e)|设置监听。|
|[switchCamera](#li_79c_ri9_qm8)|翻转摄像头。|
|[setBeautyEffect](#li_5t2_mx8_eom)|设置美颜效果。|
|[getWhiteLevel](#li_axk_sjk_b5o)|获取美白等级。|
|[getSmoothLevel](#li_13q_r6c_nt2)|获取磨皮等级。|
|[createRoom](#li_lx7_yc4_g8y)|创建房间。|
|[destroyRoom](#li_0b6_r6i_xhl)|销毁房间。|
|[kickout](#li_suh_5pc_h29)|踢人。|
|[startCameraPreView](#li_czh_pwq_wyx)|本地预览。|
|[stopCameraPreView](#li_ion_u41_q27)|停止本地预览。|
|[startPlay](#li_gc8_6sd_hy3)|播放远端画面。|

|API|描述|
|---|--|
|[onEnterSeat](#li_ytw_l6u_lgw)|用户上麦通知。|
|[onLeaveSeat](#li_xby_ahu_9k3)|用户下麦通知。|
|[onOccurError](#li_zjz_55q_lec)|错误信息通知。|
|[onJoinChannelResult](#li_e08_9em_iz5)|加入频道结果回调。|
|[onLeaveChannelResult](#li_fis_uaq_lkm)|离开频道结果回调。|
|[onRoomDestroy](#li_9d2_5z5_t82)|房间被销毁的回调。|
|[onAudioPlayingStateChanged](#li_hrl_ov9_fix)|伴奏播放回调。|
|[onNetworkQualityChanged](#li_9ct_dl8_1sl)|网络状态回调。|
|[onKickedOut](#li_r2p_dh0_ycr)|被踢出房间的回调。|

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

-   joinRoom：加入房间。

    观众端调用，通过房间号等信息获取播放链接并播放旁路流。

    ```
        /**
         * 加入直播
         *
         * @param channelId 房间号
         * @param view  画面载体
         * @param userId uid
         * @param userName 昵称
         */
        public abstract void joinRoom(String channelId, String userId, String userName, SurfaceView view);
    ```

-   leaveRoom：离开房间。

    观众端调用，离开房间。

    ```
         /**
         * 退出房间
         */
        public abstract void leaveRoom();
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

-   setDelegate：设置监听。

    ```
        /**
         * 设置rtc监听
         *
         * @param audioLiveRoomDelegate 监听
         */
        public abstract void setDelegate(RTCVideoLiveRoomDelegate audioLiveRoomDelegate);
    ```

-   switchCamera：翻转摄像头。

    ```
        /**
         * 翻转摄像头
         */
        public abstract void switchCamera();
    ```

-   setBeautyEffect：设置美颜效果。

    ```
        /**
         * 设置美颜等级
         */
        public abstract void setBeautyEffect(float whiteLevel, float smoothLevel);
    ```

-   getWhiteLevel：获取美白等级。

    ```
        /**
         * 获取当前美白等级
         */
        public abstract float getWhiteLevel();
    ```

-   getSmoothLevel：获取磨皮等级。

    ```
        /**
         * 获取当前磨皮等级
         */
        public abstract float getSmoothLevel();
    ```

-   createRoom：创建房间。

    主播调用，创建RTC频道并加入。

    ```
        /**
         * 创建房间
         * @param channelId 房间号
         * @param userId uid
         * @param userName  用户名
         */
        public abstract void createRoom(String channelId, String userId, String userName);
    ```

-   destroyRoom：销毁房间。

    主播调用，销毁RTC频道并退出。

    ```
        /**
         * 销毁房间
         */
        public abstract void destroyRoom();
    ```

-   kickout：踢人。

    主播调用，将连麦观众都踢下线。

    ```
        /**
         * 踢人（主播才可以踢人）
         */
        public abstract void kickOut();
    ```

-   startCameraPreView：本地预览。

    ```
        /**
         * 预览本地摄像头画面
         * @param viewGroup 播放画面的载体
         */
        public abstract void startCameraPreView(ViewGroup viewGroup);
    ```

-   stopCameraPreView：停止本地预览。

    ```
        /**
         * 停止预览本地摄像头画面
         */
        public abstract void stopCameraPreview();        
    ```

-   startPlay：播放远端画面。

    ```
        /**
         * 播放远端流
         * @param uid 用户id
         * @param viewGroup 播放画面的载体
         */
        public abstract void startPlay(String uid, ViewGroup viewGroup);
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

    ```
        /**
         * sdk报错,需要销毁实例
         */
        void onOccurError(int error);
    ```

-   onJoinChannelResult：创建房间的回调。

    ```
        /**
         * 创建房间的回调
         * @param result 0为成功 反之失败
         */
        void onJoinChannelResult(int result);
    ```

-   onLeaveChannelResult：退出房间的回调。

    ```
        /**
         * 退出房间回调
         */
        void onLeaveChannelResult(int result);
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

-   onRoomDestroy：房间被销毁回调。

    ```
        /**
         * 房间被销毁回调
         */
        void onRoomDestroy();
    ```

-   onNetworkQualityChanged：网络质量变化时回调。

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

-   onKickedOut：被踢出房间的回调。

    ```
        /**
         * 被踢出房间
         */
        void onKickOuted();
    ```


