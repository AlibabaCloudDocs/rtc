---
keyword: Mac
---

# Mac SDK

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## bitcode错误

![bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128334.png)

解决办法：

SDK暂不支持bitcode配置，请关闭bitcode编译选项。

![解决bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128335.png)

## UTDID image not found

![UTDID image not found](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p49512.png)

解决办法：

将UTDID.framework加载到Embedded Binaries中。具体操作请参见[集成Mac SDK](/cn.zh-CN/快速入门/集成客户端SDK/Mac.md)。

## 参数不符合规范

![参数](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4341158951/p128349.png)

解决办法：

根据规范，请您重新对channelID、userID、name进行命名。字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节。

