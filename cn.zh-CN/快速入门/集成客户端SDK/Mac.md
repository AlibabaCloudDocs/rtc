---
keyword: [Mac, SDK, 集成]
---

# Mac

通过阅读本文，您可以了解Mac端集成SDK的方法。

-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。
-   如果使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 集成SDK

1.  下载并解压Mac SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  新建工程，将解压后的SDK文件复制到工程中。

3.  在工程中添加SDK中的依赖文件。

    1.  在**Build Phases**页签中，在**Link Binary With Libraries**区域添加依赖文件AliRTCSdk.framework和UTDID.framework。

    2.  在**General**页签中，在**Frameworks, Libraries, and Embedded Content**区域中添加UTDID.framework，并将对应的**Embed**属性设置成**Embed & Sign**。

        **说明：** Mac SDK1.1版本增加了UTDID.framework，该库为动态库，需要加载到**Embedded Binaries**中。

        ![添加动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p128304.png)

4.  在**Build Phases**页签中添加以下系统依赖。

    相关系统库如下所示。

    -   libc++.tbd
    -   libresolv.tbd
    -   libcurl.tbd
    -   libz.tbd
    -   CoreMedia.framework
    -   CoreAudio.framework
    -   AudioToolbox.framework
    -   AVFoundation.framework
5.  在**Build Settings**页签中，在**Framework Search Path**区域，将AliRTCSDK.framework文件夹拖入弹框内。

    ![Framework Search Path](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p57381.png)

6.  编辑info.plist文件，添加权限。

    ![添加权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p128305.png)

7.  在**Signing & Capabilities**页签中设置权限。

    ![设置权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p57363.png)

8.  按Commond+B，如果界面提示**Build Success**，表示SDK集成成功。


完成集成SDK操作后，您可以实现音视频通信的基本功能，详情请参见[Mac端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Mac.md)。

