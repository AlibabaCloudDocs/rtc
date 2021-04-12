---
keyword: [基本功能, Web]
---

# Web

阿里云RTC的基本功能包含初始化SDK、加入频道、本地发布、订阅远端和离开频道等。通过阅读本文，您可以了解阿里云RTC的基本功能。

-   您已下载并集成最新版本的SDK。具体操作，请参见[Web端集成SDK](/cn.zh-CN/快速入门/集成客户端SDK/Web.md)。
-   您已获取加入频道必须的频道鉴权令牌（Token）。具体操作，请参见[生成Token](/cn.zh-CN/基础功能/生成Token.md)。

**说明：** 本文中的实现方法仅供参考，您可以根据实际业务需求进行开发。

1.  初始化SDK。

    创建AliRtcEngine实例。

    ```
    var aliWebrtc = new AliRtcEngine();
    ```

    本地预览。在创建完AliRtcEngine实例后，您可以通过video标签播放。

    ```
    aliWebrtc.startPreview(
        video    // html中的video元素
    ).then(()=>{
    }).catch((error) => {
        // 预览失败
    });
    ```

2.  加入频道。

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

    **说明：** 加入频道需要传递两个参数。第一个是AliRtcAuthInfo，第二个参数是频道里显示的用户名。

    |参数|描述|
    |--|--|
    |AppID|应用ID，在控制台**应用管理**页面创建和查看。|
    |ChannelId|频道ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。|
    |UserId|用户ID。1~64位，由大小写字母、数字、下划线（\_）、短划线（-）组成。 **说明：** 同一个用户ID在其他端登录，先入会的端会被后入会的端踢出频道。 |
    |Nonce|随机码。以前缀AK-开头，由大小写字母、数字组成，最大64字节。例如：AK-2b9be4b25c2d38c409c376ffd2372be1。|
    |TimeStamp|过期时间戳。可以选择12小时、24小时、3天和7天，代表令牌有效时间。|
    |Token|频道鉴权令牌，计算方法：`token = sha256(appId + appKey + channelId + userId + nonce + timestamp)`。|
    |GSLB|服务地址，该参数是数组类型，当前请使用：`["https://rgslb.rtc.aliyuncs.com"]`，请您通过业务服务器下发到客户端SDK，不建议您将该地址固化在客户端代码。|

3.  发布或取消发布本地流。

    -   发布本地流。如果需要让远程订阅本地的流，您需要调用publish接口，发布本地流，远程会接收到onPublisher回调。

        ```
        aliWebrtc.publish().then(()=>{
        } ,(error)=>{
            console.log(error.message);
        });
        ```

    -   取消发布本地流。当您取消发布本地流时，远程会收到onUnPublisher回调。

        ```
        aliWebrtc.unPublish().then(()=>{
        } ,(error)=>{
            console.log(error.message);
        });
        ```

4.  订阅onPublisher回调或onUnPublisher回调。

    -   订阅onPublisher回调。当远程用户推流时，在SDK里会触发onPublisher回调，通过订阅这个回调，能够得到频道里已经推流的用户。

        ```
        aliWebrtc.on('onPublisher',(publisher) =>{
            //远程发布者userId
            console.log(publisher.userId);
            //远程发布名字
            console.log(publisher.displayName);
            //远程流内容，streamConfigs是数组格式
            console.log(publisher.streamConfigs);
          });
        ```

    -   订阅onUnPublisher回调。当远程用户结束推流时，会触发这个回调。

        ```
        aliWebrtc.on('onUnPublisher',(publisher) =>{
            //远程发布者userId
            console.log(publisher.userId);
            //远程发布名字
            console.log(publisher.displayName);
        });
        ```

    **说明：** onPublisher、onUnPublisher回调只有加入频道以后才会触发。

5.  订阅或取消订阅远程流。

    **说明：** 1.10及以上版本不支持onMediaStream事件。

    -   订阅和显示远程流。通过subscribe方法订阅远程流，订阅成功后在调用setDisplayRemoteVideo显示远程流。

        ```
        aliWebrtc.subscribe(userId).then((userId)=>{
            aliWebrtc.setDisplayRemoteVideo(
                userId,       // 用户ID
                video,        // html中用于显示stream对象的video元素
                1             // 1表示摄像头流（大流和小流），2表示屏幕分享流
            )
        },(error)=>{
            console.log(error.message);
        });
        ```

        **说明：** 音频流无需设置视图，订阅后可以自动播放。

    -   取消订阅。通过unSubscribe方法可以取消订阅远程流。

        ```
        aliWebrtc.unSubscribe(userId).then(() => {
        },(error)=>{
            console.log(error.message);
        });
        ```

6.  离开频道。

    ```
    aliWebrtc.leaveChannel().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```


您可以下载示例代码，快速运行Demo，实现频道内和其他人进行实时音视频通话，详情请参见[运行Web Demo](/cn.zh-CN/快速入门/运行Demo示例/运行Web Demo.md)。

