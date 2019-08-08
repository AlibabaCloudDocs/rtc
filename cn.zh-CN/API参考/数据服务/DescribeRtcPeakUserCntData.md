# DescribeRtcPeakUserCntData {#doc_api_rtc_DescribeRtcPeakUserCntData .reference}

调用DescribeRtcPeakUserCntData查询应用在一段时间内的并发通信峰值，一组“发布-订阅”关系被标记为一次通信。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcPeakUserCntData&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcPeakUserCntData|操作接口名。系统规定参数，取值：**DescribeRtcPeakUserCntData**。

 |
|AppId|String|否|yourAppId|应用ID。如果不填，则返回所有AppId的汇总数据。

 |
|EndTime|String|否|2018-01-29T00:00:00Z|结束时间，UTC格式。

 |
|Interval|String|否|3600|时间粒度参数。取值为**3600**（小时粒度）或**86400**（天粒度），默认值为**3600**。

 |
|StartTime|String|否|2018-01-29T00:00:00Z|起始时间，UTC格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PeakUserCntDataPerInterval| | |峰值并发通信统计数据结构。

 |
|ActiveUserPeak|Long|10|峰值时刻的并发通信数。

 |
|ActiveUserPeakTime|String|2018-01-29T00:01:00Z|并发通信峰值时刻，UTC格式。

 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|任务请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcPeakUserCntData
&AppId=xxx
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcPeakUserCntDataResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <PeakUserCntDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <ActiveUserPeak>10</ActiveUserPeak>
		    <ActiveUserPeakTime>2018-01-29T00:01:00Z</ActiveUserPeakTime>
	  </PeakUserCntDataPerInterval>
</DescribeRtcPeakUserCntDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PeakUserCntDataPerInterval":[
		{
			"TimeStamp":"2018-01-29T00:00:00Z",
			"ActiveUserPeakTime":"2018-01-29T00:01:00Z",
			"ActiveUserPeak":10
		}
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

