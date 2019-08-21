# Android Demo {#task889 .task}

本文档为您介绍了运行Android Demo的前提条件及具体步骤。您可以加入频道和远端用户进行音视频通信。

在执行跑通Demo步骤之前，您需要搭建App Server，具体操作请参见[搭建App Server](../../../../cn.zh-CN/快速入门/搭建App Server.md#)。

您需要下载示例代码，详情请参见[SDK下载](../../../../cn.zh-CN/SDK参考/SDK下载.md#khd_sdk_1)。

1.  打开AliRtcConstants.java，配置App Server地址。 

    ``` {#codeblock_wif_26d_361 .language-java}
    public class AliRtcConstants {
        /**
         * App Server的url，只需填写域名
         */
        public static final String GSLB_TEST = "your URL";
    }
    ```

2.  运行。 

    **说明：** android端Demo必须在真机上运行，支持Android 4.1及以上，完成以上配置即可运行Demo。

    1.  Demo运行成功进入首页，输入频道号，单击**确定**，进入下一页面。 

        ![Android Demo](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170945/156636983349548_zh-CN.png)

    2.  进入频道页面后，可以看到本地已经开启的预览视图，单击**开始**加入频道，如果该频道中有其他用户即可开始实时音视频通话。 

        ![运行成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170945/156636983349549_zh-CN.png)


