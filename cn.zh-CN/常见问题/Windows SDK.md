# Windows SDK {#concept_111355_zh .concept}

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## x64编译报错 {#section_a1y_chn_2k3 .section}

![x64编译报错](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149518_zh-CN.png)

解决办法：

SDK目前只支持32位，请切换编译选项。

## 头文件或静态库路径设置错误 {#section_mnj_hd8_kss .section}

![头文件或静态库路径设置错误](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149519_zh-CN.png)

解决办法：

设置头文件和静态库路径。

![头文件或静态库路径设置错误](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149520_zh-CN.png)

![头文件或静态库路径设置错误](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149521_zh-CN.png)

## 动态库路径错误 {#section_4vm_5t0_vc8 .section}

![动态库路径错误](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149522_zh-CN.png)

![动态库路径错误](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156704509149523_zh-CN.png)

解决办法：

复制AliRTCSdk.dll及依赖的ffmpeg.dll到程序的执行路径下。

