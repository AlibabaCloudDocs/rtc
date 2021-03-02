# 生成Token

阿里云RTC为您提供两种生成Token方式，您可以根据业务需求选择在控制台生成或服务端生成。

在生成Token前，您需要完成以下操作：

-   [开通服务](/cn.zh-CN/快速入门/开通服务.md)
-   [创建应用](/cn.zh-CN/快速入门/创建应用.md)
-   [查询AppKey](/cn.zh-CN/控制台指南/查询AppKey.md)

Token是阿里云设计的一种安全保护签名，目的是为了阻止恶意攻击者盗用您的云服务使用权。您需要在相应SDK的登录函数中提供AppID、UserID、ChannelId、Nonce、TimeStamp、GSLB和Token信息。其中AppID用于标识您的应用，UserID用于标识您的用户，而Token则是基于前两者计算出的安全签名，它由SHA256加密算法计算得出。只要攻击者不能伪造Token，就无法盗用您的云服务流量。

## 控制台

1.  登录[音视频通信RTC控制台](https://rtc.console.aliyun.com)。

2.  在左侧导航栏，单击**接入工具**。

3.  在**Token生成器**页签下，输入生成Token所需要的参数。

    |参数|描述|
    |--|--|
    |AppID|应用ID，在控制台**应用管理**页面创建和查看。|
    |AppKey|应用AppKey，在控制台**应用管理**页面查询。|
    |ChannelId|频道ID。1~64位，支持大小写字母、数字、下划线（\_）、中划线（-）。|
    |UserId|用户ID。1~64位，支持大小写字母、数字、下划线（\_）、中划线（-）。|
    |Nonce|随机码。需要加上前缀AK-，由字母\[a,z\]，\[A,Z\]和数字\[0,9\]组成，不包含特殊字符，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |TimeStamp|过期时间戳。可以选择12小时、24小时、3天和7天，代表令牌有效时间为当前时间+所选择小时数。|

4.  单击**生成**。

    ![生成Token](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2245068951/p72646.png)


## 服务端

采用服务端计算Token的方案，可以最大限度地保障计算Token的密钥不被泄露，具体的流程如下所示。

1.  您的App在调用SDK的初始化函数之前，首先要向您的服务器请求Token。
2.  您的服务器根据如下参数计算Token。

    ```
    token = sha256(appId + appKey + channelId + userId + nonce + timestamp)
    ```

3.  服务器将计算好的鉴权信息返回给您的App。
4.  您的App将获得的鉴权信息通过特定API传递给SDK。
5.  SDK将鉴权信息提交给阿里云服务器进行校验。
6.  阿里云校验鉴权信息，确认合法性。
7.  校验通过后，即可开始提供实时音视频服务。

![服务端获取流程图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1616764161/p94321.png)

|参数|说明|
|--|--|
|AppID|应用ID，通过控制台创建。|
|UserID|您的唯一标识，AppServer生成。同一个UserId的用户在其他端登录，先入会的端会被后入会的端踢出房间。 由字母\[a-zA-Z\]和数字\[0-9\]组成，不包含特殊字符，最大64字节。例如：2b9be4b25c2d38c409c376ffd2372be1。 |
|ChannelID|频道ID，AppServer生成。 由字母\[a-zA-Z\]和数字\[0-9\]组成，不包含特殊字符，可以用连接号（-）分隔，最大64字节。例如：181-218-3406。不支持设置ChannelID为0。ChannelID不可以重复，需要保持ChannelID的唯一性。 |
|Nonce|令牌随机码，由AppServe生成。 需要加上前缀AK-，以标识采用应用鉴权私钥（AppKey）方案。格式推荐您用UUID，由字母\[a-zA-Z\]和数字\[0-9\]组成，不包含特殊字符，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。 |
|Timestamp|令牌过期时间戳，由您生成指定令牌过期时间。为Unix时间格式，AppServer所运行的服务器需保持时间同步。例如：当前时间戳为1560415794（2019-06-13 16:49:54）令牌2天后过期，Timestamp设置为1560588594（2019-06-15 16:49:54）。|
|Token|加入频道Token，可以通过AppServer生成。实际算法为`sha256(appId + appKey + channelId + userId + nonce + timestamp)`。|
|GSLB|服务地址，该参数是数组类型，当前请使用：\["https://rgslb.rtc.aliyuncs.com"\]，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

服务端生成Token的签名算法为SHA256，您可以参见如下版本的生成Token函数：

-   Golang程序实例请查看`CreateToken`函数，详情请参见[Golang Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/golang/main.go)。

-   Java程序实例请查看`createToken`函数，详情请参见[Java Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/java/src/main/java/com/company/App.java)。

-   Python程序实例请查看`create_token`函数，详情请参见[Python Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/python/server.py)。

-   C\#程序实例请查看`CreateToken`函数，详情请参见[C\# Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/csharp/rtc-app-csharp/Program.cs)。

-   Nodejs程序实例请查看`CreateToken`函数，详情请参见[Node.js Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/nodejs/index.js)。

-   PHP程序实例请参查看`CreateToken`函数，详情请参见[PHP Demo](https://github.com/aliyunvideo/AliRtcAppServer/blob/master/php/app/v1/login.php)。


