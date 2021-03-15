---
keyword: [iOS, Mac, rtc]
---

# iOS和Mac

RTC SDK为您提供了频道成员管理的接口方法，您可以获取远端在线用户列表、查询远端用户信息、查询用户是否在线等功能。通过阅读本文，您可以了解频道成员管理的方法。

## 实现方法

以下为常用的频道成员管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)。

-   getOnlineRemoteUsers：获取远端在线用户列表。

    ```
    - (NSArray<NSString *> *)getOnlineRemoteUsers;
    ```

    返回说明

    返回用户ID列表。

-   getUserInfo：查询远端用户信息。

    ```
    - (NSDictionary *)getUserInfo:(NSString *)uid;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|

-   isUserOnline：查询用户是否在线。

    ```
    - (BOOL)isUserOnline:(NSString *)uid;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|

    返回说明

    YES表示在线，NO表示不在线。


