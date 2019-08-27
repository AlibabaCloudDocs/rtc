# DescribeRtcChannelMetric {#doc_api_rtc_DescribeRtcChannelMetric .reference}

调用DescribeRtcChannelMetric获取频道通信记录详情，最多支持查询180天内的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelMetric&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelMetric|操作接口名，系统规定参数，取值：**DescribeRtcChannelMetric**。

 |
|AppId|String|是|xxx|应用ID。

 |
|ChannelId|String|是|0101|频道ID。

 |
|TimePoint|String|是|2018-01-29T00:00:00Z|时间点, 天粒度, UTC格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelMetricInfo| | |详细信息。

 |
|ChannelMetric| | |综述信息。

 |
|ChannelId|String|example\_channel|频道ID。

 |
|EndTime|String|2019-06-06T18:57:00Z|用户离开频道时间，UTC格式。

 |
|PubUserCount|Integer|10|曾经进入过频道并且发布过的用户数量。

 |
|StartTime|String|2019-06-06T17:57:00Z|用户加入频道时间，UTC格式。

 |
|SubUserCount|Integer|25|曾经进入过频道并且订阅过的用户数量。

 |
|UserCount|Integer|30|曾经进入过频道的用户数量。

 |
|Duration| | |时长信息。

 |
|PubDuration| | |发布时长信息。

 |
|Audio|Integer|100|音频时长，单位：分钟。

 |
|Content|Integer|100|屏幕分享时长，单位：分钟。

 |
|Video1080|Integer|100|全高清视频时长，单位：分钟。

 |
|Video360|Integer|100|标清视频时长，单位：分钟。

 |
|Video720|Integer|100|高清视频时长，单位：分钟。

 |
|SubDuration| | |订阅时长信息。

 |
|Audio|Integer|100|音频时长，单位：分钟。

 |
|Content|Integer|100|屏幕分享时长，单位：分钟。

 |
|Video1080|Integer|100|全高清视频时长，单位：分钟。

 |
|Video360|Integer|100|标清视频时长，单位：分钟。

 |
|Video720|Integer|100|高清视频时长，单位：分钟。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeRtcChannelMetric
&AppId=xxx
&ChannelId=0101
&TimePoint=2018-01-29T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRtcChannelMetricResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ChannelMetricInfo>
		    <ChannelMetric>
			      <ChannelId>example_channel</ChannelId>
			      <UserCount>30</UserCount>
			      <PubUserCount>10</PubUserCount>
			      <SubUserCount>25</SubUserCount>
			      <StartTime>2019-06-06T17:57:00Z</StartTime>
			      <EndTime>2019-06-06T18:57:00Z</EndTime>
		    </ChannelMetric>
		    <Duration>
			      <PubDuration>
				        <Audio>100</Audio>
				        <Video360>100</Video360>
				        <Video720>100</Video720>
				        <Video1080>100</Video1080>
				        <Content>300</Content>
			      </PubDuration>
			      <SubDuration>
				        <Audio>100</Audio>
				        <Video360>100</Video360>
				        <Video720>100</Video720>
				        <Video1080>100</Video1080>
				        <Content>300</Content>
			      </SubDuration>
		    </Duration>
	  </ChannelMetricInfo>
</DescribeRtcChannelMetricResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"ChannelMetricInfo":{
		"Duration":{
			"SubDuration":{
				"Video1080":100,
				"Video360":100,
				"Video720":100,
				"Content":300,
				"Audio":100
			},
			"PubDuration":{
				"Video1080":100,
				"Video360":100,
				"Video720":100,
				"Content":300,
				"Audio":100
			}
		},
		"ChannelMetric":{
			"ChannelId":"example_channel",
			"UserCount":30,
			"PubUserCount":10,
			"EndTime":"2019-06-06T18:57:00Z",
			"StartTime":"2019-06-06T17:57:00Z",
			"SubUserCount":25
		}
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

