# API概览

音视频通信提供以下相关API接口。

## 应用管理

|API|描述|
|---|--|
|[DescribeApps](/cn.zh-CN/API参考/应用管理/DescribeApps.md)|调用DescribeApps查询应用列表。|
|[ModifyApp](/cn.zh-CN/API参考/应用管理/ModifyApp.md)|调用ModifyApp修改指定应用的名称。|

## 频道管理

|API|描述|
|---|--|
|[DeleteChannel](/cn.zh-CN/API参考/频道管理/DeleteChannel.md)|调用DeleteChannel删除频道。|
|[DescribeUserInfoInChannel](/cn.zh-CN/API参考/频道管理/DescribeUserInfoInChannel.md)|调用DescribeUserInfoInChannel查询User（用户）在某个Channel（频道）中实时信息。|
|[DescribeChannelUsers](/cn.zh-CN/API参考/频道管理/DescribeChannelUsers.md)|调用DescribeChannelUsers查询Channel（频道）实时在线用户列表。|
|[DescribeRtcChannels](/cn.zh-CN/API参考/频道管理/DescribeRtcChannels.md)|调用DescribeRtcChannelList获取频道通信记录列表。|
|[DescribeChannelParticipants](/cn.zh-CN/API参考/频道管理/DescribeChannelParticipants.md)|调用DescribeChannelParticipants查询频道在线用户列表。|
|[DescribeRtcChannelMetrics](/cn.zh-CN/API参考/数据服务/DescribeRtcChannelMetrics.md)|调用DescribeRtcChannelMetrics获取频道通信记录详情，支持查询近180天内的数据。|
|[DescribeRtcChannelUserList](/cn.zh-CN/API参考/数据服务/DescribeRtcChannelUserList.md)|调用DescribeRtcChannelUserList获取频道通信用户列表。|
|[RemoveTerminals](/cn.zh-CN/API参考/频道管理/RemoveTerminals.md)|调用RemoveTerminals将指定终端用户从频道踢出。|
|[UpdateChannel](/cn.zh-CN/API参考/频道管理/UpdateChannel.md)|调用UpdateChannel刷新频道信息。|

## 数据服务

|API|描述|
|---|--|
|[DescribeRtcDurationData](/cn.zh-CN/API参考/数据服务/DescribeRtcDurationData.md)|调用DescribeRtcDurationData获取应用在一段时间内的累计通信时长，区分音视频规格进行统计。|
|[DescribeRtcUserCntData](/cn.zh-CN/API参考/数据服务/DescribeRtcUserCntData.md)|调用DescribeRtcUserCntData查询应用在一段时间内的活跃用户数，即发生通信的用户终端数。|
|[DescribeRtcChannelCntData](/cn.zh-CN/API参考/数据服务/DescribeRtcChannelCntData.md)|调用DescribeRtcChannelCntData查询应用在一段时间内的活跃频道数，即发生通信的频道数。|
|[DescribeRtcPeakUserCntData](/cn.zh-CN/API参考/数据服务/DescribeRtcPeakUserCntData.md)|调用DescribeRtcPeakUserCntData查询应用在一段时间内的并发通信峰值，一组“发布-订阅”关系被标记为一次通信。|
|[DescribeRtcPeakChannelCntData](/cn.zh-CN/API参考/数据服务/DescribeRtcPeakChannelCntData.md)|调用DescribeRtcPeakChannelCntData查询应用在一段时间内的并发频道峰值数量。|

## 旁路直播

|API|描述|
|---|--|
|[StartMPUTask](/cn.zh-CN/API参考/旁路转推/StartMPUTask.md)|调用StartMPUTask开始任务。|
|[GetMPUTaskStatus](/cn.zh-CN/API参考/旁路转推/GetMPUTaskStatus.md)|调用GetMPUTaskStatus获取任务状态。|
|[StopMPUTask](/cn.zh-CN/API参考/旁路转推/StopMPUTask.md)|调用StopMPUTask停止任务。|
|[UpdateMPULayout](/cn.zh-CN/API参考/旁路转推/UpdateMPULayout.md)|调用UpdateMPULayout更新任务的布局。|

