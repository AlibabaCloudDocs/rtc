# API服务变更

自2021年3月起，阿里云RTC将逐步停止对旧版数据服务接口的支持。截止到2021年6月30日，将停止对以下接口的支持：

|API|描述|
|---|--|
|DescribeRtcDurationData|获取应用在一段时间内按照音视频规格进行统计的累计通信时长。|
|DescribeRtcUserCntData|查询应用在一段时间内的活跃用户数（发生通信的用户终端数）。|
|DescribeRtcChannelCntData|查询应用在一段时间内的活跃频道数（发生通信的频道数）。|
|DescribeRtcPeakUserCntData|查询应用在一段时间内的并发通信峰值，一组”发布-订阅“关系被标记为一次通信。|
|DescribeRtcPeakChannelCntData|查询应用在指定时间内的并发频道峰值数量。|
|DescribeRtcChannelList|获取频道通信记录列表。|
|DescribeRtcChannelMetric|获取频道通信记录详情。|
|DescribeRtcChannelUserList|获取频道通信用户列表。|
|DescribeRtcUserEvents|获取指定用户通话关键事件。|
|DescribeRtcChannelDetail|获取频道详情。|
|DescribeRtcScale|按天获取指定应用通话规模，在每天0点完成前一天的数据统计。|
|DescribeRtcScaleDetail|按分钟获取指定应用通话规模详情。|
|DescribeRtcChannelMetrics|获取用户通话指标。|

关于新版数据服务接口，请参见[API概览](/cn.zh-CN/数据服务API/API概览.md)。

