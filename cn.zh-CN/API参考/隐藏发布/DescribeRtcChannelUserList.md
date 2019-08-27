# DescribeRtcChannelUserList {#doc_api_rtc_DescribeRtcChannelUserList .reference}

调用DescribeRtcChannelUserList获取频道通信用户列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelUserList&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelUserList|操作接口名，系统规定参数，取值：**DescribeRtcChannelUserList**。

 |
|AppId|String|是|xxx|应用ID。

 |
|PageNo|Long|是|0|页号。

 |
|PageSize|Long|是|100|显示数量。

 |
|TimePoint|String|是|2018-01-29T00:00:00Z|查询时间点日期，时间粒度为天，UTC格式。

 |
|ChannelId|String|否|xx|频道ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNo|Long|0|页号。

 |
|PageSize|Long|100|显示数量。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|TotalCnt|Long|1000|总页数。

 |
|UserList| | |用户列表。

 |
|ChannelId|String|demo\_channel|频道ID。

 |
|EndTime|String|2019-06-07T02:00:00Z|用户加入频道时间，UTC格式。

 |
|PubAudio|Integer|10|发布音频时长，单位：分钟。

 |
|PubContent|Integer|30|发布屏幕共享时长，单位：分钟。

 |
|PubVideo1080|Integer|10|发布1080P视频时长，单位：分钟。

 |
|PubVideo360|Integer|10|发布360P视频时长，单位：分钟。

 |
|PubVideo720|Integer|10|发布720P视频时长，单位：分钟。

 |
|ServiceArea|String|10|服务大区。

 |
|StartTime|String|2019-06-07T01:00:00Z|用户加入频道时间，UTC格式。

 |
|SubAudio|Integer|0|订阅音频时长，单位：分钟。

 |
|SubContent|Integer|10|订阅屏幕共享时长，单位：分钟。

 |
|SubVideo1080|Integer|10|订阅1080P视频时长，单位：分钟。

 |
|SubVideo360|Integer|10|订阅360P视频时长，单位：分钟。

 |
|SubVideo720|Integer|10|订阅720P视频时长，单位：分钟。

 |
|UserId|String|demo\_user|用户ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcChannelList
&AppId=xxx
&ChannelId=xx
&PageNo=1
&PageSize=100
&TimePoint=2018-01-29T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcChannelListResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <UserList>
		    <UserId>demo_user</UserId>
		    <ChannelId>demo_channel</ChannelId>
		    <StartTime>2019-06-07T01:00:00Z</StartTime>
		    <EndTime>2019-06-07T02:00:00Z</EndTime>
		    <ServiceArea>cn</ServiceArea>
		    <SubAudio>10</SubAudio>
		    <PubAudio>30</PubAudio>
		    <SubVideo360>10</SubVideo360>
		    <PubVideo360>30</PubVideo360>
		    <SubVideo720>0</SubVideo720>
		    <PubVideo720>0</PubVideo720>
		    <SubVideo1080>0</SubVideo1080>
		    <PubVideo1080>0</PubVideo1080>
		    <SubContent>0</SubContent>
		    <PubContent>0</PubContent>
	  </UserList>
	  <PageSize>100</PageSize>
	  <PageNo>0</PageNo>
	  <TotalCnt>1000</TotalCnt>
</DescribeRtcChannelListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"UserList":[
		{
			"SubVideo720":0,
			"PubVideo1080":0,
			"SubVideo360":10,
			"SubAudio":10,
			"UserId":"demo_user",
			"ChannelId":"demo_channel",
			"SubVideo1080":0,
			"SubContent":0,
			"PubAudio":30,
			"PubVideo360":30,
			"PubContent":0,
			"EndTime":"2019-06-07T02:00:00Z",
			"PubVideo720":0,
			"StartTime":"2019-06-07T01:00:00Z",
			"ServiceArea":"cn"
		}
	],
	"PageSize":100,
	"PageNo":0,
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"TotalCnt":1000
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

