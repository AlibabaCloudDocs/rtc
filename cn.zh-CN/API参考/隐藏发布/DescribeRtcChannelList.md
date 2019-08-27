# DescribeRtcChannelList {#doc_api_rtc_DescribeRtcChannelList .reference}

调用DescribeRtcChannelList获取频道通信记录列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelList&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelList|操作接口名，系统规定参数，取值：**DescribeRtcChannelList**。

 |
|PageNo|Long|是|1|页号。

 |
|PageSize|Long|是|20|显示数量。

 |
|TimePoint|String|是|2018-01-29T00:00:00Z|查询时间点，时间粒度为天，UTC格式。

 |
|AppId|String|否|xxx|应用ID。

 |
|ChannelId|String|否|123|频道ID。

 |
|ServiceArea|String|否|cn|服务区域，不填表示所有区域。

 |
|SortType|String|否|desc|排序顺序，默认按**starttime**逆序。

 |
|UserId|String|否|a123|用户ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelList| | |通信记录。

 |
|CallArea| |cn|通信区域。

 |
|ChannelId|String|20180129|频道ID。

 |
|EndTime|String|2018-01-29T02:00:00Z|会话结束时间，UTC格式。

 |
|StartTime|String|2018-01-29T01:00:00Z|会话起始时间，UTC格式。

 |
|TotalUserCnt|Long|2|累计用户。

 |
|PageNo|Long|0|页号。

 |
|PageSize|Long|100|显示数量。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|TotalCnt|Long|1000|总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcChannelList
&PageSize=20
&PageNo=1
&TimePoint=2018-01-29T00:00:00Z
&ChannelId=xx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcChannelListResesponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ChannelListChannelInfos>
		    <ChannelListChannelInfo>
			      <ChannelId>20180129</ChannelId>
			      <StartTime>2018-01-29T01:00:00Z</StartTime>
			      <EndTime>2018-01-29T02:00:00Z</EndTime>
			      <TotalUserCnt>2</TotalUserCnt>
			      <CallArea>cn</CallArea>
			      <CallArea>us</CallArea>
		    </ChannelListChannelInfo>
		    <PageSize>100</PageSize>
		    <PageNo>0</PageNo>
		    <TotalCnt>1000</TotalCnt>
	  </ChannelListChannelInfos>
</DescribeRtcChannelListResesponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ChannelListChannelInfos":{
		"PageSize":100,
		"PageNo":0,
		"TotalCnt":1000,
		"ChannelListChannelInfo":[
			{
				"ChannelId":"20180129",
				"CallArea":[
					"cn",
					"us"
				],
				"TotalUserCnt":2,
				"EndTime":"2018-01-29T02:00:00Z",
				"StartTime":"2018-01-29T01:00:00Z"
			}
		]
	},
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

