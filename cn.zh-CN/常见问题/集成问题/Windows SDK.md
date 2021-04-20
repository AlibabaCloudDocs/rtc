---
keyword: Windows SDK
---

# Windows SDK

## x64编译报错

![x64编译报错](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49518.png)

解决办法：

SDK目前只支持32位，请切换编译选项。

## 头文件或静态库路径设置错误

![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49519.png)

解决办法：

设置头文件和静态库路径。

![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49520.png)

![头文件或静态库路径设置错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49521.png)

## 动态库路径错误

![动态库路径错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49522.png)

![动态库路径错误](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5341158951/p49523.png)

解决办法：

复制AliRTCSdk.dll及依赖的ffmpeg.dll到程序的执行路径下。

