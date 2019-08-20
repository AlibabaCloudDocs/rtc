# Windows Demo {#task623 .task}

本文档为您介绍了运行Windows Demo的前提条件及具体操作步骤。您可以加入频道和远端用户进行音视频通信。

在执行跑通Demo步骤之前，您需要搭建App Server，具体操作请参见[搭建App Server](../../../../cn.zh-CN/快速入门/搭建App Server.md#)。

您需要下载示例代码，详情请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#khd_sdk_1)。

1.  配置参数。 
    1.  在FakeAuthrization.h文件当中找到pstrAppServer和pstrUserPW字段。pstrAppServer对应App Server地址，pstrUserPW字段对应的参数值需要根据自身App server来定 ，阿里云提供的App Server示例代码中未校验此字段。 

        ``` {#codeblock_q50_zwe_4cp .language-cpp}
        char* pstrAppServer = "http://127.0.0.1:8080/app/v1/";//在此处填写服务器App Server地址
        char* pstrUserPW = "hello1234";   //需要根据app server来定        
        ```

2.  运行。 

    **说明：** Windows端Demo如果使用不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。系统支持Windows XP（SP3）、Windows 7、Windows 8.X、Windows 10，不支持Windows XP（SP3）以下版本。

    1.  Demo运行成功进入首页，单击**设置**进入参数设置界面，输入您的AppServer地址，例如：https://xxx.com/app/v1/。 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170947/156627558356334_zh-CN.png)

        如果您想和Web端连接，请勾选**兼容H5模式**。推视频请勾选**视频流**，推音频请勾选**音频流**。

    2.  关闭设置页面，在首页输入相应频道号和用户名，单击**创建/加入房间**按钮，进入下一页面。 

        ![Windows Demo输入](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170947/156627558449615_zh-CN.png)

    3.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户，即可开始实时音视频通话。 

        ![Windows Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170947/156627558449616_zh-CN.png)

        您也可以勾选**屏幕共享**把自己的屏幕分享给远端用户。


