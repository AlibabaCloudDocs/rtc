# DescribeRtcUserEvents

调用DescribeRtcUserEvents获取指定用户通话关键事件。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcUserEvents&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcUserEvents|操作接口名，系统规定参数，取值：**DescribeRtcUserEvents**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|ChannelId|String|是|yourChannelId|频道ID，仅支持传单个ID。 |
|Uid|String|是|yourUId|用户ID，仅支持传单个ID。 |
|StartTime|String|是|2020-02-04T05:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|是|2020-02-04T05:10:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。结束时间和开始时间之差不能超过1800秒。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Events|Array of Event| |指标列表。 |
|Category|String|通信事件|事件类型。 |
|EventId|String|10030|事件ID。 |
|EventTime|Long|1604415274|时间发生时间，单位：毫秒。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |

|EventId

|语义

|事件类型 |
|---------|----|------|
|10010

|加入房间

|通信事件 |
|10020

|离开房间

|通信事件 |
|10030

|开始发布

|通信事件 |
|10032

|重新发布

|通信事件 |
|10040

|取消发布

|通信事件 |
|10050

|开始订阅

|通信事件 |
|10053

|重新订阅

|通信事件 |
|10060

|取消订阅

|通信事件 |
|11030

|本地媒体静音

|媒体事件 |
|80014

|音频设备开启

|媒体事件 |
|90012

|启动视频采集

|媒体事件 |
|90014

|启动屏幕共享

|媒体事件 |
|90016

|启动视频渲染

|媒体事件 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcUserEvents
&AppId=yourAppId
&ChannelId=yourChannelId
&Uid=yourUId
&StartTime=2020-02-04T05:00:00Z
&EndTime=2020-02-04T05:10:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcUserEventsResponse>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
  <Events>
        <EventId>10030</EventId>
        <Category>通信事件</Category>
        <EventTime>1604415274</EventTime>
  </Events>
</DescribeRtcUserEventsResponse>
```

`JSON` 格式

```
{"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"Events":[{
    "EventId":"10030",
    "Category":"通信事件",
    "EventTime":"1604415274"
    }]}
```

