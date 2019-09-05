# Windows {#concept_2022822 .concept}

本文档为您介绍了频道成员管理的功能简介和实现方法。您可以通过使用AliRtcSDK实现获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。

## 功能简介 { .section}

AliRtcSDK提供了getOnlineRemoteUsers、getUserInfo和isUserOnline三个方法帮助您进行已经加入频道的成员管理。您可以获取在线用户的ID列表，查询频道内订阅的远端用户信息，也可以根据某个用户ID查询该用户是否在线。

## 实现方法 {#section_olx_l6l_hzy .section}

在设置视频属性前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

具体实现方法如下所示。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ``` {#d9e3195 .lanuage-c}
    void getOnlineRemoteUsers(AliRtc::StringArray& array)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |array|AliRtc::StringArray&|用户列表，保存的是用户ID。|

-   getUserInfo：查询远端用户信息。返回0表示成功获取，其他表示失败。

    ``` {#d9e3250 .lanuage-c}
    int getUserInfo(const AliRtc::String& uid, AliRtc::Dictionary& dict)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符。|
    |dict|AliRtc::Dictionary&|用于存放用户数据。|

    dict当中key值包括：userID、isOnline、sessionID、callID、displayName、hasAudio,hasCameraMaster、hasCameraSlave、hasScreenSharing、requestAudio,requestCameraMaster、requestCameraSlave、requestScreenSharing、preferCameraMaster subScribedAudio、subScribedCameraMaster,subScribedCamearSlave、subScribedScreenSharing、hasCameraView、hasScreenView、muteAudioPlaying

-   isUserOnline：查询用户是否在线。返回true表示在线，false表示不在线。

    ``` {#d9e3321 .lanuage-c}
    bool isUserOnline(const AliRtc::String& uid)
    ```

    参数：

    |参数|类型|说明|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID，从App server分配的唯一标示符。|


更多接口方法，请参见[AliRtcEngine接口](../cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md#)。

