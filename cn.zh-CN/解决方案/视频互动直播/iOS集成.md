# iOS集成

您可以阅读本文，了解iOS端视频互动直播的集成操作。

## 前提条件

-   开发环境符合iOS SDK使用限制。详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。
-   已经集成并启动服务端。详情请参见[服务端集成](/cn.zh-CN/解决方案/视频互动直播/服务端集成.md)。

**说明：** 您需要持有Apple开发证书或个人账号。

## Demo运行指引

**说明：**

您在集成iOS端时，如果遇到问题，或者Demo体验过程中出现无法创建房间或通话等问题，请参见[iOS端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcVideoLiveRoom-demo)并解压。

    解压成功之后如下图所示：

    ![解压目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3524688061/p204678.png)

    **说明：**

    -   Demo源码中已经集成AliRTC SDK。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  修改配置文件。

    1.  打开解压后的Demo文件夹alibabacloud-AliRtcVideoLiveRoom-demo-master，找到iOS/RTCSolution/RTCCommon/⁨AppConfig.h⁩文件。

    2.  修改文件中的变量。

        -   修改`kBaseUrl`变量，如：`http://<服务器IP> :8080/`，部署到正式环境上建议绑定域名并使用：`http://<域名>/`。
        -   修改`kProject_VideoRoom`变量，修改为`videoliveRoom`。
        示例

        假设本地IP为192.0.2.1，那么`kBaseUrl="http://192.0.2.1:8080/"`。本地IP查询，请参见[查询IP地址]()。

        ![修改变量](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6934688061/p204880.png)

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机和电脑的浏览器验证。

        在浏览器中输入正确的URL（`http://<服务器IP> :8080/videoliveRoom`）地址，看到**videoliveRoom!**表示IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4524688061/p204853.png)

3.  导入Demo源码。

    打开**Xcode**，单击**Open a project or file**，双击打开iOS/RTCSolution目录下的RTCSolution.xcworkspace文件。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6934688061/p204988.png)

4.  选择运行Target为RTCSolution，将一台iOS设备设备使用数据线与电脑链接，在**Xcode**中选择相应的设备，设备在设置中打开开发者模式。（暂不支持模拟器运行）

    ![Target选择](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6934688061/p204987.png)

5.  修改Bundle Identifier。

    **说明：** Bundle Identifier改成为`com.<公司名>.<项目名>`，避免由于Bundle已被注册从而运行失败。

    **General**选项卡中修改Bundle Identifier。

    ![修改General](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6934688061/p204989.png)

    **Sign & Capabilities**选项卡中修改Bundle Identifier。

    ![修改Sign](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6934688061/p204991.png)

6.  在**Sign & Capabilities**选项卡，勾选**Automatically manage signing**，在下方选择自己的**Team**。

    1.  选择**Team**。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

    2.  若以前没添加过账号，单击**Add an Account**添加。

        ![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184855.png)

    3.  完成账号添加。

        ![添加Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3457036061/p184858.png)

    4.  在Team里选择新创建的账号即可，并且在完成签名后确保下方没有报错提示。

7.  单击**build and run**按钮编译。

    ![编译](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7934688061/p204986.png)

8.  开启视频互动直播。

    1.  将2台或2台以上移动设备（Android或iOS）安装Demo App。

    2.  将设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间标题开始直播。

    4.  其余设备可在视频直播区看到该房间后，进入直播间观看。


## Demo源码解析

1.  项目结构说明

    -   阿里云RTC把业务代码封装到RTCVideoLiveRoom的库当中，RTCVideoLiveRoom就可以像一个本地的第三方库一样，可以移植到其他项目中，只需在Podfile中指定RTCVideoLiveRoom库的路径即可。如下所示：

        ```
         pod 'RTCVideoLiveRoom', :path => 'RTCVideoLiveRoom'
            ##   pod 'RTCVideoLiveRoom'  说明项目依赖RTCVideoLiveRoom库
            ##   path => 'RTCVideoLiveRoom'  指明RTCVideoLiveRoom库的位置（podfile文件路径）
        ```

    -   RTCVideoLiveRoom组件库目录

        |文件名|说明|
        |---|--|
        |RTCVideoLiveRoom.podspec|组件的描述文件。|
        |RTCVideoLiveRoom.bundle|存放资源的bundle。|
        |RTC|RTC相关功能的封装（建议直接复用）。|
        |UI|UI相关文件。|

