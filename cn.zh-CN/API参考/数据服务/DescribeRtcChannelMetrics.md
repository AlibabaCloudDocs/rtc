# DescribeRtcChannelMetrics

调用DescribeRtcChannelMetrics获取用户通话指标。

该接口若同时查询PubUid和SubUid，则返回两个用户之间的通话指标，若只查询PubUid，则返回发布端用户的通话指标。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelMetrics&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelMetrics|操作接口名，系统规定参数，取值：**DescribeRtcChannelMetrics**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|ChannelId|String|是|yourChannelId|频道ID。 |
|PubUid|String|是|yourPubUid|发布端用户ID。 |
|StartTime|String|是|2020-02-04T05:00:00Z|起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|是|2020-02-04T05:10:00Z|结束时间，UTC 格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间和开始时间之差不能超过1800秒。 |
|SubUid|String|否|yourSubUid|接收端用户ID 。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Metrics|Array of Metric| |指标列表。 |
|KVs|List|\["1604415274","WiFi"\]|指标键值对。 |
|Mid|String|1001|指标ID。取值请参见Metric码。 |
|Uid|String|yourUid|用户ID。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID、 |

## Metric码

|Mid

|语义 |
|-----|----|
|1001

|网络类型。 |
|1002

|用户地域。 |
|1003

|APP CPU占用率，单位：百分比。 |
|1004

|系统 CPU占用率，单位：百分比。 |
|1005

|上行RTT（网络延迟）。 |
|1006

|下行RTT（网络延迟）。 |
|2001

|频道采集音量，取值范围：**0**~**32767**。 |
|2002

|频道播放音量，取值范围：**0**~**32767**。 |
|2003

|音频发送码率，单位：Kbps。 |
|2004

|音频接收码率，单位：Kbps。 |
|2006

|1秒中音频渲染卡顿时间，单位：ms。 |
|2007

|音频上行丢包率，单位：百分比。 |
|2008

|音频下行丢包率，单位：百分比。 |
|3001

|small视频流采集帧率，单位：FPS。 |
|3003

|small视频流发送帧率，单位：FPS。 |
|3004

|small视频流接收帧率，单位：FPS。 |
|3006

|1秒中small视频渲染卡顿时间，单位：ms。 |
|3007

|small视频流发送码率，单位：Kbps。 |
|3008

|small视频流接收码率，单位：Kbps。 |
|3011

|small视频流分辨率的宽。 |
|3012

|small视频流分辨率的高。 |
|3101

|large视频流采集帧率，单位：FPS。 |
|3103

|large视频流发送帧率，单位：FPS。 |
|3104

|large视频流接收帧率，单位：FPS。 |
|3106

|1秒中large视频渲染卡顿时间，单位：ms。 |
|3107

|large视频流发送码率，单位：Kbps。 |
|3108

|large视频流接收码率，单位：Kbps。 |
|3111

|large视频流分辨率的宽。 |
|3112

|large视频流分辨率的高。 |
|3201

|super视频流采集帧率，单位：FPS。 |
|3203

|super视频流发送帧率，单位：FPS。 |
|3204

|super视频流接收帧率，单位：FPS。 |
|3206

|1秒中super视频渲染卡顿时间，单位：ms。 |
|3207

|super视频流发送码率，单位：Kbps。 |
|3208

|super视频流接收码率，单位：Kbps。 |
|3211

|super视频流分辨率的宽。 |
|3212

|super视频流分辨率的高。 |
|3301

|share视频流采集帧率，单位：FPS。 |
|3303

|share视频流发送帧率，单位：FPS。 |
|3304

|share视频流接收帧率，单位：FPS。 |
|3306

|1秒中share视频渲染卡顿时间，单位：ms。 |
|3307

|share视频流发送码率，单位：Kbps。 |
|3308

|share视频流接收码率，单位：Kbps。 |
|3311

|share视频流分辨率的宽。 |
|3312

|share视频流分辨率的高。 |
|3401

|视频流上行丢包率，单位：百分比。 |
|3402

|视频流下行丢包率，单位：百分比。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcChannelMetrics
&AppId=yourAppId
&ChannelId=yourChannelId
&PubUid=yourPubUid
&StartTime=2020-02-04T05:00:00Z
&EndTime=2020-02-04T05:10:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelMetricsResponse>
<RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
<Metrics>
    <Uid>xx</Uid>
    <Mid>1001</Mid>
    <KVs>
        <0>1604415274</0>
        <1>WiFi</1>
    </KVs>
</Metrics>
</DescribeRtcChannelMetricsResponse>
```

`JSON` 格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "Metrics":[
        {
            "Uid":"yourUid",
            "Mid":"1001",
            "KVs":[
                [
                    "1604415274",
                    "WiFi"
                ]
            ]
        }
    ]
}
```

