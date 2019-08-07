# DescribeRtcUserCntData {#doc_api_rtc_DescribeRtcUserCntData .reference}

调用DescribeRtcUserCntData查询应用在一段时间内的活跃用户数，即发生通信的用户终端数。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcUserCntData&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcUserCntData|操作接口名，系统规定参数，取值：**DescribeRtcUserCntData**。

 |
|AppId|String|否|AppId|应用id，不填则返回所有AppId的汇总数据。

 |
|EndTime|String|否|2018-01-29T00:00:00Z|结束时间，UTC格式。

 |
|Interval|String|否|3600|时间粒度参数，取值为**3600**（小时粒度） 或**86400**（天粒度），默认为**3600**。

 |
|ServiceArea|String|否|cn|服务区域。

 |
|StartTime|String|否|2018-01-29T00:00:00Z|起始时间，UTC格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|该条任务请求Id。

 |
|UserCntDataPerInterval| | |活跃用户统计数据结构。

 |
|ActiveUserCnt|Long|10|当前活跃用户数（基于发生通信的用户终端统计）。

 |
|TimeStamp|String|2018-01-29T00:00:00Z|时间戳，UTC格式。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcUserCntData
&AppId=xxx
&StartTime=2018-01-29T00:00:00Z
&EndTime=2018-01-30T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcUserCntDataResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <UserCntDataPerInterval>
		    <TimeStamp>2018-01-29T00:00:00Z</TimeStamp>
		    <ActiveUserCnt>10</ActiveUserCnt>
	  </UserCntDataPerInterval>
</DescribeRtcUserCntDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"UserCntDataPerInterval":[
		{
			"ActiveUserCnt":10,
			"TimeStamp":"2018-01-29T00:00:00Z"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

