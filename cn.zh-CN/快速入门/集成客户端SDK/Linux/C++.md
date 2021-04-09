---
keyword: [Linux, SDK, 集成]
---

# C++

通过阅读本文，您可以了解Linux（C++）端集成SDK的方法。

## 环境要求

Linux端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 集成SDK

1.  下载并解压Linux（C++） SDK，下载地址请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  引入头文件和库文件。

    -   AliRtcCoreService：RTC引擎的可执行程序。请放置在有执行权限的路径下，并记录好路径地址。建议放在业务进程的当前路径下。
    -   include：包含需要引入的头文件。
    -   lib：待导入的SDK动态库，需要配置正确的动态库链接地址。

        ```
        export PROJECT_PATH=当前工程的目录
        export LD_LIBRARY_PATH=$PROJECT_PATH/lib
        ```

3.  编译。

    g++ -std=c++11 -g -Wall -O2 -o test Test\_Demo.cc -lAliRTCLinuxEngine -I/$PROJECT\_PATH/include -L/$PROJECT\_PATH/lib


完成集成SDK操作后，您可以实现音视频通信的基本功能，详情请参见[Linux（C++）端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Linux/C++.md)。

