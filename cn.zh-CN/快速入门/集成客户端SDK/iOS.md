---
keyword: [iOS, SDK, 集成]
---

# iOS

通过阅读本文，您可以了解iOS端集成SDK的方法。

-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## pod方式集成

**说明：** 请确保您的Mac已经安装Ruby环境。

1.  打开终端窗口。

2.  安装CocoaPods。

    sudo gem install cocoapods

3.  创建Podfile文件。

    进入项目所在路径，执行以下命令创建Podfile文件。

    pop init

4.  编辑Podfile文件。

    ```
    platform :ios, '8.0'
    target 'AliRTCPodTest' do
        pod 'AliRTCSdk', '1.17.44'
    end          
    ```

    **说明：** 此处pod版本号仅供参考，获取最新的pod版本号，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

5.  安装SDK。

    pod install

    命令执行完毕之后，会生成\*.xcworkspace文件，表示SDK集成完成。


## 手动集成

1.  下载并解压iOS SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  新建工程，将解压后的SDK文件复制到工程中。

3.  在**General**页签中将SDK中AliRTCSdk.framework文件加入到工程。

    **说明：** iOS SDK1.7版本以上为动态库SDK，需要加载到Embedded Binaries中。

    ![添加路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57334.png)

4.  在**Build Phases**页签中添加以下系统依赖。

    -   libc++.tbd
    -   CoreMedia.framework
    -   AVFoundation.framework
    -   libz.tbd
    -   libresolv.tbd
    -   AudioToolbox.framework
    -   VideoToolbox.framework
5.  在**Build Settings**页签中设置**Enable Bitcode**为No。

    ![Enable Bitcode](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57342.png)

6.  在**Build Settings**页签中添加-ObjC链接选项。

    ![-ObjC](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p57343.png)

7.  在**Signing & Capabilities**页签中打开后台音频权限。

    **说明：** 为保障应用进入手机后台之后，通话可以保持不中断，建议您开启后台音频权限，SDK默认进入后台之后继续推送音频流。

    ![编辑权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p128287.png)

8.  编辑info.plist文件，添加权限。

    ![添加权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4395348951/p128288.png)

9.  使用Xcode连接终端设备，按Commond+B，如果界面提示**Build Success**，表示SDK集成成功。


完成集成SDK操作后，您可以实现音视频通信的基本功能。具体操作，请参见[iOS端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/iOS.md)。

