---
keyword: [常见问题, Windows SDK]
---

# 集成Windows SDK时的常见问题

通过阅读本文，您可以了解集成Windows SDK时常见的问题及解决方法。

## 编译代码时报x64编译报错

-   问题现象：编译代码时可能会出现以下错误：

    ![x64编译报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49518.png)

-   可能原因：使用64位编译。
-   解决方案：SDK目前只支持32位，请切换编译选项。

## 头文件或静态库路径设置错误

-   问题现象：编译代码时可能会出现以下错误：

    ![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49519.png)

-   可能原因：头文件或静态库路径未设置或设置错误。
-   解决方案：设置头文件和静态库路径。

    ![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49520.png)

    ![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49521.png)


## 动态库路径错误

-   问题现象：程序运行时可能会出现以下错误：

    ![动态库路径错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49522.png)

    ![动态库路径错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49523.png)

-   可能原因：缺少依赖的库文件。
-   解决方案：复制AliRTCSdk.dll及依赖的ffmpeg.dll到程序的执行路径下。

