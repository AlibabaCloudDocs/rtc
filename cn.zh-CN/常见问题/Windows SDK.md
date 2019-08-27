# Windows SDK {#concept_111355_zh .concept}

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## x64编译报错 {#section_a1y_chn_2k3 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881649518_zh-CN.png)

解决办法：

SDK目前只支持32位，请切换编译选项。

## 头文件或静态库路径设置错误 {#section_mnj_hd8_kss .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881649519_zh-CN.png)

解决办法：

设置头文件和静态库路径，具体操作请参见[接入指南](../../../../cn.zh-CN/API参考/Windows SDK/接入指南.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881649520_zh-CN.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881749521_zh-CN.png)

## 动态库路径错误 {#section_4vm_5t0_vc8 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881749522_zh-CN.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170954/156689881749523_zh-CN.png)

解决办法：

复制AliRTCSdk.dll及依赖的ffmpeg.dll到程序的执行路径下。具体操作请参见[接入指南](../../../../cn.zh-CN/API参考/Windows SDK/接入指南.md#)。

