# Android集成

您可以阅读本文，了解Android端视频互动直播的集成操作。

## 前提条件

-   开发环境符合Android SDK使用限制。详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。
-   已经集成并启动服务端。详情请参见[服务端集成](/cn.zh-CN/解决方案/视频互动直播/服务端集成.md)。

## Demo运行指引

**说明：** 您在集成Android端时，如果遇到Demo体验过程中出现无法创建房间或通话等问题，请参见[Android端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcVideoLiveRoom-demo)并解压。

    解压成功之后如下图所示：

    ![解压目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3524688061/p204678.png)

    **说明：**

    -   Demo源码中已经集成AliRTC SDK。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  在Android Studio打开Android端工程。

    打开**Android Studio**，单击**Open an existing Android Studio project**并选择android目录下的RtcSolutionVideoLiveRoom文件夹。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180032.png)

3.  修改配置文件。

    1.  打开Android Studio，在Demo中找到RtcSolutionVideoLiveRoom/RTCVideoLiveRoom/RTCVideoLiveRoom\_Demo/src/main/java/com/aliyun/rtc/videoliveroom/constant/Constant.java文件。

        ![配置文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204677.png)

    2.  修改文件中的`API_URL`变量，如：`http://<服务器IP> :端口:8080/videoliveRoom`，部署到正式环境上建议绑定域名并使用：`http://<域名>/videoliveRoom`。

        示例

        假设本地IP为192.0.2.1，那么`API_URL="http://192.0.2.1:8080/videoliveRoom"`。本地IP查询，请参见[查询IP地址]()。

        ![修改API_URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204852.png)

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机端和电脑端浏览器验证。

        在浏览器中输入正确的URL（`API_URL`变量）地址，看到**videoliveRoom!**表示IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204853.png)

4.  选择一台已连接的真机设备。（暂不支持模拟器运行）

    将一台Android设备（需在系统设置中开启开发者模式和USB调试功能）使用数据线与电脑连接，在手机端同意调试后在Android Studio中选择接入的设备。

5.  单击**build and run**编译，Android设备会安装并启动视频互动直播App。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204857.png)

6.  开启视频互动直播。

    1.  将2台或2台以上移动设备（Android或iOS）安装Demo App。

    2.  将设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间标题开始直播。

    4.  其余设备可在视频直播区看到该房间后，进入直播间观看。


## Demo源码解析

1.  项目结构说明。

    -   RTCVideoLiveRoom：视频直播连麦功能实现库。
    -   RTCSolutionCommon：公共组建库。
    -   RTCViewCommon：公共UI库。
    -   app：程序入口。
    -   thirdparty-lib：第三方库的引用。
    ![项目结构](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p205139.png)

    -   adapter：列表控件adapter。
    -   bean：实体类。
    -   Constant：常量数据管理类，在这配置Server端请求域名和分享链接的域名。
    -   api：网络请求。
    -   rtc：RTC。
    -   ui：放的互动界面和登录界面。
    -   util：工具类。
    -   view：自定义view。
    ![目录结构](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p205140.png)

