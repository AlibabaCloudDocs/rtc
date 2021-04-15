---
keyword: iOS SDK
---

# iOS SDK

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## 编译时报x86或i386错误

![编译报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1341158951/p128333.png)

解决办法：

iOS SDK目前暂不支持模拟器，请使用真机调试和运行。

## bitcode错误

![bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128334.png)

解决办法：

SDK暂不支持bitcode配置，请关闭bitcode编译选项。

![解决bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128335.png)

## image not found

![image not found](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128339.png)

解决办法：

SDK从1.7版本开始切换为动态库，将AliRTCSdk.framework加载到Embedded Binaries中。

![切换成动态库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128340.png)

## 隐私权限错误

![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p49506.png)

解决办法：

您需要编辑info.plist，申请摄像头、麦克风权限。具体操作请参见[集成iOS SDK](/cn.zh-CN/快速入门/集成客户端SDK/iOS.md)。

![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128342.png)

## UIDevice方法调用错误

![iOS SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p49510.png)

解决办法：

添加-ObjC到链接选项里。

![增加-Objc编译选项](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2341158951/p128341.png)

## 弱网情况下人声有卡顿

为了保证合唱的实时性，客户端采用了低延时策略，弱网下丢包率会相应增加。

## 开启耳返模式下，声音外放出现回声

您需要带上耳机然后进行合唱，不能通过外放。

