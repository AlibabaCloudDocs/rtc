# iOS {#concept_1909409 .concept}

本文档为您介绍了频道成员管理的功能简介和实现方法。您可以通过使用AliRtcSDK实现获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。

## 功能简介 {#section_muy_nnh_21y .section}

AliRtcSDK提供了getOnlineRemoteUsers、getUserInfo和isUserOnline三个方法帮助您进行已经加入频道的成员管理。您可以获取在线用户的ID列表，查询频道内订阅的远端用户信息，也可以根据某个用户ID查询该用户是否在线。

## 实现方法 {#section_zxa_l3d_h4c .section}

在设置视频属性前，需要您已经搭建App Server、实现基本功能等操作。详情请参见[入门概述](../cn.zh-CN/快速入门/入门概述.md#)。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ``` {#codeblock_wlh_02c_ge3}
    - (NSArray<NSString *> *)getOnlineRemoteUsers;
    ```

    该方法返回用户ID列表。

-   getUserInfo：查询远端用户信息。

    ``` {#codeblock_vv5_upb_bjy}
    - (NSDictionary *)getUserInfo:(NSString *)uid;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|

-   isUserOnline：查询用户是否在线。

    ``` {#codeblock_juc_m31_zmj}
    - (BOOL)isUserOnline:(NSString *)uid;
    ```

    参数：

    |参数|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID，从App server获取的唯一标示符。|

    返回YES表示在线，NO表示不在线。


获得更多视频类功能实现方法，请参见[AliRtcEngine接口](../cn.zh-CN/API参考/iOS SDK/接口说明/AliRtcEngine接口.md#)。

