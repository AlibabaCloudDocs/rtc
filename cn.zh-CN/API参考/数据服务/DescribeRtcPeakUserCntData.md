# DescribeRtcPeakUserCntData

调用DescribeRtcPeakUserCntData查询应用在一段时间内的并发通信峰值，一组“发布-订阅”关系被标记为一次通信。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcPeakUserCntData&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcPeakUserCntData|操作接口名。系统规定参数，取值：**DescribeRtcPeakUserCntData**。 |
|StartTime|String|否|2018-01-29T00:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|否|2018-01-29T01:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。 |
|AppId|String|否|yourAppId|应用ID，不填则返回所有应用的汇总数据。 |
|ServiceArea|String|否|CN|服务区域。CN：中国（默认值）。 |
|Interval|String|否|3600|查询数据时间粒度，单位：秒。

 取值为**3600**（1小时）或**86400**（1天），默认值为**3600**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PeakUserCntDataPerInterval|Array of PeakUserCntModule| |峰值并发通信统计数据结构。 |
|PeakUserCntModule| | | |
|ActiveUserPeak|Long|10|峰值时刻的并发通信数。 |
|ActiveUserPeakTime|String|2018-01-29T00:01:00Z|并发通信峰值时刻，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcPeakUserCntData
&AppId=yourAppId
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcPeakUserCntDataResponse>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
  <PeakUserCntDataPerInterval>
        <PeakUserCntModule>
              <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
              <ActiveUserPeak>10</ActiveUserPeak>
              <ActiveUserPeakTime>2018-01-29T00:01:00Z</ActiveUserPeakTime>
        </PeakUserCntModule>
  </PeakUserCntDataPerInterval>
</DescribeRtcPeakUserCntDataResponse>
```

`JSON` 格式

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "PeakUserCntDataPerInterval": {
        "PeakUserCntModule": [
        {  
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveUserPeak": 10,
            "ActiveUserPeakTime": "2018-01-29T00:01:00Z"
        }
      ]
    }
}
```

