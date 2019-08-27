# Mac SDK集成常见问题 {#concept_111353_zh .concept}

本文档为您列出了集成Android SDK时遇到的常见问题和解决办法。

## bitcode错误 {#section_keu_6qc_312 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689494849501_zh-CN.png)

解决办法：

SDK暂不支持bitcode配置，请关闭bitcode编译选项。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689494949502_zh-CN.png)

## UTDID image not found {#section_b27_hxf_706 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170953/156689494949512_zh-CN.png)

解决办法：

将UTDID.framework加载到Embedded Binaries中。具体操作请参见[接入指南](../../../../cn.zh-CN/API参考/Mac SDK/接入指南.md#section_840_91z_9ae)。

## 参数不符合规范 {#section_jvr_0e6_pdy .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170953/156689494949513_zh-CN.png)

解决办法：

根据规范，请您重新对channelID、userID、name进行命名。字符内容只允许\[A-Za-z0-9\_-\]，长度限制64字节。详情请参见[接入指南](../../../../cn.zh-CN/API参考/Mac SDK/接入指南.md#)。

