---
keyword: [常见问题, iOS SDK]
---

# 集成iOS SDK时的常见问题

通过阅读本文，您可以了解集成iOS SDK时常见的问题及解决方法。

## 编译代码时报x86或i386错误

-   问题现象：编译代码时可能会出现以下错误：

    ![编译报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1341158951/p128333.png)

-   可能原因：使用模拟器调试和运行。
-   解决方案：请使用真实设备调试和运行。

## 编译代码时报bitcode错误

-   问题现象：编译代码时可能会出现以下错误：

    ![bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128334.png)

-   可能原因：SDK暂不支持bitcode配置。
-   解决方案：关闭bitcode编译选项。

    ![解决bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128335.png)


## 编译代码时报image not found

-   问题现象：编译代码时可能会出现以下错误：

    ![image not found](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128339.png)

-   可能原因：SDK 1.6及之前版本是静态加载，从1.7版本开始切换为动态加载。
-   解决方案：将AliRTCSdk.framework加载到Embedded Binaries中。

    ![切换成动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128340.png)


## 隐私权限未申请导致程序运行时报

-   问题现象：程序运行时可能会出现以下错误：

    ![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p49506.png)

-   可能原因：隐私权限未申请。
-   解决方案：编辑info.plist，申请摄像头、麦克风等权限。具体操作，请参见[集成iOS SDK](/cn.zh-CN/快速入门/集成客户端SDK/iOS.md)。

    ![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128342.png)


## UIDevice方法调用错误

-   问题现象：程序运行时可能会出现以下错误：

    ![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p49510.png)

-   解决方案：添加-ObjC到链接选项里。

    ![增加-Objc编译选项](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128341.png)


## 弱网情况下人声有卡顿

-   问题现象：在线KTV场景下，弱网情况下人声有卡顿。
-   可能原因：为了保证合唱实时性，客户端采用了低延时策略，弱网下丢包率会相应增加。

## 开启耳返模式下声音外放有回声

-   问题现象：在线KTV场景下，开启耳返模式下声音外放有回声。
-   解决方案：您需要带上耳机然后进行合唱，不能通过外放。

