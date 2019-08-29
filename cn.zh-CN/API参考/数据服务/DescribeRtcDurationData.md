# DescribeRtcDurationData {#doc_api_rtc_DescribeRtcDurationData .reference}

调用DescribeRtcDurationData获取应用在一段时间内的累计通信时长，区分音视频规格进行统计。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcDurationData&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcDurationData|操作接口名，系统规定参数，取值：**DescribeRtcDurationData**。

 |
|AppId|String|否|AppId|应用ID，不填则返回所有应用汇总数据。

 |
|EndTime|String|否|2018-01-29T00:00:00Z|结束时间，UTC格式。

 |
|Interval|String|否|3600|时间粒度参数，单位：秒。

 取值为**3600**（小时粒度）或**86400**（天粒度），默认为**3600**。

 |
|ServiceArea|String|否|cn|服务区域。

 |
|StartTime|String|否|2018-01-29T00:00:00Z|起始时间，UTC格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DurationDataPerInterval| | |通信时长统计数据结构。

 |
|AudioDuration|Long|200|纯音频通信时长，音频为基础规格。

 |
|ContentDuration|Long|200|屏幕共享时长，音频为基础规格。

 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式。

 |
|TotalDuration|Long|1000|通信总时长，单位：分钟。

 |
|V1080Duration|Long|300|全高清通信时长，视频为1920X1080及以下，音频为基础规格。

 |
|V360Duration|Long|300|标清通信时长，视频为640X480及以下，音频为基础规格。

 |
|V720Duration|Long|200|高清通信时长，视频为1280X720及以下，音频为基础规格。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcDurationData
&AppId=xxx
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcDurationDataResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <DurationDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <TotalDuration>1000</TotalDuration>
		    <AudioDuration>200</AudioDuration>
		    <V360Duration>300</V360Duration>
		    <V720Duration>300</V720Duration>
		    <V1080Duration>300</V1080Duration>
		    <ContentDuration>200</ContentDuration>
	  </DurationDataPerInterval>
</DescribeRtcDurationDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DurationDataPerInterval":[
		{
			"TimeStamp":"2018-01-29T00:00:00Z",
			"ContentDuration":200,
			"AudioDuration":200,
			"TotalDuration":1000,
			"V1080Duration":300,
			"V360Duration":300,
			"V720Duration":300
		}
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

