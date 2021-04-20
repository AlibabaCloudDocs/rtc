---
keyword: [常见问题, Mac SDK]
---

# 集成Mac SDK时的常见问题

通过阅读本文，您可以了解集成Mac SDK时常见的问题及解决方法。

## 编译代码时报bitcode错误

-   问题现象：编译代码时可能会出现以下错误：

    ![bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128334.png)

-   可能原因：SDK暂不支持bitcode配置。
-   解决方案：关闭bitcode编译选项。

    ![解决bitcode报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p128335.png)


## 编译代码时报image not found

-   问题现象：编译代码时可能会出现以下错误：

    ![UTDID image not found](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3341158951/p49512.png)

-   可能原因：SDK 1.6及之前版本是静态加载，从1.7版本开始切换为动态加载。
-   解决方案：将UTDID.framework加载到Embedded Binaries中。具体操作，请参见[集成Mac SDK](/cn.zh-CN/快速入门/集成客户端SDK/Mac.md)。

## 参数不符合规范

-   问题现象：程序运行时可能会出现以下错误：

    ![参数](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4341158951/p128349.png)

-   可能原因：channelID、userID或name命名不规范。
-   解决方案：根据规范，请您对channelID、userID、name重新命名。字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节。

