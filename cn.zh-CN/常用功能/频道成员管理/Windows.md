---
keyword: [Windows, rtc, 成员管理]
---

# Windows

RTC SDK为您提供了频道成员管理的接口方法，您可以获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。通过阅读本文，您可以了解频道成员管理的方法。

## 实现方法

以下为常用的频道成员管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    void getOnlineRemoteUsers(AliRtc::StringArray& array)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |array|AliRtc::StringArray&|用户列表（用户ID列表）。|

-   getUserInfo：查询远端用户信息。返回0表示成功获取，其他表示失败。

    ```
    int getUserInfo(const AliRtc::String& uid, AliRtc::Dictionary& dict)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|
    |dict|AliRtc::Dictionary&|用于存放用户数据。取值：|

    dict当中key值包括：userID、isOnline、sessionID、callID、displayName、hasAudio,hasCameraMaster、hasCameraSlave、hasScreenSharing、requestAudio,requestCameraMaster、requestCameraSlave、requestScreenSharing、preferCameraMaster subScribedAudio、subScribedCameraMaster,subScribedCamearSlave、subScribedScreenSharing、hasCameraView、hasScreenView、muteAudioPlaying。

    返回说明

    0表示方法调用成功，其它表示方法调用失败。

-   isUserOnline：查询用户是否在线。

    ```
    bool isUserOnline(const AliRtc::String& uid)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|const AliRtc::String&|用户ID。|

    返回说明

    true表示用户在线，false表示用户不在线。


