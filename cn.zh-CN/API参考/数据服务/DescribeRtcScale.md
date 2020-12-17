# DescribeRtcScale

调用DescribeRtcScale获取应用通话规模。按天获取指定应用通话规模，在每天0点完成前一天的数据统计。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcScale&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcScale|操作接口名，系统规定参数，取值：**DescribeRtcScale**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|StartTime|String|是|2020-02-04T05:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|是|2020-02-04T06:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。结束时间和开始时间之差不能超过20天。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|Scale|Array of Scale| |规模列表。 |
|AudioDuration|Long|500|语音通话时长，单位：分钟。 |
|ChannelCount|Long|10|频道数量。 |
|SessionCount|Long|40|通话人次。 |
|Time|String|2020-06-30T00:00:00Z|日期。 |
|UserCount|Long|30|通话人数。 |
|VideoDuration|Long|300|视频通话时长，单位：分钟。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcScale
&AppId=yourAppId
&StartTime=2020-02-04T05:00:00Z
&EndTime=2020-02-04T06:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcScaleResponse>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
  <Scale>
        <VideoDuration>300</VideoDuration>
        <ChannelCount>10</ChannelCount>
        <UserCount>30</UserCount>
        <Time>2020-06-30T00:00:00Z</Time>
        <SessionCount>40</SessionCount>
        <AudioDuration>500</AudioDuration>
  </Scale>
</DescribeRtcScaleResponse>
```

`JSON` 格式

```
{"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"Scale":[{
    "VideoDuration":"300",
    "ChannelCount":"10",
    "UserCount":"30",
    "Time":"2020-06-30T00:00:00Z",
    "SessionCount":"40",
    "AudioDuration":"500"
    }]
}
```

