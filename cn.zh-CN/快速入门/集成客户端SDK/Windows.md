# Windows {#task_2022247 .task}

本文为您介绍了Windows端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示，详情请参见[使用限制](../../../../cn.zh-CN/产品简介/使用限制.md#)。

|类别|说明|
|--|--|
|系统版本|支持Windows XP（SP3）、Windows 7、Windows 8.X、Windows 10|
|系统位数|只支持32位|
|开发环境|支持Visual Studio 2010及以上|

**说明：** 本文以MFC的工程为例，您也可以选择其他UI框架。

1.  下载[SDK](../../../../cn.zh-CN/SDK参考/SDK下载.md#)。
2.  使用Visual Studio创建一个MFC Dialog based类型的工程，工程命名为RTCSample。 

    ![创建工程](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058822_zh-CN.png)

    ![创建工程](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058823_zh-CN.png)

3.  将RTC EngineSDK的相关文件移动到.sln文件所在的目录。
4.  配置RtcSample工程的属性，添加RTC EngineSDK库及头文件的路径。 

    **说明：** 当前版本SDK只支持Release x86版。

5.  设置32位工程属性。 

    ![设置工程属性](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058824_zh-CN.png)

6.  在工程属性页面，设置依赖头文件的路径。 

    ![设置依赖头路径](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058826_zh-CN.png)

7.  设置静态库的路径。 

    ![设置依赖头路径](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058827_zh-CN.png)

8.  复制AliRTCSdk.dll文件及依赖的ffmpeg.dll到程序的执行路径下。 

    ![复制文件](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1605564/156764622058828_zh-CN.png)

9.  执行编译。如果编译成功，表示SDK集成成功。

完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Windows实现基本功能](cn.zh-CN/快速入门/实现基本功能/Windows.md#)。

