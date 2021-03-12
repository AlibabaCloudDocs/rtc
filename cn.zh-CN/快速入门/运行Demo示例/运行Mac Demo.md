---
keyword: Mac Demo
---

# 运行Mac Demo

您可以阅读本文，了解快速运行Mac Demo的操作方法，实现加入频道和远端用户进行音视频通信。

在执行Demo步骤之前，您需要从控制台获取鉴权信息，具体操作请参见[生成Token](/cn.zh-CN/控制台指南/接入工具.md)。

您需要下载示例代码，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

1.  下载[SDK](https://help.aliyun.com/document_detail/71770.html?spm=a2c4g.11186623.6.684.66be6060ZOCIUr)，复制一份到该文件夹下。

    ![文件夹](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p110341.png)

2.  配置参数。

    1.  将AliRTCSdk.framework和UTDID.framework设置动态库，如下图所示：

        ![动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p110344.png)

    2.  打开ViewController.m文件，配置鉴权信息AliRtcAuthInfo（在sureButtonClick方法中）。

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

3.  运行。

    **说明：** Mac端Demo如果使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。系统版本支持macOS 10.12及以上。

    1.  Demo运行成功进入首页，输入频道号并单击**确定**，进入下一页面。

        ![Mac Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p49638.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户即可开始实时音视频通话。

        ![Mac Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8555588951/p49639.png)

        您也可以单击**屏幕共享**把自己的屏幕分享给远端用户。


