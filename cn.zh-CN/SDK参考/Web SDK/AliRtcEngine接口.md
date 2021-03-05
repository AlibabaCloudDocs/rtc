---
keyword: [Web, AliRtcEngine]
---

# AliRtcEngine接口

通过阅读本文，您可以了解到Web SDK的AliRtcEngine接口详情。

## 目录

基础接口

|API|描述|以上版本支持|
|---|--|------|
|[isSupport](#li_tug_pff_d6o)|检测浏览器是否支持RTC SDK。|1.14|
|[getDevices](#li_oue_oog_rv0)|获取设备信息。|1.2|
|[getAvailableResolutions](#li_od6_3v6_cff)|获取可支持的分辨率。|1.2|
|[isSupportScreenShare](#li_jsg_21y_eqb)|是否支持屏幕共享。|1.12|
|[setChannelProfile](#li_uq5_q53_isf)|设置频道模式。|1.12|
|[setClientRole](#li_zeq_ic0_6ub)|设置角色。|1.12|
|[setAudioOnlyMode](#li_dir_9u2_amx)|设置是否为纯音频模式。|1.12.2|

频道相关接口

|API|描述|以上版本支持|
|---|--|------|
|[joinChannel](#li_oc0_s51_2gm)|加入频道。|1.2|
|[leaveChannel](#li_4gx_qmo_cfz)|离开频道。|1.2|

发布相关接口

|API|描述|以上版本支持|
|---|--|------|
|[configLocalAudioPublish](#li_zq3_78u_31m)|设置是否允许发布音频流。|1.9|
|[configLocalCameraPublish](#li_342_kx3_twr)|设置是否允许发布相机流。|1.9|
|[configLocalScreenPublish](#li_yi7_0js_vo7)|设置是否允许发布屏幕共享流。|1.9|
|[publish](#li_u14_h7l_40t)|发布本地视频流。|1.2|
|[unPublish](#li_v1w_jmp_kxr)|结束发布本地流。|1.2|

订阅相关接口

|API|描述|以上版本支持|
|---|--|------|
|[configRemoteAudio](#li_22b_5dy_94j)|设置是否订阅远端音频流。|1.9|
|[configRemoteCameraTrack](#li_2oq_y38_8fr)|设置是否订阅远端相机流。|1.9|
|[configRemoteScreenTrack](#li_fep_s8y_b92)|设置是否订阅远端屏幕流。|1.9|
|[subscribe](#li_f4m_2kv_97u)|订阅远程发布流。|1.2|
|[unSubscribe](#li_jfu_j59_hma)|取消订阅该用户所有的流。|1.2|

视频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[currentCamera](#li_7kr_1ot_5vf)|指定摄像头设备。|1.9|
|[videoProfile](#li_eph_agq_kbu)|设置视频流参数。|1.9|
|[muteLocalCamera](#li_22i_jy6_nt0)|是否停止本地视频采集。|1.2|
|[setDisplayRemoteVideo](#li_1ju_ght_n22)|为远端的视频设置渲染窗口以及绘制参数。|1.14|
|[setVideoProfile](#li_pr2_8f3_iim)|设置视频流或共享流参数。|1.11|
|[enableCamera](#li_80k_y5g_m06)|设置是否使用摄像头。|1.13.0|

音频相关接口

|API|描述|以上版本支持|
|---|--|------|
|[currentAudioCapture](#li_e0n_h1y_fvj)|指定麦克风设备。|1.9|
|[muteLocalMic](#li_kx3_f9b_xai)|是否停止本地音频采集。|1.2|
|[muteRemoteAudioPlaying](#li_dgb_8yu_48m)|设置是否停止播放远端音频流。|1.12.2|
|[muteAllRemoteAudioPlaying](#li_4ol_ow8_546)|设置是否停止远端的所有音频流的播放。|1.12.2|
|[setAudioVolume](#li_unr_g3v_iy2)|设置订阅用户音量。|1.13.0|
|[getAudioVolume](#li_3m3_j7u_1yi)|获取订阅用户音量。|1.13.0|
|[enableAudioVolumeIndicator](#li_qsn_el9_eov)|设置接收音量值回调。|1.13.0|

预览接口

|API|描述|以上版本支持|
|---|--|------|
|[startPreview](#li_q8y_3m7_5z9)|预览本地摄像头。|1.2|
|[stopPreview](#li_rnn_eih_bir)|结束预览本地摄像头。|1.2|
|[enableHighDefinitionPreview](#li_j6u_7vu_nyd)|设置是否开启高清预览。|1.12.1|

远端用户查询接口

|API|描述|以上版本支持|
|---|--|------|
|[getUserList](#li_r4b_x22_2me)|获取当前房间在线用户。|1.9|
|[getUserInfo](#li_vor_zpx_gsi)|获取用户信息。|1.9|

其他接口

|API|描述|以上版本支持|
|---|--|------|
|[on](#li_rdp_eyf_b1p)|订阅事件。|1.2|
|[off](#li_bz5_z76_25m)|取消订阅事件。|1.2|
|[setExternalMediaTrack](#li_la6_ta9_c59)|设置外部输入音视频流替换。|1.12.1|

## 接口详情

-   isSupport：检测浏览器是否支持RTC SDK。

    ```
    aliWebrtc.isSupport(option).then(re =>{
        console.log(re)
    }).catch(error => {
        console.log(error)
    })
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |option|isReceiveOnly|Boolean|是否为纯订阅模式。取值：true\|false（默认值）。|
    |isDebug|Boolean|是否为本地调试模式。取值：true\|false（默认值）。|

    线上环境必须使用https协议。您可以添加\{isDebug: true\}参数进行localhost（本地主机）调试跳过https协议检测。

    **说明：**

    1.11版本：

    -   新增参数\{channelProfile: 2\}，检测浏览器是否支持低延迟互动直播模式；默认参数\{channelProfile: 0\} 检测浏览器是否支持通信模式。
    -   在实例化之前，调用该接口。
    1.12及以上版本：

    -   无需设置相关频道信息。
    -   不再是静态方法。
    -   在实例化之后加入频道前，调用该接口。
    -   取消参数\{channelProfile: 0\}、\{channelProfile: 2\}。
    返回参数

    |名称|类型|描述|
    |--|--|--|
    |audioDevice|Boolean|音频设备是否可用。取值：true\|false。|
    |browser|String|浏览器名称。|
    |browser\_version|String|浏览器版本。|
    |isSupported|Boolean|是否支持webRTC。取值：true\|false。|
    |message|String|错误信息。|
    |supportH264|Boolean|是否支持H264。取值：true\|false。|
    |supportScreenShare|Boolean|是否支持屏幕分享。取值：true\|false。|
    |supportMixBackgroundAudio|Boolean|是否支持屏幕声音分享。取值：true\|false。|
    |videoDevice|Boolean|摄像头是否可用。取值：true\|false。|

-   getDevices：获取设备信息，返回摄像头和音频输入设备。如果外接设备重新插拔后获取不到设备信息，请尝试重新启动电脑。

    ```
    aliWebrtc.getDevices().then((re)=>{
    }).catch((error)=>{ 
      console.log(error.message)
    });
    ```

-   getAvailableResolutions：获取可支持的分辨率的数组信息。

    ```
    aliWebrtc.getAvailableResolutions(deviceId).then((re)=>{
    }).catch((error)=>{ 
      console.log(error.message)
    });
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceId|String|摄像头ID。|

-   isSupportScreenShare：是否支持屏幕共享。

    ```
    aliWebrtc.isSupportScreenShare();
    ```

-   setChannelProfile：设置频道模式。

    ```
    aliWebrtc.setChannelProfile(channelProfile);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |channelProfile|Number|频道模式。取值：     -   0：普通模式。
    -   1：互动模式。
默认取值0。|

-   setClientRole：设置角色。

    ```
    aliWebrtc.setClientRole(role);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |role|Number|角色类型。取值：     -   0：互动身份。
    -   1：观众身份。
默认取值0。|

-   setAudioOnlyMode：设置是否为纯音频模式。

    ```
    aliWebrtc.setAudioOnlyMode(audioOnly);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |audioOnly|Boolean|是否开启纯音频模式，取值：true\|false（默认值）。|

    **说明：** 需要早调用isSupport接口之前调用该接口。设置纯音频模式后，可以在调用isSupport时不再检测摄像头。加入频道后无法进行本地预览，推拉流只能是音频流。

-   joinChannel：加入频道。

    ```
    aliWebrtc.joinChannel({
        userid,         // 用户ID
        channel,        // 频道
        appid,          // 应用ID
        nonce,          // 随机码
        timestamp,      // 时间戳
        gslb,           // gslb服务地址
        token,          // 令牌
    },displayName).then(()=>{
        // 入会成功
    } ,(error)=>{
        // 入会失败，打印错误内容，可以看到失败原因
        console.log(error.message);
    });
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |authInfo|userid|String|用户ID。|
    |channel|String|频道。|
    |appid|String|应用ID。|
    |nonce|String|随机码。|
    |timestamp|String|时间戳。|
    |token|String|令牌。|
    |gslb|Array|gslb（Global Server Load Balancing）服务地址。|
    |displayName|String|用户名字。|

-   leaveChannel：离开频道。

    ```
    aliWebrtc.leaveChannel().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

-   configLocalAudioPublish：设置是否允许发布音频流。

    ```
    aliWebrtc.configLocalAudioPublish=enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|是否允许发布音频流。true表示允许发布音频流，false表示不允许发布音频流。默认为允许发布音频流。|

    **说明：** 需要调用publish才能生效。

-   configLocalCameraPublish：设置是否允许发布相机流。

    ```
    aliWebrtc.configLocalCameraPublish=enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|是否允许发布相机流。true表示允许发布相机流，false表示不允许发布相机流。默认为允许发布相机流。|

    **说明：** 需要调用publish进行推流后，设置才能生效。

-   configLocalScreenPublish：设置是否允许发布屏幕共享流。

    ```
    aliWebrtc.configLocalScreenPublish=enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|是否表示允许发布屏幕共享流。true表示允许发布屏幕共享流，false表示不允许发布屏幕共享流。默认为不允许发布屏幕共享流。|

-   publish：发布本地视频流。

    ```
    aliWebrtc.publish().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

    Web SDK只能推送大流。

    **说明：** 需要在加入频道成功之后调用该接口。如果需要让远程订阅本地的流，需要调用publish接口，发布本地流，远程会接收到onPublisher事件。

-   unPublish：结束发布本地流，当您取消发布本地流时，远程会收到onUnPublisher事件。

    ```
    aliWebrtc.unPublish().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

    **说明：** 1.14版本开始取消该接口，建议设置config后调用publish接口。

-   configRemoteAudio：设置是否订阅远端音频流。

    ```
    aliWebrtc.configRemoteAudio(userId,enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|
    |enable|Boolean|是否订阅远端音频流。true表示订阅远端音频流，false表示不订阅远端音频流。默认为订阅远端音频流。|

    **说明：** 需要调用subscribe后，才能设置生效。

-   configRemoteCameraTrack：设置是否订阅远端相机流。

    ```
    
    aliWebrtc.configRemoteCameraTrack(userId,preferMaster,enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|
    |preferMaster|Boolean|true表示优先订阅大流，false表示优先订阅次小流。默认为订阅大流。|
    |enable|Boolean|是否订阅远端相机流，true表示订阅远端相机流，false表示不订阅远端相机流。默认不订阅。|

    相机流包含大流和小流，大流分辨率更高，小流分辨率较低··

    **说明：** 需要调用subscribe后，才能设置生效。

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。

    ```
    aliWebrtc.configRemoteScreenTrack(userId,enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|
    |enable|Boolean|是否订阅远端屏幕流。true表示订阅远端屏幕流，false表示不订阅远端屏幕流。默认不订阅远端屏幕流。|

    **说明：** 需要调用subscribe后，才能设置生效。

-   subscribe：订阅远程发布流。

    ```
    aliWebrtc.subscribe(userId).then((userId)=>{
    },(error)=>{
        console.log(error.message);
    });
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|

    通过subscirbe方法可以订阅远程的流，默认订阅相机流和音频流，可以通过调用configRemoteAudio、configRemoteCameraTrack、configRemoteScreenTrack来设置订阅内容。

-   unSubscribe：取消订阅该用户所有的流。

    ```
    aliWebrtc.unSubscribe(userId).then(() => {
    },(error)=>{
        console.log(error.message);
    });
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID。|

    **说明：** 1.14版本开始取消该接口，建议设置config后调用subscribe接口。

-   currentCamera：指定摄像头设备。

    ```
    //pc端
    aliWebrtc.currentCamera = {
      deviceId: deviceId
    };
    //手机端 facingMode指定user时启用前摄像头、指定environment时启用后置摄像头
    aliWebrtc.currentCamera = {
      facingMode:"user"
    };
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceId|String|摄像头ID。|

    **说明：** 暂不支持热切换，需要在预览和推流之前设置。

-   videoProfile：设置视频流参数。

    ```
    aliWebrtc.videoProfile = { 
      frameRate:20,
      width: 640,
      height: 480
    };
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |frameRate|int|帧率，取值范围：5~30。默认取值15。|
    |width|int|视频宽度。默认取值640。|
    |height|int|设备高度。默认取值480。|

    设置的分辨率需要调用getAvailableResolutions返回，然后调用publish才能生效。如果设置的分辨率不合适，系统会自动进行调整。

    **说明：** 1.14版本SDK取消该接口，请您使用setVideoProfile。

-   muteLocalCamera：是否停止本地视频采集。

    ```
    aliWebrtc.muteLocalCamera(true);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|Boolean|是否停止本地视频采集。true表示停止本地视频采集，false表示不停止本地视频采集。默认不采集本地视频。|

    返回说明

    true表示成功，false表示失败。

    **说明：** 1.10及以上版本，该接口增加返回值。该接口需要在推流状态下设置有效。

-   setDisplayRemoteVideo：为远端的视频设置渲染窗口以及绘制参数。

    ```
    aliWebrtc.setDisplayRemoteVideo(
        userId,       // 用户ID
        video,        // html中用于显示stream对象的video元素
        1             // 1表示摄像头流（大流和小流），2表示屏幕分享流
    )
    ```

    **说明：**

    -   1.10.0到1.14.0版本以下音频流无需设置视图，订阅后可以自动播放。
    -   1.14.0版本及以上音频流必须有一个播放视频的video才能播放，具体策略如下。
        -   订阅音频流的同时仅设置摄像头的视图，音频可以播放，音频流跟随摄像头的视图播放。
        -   订阅音频流的同时仅设置屏幕共享流的视图，音频可以播放，音频流跟随屏幕共享的视图播放。
        -   订阅音频流的同时设置摄像头及屏幕共享流的视图，音频可以播放，音频流跟随摄像头的视图播放。
        -   订阅音频流的同时没有设置视图，音频无法播放。
    -   safari浏览器音频订阅后就在后台默认播放。
-   setVideoProfile：设置摄像头或屏幕共享参数。

    ```
    aliWebrtc.setVideoProfile({ 
          width,
          height,
          frameRate,
        },type);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |config|width|Number|宽度。取值：     -   摄像头：640（默认值）。
    -   屏幕共享：960（默认值）。 |
    |height|Number|高度。取值：     -   摄像头：480（默认值）。
    -   屏幕共享：540（默认值）。 |
    |frameRate|Number|帧率。取值范围：5~30。默认取值：

    -   摄像头：15（默认值）。
    -   屏幕共享：10（默认值）。 |
    |maxBitrate|Number|最大码率。取值：     -   摄像头：500000（默认值）。
    -   屏幕共享：1500000（默认值）。
**说明：** 1.13.2版本已删除该参数，SDK会根据设置的分辨率和帧率自动设置最大码率。1.13.2以下版本如果调用setVideoProfile，还需要配置该参数。 |
    |type|Number|1表示摄像头，2表示屏幕共享。|

    **说明：** 屏幕共享清晰度与网络质量、设备性能有关，而不是设置的分辨率越高显示的越清晰。该接口设置之后需要重新发布。

-   enableCamera：设置是否使用摄像头。

    ```
    aliWebrtc.enableCamera = enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|设置是否允许使用摄像头。true表示允许使用摄像头，false表示不允许使用摄像头。默认为允许使用摄像头。|

    **说明：** 该接口需要在isSupport之前调用，设置后isSupport将不再检测摄像头。

-   currentAudioCapture：指定麦克风设备。

    ```
    aliWebrtc.currentAudioCapture = {
      deviceId: deviceId
    };
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |deviceId|String|麦克风ID。|

    **说明：** 该接口暂不支持热切换，您需要在预览和推流之前进行设置。

-   muteLocalMic：是否停止本地音频采集

    ```
    aliWebrtc.muteLocalMic(true);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |mute|Boolean|是否停止本地音频采集。true表示停止本地音频采集，false表示不停止本地音频采集。默认不采集本地音频。|

    返回说明

    true表示成功，false表示失败。

    **说明：** 1.10及以上版本，该接口增加返回值。该接口需要在推流状态下设置有效。

-   muteRemoteAudioPlaying：设置是否停止播放远端音频流。

    ```
    aliWebrtc.muteRemoteAudioPlaying(userId, muted);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID|
    |muted|Boolean|是否开启静音，true表示开启静音，false表示不开启静音。默认不开启静音。|

-   muteAllRemoteAudioPlaying：设置是否停止远端的所有音频流的播放

    ```
    aliWebrtc.muteAllRemoteAudioPlaying(muted);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |muted|Boolean|是否开启全员静音，true开启全员静音，false不开启全员静音。默认为不静音。|

-   setAudioVolume：设置订阅用户音量。

    ```
    aliWebrtc.setAudioVolume (userId, volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID|
    |volume|Number|音量值，取值\[0,1\]。设置成功返回true，失败返回false。|

    **说明：**

    -   该接口与静音接口互不冲突。
    -   该接口在ios设备上不支持。
-   getAudioVolume：获取订阅用户音量。

    ```
    aliWebrtc.getAudioVolume(userId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |userId|String|用户ID|

    返回参数

    |名称|类型|描述|
    |--|--|--|
    |volume|Number|音量值，取值\[0,1\]|

-   enableAudioVolumeIndicator：设置接收音频音量值回调。

    ```
    aliWebrtc.enableAudioVolumeIndicator = enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|是否接收。true表示接收，false表示不接受。默认为false不接收。|

-   startPreview：预览本地摄像头。

    ```
    aliWebrtc.startPreview(
        video    // html中的video元素
    ).then(()=>{
    }).catch((error) => {
        // 预览失败
    });
    ```

    通过video标签播放。

-   stopPreview：结束预览本地摄像头。

    ```
    aliWebrtc.stopPreview().then(()=>{
    }).catch((error) => {
        // 结束预览失败
    });
    ```

-   enableHighDefinitionPreview：设置高清预览接口。

    ```
    aliWebrtc.enableHighDefinitionPreview(enable);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|Boolean|是否开启高清预览，true表示开启高清预览，false表示不开启高清预览。默认为开启高清预览。|

-   getUserList：获取当前房间在线用户。返回当前房间所有在线用户列表信息。

    ```
    aliWebrtc.getUserList();
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |displayName|String|用户名称。|
    |userId|String|用户ID。|
    |muteAudioPlaying|Boolean|是否设置静音。取值：true\|false。|
    |streamConfigs|—|Array|音视频流数组。|
    |label|String|流标签。|
    |state|String|active表示流可用，inactive表示流不可用。|
    |subscribed|Boolean|是否订阅远端用户。取值：true\|false。|
    |type|String|audio表示音频，video表示视频。|

-   getUserInfo：获取用户信息。

    ```
    aliWebrtc.getUserInfo(userId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |displayName|String|用户名称。|
    |userId|String|用户ID。|
    |muteAudioPlaying|Boolean|是否设置静音。取值：true\|false。|
    |streamConfigs|——|Array|音视频流数组。|
    |label|String|流标签。|
    |state|String|active表示流可用，inactive表示流不可用。|
    |subscribed|Boolean|是否订阅远端用户。取值：true\|false。|
    |type|String|audio表示音频，video表示视频。|

-   on：订阅事件。

    ```
    on(name, handler)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |name|String|事件名字。|
    |handler|String|处理事件的方法。|

-   off：取消订阅事件。

    ```
    off(name, handler)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |name|String|事件名字。|
    |handler|String|处理事件的方法。|

-   setExternalMediaTrack：设置外部输入。

    ```
    aliWebrtc.setExternalMediaTrack(track, type);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |track|MediaStreamTrack|媒体流，传入音频流类型（audiotrack）或视频流类型（videotrack）。|
    |type|Number|替换的流类型。取值：     -   0：音频流。
    -   1：视频流。
    -   2：屏幕共享流。 |

    **说明：**

    -   外部输入的视频分辨率就是传入媒体流的分辨率，该分辨率不受[setVideoProfile](#li_pr2_8f3_iim)接口设置的影响。
    -   用audiotrack替换麦克风，用videotrack替换摄像头或屏幕共享进。
    -   setExternalMediaTrack接口未推流状态才可以设置外部音视频流。
    -   setExternalMediaTrack接口想取消设置外部音视频流，可以track传null，都需要在未推流状态下设置。
    -   setExternalMediaTrack接口取消推流后需要重新设置。