2.  功能实现流程。

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_07a_57l_to9)|获取单例对象|
    |[destorySharedInstance](#li_n61_vcr_0yy)|毁单例对象|
    |[joinRoom](#li_gof_yks_tlp)|加入直播|
    |[leaveRoom](#li_lb6_c3d_5h2)|退出直播|
    |[setAudioEffectVolume](#li_suo_g8s_8pg)|设置音效音量|
    |[setAudioAccompanyVolume](#li_u5h_p3b_w3b)|设置伴奏音量|
    |[enterSeat](#li_zst_ghz_arl)|上麦|
    |[leavelSeat](#li_53z_598_92x)|下麦|
    |[enableEarBack](#li_vxt_isw_wst)|设置耳返|
    |[startAudioAccompany](#li_8ju_j0g_gek)|播放伴奏|
    |[stopAudioAccompany](#li_yby_0fy_ygs)|停止伴奏|
    |[playAudioEffect](#li_yfp_vny_61j)|播放音效|
    |[stopAudioEffect](#li_0sx_9k6_5oe)|停止音效|
    |[setAudioEffectReverbMode](#li_f73_mzx_ywk)|设置音效场景（混音模式）|
    |[setDelegate](#li_z5d_tp9_x3e)|设置监听|
    |[switchCamera](#li_79c_ri9_qm8)|翻转摄像头|
    |[setBeautyEffect](#li_5t2_mx8_eom)|设置美颜效果|
    |[getWhiteLevel](#li_axk_sjk_b5o)|获取美白等级|
    |[getSmoothLevel](#li_13q_r6c_nt2)|获取磨皮等级|
    |[createRoom](#li_lx7_yc4_g8y)|创建房间|
    |[destroyRoom](#li_0b6_r6i_xhl)|销毁房间|
    |[kickout](#li_suh_5pc_h29)|踢人|
    |[startCameraPreView](#li_czh_pwq_wyx)|本地预览|
    |[stopCameraPreView](#li_ion_u41_q27)|停止本地预览|
    |[startPlay](#li_gc8_6sd_hy3)|播放远端画面|

    事件回调

    |API|描述|
    |---|--|
    |[onEnterSeat](#li_ytw_l6u_lgw)|用户上麦通知|
    |[onLeaveSeat](#li_xby_ahu_9k3)|用户下麦通知|
    |[onOccurError](#li_zjz_55q_lec)|错误信息通知|
    |[onJoinChannelResult](#li_e08_9em_iz5)|加入频道结果回调|
    |[onLeaveChannelResult](#li_fis_uaq_lkm)|离开频道结果回调|
    |[onRoomDestroy](#li_9d2_5z5_t82)|房间被销毁的回调|
    |[onAudioPlayingStateChanged](#li_hrl_ov9_fix)|伴奏播放回调|
    |[onNetworkQualityChanged](#li_9ct_dl8_1sl)|网络状态回调|
    |[onKickedOut](#li_r2p_dh0_ycr)|被踢出房间的回调|

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

        接口名称：joinRoom。

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

    -   离开房间

        接口名称：leaveRoom。

        观众端调用，离开房间。

        ```
             /**
             * 退出房间
             */
            public abstract void leaveRoom();
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

    -   设置监听

        接口名称：setDelegate。

        ```
            /**
             * 设置rtc监听
             *
             * @param audioLiveRoomDelegate 监听
             */
            public abstract void setDelegate(RTCVideoLiveRoomDelegate audioLiveRoomDelegate);
        ```

    -   翻转摄像头

        接口名称：switchCamera。

        ```
            /**
             * 翻转摄像头
             */
            public abstract void switchCamera();
        ```

    -   设置美颜效果

        接口名称：setBeautyEffect。

        ```
            /**
             * 设置美颜等级
             */
            public abstract void setBeautyEffect(float whiteLevel, float smoothLevel);
        ```

    -   获取美白等级

        接口名称：getWhiteLevel。

        ```
            /**
             * 获取当前美白等级
             */
            public abstract float getWhiteLevel();
        ```

    -   获取磨皮等级

        接口名称：getSmoothLevel。

        ```
            /**
             * 获取当前磨皮等级
             */
            public abstract float getSmoothLevel();
        ```

    -   创建房间

        接口名称：createRoom。

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

    -   销毁房间

        接口名称：destroyRoom。

        主播调用，销毁RTC频道并退出。

        ```
            /**
             * 销毁房间
             */
            public abstract void destroyRoom();
        ```

    -   踢人

        接口名称：kickout。

        主播调用，将连麦观众都踢下线。

        ```
            /**
             * 踢人（主播才可以踢人）
             */
            public abstract void kickOut();
        ```

    -   本地预览

        接口名称：startCameraPreView。

        ```
            /**
             * 预览本地摄像头画面
             * @param viewGroup 播放画面的载体
             */
            public abstract void startCameraPreView(ViewGroup viewGroup);
        ```

    -   停止本地预览

        接口名称：stopCameraPreView。

        ```
            /**
             * 停止预览本地摄像头画面
             */
            public abstract void stopCameraPreview();        
        ```

    -   播放远端画面

        接口名称：startPlay。

        ```
            /**
             * 播放远端流
             * @param uid 用户id
             * @param viewGroup 播放画面的载体
             */
            public abstract void startPlay(String uid, ViewGroup viewGroup);
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

        ```
            /**
             * sdk报错,需要销毁实例
             */
            void onOccurError(int error);
        ```

    -   创建房间的回调

        回调名称：onJoinChannelResult。

        ```
            /**
             * 创建房间的回调
             * @param result 0为成功 反之失败
             */
            void onJoinChannelResult(int result);
        ```

    -   退出房间的回调

        回调名称：onLeaveChannelResult。

        ```
            /**
             * 退出房间回调
             */
            void onLeaveChannelResult(int result);
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

    -   房间被销毁回调

        回调名称：onRoomDestroy。

        ```
            /**
             * 房间被销毁回调
             */
            void onRoomDestroy();
        ```

    -   网络质量变化时回调

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

    -   被踢出房间的回调

        回调名称：onKickedOut。

        ```
            /**
             * 被踢出房间
             */
            void onKickOuted();
        ```


