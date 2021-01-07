---
keyword: [Mac, rtc]
---

# Mac

本文为您介绍了Mac端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示，详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|Mac设备|使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风|
|系统版本|支持macOS 10.12及以上|
|CPU架构|支持真机架构armv7+arm64，不支持模拟器i386、x86架构|
|Xcode版本|9.0及以上|
|其他|不支持屏幕旋转|

**说明：** 您需要持有Apple开发证书或个人账号。

1.  下载[SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  使用XCode工具创建一个新的iOS工程，并把SDK包拷贝到您的工程中。

    ![iOS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5395348951/p112435.png)

3.  添加文件。

    1.  选择**Build Phases** \> **Link Binary With Libraries**，将AliRTCSdk.framework和UTDID.framework加入到**Link Binary With Libraries**。

    2.  在**General**页面，添加UTDID.framework到**Embedded Binaries**中。

        **说明：** Mac SDK1.1版本增加了UTDID.framework，该库为动态库，需要加载到**Embedded Binaries**中。

        ![添加动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p128304.png)

4.  在**Build Phases**页面，添加系统依赖。

    相关系统库如下所示。

    -   libc++.tbd
    -   libresolv.tbd
    -   libcurl.tbd
    -   libz.tbd
    -   CoreMedia.framework
    -   CoreAudio.framework
    -   AudioToolbox.framework
    -   AVFoundation.framework
5.  选择**Build Settings** \> **Framework Search Path**，将AliRTCSDK.framework文件夹拖入弹出框内。

    ![Framework Search Path](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p57381.png)

6.  编辑info.plist文件，添加权限。

    ![添加权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p128305.png)

7.  在Capabilities页面，设置权限。

    ![设置权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6395348951/p57363.png)

8.  执行编译Commond+B，界面提示Build Success，表示SDK集成成功。


完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Mac端基本功能实现](/cn.zh-CN/快速入门/实现基本功能/Mac.md)。

