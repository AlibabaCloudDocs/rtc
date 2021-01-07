---
keyword: [iOS, rtc]
---

# iOS

本文为您介绍了iOS端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示，详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|iPhone设备|支持iPhone5及以上|
|系统版本|支持iOS 8.0及以上|
|CPU架构|支持真机架构armv7+arm64，不支持模拟器i386、x86架构|
|Xcode版本|支持Xcode9.0及以上|
|其他|不支持Bitcode，不支持屏幕旋转|

**说明：** 您需要持有Apple开发证书或个人账号。

## CocoaPods集成

**说明：** 请确保您的Mac已经安装Ruby环境。

1.  安装CocoaPods。

    在Mac终端窗口中输入如下命令：

    ```
    sudo gem install cocoapods
    ```

2.  创建Podfile文件。

    进入您所创建项目所在路径，输入如下命令创建Podfile文件。

    ```
    pod init
    ```

3.  编辑Podfile文件。

    ```
    platform :ios, '8.0'
    target 'AliRTCPodTest' do
        pod 'AliRTCSdk'
    end          
    ```

4.  安装SDK。

    ```
    pod install        
    ```

    命令执行完毕之后，会生成\*.xcworkspace文件，表示SDK集成完成。


## 手动集成

1.  下载[SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  使用XCode工具创建一个新的iOS工程，并把SDK包拷贝到您的工程中。

    ![iOS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5395348951/p112435.png)

3.  在**General**页面，将SDK中AliRTCSdk.framework文件加入到工程。

    **说明：** iOS SDK1.7版本以上为动态库SDK，需要加载到Embedded Binaries中。

    ![添加路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57334.png)

4.  在**Build Phases**页面，添加系统依赖。

    -   libc++.tbd
    -   CoreMedia.framework
    -   AVFoundation.framework
    -   libz.tbd
    -   libresolv.tbd
    -   AudioToolbox.framework
    -   VideoToolbox.framework
5.  在**Build Settings**页面，设置**Enable Bitcode**为No。

    ![Enable Bitcode](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57342.png)

6.  在**Build Settings**页面，添加-ObjC链接选项。

    ![-ObjC](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57343.png)

7.  在**Capabilities**页面，打开后台音频权限。

    **说明：** 为保障应用进入手机后台之后，通话可以保持不中断，建议您开启后台音频权限，SDK默认进入后台之后继续推送音频流。

    ![编辑权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p128287.png)

8.  编辑info.plist文件，添加权限。

    ![添加权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p128288.png)

9.  使用Xcode连接iPhone，执行编译Commond+B，界面提示Build Success，表示SDK集成成功。


完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[iOS端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/iOS.md)。

