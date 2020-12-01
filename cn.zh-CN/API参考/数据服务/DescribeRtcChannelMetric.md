# DescribeRtcChannelMetric

调用DescribeRtcChannelMetric获取频道通信记录详情，支持查询近180天内的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelMetric&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelMetric|操作接口名，系统规定参数，取值：**DescribeRtcChannelMetric**。 |
|AppId|String|是|aoe\*\*\*\*|应用ID，可通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|testId|频道ID，仅支持传单个ID。 |
|TimePoint|String|是|2018-01-29T00:00:00Z|查询记录时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 时间粒度为天。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelMetricInfo|Struct| |详细信息。 |
|ChannelMetric|Struct| |频道用户信息。 |
|ChannelId|String|example\_channel|频道ID。 |
|EndTime|String|2019-06-06T18:57:00Z|用户离开频道时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|PubUserCount|Integer|10|曾经进入频道并且成功发布的用户数量。 |
|StartTime|String|2019-06-06T17:57:00Z|用户加入频道时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|SubUserCount|Integer|25|曾经进入频道并且成功订阅的用户数量。 |
|UserCount|Integer|30|曾经进入频道的用户数量。 |
|Duration|Struct| |时长信息。 |
|PubDuration|Struct| |发布时长信息。 |
|Audio|Integer|100|音频时长，单位：分钟。 |
|Content|Integer|100|屏幕分享时长，单位：分钟。 |
|Video1080|Integer|100|全高清视频时长，单位：分钟。 |
|Video360|Integer|100|标清视频时长，单位：分钟。 |
|Video720|Integer|100|高清视频时长，单位：分钟。 |
|SubDuration|Struct| |订阅时长信息。 |
|Audio|Integer|100|音频时长，单位：分钟。 |
|Content|Integer|100|屏幕分享时长，单位：分钟。 |
|Video1080|Integer|100|全高清视频时长，单位：分钟。 |
|Video360|Integer|100|标清视频时长，单位：分钟。 |
|Video720|Integer|100|高清视频时长，单位：分钟。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcChannelMetric
&AppId=aoe****
&ChannelId=testId
&TimePoint=2018-01-29T00:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelMetricResponse>
  <RequestId>F7748E0F-1FC6-4410-9799-19757EF3C837</RequestId>
  <ChannelMetricInfo>
        <ChannelMetric>
              <EndTime>2020-04-14T14:04:00+08:00</EndTime>
              <UserCount>2</UserCount>
              <StartTime>2020-04-14T14:04:00+08:00</StartTime>
              <SubUserCount>2</SubUserCount>
              <ChannelId>example_channel</ChannelId>
              <PubUserCount>2</PubUserCount>
        </ChannelMetric>
        <Duration>
              <SubDuration>
                    <Video720>2</Video720>
                    <Video1080>0</Video1080>
                    <Content>0</Content>
                    <Video360>0</Video360>
                    <Audio>0</Audio>
              </SubDuration>
              <PubDuration>
                    <Video720>2</Video720>
                    <Video1080>0</Video1080>
                    <Content>0</Content>
                    <Video360>0</Video360>
                    <Audio>2</Audio>
              </PubDuration>
        </Duration>
  </ChannelMetricInfo>
</DescribeRtcChannelMetricResponse>
```

`JSON` 格式

```
{
	"RequestId": "F7748E0F-1FC6-4410-9799-19757EF3C837",
	"ChannelMetricInfo": {
		"ChannelMetric": {
			"EndTime": "2020-04-14T14:04:00+08:00",
			"UserCount": 2,
			"StartTime": "2020-04-14T14:04:00+08:00",
			"SubUserCount": 2,
			"ChannelId": "example_channel",
			"PubUserCount": 2
		},
		"Duration": {
			"SubDuration": {
				"Video720": 2,
				"Video1080": 0,
				"Content": 0,
				"Video360": 0,
				"Audio": 0
			},
			"PubDuration": {
				"Video720": 2,
				"Video1080": 0,
				"Content": 0,
				"Video360": 0,
				"Audio": 2
			}
		}
	}
}
```

