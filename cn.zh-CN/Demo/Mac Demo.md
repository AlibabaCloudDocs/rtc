# Mac Demo {#task625 .task}

本文档为您介绍了运行Mac Demo的前提条件及具体操作步骤。您可以加入频道和远端用户进行音视频通信。

在执行跑通Demo步骤之前，您需要搭建App Server，具体操作请参见[搭建App Server](../../../../cn.zh-CN/快速入门/搭建App Server.md#)。

您需要下载示例代码，详情请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#khd_sdk_1)。

1.  打开FakeAuthrization.h文件，配置App Server地址。 

    ``` {#codeblock_624_8s7_uut .language-objc}
    static NSString *AppServer   =  ;//在此处填写服务器App Server地址
    ```

2.  运行。 

    **说明：** Mac端Demo如果使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。系统版本支持macOS 10.12及以上。

    1.  Demo运行成功进入首页，输入频道号，单击**确定**，进入下一页面。 

        ![Mac Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170948/156638088849638_zh-CN.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户即可开始实时音视频通话。 

        ![Mac Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170948/156638088849639_zh-CN.png)

        您也可以单击**屏幕共享**把自己的屏幕分享给远端用户。


