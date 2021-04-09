---
keyword: [Linux, SDK, 集成]
---

# Java

通过阅读本文，您可以了解Linux（Java）端集成SDK的方法。

## 环境要求

Java环境：Java 6及以上版本。更多Linux端环境要求，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 集成SDK

1.  下载并解压Linux（Java） SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  引入库文件。

    -   AliRtcCoreService：RTC引擎的可执行程序。请放置在有执行权限的路径下，并记录好路径地址。建议放在业务进程的当前路径下。
    -   libs：业务执行程序必须依赖的jar和so库，需要配置正确的动态库链接地址。

        ```
        export PROJECT_PATH=当前工程的目录
        export LD_LIBRARY_PATH=$PROJECT_PATH/libs
        ```

3.  编译。

    javac -cp $PROJECT\_PATH/libs/alirtc\_linux\_java.jar -encoding utf-8 Test\_Demo.java


完成集成SDK操作后，您可以实现音视频通信的基本功能，详情请参见[Linux（Java）实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Linux/Java.md)。

