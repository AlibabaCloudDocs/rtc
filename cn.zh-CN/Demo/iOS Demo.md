# iOS Demo {#task707 .task}

本文档为您介绍了运行iOS Demo的前提条件及具体操作步骤。您可以加入频道和远端用户进行音视频通信。

在执行跑通Demo步骤之前，您需要搭建App Server，具体操作请参见[搭建App Server](../../../../cn.zh-CN/快速入门/搭建App Server.md#)。

您需要下载示例代码，详情请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#khd_sdk_1)。

1.  配置参数。 
    1.  证书配置Demo工程需要真机环境，因此需要选择自己的证书和profile文件。Xcode9.0之后版本可以通过勾选**Automaticall manage signing**选项由Xcode自动管理。 

        ![iOS Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170946/156664206149607_zh-CN.png)

    2.  打开RTCSampleUserAuthrization.h，配置App Server地址。 

        ``` {#codeblock_y7k_ub1_70b .language-objc}
        static NSString *AppServer   = "your URL"  ;//在此处填写服务器App Server地址            
        ```

2.  运行。 

    **说明：** iOS端Demo必须在真机上运行，设备支持iPhone5及以上，系统iOS9及以上版本，完成以上设置即可运行Demo。

    1.  Demo运行成功进入首页，输入频道号，单击**确定**，进入下一页面。 

        ![iOS Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170946/156664206149609_zh-CN.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户即可开始实时音视频通话。 

        ![iOS Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170946/156664206249610_zh-CN.png)


