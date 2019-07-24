# API概览 {#reference682 .reference}

本文为您汇总了音视频通信所有可调用API，具体接口信息请参见相关文档。 当前音视频通信OpenAPI版本号为：2018-01-11。

## 应用管理 {#section_src_b06_6h3 .section}

|接口|描述|
|--|--|
|[DescribeApps](cn.zh-CN/API参考/应用管理/DescribeApps.md#)|获取应用列表。|
|[ModifyApp](cn.zh-CN/API参考/应用管理/ModifyApp.md#)|修改应用，可修改应用名称。|

## 频道管理 {#section_fpk_x59_jka .section}

|接口|描述|
|--|--|
|[DeleteChannel](cn.zh-CN/API参考/频道管理/DeleteChannel.md#)|删除频道。|
|[RemoveTerminals](cn.zh-CN/API参考/频道管理/RemoveTerminals.md#)|删除指定终端。|

## 数据服务 {#section_lp2_iwz_2w9 .section}

|接口|描述|
|--|--|
|[DescribeRtcDurationData](cn.zh-CN/API参考/数据服务/DescribeRtcDurationData.md#)|查询历史通信时长，区分音视频规格的统计数值（音频、360P及以下、720P及以下、1080P及以下）。|
|[DescribeRtcUserCntData](cn.zh-CN/API参考/数据服务/DescribeRtcUserCntData.md#)|查询活跃用户数。|
|[DescribeRtcChannelCntData](cn.zh-CN/API参考/数据服务/DescribeRtcChannelCntData.md#)|查询活跃频道数。|
|[DescribeRtcPeakUserCntData](cn.zh-CN/API参考/数据服务/DescribeRtcPeakUserCntData.md#)|查询并发通信峰值，及并发通信用户终端的峰值数量。|
|[DescribeRtcPeakChannelCntData](cn.zh-CN/API参考/数据服务/DescribeRtcPeakChannelCntData.md#)|查询并发频道峰值。|

## 旁路直播 {#section_zh2_8ii_u9u .section}

|接口|描述|
|--|--|
|[StartMPUTask](cn.zh-CN/API参考/旁路直播/StartMPUTask.md#)|开始任务。|
|[GetMPUTaskStatus](cn.zh-CN/API参考/旁路直播/GetMPUTaskStatus.md#)|获取任务状态。|
|[StopMPUTask](cn.zh-CN/API参考/旁路直播/StopMPUTask.md#)|停止任务。|

