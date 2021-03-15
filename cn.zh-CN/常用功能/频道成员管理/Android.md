---
keyword: [Android, rtc, 成员管理]
---

# Android

RTC SDK为您提供了频道成员管理的接口方法，您可以获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。通过阅读本文，您可以了解频道成员管理的方法。

## 实现方法

以下为常用的频道成员管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    public abstract String[] getOnlineRemoteUsers()                
    ```

    返回说明

    返回用户ID列表。

    **说明：** 该方法在加入频道时调用有延时，建议在调用[onRemoteUserOnLineNotify](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)后再调用此接口或自己维护一个远端用户列表。

-   getUserInfo：查询远端用户信息。

    ```
    public abstract AliRtcRemoteUserInfo getUserInfo(String uid)                  
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|

    返回说明

    返回远程用户信息[AliRtcRemoteUserInfo](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)。

-   isUserOnline：查询用户是否在线。

    ```
    public abstract boolean isUserOnline(String uid)
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|String|用户ID。|

    返回说明

    true表示在线，false表示不在线。


