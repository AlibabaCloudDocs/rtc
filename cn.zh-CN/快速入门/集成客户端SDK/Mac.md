# Mac {#task_1846597 .task}

本文为您介绍了Mac端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示，详情请参见[使用限制](../../../../cn.zh-CN/产品简介/使用限制.md#)。

|类别|说明|
|--|--|
|Mac设备|使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风|
|系统版本|支持macOS 10.12及以上|
|CPU架构|支持真机架构armv7+arm64，不支持模拟器i386、x86架构|
|Xcode版本|9.0及以上|
|其他|不支持屏幕旋转|

**说明：** 您需要持有Apple开发证书或个人账号。

1.  下载[SDK](../../../../cn.zh-CN/快速入门/SDK下载.md#)。
2.  使用XCode工具创建一个新的iOS工程。 

    ![创建工程](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1463386/156689436557333_zh-CN.png)

3.  选择**Build Phases** \> **Link Binary With Libraries**，添加AliRTCSdk.framework和UTDID.framework。
4.  在Build Rules页面，添加如下依赖。 

    相关系统库如下所示。

    -   libc++.tbd
    -   libresolv.tbd
    -   libcurl.tbd
    -   libz.tbd
    -   CoreMedia.framework
    -   CoreAudio.framework
    -   CoreAudio.framework
    -   AudioToolbox.framework
    -   AVFoundation.framework
5.  选择**Build Settings** \> **Framework Search Path**，将AliRTCSDK.framework文件夹拖入弹出框内。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1463395/156689436657381_zh-CN.png)

6.  编辑info.plist文件，添加权限。 

    ![添加权限](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1463386/156689436657346_zh-CN.png)

7.  在Capabilities页面，设置权限。 

    ![设置权限](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1463395/156689436657363_zh-CN.png)

8.  执行编译Commond+B，提示Build Success，表示SDK集成成功。

完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Mac端基本功能实现](cn.zh-CN/快速入门/实现基本功能/Mac.md#)。

