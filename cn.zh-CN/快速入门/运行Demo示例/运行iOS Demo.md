---
keyword: iOS Demo
---

# 运行iOS Demo

您可以阅读本文，了解快速运行iOS Demo的操作方法，实现加入频道和远端用户进行音视频通信。

在执行Demo步骤之前，您需要从控制台获取鉴权信息，具体操作请参见[生成Token](/cn.zh-CN/控制台指南/接入工具.md)。

您需要下载示例代码，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

1.  下载[SDK](https://help.aliyun.com/document_detail/71770.html?spm=a2c4g.11186623.6.684.66be6060ZOCIUr)，复制一份到该文件夹下。

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p110334.png)

2.  配置参数。

    1.  将AliRTCSdk.framework设置动态库，如下图所示：

        ![动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p128040.png)

    2.  证书配置Demo工程需要真机环境，因此需要选择自己的证书和profile文件，修改Bundle Identifier为与自己证书匹配的值。Xcode9.0之后版本可以通过选中**Automaticall manage signing**选项由Xcode自动管理。

        ![自动管理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p128041.png)

    3.  打开RTCSampleChatViewController.m文件，配置鉴权信息AliRtcAuthInfo（在joinBegin方法中）。

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

3.  运行。

    Demo运行成功进入首页，您可以看到本地预览视图并进入房间。如果该频道中有其他用户即可开始实时音视频通话。

    **说明：** iOS端Demo必须在真机上运行，设备支持iPhone5及以上，系统iOS9及以上版本。

    ![iOS Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7555588951/p49610.png)


