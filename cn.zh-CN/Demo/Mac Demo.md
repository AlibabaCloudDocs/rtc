# Mac Demo {#task625 .task}

本文档为您介绍了运行Mac Demo的前提条件及具体操作步骤。您可以加入频道和远端用户进行音视频通信。

在执行跑通Demo步骤之前，您需要搭建App Server，具体操作请参见[搭建App Server](../../../../cn.zh-CN/快速入门/搭建App Server.md#)。

您需要下载示例代码，详情请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#khd_sdk_1)。

1.  配置参数。 
    1.  打开FakeAuthrization.h，配置App Server地址。 

        ``` {#codeblock_7cq_jr3_hr4 .language-objc}
        static NSString *AppServer   =  ;//在此处填写服务器App Server地址
        ```

    2.  在FakeAuthrization.m文件中，passwd字段对应的参数值需要根据自身App server来定 ，阿里云提供的App Server示例代码中未校验此字段。 

        ``` {#codeblock_ms7_drc_1kz .language-objc}
        NSDictionary *param = @{@"user":name,
                                @"room":channelName,
                                @"passwd":@"Hello1234"//需要根据app server来定
                                };
        ```

2.  运行。 

    **说明：** Mac端Demo如果使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。系统版本最低支持macOS 10.12。

    1.  Demo运行成功进入首页，输入相应频道号，单击确定按钮，进入下一页面。 

        ![Mac Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170948/156462389449638_zh-CN.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图。单击开始按钮加入频道，如果该频道中有其他用户即可开始实时音视频通话。 

        ![Mac Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170948/156462389549639_zh-CN.png)

    3.  您可以单击屏幕共享按钮把自己的屏幕分享给远端用户。

