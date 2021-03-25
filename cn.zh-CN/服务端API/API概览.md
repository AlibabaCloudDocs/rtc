# API概览

## 应用管理

|API|描述|
|---|--|
|[ModifyApp](/cn.zh-CN/服务端API/应用管理/ModifyApp.md)|修改指定应用的名称。|
|[DescribeApps](/cn.zh-CN/服务端API/应用管理/DescribeApps.md)|查询应用列表。|

## 频道管理

|API|描述|
|---|--|
|[DeleteChannel](/cn.zh-CN/服务端API/频道管理/DeleteChannel.md)|删除频道。|
|[RemoveTerminals](/cn.zh-CN/服务端API/频道管理/RemoveTerminals.md)|将指定终端用户从频道踢出。|
|[DescribeChannelUsers](/cn.zh-CN/服务端API/频道管理/DescribeChannelUsers.md)|查询频道内各种模式下在线用户列表的详细信息。|
|[DescribeUserInfoInChannel](/cn.zh-CN/服务端API/频道管理/DescribeUserInfoInChannel.md)|查询用户在频道中实时信息。|
|[DescribeChannelParticipants](/cn.zh-CN/服务端API/频道管理/DescribeChannelParticipants.md)|查询频道在线用户列表，不包含详细信息。|

## 旁路转推

|API|描述|
|---|--|
|[StartMPUTask](/cn.zh-CN/服务端API/旁路转推/StartMPUTask.md)|开始任务。|
|[GetMPUTaskStatus](/cn.zh-CN/服务端API/旁路转推/GetMPUTaskStatus.md)|获取任务状态。|
|[StopMPUTask](/cn.zh-CN/服务端API/旁路转推/StopMPUTask.md)|停止任务。|
|[UpdateMPULayout](/cn.zh-CN/服务端API/旁路转推/UpdateMPULayout.md)|更新任务的布局。|

## 布局管理

|API|描述|
|---|--|
|[DeleteMPULayout](/cn.zh-CN/服务端API/布局管理/DeleteMPULayout.md)|删除旁路直播布局。|
|[CreateMPULayout](/cn.zh-CN/服务端API/布局管理/CreateMPULayout.md)|创建旁路直播布局。|
|[DescribeMPULayoutInfoList](/cn.zh-CN/服务端API/布局管理/DescribeMPULayoutInfoList.md)|获取旁路直播任务布局参数。|
|[ModifyMPULayout](/cn.zh-CN/服务端API/布局管理/ModifyMPULayout.md)|修改旁路直播布局。|
|[DescribeMPULayoutList](/cn.zh-CN/服务端API/布局管理/DescribeMPULayoutList.md)|获取旁路直播布局列表。|

## 云端录制

|API|描述|
|---|--|
|[AddRecordTemplate](/cn.zh-CN/服务端API/云端录制/AddRecordTemplate.md)|添加录制配置模板。|
|[DeleteRecordTemplate](/cn.zh-CN/服务端API/云端录制/DeleteRecordTemplate.md)|删除录制配置模板。|
|[UpdateRecordTemplate](/cn.zh-CN/服务端API/云端录制/UpdateRecordTemplate.md)|更新录制配置模板。|
|[DescribeRecordTemplates](/cn.zh-CN/服务端API/云端录制/DescribeRecordTemplates.md)|查询录制模板配置列表。|
|[DescribeRecordFiles](/cn.zh-CN/服务端API/云端录制/DescribeRecordFiles.md)|查询录制生成的文件列表。|
|[StartRecordTask](/cn.zh-CN/服务端API/云端录制/StartRecordTask.md)|录制视频任务。|
|[StopRecordTask](/cn.zh-CN/服务端API/云端录制/StopRecordTask.md)|停止视频录制任务。|
|[UpdateRecordTask](/cn.zh-CN/服务端API/云端录制/UpdateRecordTask.md)|更新录制视频任务。|

## 数据服务

|API|描述|
|---|--|
|[DescribeCallList]()|分页查询时间范围内创建的通信信息。|
|[DescribeCall]()|获取单次通信详情。|
|[DescribeQoeMetricData]()|获取单次通信中用户的下行体验质量指标。|
|[DescribePubUserListBySubUser]()|根据订阅端获取通信中发布端用户列表。|
|[DescribeEndPointMetricData]()|获取端对端指标数据。|
|[DescribeEndPointEventList]()|获取端对端用户事件列表。|
|[DescribeChannelOverallData]()|查询频道概览数据。|
|[DescribeChannelUserMetrics]()|查询频道概览中的用户数据。|
|[DescribeChannelTopPubUserList]()|获取频道内发布端的用户列表（按用户在线时长降序）。|
|[DescribeChannelAreaDistributionStatData]()|获取频道地区分布统计数据。|
|[DescribeChannelDistributionStatData]()|获取频道分布统计数据。|

