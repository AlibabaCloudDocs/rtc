# Android {#concept_1130528 .concept}

本文档为您介绍了频道成员管理的功能简介和实现方法。您可以通过使用AliRtcSDK实现获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。

## 功能简介 {#section_cqt_ytq_fl9 .section}

AliRtcSDK提供了getOnlineRemoteUsers、getUserInfo和isUserOnline三个方法帮助您进行已经加入频道的成员管理。您可以获取在线用户的ID列表，查询频道内订阅的远端用户信息，也可以根据某个用户ID查询该用户是否在线。

## 实现方法 {#section_nfv_g01_wly .section}

在设置视频属性前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../../../../cn.zh-CN/快速入门/入门概述.md#)。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ``` {#codeblock_0bk_eox_qk3 .language-java}
    public abstract String[] getOnlineRemoteUsers()
    ```

    该方法返回用户ID列表。

-   getUserInfo：查询远端用户信息。

    ``` {#codeblock_1w3_1ic_jhq .language-java}
    public abstract AliRtcRemoteUserInfo getUserInfo(String uid)
    ```

    参数说明：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server下发的唯一标示符|

    该方法返回AliUserAuthInfo信息。

-   isUserOnline：查询用户是否在线。

    ``` {#codeblock_byx_s4j_8ie .language-java}
    public abstract boolean isUserOnline(String uid)
    ```

    参数说明：

    |参数|类型|说明|
    |--|--|--|
    |uid|String|用户ID，从App server下发的唯一标示符|

    返回true代表在线，false代表不在线。


更多接口方法，请参见[AliRtcEngine接口](../../../../cn.zh-CN/API参考/Android SDK/AliRtcEngine接口.md#)。

