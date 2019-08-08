# AliRtcEngine接口 {#reference_269597 .reference}

本文为您介绍了AliRtcSDK Web端的所有接口信息，您可以根据接口详细说明集成SDK。

## 目录 {#section_m3b_hg3_jvb .section}

基础接口

|API|描述|
|---|--|
|[isSupport](#)|检测浏览器是否支持|
|[getDevices](#)|获取设备信息|
|[getAvailableResolutions](#)|获取可支持的分辨率|

频道相关接口

|API|描述|
|---|--|
|[joinChannel](#)|加入频道|
|[leaveChannel](#)|离开频道|

发布相关接口

|API|描述|
|---|--|
|[configLocalAudioPublish](#)|设置是否允许发布音频流|
|[configLocalCameraPublish](#)|设置是否允许发布相机流|
|[configLocalScreenPublish](#)|设置是否允许发布屏幕共享流|
|[publish](#)|发布本地视频流|
|[unPublish](#)|结束发布本地流|

订阅相关接口

|API|描述|
|---|--|
|[configRemoteAudio](#)|设置是否订阅远端音频流|
|[configRemoteCameraTrack](#)|设置是否订阅远端相机流|
|[configRemoteScreenTrack](#)|设置是否订阅远端屏幕流|
|[subscribe](#)|订阅远程发布流|
|[unSubscribe](#)|取消订阅该用户所有的流|

视频相关接口

|API|描述|
|---|--|
|[currentCamera](#)|指定摄像头设备|
|[videoProfile](#)|指定帧率和分辨率设备|
|[muteLocalCamera](#)|是否停止本地视频采集|

音频相关接口

|API|描述|
|---|--|
|[currentAudioCapture](#)|指定麦克风设备|
|[muteLocalMic](#)|是否停止本地音频采集|

预览接口

|API|描述|
|---|--|
|[startPreview](#)|预览本地摄像头|
|[stopPreview](#)|结束预览本地摄像头|

远端用户查询接口

|API|描述|
|---|--|
|[getUserList](#)|获取当前房间在线用户|
|[getUserInfo](#)|获取用户信息|

其他接口

|API|描述|
|---|--|
|[on](#)|订阅事件|
|[off](#)|取消订阅事件|

## 接口详情 {#section_eh0_lef_s32 .section}

AliRtcSDK Web端接口信息如下所示。

-   isSupport\(\)：检测浏览器是否支持。

    ``` {#codeblock_wpf_dyo_s3y}
    AliRtcEngine.isSupport().then((re)=> {
          console.log(re);
        }).catch(error => {
          console.log(error);
        })
    ```

    返回参数：

    |参数|类型|描述|
    |--|--|--|
    |audioDevice|Boolean|true表示音频设备可用，false表示音频设备不可用|
    |browser|String|浏览器名称|
    |browser\_version|String|浏览器版本|
    |isSupported|Boolean|是否支持webRTC|
    |message|String|错误信息|
    |supportH264|Boolean|true表示支持H264，false表示不支持H264|
    |supportScreenShare|Boolean|true表示支持屏幕分享，false表示不支持屏幕分享|
    |videoDevice|Boolean|true表示支持摄像头可用，false表示摄像头不可用|

-   getDevices\(\)：获取设备信息，返回摄像头和音频输入设备，在Safari浏览器下面，如果外接设备重插拔后获取不到，请尝试重新启动电脑。

    ``` {#codeblock_e7f_fx8_oui}
    aliwebrtc.getDevices().then((re)=>{
    }).catch((error)=>{ 
      console.log(error.message)
    });
    ```

-   getAvailableResolutions\(deviceId\)：获取可支持的分辨率。返回支持分辨率的Array数组信息。

    ``` {#codeblock_xm5_6nq_d10}
    aliwebrtc.getAvailableResolutions(deviceId).then((re)=>{
    }).catch((error)=>{ 
      console.log(error.message)
    });
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |deviceId|String|摄像头ID|

-   joinChannel\(config,displayName\)：加入频道。

    ``` {#codeblock_va6_kwy_5la}
    aliwebrtc.joinChannel({
        userid,         // 用户ID，只能由数字、字母、下划线组成
        channel,        // 频道
        appid,          // 应用ID
        nonce,          // nonce
        timestamp,      // 时间戳
        gslb,           // gslb
    },displayName).then(()=>{
        // 入会成功
    } ,(error)=>{
        // 入会失败，这里console下error内容，可以看到失败原因
        console.log(error.message);
    });
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |config|—|Object|鉴权频道信息|
    |userid|String|用户ID（只能包含数字和字母）|
    |channel|String|频道|
    |appid|String|应用ID|
    |nonce|String|nonce|
    |timestamp|String|时间戳|
    |gslb|Array|Global Server Load Balancing（简称gslb）|
    |displayName|String|用户名字|

-   leaveChannel\(\)：离开频道。

    ``` {#codeblock_f2u_deb_pi8}
    aliwebrtc.leaveChannel().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

-   configLocalAudioPublish：设置是否允许发布音频流。

    **说明：** 默认为允许发布音频流，需要调用publish才能生效。

    ``` {#codeblock_h79_7p8_p8b}
    aliWebrtc.configLocalAudioPublish=enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|Boolean|true表示允许发布音频流；false表示不允许|

-   configLocalCameraPublish：设置是否允许发布相机流。

    **说明：** 默认为允许发布相机流，需要调用publish才能生效。

    ``` {#codeblock_mr6_fh4_h82}
    aliWebrtc.configLocalCameraPublish=enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|Boolean|true表示允许发布音频流，false表示不允许|

-   configLocalScreenPublish：设置是否允许发布屏幕共享流。

    **说明：** 默认为允许发布音频流，需要调用publish才能生效。

    ``` {#codeblock_4d2_lck_n98}
    aliWebrtc.configLocalAudioPublish=enable;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |enable|Boolean|true表示允许发布音频流；false表示不允许|

-   publish\(\)：发布本地视频流，如果需要让远程订阅本地的流，需要调用publish接口，发布本地流，远程会接收到onPublisher事件。

    ``` {#codeblock_4f9_dsw_u9o}
    aliwebrtc.publish().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

-   unPublish\(\)：结束发布本地流，当您取消发布本地流时，远程会收到onUnPublisher事件。

    ``` {#codeblock_53g_cqo_os0}
    aliwebrtc.unPublish().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```

-   configRemoteAudio：设置是否订阅远端音频流。

    **说明：** 默认为订阅远端音频流，需要调用subscribe才能生效。

    ``` {#codeblock_l9l_5ag_pz3}
    aliWebrtc.configRemoteAudio(userId,enable);
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID|
    |enable|Boolean|true为订阅远端音频流，false为停止订阅远端音频流|

-   configRemoteCameraTrack：设置是否订阅远端相机流。

    相机流包含大流和小流，大流分辨率更高，小流分辨率较低。

    **说明：** 默认为订阅大流，需要调用subscribe才能生效。

    ``` {#codeblock_n63_59r_oe5}
    aliWebrtc.configRemoteCameraTrack(userId,preferMaster,enable);
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID|
    |preferMaster|Boolean|是否优先订阅大流。true为订阅大流，false为订阅次小流|
    |enable|Boolean|true为订阅远端相机流，false为停止订阅远端相机流|

-   configRemoteScreenTrack：设置是否订阅远端屏幕流。

    **说明：** 默认为不订阅远端屏幕流，需要调用subscribe才能生效。

    ``` {#codeblock_i6h_294_ee6}
    aliWebrtc.configRemoteScreenTrack(userId,enable);
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID|
    |enable|Boolean|true为订阅远端屏幕流，false为停止订阅远端屏幕流|

-   subscribe\(userId\)：订阅远程发布流，通过subscirbe方法可以订阅远程的流，默认订阅相机流和音频流，可以通过调用configRemoteAudio、configRemoteCameraTrack、configRemoteScreenTrack来设置订阅内容。

    ``` {#codeblock_ufi_93t_xjb}
    aliwebrtc.subscribe(userId).then((userId)=>{
    },(error)=>{
        console.log(error.message);
    });
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID|

-   unSubscribe\(userId\)：取消订阅该用户所有的流。

    ``` {#codeblock_01y_177_8kv}
    aliwebrtc.unSubscribe(userId).then(() => {
    },(error)=>{
        console.log(error.message);
    });
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |userId|String|用户ID|

-   currentCamera：指定摄像头设备。

    ``` {#codeblock_j4a_hc3_t42}
    //pc端
    aliWebrtc.currentCamera = {
      deviceId: deviceId
    };
    //手机端 facingMode指定user时启用前摄像头、指定environment时启用后置摄像头
    aliWebrtc.currentCamera = {
      facingMode:"user"
    };
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |deviceId|String|摄像头ID|

-   videoProfile：指定帧率和分辨率设备。

    ``` {#codeblock_266_8f2_4a3}
    aliWebrtc.videoProfile = { 
      frameRate:20,
      width: 640,
      height: 480
    };
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |frameRate|int|帧率|
    |width|int|视频宽度|
    |height|int|设备高度|

-   muteLocalCamera\(mute\)：是否停止本地视频采集。

    ``` {#codeblock_8ds_719_90a}
    aliwebrtc.muteLocalCamera(true);
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |mute|Boolean|true为视频采集，false为恢复正常|

-   currentAudioCapture：指定麦克风设备。

    ``` {#codeblock_vuf_5hn_rb2}
    aliWebrtc.currentAudioCapture = {
      deviceId: deviceId
    };
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |deviceId|String|麦克风ID|

-   muteLocalMic\(mute\)：是否停止本地音频采集。

    ``` {#codeblock_ojj_rd6_vny}
    aliwebrtc.muteLocalMic(true);
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |mute|Boolean|true为停止视频采集，false为恢复正常|

-   startPreview\(video\)：预览本地摄像头，通过video标签播放。

    ``` {#codeblock_zg0_cgs_bux}
    aliwebrtc.startPreview(
        video    // html中的video元素
    ).then(()=>{
    }).catch((error) => {
        // 预览失败
    });
    ```

-   stopPreview\(\)：结束预览本地摄像头。

    ``` {#codeblock_5fz_wl4_pj3}
    aliwebrtc.stopPreview().then(()=>{
    }).catch((error) => {
        // 结束预览失败
    });
    ```

-   getUserList\(\)：获取当前房间在线用户。返回当前房间的在线用户列表信息。

    ``` {#codeblock_wlt_agj_3u2}
    aliWebrtc.getUserList();
    ```

    返回参数：

    |参数|类型|描述|
    |--|--|--|
    |displayName|String|用户名称|
    |userId|String|用户ID|

-   getUserInfo\(userId\)：获取用户信息。

    ``` {#codeblock_w6d_ovd_je0}
    aliWebrtc.getUserInfo(userId);
    ```

    返回参数：

    |参数| |类型|描述|
    |--|--|--|--|
    |displayName|String|用户名称|
    |streamConfigs|——|Array|音视频流数组|
    |label|String|流标签|
    |state|String|active表示流可用，inactive表示流不可用|
    |subscribed|Boolean|true表示已订阅，false表示未订阅|
    |type|String|audio表示音频，video表示视频|
    |userId|String|用户ID|

-   on\(name, handler\)：订阅事件。

    参数：

    |参数|类型|描述|
    |--|--|--|
    |name|String|事件名字|
    |handler|String|处理事件的方法|

-   off\(name, handler\)：取消订阅事件。

    参数：

    |参数|类型|描述|
    |--|--|--|
    |name|String|事件名字|
    |handler|String|处理事件的方法|


