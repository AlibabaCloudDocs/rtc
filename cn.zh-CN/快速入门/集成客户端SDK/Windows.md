---
keyword: [Windows, SDK, 集成]
---

# Windows

通过阅读本文，您可以了解Windows端集成SDK的方法。

环境中已安装Visual Studio 2010或以上版本。

## 环境要求

Windows端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 集成SDK

**说明：** 本文以MFC的工程为例说明，您也可以根据实际情况选择其他UI框架。

1.  下载并解压Windows SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  使用Visual Studio创建一个MFC Dialog based类型的工程，并输入工程名，例如：RtcSample。

    ![创建工程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7395348951/p58822.png)

3.  将解压好的SDK的相关文件移动到.sln文件所在的目录。

4.  配置RtcSample工程的属性，添加SDK库及头文件的路径。

    **说明：** 当前版本SDK只支持Release x86版。

5.  设置32位工程属性。

    ![设置工程属性](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7395348951/p128157.png)

6.  在工程属性页面，设置依赖头文件的路径。

    ![设置依赖头文件的路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8395348951/p128160.png)

7.  设置静态库的路径。

    ![设置静态库的路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8395348951/p128161.png)

8.  复制AliRTCSdk.dll文件及依赖的alivcffmpeg.dll文件到程序的执行路径下。

9.  执行编译。如果编译成功，表示SDK集成成功。


完成集成SDK操作后，您可以实现音视频通信的基本功能，详情请参见[Windows端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Windows.md)。

