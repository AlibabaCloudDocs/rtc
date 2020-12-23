---
keyword: [Linux, SDK, Java]
---

# Java

本文为您介绍了Linux（Java）端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

## 前提条件

Linux系统版本支持CentOS 7及以上。

Java环境支持Java 6及以上。

## 集成SDK

1.  您需要下载SDK，下载链接请参见[SDK下载](https://helpcdn.aliyun.com/document_detail/71770.html#khd-sdk-1)。

2.  SDK压缩包解压后包含：libs文件。文件功能如下所示：

    -   AliRtcCoreService：RTC引擎的可执行程序。请放置在有执行权限的路径下，并记录好路径地址。建议放在业务进程的当前路径下。
    -   libs：是业务执行程序必须依赖的jar和so库，并且需要配置正确的动态库链接地址。

        ```
        export PROJECT_PATH=当前工程的目录
        export LD_LIBRARY_PATH=$PROJECT_PATH/libs
        ```

3.  编译命令示例。

    ```
    javac -cp $PROJECT_PATH/libs/alirtc_linux_java.jar -encoding utf-8 Test_Demo.java
    ```


完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Linux（Java）实现基本功能]()。

