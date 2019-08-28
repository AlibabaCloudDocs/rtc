# Mac SDK {#concept_111353_zh .concept}

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## bitcode错误 {#section_keu_6qc_312 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156698609249501_zh-CN.png)

解决办法：

SDK暂不支持bitcode配置，请关闭bitcode编译选项。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156698609349502_zh-CN.png)

## UTDID image not found {#section_b27_hxf_706 .section}

![UTDID image not found](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170953/156698609349512_zh-CN.png)

解决办法：

将UTDID.framework加载到Embedded Binaries中。具体操作请参见[集成Mac SDK](../../../../cn.zh-CN/快速入门/集成客户端SDK/Mac.md#)。

## 参数不符合规范 {#section_jvr_0e6_pdy .section}

![参数不符合规范](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170953/156698609349513_zh-CN.png)

解决办法：

根据规范，请您重新对channelID、userID、name进行命名。字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节。

