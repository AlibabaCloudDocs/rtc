# DescribeRtcPeakChannelCntData {#doc_api_rtc_DescribeRtcPeakChannelCntData .reference}

调用DescribeRtcPeakChannelCntData查询应用在一段时间内的并发频道峰值数量。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcPeakChannelCntData&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcPeakChannelCntData|操作接口名，系统规定参数，取值：**DescribeRtcPeakChannelCntData**。

 |
|AppId|String|否|yourAppId|应用ID，不填返回所有应用的汇总数据。

 |
|EndTime|String|否|2018-01-29T00:00:00Z|结束时间，UTC格式。

 |
|Interval|String|否|3600|时间粒度参数，单位：秒。

 取值为**3600**（小时粒度） 或**86400**（天粒度），默认为**3600**。

 |
|ServiceArea|String|否|cn|服务区域。

 |
|StartTime|String|否|2018-01-29T00:00:00Z|起始时间，UTC格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PeakChannelCntDataPerInterval| | |并发频道峰值数据结构。

 |
|ActiveChannelPeak|Long|10|并发频道峰值数量。

 |
|ActiveChannelPeakTime|String|2018-01-29T00:01:00Z|峰值时刻，UTC格式。

 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcPeakChannelCntData
&AppId=xxx
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcPeakChannelCntDataResesponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <PeakChannelCntDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <ActiveChannelPeak>10</ActiveChannelPeak>
		    <ActiveChannelPeakTime>2018-01-29T00:01:00Z</ActiveChannelPeakTime>
	  </PeakChannelCntDataPerInterval>
</DescribeRtcPeakChannelCntDataResesponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PeakChannelCntDataPerInterval":[
		{
			"TimeStamp":"2018-01-29T00:00:00Z",
			"ActiveChannelPeak":10,
			"ActiveChannelPeakTime":"2018-01-29T00:01:00Z"
		}
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

