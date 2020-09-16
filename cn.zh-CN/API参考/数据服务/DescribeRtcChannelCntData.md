# DescribeRtcChannelCntData

调用DescribeRtcChannelCntData查询应用在一段时间内的活跃频道数，即发生通信的频道数。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelCntData&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelCntData|操作接口名，系统规定参数，取值：**DescribeRtcChannelCntData**。 |
|StartTime|String|否|2018-01-29T00:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|否|2018-01-29T00:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。 |
|AppId|String|否|yourAppId|应用ID，仅支持传单个ID。

 默认查询所有应用ID。 |
|ServiceArea|String|否|CN|服务区域。CN：中国（默认值）。 |
|Interval|String|否|3600|查询数据时间粒度，单位：秒。

 取值为**3600**（1小时）或**86400**（1天），默认为**3600**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelCntDataPerInterval|Array| |活跃频道统计数据结构。 |
|ChannelCntModule| | | |
|ActiveChannelCnt|Long|10|活跃频道数量统计（时间单元累计）。 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcChannelCntData
&AppId=yourAppId
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelCntDataResesponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ChannelCntDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <ActiveChannelCnt>10</ActiveChannelCnt>
	  </ChannelCntDataPerInterval>
</DescribeRtcChannelCntDataResesponse>
```

`JSON` 格式

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "ChannelCntDataPerInterval": [
        {
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveChannelCnt": 10
        }
    ]
}
```

