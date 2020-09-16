# DescribeRtcUserCntData

调用DescribeRtcUserCntData查询应用在一段时间内的活跃用户数，即发生通信的用户终端数。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcUserCntData&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcUserCntData|操作接口名，系统规定参数，取值：**DescribeRtcUserCntData**。 |
|StartTime|String|否|2018-01-29T00:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|否|2018-01-29T00:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。 |
|AppId|String|否|yourAppId|应用ID，仅支持传单个ID。

 默认查询所有应用ID。 |
|ServiceArea|String|否|CN|服务区域。CN：中国（默认值）。 |
|Interval|String|否|3600|查询数据时间粒度，单位：秒。

 取值为**3600**（1小时） 或**86400**（1天），默认为**3600**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|UserCntDataPerInterval|Array| |活跃用户统计数据结构。 |
|UserCntModule| | | |
|ActiveUserCnt|Long|10|当前活跃用户数（基于发生通信的用户终端统计）。 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcUserCntData
&AppId=yourAppId
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcUserCntDataResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <UserCntDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <ActiveUserCnt>10</ActiveUserCnt>
	  </UserCntDataPerInterval>
</DescribeRtcUserCntDataResponse>
```

`JSON` 格式

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "UserCntDataPerInterval": [ 
        {  
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveUserCnt": 10
        }
    ]
}
```

