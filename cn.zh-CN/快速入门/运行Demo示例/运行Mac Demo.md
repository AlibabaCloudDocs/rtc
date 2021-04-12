---
keyword: Mac Demo
---

# 运行Mac Demo

通过阅读本文，您可以了解运行Mac Demo的方法。

您已从控制台获取鉴权信息，具体操作，请参见[接入工具](/cn.zh-CN/控制台指南/接入工具.md)。

**说明：** 从控制台获取的Token仅为开发测试使用，正式上线有被攻击风险。建议您自己搭建服务端生成Token，并使用HTTPS协议。搭建服务端请参见[服务端生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 环境要求

|类型|说明|
|--|--|
|终端设备|如果使用Mac mini等不自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。|
|系统版本|macOS 10.12及以上版本。|

## 操作步骤

1.  下载并解压SDK及示例代码，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件至示例代码中的此目录下。

    ![文件夹](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p110341.png)

3.  配置参数。

    1.  将AliRTCSdk.framework设置动态库，如下所示：

        ![动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p110344.png)

    2.  打开ViewController.m文件，配置鉴权信息AliRtcAuthInfo（在`sureButtonClick`方法中）。

        ```
        /*
            NSString *AppID   =  @"aoe****";
            NSString *userID  =  @"f303d****";
            NSString *channelID  =  @"23****";
            NSString *nonce  =  @"AK-7c8f947b-e55e-4ed5-ab09-bc849efe5bee";
            long long timestamp = 1585119606;   
            NSString *token  =  @"70f77b873****";
            NSArray <NSString *> *GSLB  =  @[@"https://rgslb.rtc.aliyuncs.com"];
            NSArray <NSString *> *agent =  @[@""];
        */
        ```

4.  运行。

    1.  Demo运行成功进入首页，输入频道号并单击**确定**。

        ![Mac Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p49638.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户即可开始实时音视频通话。

        ![Mac Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p49639.png)

        您也可以单击**屏幕共享**把自己的屏幕分享给远端用户。


