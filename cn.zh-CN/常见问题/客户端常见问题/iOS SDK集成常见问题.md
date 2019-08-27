# iOS SDK集成常见问题 {#concept_111352_zh .concept}

本文档为您列出了集成iOS SDK时遇到的的常见问题及解决办法。

## 编译时报x86或i386错误 {#section_dqy_q4h_aok .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493649500_zh-CN.png)

解决办法：

iOS SDK目前暂不支持模拟器，请使用真机调试和运行。

## bitcode错误 {#section_tw0_nsl_xnb .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493749501_zh-CN.png)

解决办法：

SDK暂不支持bitcode配置，请关闭bitcode编译选项。

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493749502_zh-CN.png)

## image not found {#section_2ee_t7q_7mz .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493749503_zh-CN.png)

解决办法：

SDK从1.7版本开始切换为动态库，需要加载到动态库link。

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493849504_zh-CN.png)

## 隐私权限错误 {#section_rco_hcv_gyc .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493849506_zh-CN.png)

解决办法：

您需要编辑info.plist，申请摄像头、麦克风权限。具体操作请参见[接入指南](../../../../cn.zh-CN/API参考/iOS SDK/接入指南.md#)。

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493849507_zh-CN.png)

## UTDID引用错误 {#section_qqd_2zt_vbp .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493949508_zh-CN.png)

解决办法：

将UTDID.framework加入到demo工程，具体操作请参见[接入指南](../../../../cn.zh-CN/API参考/iOS SDK/接入指南.md#)。

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493949509_zh-CN.png)

## UIDevice方法调用错误 {#section_ki1_isj_1la .section}

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689493949510_zh-CN.png)

解决办法：

增加-ObjC编译选项。

![iOS SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170952/156689494049511_zh-CN.png)