2.  功能实现流程

    接口

    |API|描述|
    |---|--|
    |[sharedInstance](#li_hfw_w86_3do)|获取单例对象|
    |[destorySharedInstance](#li_18n_tz0_rxu)|毁单例对象|
    |[joinRoom](#li_lgd_0nc_0ah)|加入直播|
    |[leaveRoom](#li_a5q_6do_5xz)|退出直播|
    |[setAudioEffectVolume](#li_8hd_4b1_mtb)|设置音效音量|
    |[setAudioAccompanyVolume](#li_ipr_m8q_cgj)|设置伴奏音量|
    |[enterSeat](#li_x5w_ekh_hmc)|上麦|
    |[leavelSeat](#li_4of_od1_2hd)|下麦|
    |[enableEarBack](#li_l3b_m1q_vfp)|设置耳返|
    |[startAudioAccompany](#li_nch_rw2_msc)|播放伴奏|
    |[stopAudioAccompany](#li_3kj_kcu_ouj)|停止伴奏|
    |[playAudioEffect](#li_ghf_mqf_ot7)|播放音效|
    |[stopAudioEffect](#li_inh_lgb_lto)|停止音效|
    |[setAudioEffectReverbMode](#li_yc9_vz8_n2u)|设置音效场景（混音模式）|
    |[setDelegate](#li_vnm_w8o_lj6)|设置监听|
    |[switchCamera](#li_ypm_hcm_6cb)|翻转摄像头|
    |[setWhiteLevel](#li_tr8_z6i_va4)|设置美白效果|
    |[setSmoothLevel](#li_686_ybr_5ii)|设置磨皮效果|
    |[getWhiteLevel](#li_bu6_0cc_ib2)|获取美白等级|
    |[getSmoothLevel](#li_yg8_mld_two)|获取磨皮等级|
    |[createRoom](#li_fo1_jm8_rh6)|创建房间|
    |[destroyRoom](#li_d4o_7r1_fpu)|销毁房间|
    |[kickout](#li_ejj_pq7_c7m)|踢人|
    |[startCameraPreView](#li_9ru_2bf_4dk)|本地预览|
    |[stopCameraPreView](#li_wp7_62j_r6n)|停止本地预览|
    |[startPlay](#li_go5_uvu_zqd)|播放远端画面|

    事件回调

    |API|描述|
    |---|--|
    |[onEnterSeat](#li_mod_03e_2ny)|用户上麦通知|
    |[onLeaveSeat](#li_6kb_2kd_7dw)|用户下麦通知|
    |[onOccurError](#li_lr1_o0u_xce)|错误信息通知|
    |[onJoinChannelResult](#li_ds1_t4e_ivo)|加入频道结果回调|
    |[onLeaveChannelResult](#li_qs1_jkm_i5z)|离开频道结果回调|
    |[onRoomDestroy](#li_uzx_pvd_q59)|房间被销毁的回调|
    |[onAudioPlayingStateChanged](#li_ua8_yqw_g5x)|伴奏播放回调|
    |[onNetworkQualityChanged](#li_a89_3ka_wvo)|网络状态回调|
    |[onKickedOut](#li_uxt_i8i_1ma)|被踢出房间的回调|

    接口示例

    -   获取单例对象

        接口名称：sharedInstance。

        获取BaseRTCAudioLiveRoom的实例对象，初始化RTC SDK。

        ```
        /// @brief 获取单例
        /// @return RTCAudioliveRoomManager 单例对象
        + (RTCVideoliveRoom *) sharedInstance;
        ```

    -   毁单例对象

        接口名称：destorySharedInstance。

        销毁BaseRTCAudioLiveRoom的实例对象，销毁后需要再调用sharedInstance接口再次初始化实例。

        ```
        /// 销毁RTCSDK
        - (void)destroySharedInstance;
        ```

    -   加入房间

        接口名称：joinRoom。

        观众端调用，通过房间号等信息获取播放链接并播放旁路流。

        ```
        /// 加入房间
        /// @param channelId  频道
        /// @param userId 观众id
        /// @param userName 观众昵称
        /// @param preview 预览view
        /// @param handler 回调
        - (void)joinRoom:(NSString *)channelId
                  userId:(NSString *)userId
                userName:(NSString *)userName
                 preview:(UIView *)preview
                complete:(void(^)(NSInteger result))handler;
        ```

    -   离开房间

        接口名称：leaveRoom。

        观众端调用，离开房间。

        ```
        /// 观众调用 退出直播
        /// @param handler 回调
        - (void)leaveRoom:(void(^)(NSInteger result))handler;
        ```

    -   设置音效音量

        接口名称：setAudioEffectVolume。

        同时设置播放和推流的音量。

        ```
        /// 设置音效的音量
        /// @param soundId 音效id
        /// @param volume 音量 0~100
        - (int)setAudioEffectVolumeWithSoundId:(NSInteger)soundId
                                        volume:(NSInteger)volume;
        ```

    -   设置伴奏音量

        接口名称：setAudioAccompanyVolume。

        同时设置播放和推流的音量。

        ```
        /// 设置背景音乐音量
        /// @param volume 音量 0~100
        - (int)setAudioAccompanyVolume:(NSInteger)volume;
        ```

    -   上麦

        接口名称：enterSeat。

        切换互动角色。

        ```
        /// 上麦
        /// @param handler 回调
        - (void)enterSeat:(void(^)(NSInteger result))handler;
        ```

    -   下麦

        接口名称：leavelSeat。

        切换观众角色。

        ```
        /// 下麦
        /// @param handler 回调
        - (void)leaveSeat:(void(^)(NSInteger result))handler;
        ```

    -   是否开启耳返

        接口名称：enableEarBack。

        ```
        /// 是否开启耳返
        /// @param enable YES/NO
        - (int)enableEarBack:(BOOL)enable;
        ```

    -   播放伴奏

        接口名称：startAudioAccompany。

        ```
        /// 播放背景音乐
        /// @param filePath 文件路径
        /// @param publish 是否推送远端
        - (int)startAudioAccompanyWithFile:(NSString *)filePath
                                   publish:(BOOL)publish;
        ```

    -   停止伴奏

        接口名称：stopAudioAccompany。

        ```
        /// 停止播放背景音乐
        - (int)stopAudioAccompany;
        ```

    -   播放音效

        接口名称：playAudioEffect。

        ```
        /// 播放音效
        /// @param soundId 音效id
        /// @param filePath 资源路径
        /// @param publish 是否推送远端
        - (int)playEffectSoundtWithSoundId:(NSInteger)soundId
                                  filePath:(NSString *)filePath
                                   publish:(BOOL)publish;
        ```

    -   停止音效

        接口名称：stopAudioEffect。

        ```
        /// 停止播放音效
        /// @param soundId 音效id
        - (int)stopAudioEffectWithSoundId:(NSInteger)soundId;
        ```

    -   设置音效场景（混音模式）

        接口名称：setAudioEffectReverbMode。

        ```
        /// 设置音效混响模式
        /// @param mode 混响模式
        - (int)setAudioEffectReverbMode:(AliRtcAudioEffectReverbMode)mode;
        ```

    -   设置监听

        接口名称：setDelegate。

        ```
         - (void)setDelegate:(id<RTCVideoliveRoomDelegate> _Nullable)delegate;
        ```

    -   翻转摄像头

        接口名称：switchCamera。

        ```
        /// 切换摄像头
        - (void)switchCamera;
        ```

    -   设置美白效果

        接口名称：setWhiteLevel。

        ```
        - (void)setWhiteLevel:(NSInteger)whiteLevel;
        ```

    -   设置磨皮效果

        接口名称：setSmoothLevel。

        ```
        - (void)setSmoothLevel:(NSInteger)smoothLevel;
        ```

    -   获取美白等级

        接口名称：getWhiteLevel。

        ```
        -(NSInteger)whiteLevel;
        ```

    -   获取磨皮等级

        接口名称：getSmoothLevel。

        ```
        - (NSInteger)smoothLevel;
        ```

    -   创建房间

        接口名称：createRoom。

        主播调用，创建RTC频道并加入。

        ```
        /// 加入频道
        /// @param channelId   频道名称
        /// @param userName   任意用于显示的用户名称。不是User ID
        /// @param userId   角色
        /// @param handler   回调
        - (void)createRoom:(NSString *)channelId
                  userName:(NSString *)userName
                    userId:(NSString *)userId
                  complete:(void(^)(AliRtcAuthInfo *authInfo,
                                    NSInteger errorCode))handler;
        ```

    -   销毁房间

        接口名称：destroyRoom。

        主播调用，销毁RTC频道并退出。

        ```
        /// 主播调用 销毁房间
        /// @param handler 回调
        - (void)destroyRoom:(void(^)(NSInteger result))handler;
        ```

    -   踢人

        接口名称：kickout。

        主播调用，将连麦观众都踢下线。

        ```
        /// 踢出房间的其他用户
        /// @param handler 回调
        - (void)kickout:(void(^)(NSInteger result))handler;
        ```

    -   本地预览

        接口名称：startCameraPreView。

        ```
        /// 开启本地预览
        /// @param preview 预览View
        - (void)startCameraPreView:(UIView *)preview;
        ```

    -   停止本地预览

        接口名称：stopCameraPreView。

        ```
        /// 停止本地预览
        - (void)stopCameraPreview;
        ```

    -   播放远端画面

        接口名称：startPlay。

        ```
        /// 播放远端画面
        /// @param preview     预览的view
        /// @param userId  对方的userId
        - (void)startPlay:(UIView *)preview
                   userId:(NSString *)userId;
        ```

    回调通知

    -   用户上麦通知

        回调名称：onEnterSeat。

        ```
        /// 远端用户上麦通知
        /// @param userId 麦序
        - (void)onEnterSeat:(NSString *)userId;
        ```

    -   用户下麦通知

        回调名称：onLeaveSeat

        ```
        /// 远端用户下线通知
        /// @param userId 麦序
        - (void)onLeaveSeat:(NSString *)userId;
        ```

    -   错误信息通知

        回调名称：onOccurError。

        ```
        - (void)onOccurError:(int)error;
        ```

    -   创建房间的回调

        回调名称：onJoinChannelResult。

        ```
        - (void)onJoinChannelResult:(int)result
                           authInfo:(AliRtcAuthInfo *)authInfo;
        ```

    -   退出房间的回调

        回调名称：onLeaveChannelResult。

        ```
        - (void)onLeaveChannelResult:(int)result;
        ```

    -   伴奏播放回调

        回调名称：onAudioPlayingStateChanged。

        背景音乐播放状态的回调。

        ```
        - (void)onAudioPlayingStateChanged:(AliRtcAudioPlayingStateCode)playState
                                 errorCode:(AliRtcAudioPlayingErrorCode)errorCode;
        ```

    -   房间被销毁回调

        回调名称：onRoomDestroy。

        ```
        /// 房间被销毁通知
        - (void)onRoomdestroy;
        ```

    -   网络质量变化时回调

        回调名称：onNetworkQualityChanged。

        ```
        - (void)onNetworkQualityChanged:(NSString *)uid
                       upNetworkQuality:(AliRtcNetworkQuality)upQuality
                     downNetworkQuality:(AliRtcNetworkQuality)downQuality;
        ```

    -   被踢出房间的回调

        回调名称：onKickedOut。

        ```
        /// 被踢出房间
        - (void)onkickedOut;
        ```


