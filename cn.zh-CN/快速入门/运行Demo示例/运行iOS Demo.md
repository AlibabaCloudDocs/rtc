---
keyword: iOS Demo
---

# 运行iOS Demo

通过阅读本文，您可以了解运行iOS Demo的方法。

您已从控制台获取鉴权信息，具体操作，请参见[接入工具](/cn.zh-CN/控制台指南/接入工具.md)。

**说明：** 从控制台获取的Token仅为开发测试使用，正式上线有被攻击风险。建议您自己搭建服务端生成Token，并使用HTTPS协议。搭建服务端请参见[服务端生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 环境要求

|类型|说明|
|--|--|
|终端设备|iPhone 5及之后的实体设备。|
|系统版本|iOS 9及以上版本。|

## 操作步骤

1.  下载并解压SDK及示例代码，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件至示例代码中的此目录下。

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p110334.png)

3.  配置参数。

    1.  将AliRTCSdk.framework设置动态库，如下所示：

        ![动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p128040.png)

    2.  选择证书和profile文件。

        证书配置Demo工程需要真机环境，因此需要选择自己的证书和profile文件，修改Bundle Identifier为与自己证书匹配的值。Xcode9.0之后版本可以通过选中**Automaticall manage signing**由Xcode自动管理。

        ![自动管理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p128041.png)

    3.  打开RTCSampleChatViewController.m文件，配置鉴权信息AliRtcAuthInfo（在`joinBegin`方法中）。

        ```
        /*
            NSString *AppID   =  @"aoe****";
            NSString *userID  =  @"f303d59acae073****";
            NSString *channelID  =  @"23****";
            NSString *nonce  =  @"AK-7c8f947b-e55e-4ed5-ab09-bc849****";
            long long timestamp = 1585119606;   //过期时间戳，例如：1560588594代表过期时间为2019-06-15 16:49:54。
            NSString *token  =  @"70f77b8****";
            NSArray <NSString *> *GSLB  =  @[@"https://rgslb.rtc.aliyuncs.com"];
            NSArray <NSString *> *agent =  @[@""];
        */         
        ```

4.  运行。

    Demo运行成功进入首页，您可以看到本地预览视图并进入房间。如果该频道中有其他用户即可开始实时音视频通话。

    ![iOS Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p49610.png)


