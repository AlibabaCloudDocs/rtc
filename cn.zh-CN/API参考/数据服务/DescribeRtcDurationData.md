# DescribeRtcDurationData

调用DescribeRtcDurationData获取应用在一段时间内按照音视频规格进行统计的累计通信时长。

**说明：** 数据查询的起止时间跨度最大为30天。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcDurationData&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcDurationData|操作接口名，系统规定参数，取值：**DescribeRtcDurationData**。 |
|StartTime|String|否|2020-02-04T05:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|否|2020-02-04T07:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。 |
|AppId|String|否|yourAppId|应用ID，仅支持传单个ID。

 默认查询所有应用ID。 |
|ServiceArea|String|否|CN|服务区域，CN：中国（默认值）。 |
|Interval|String|否|3600|查询数据的时间粒度，单位：秒。

 取值为**3600**（1小时）或**86400**（1天），默认为**3600**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DurationDataPerInterval|Array of DurationModule| |通信时长统计信息。 |
|DurationModule| | | |
|AudioDuration|Long|200|纯音频通信时长，单位：分钟。 |
|ContentDuration|Long|200|屏幕共享时长，单位：分钟。 |
|TimeStamp|String|2020-02-04T05:00:00Z|时间戳，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|TotalDuration|Long|1000|通信总时长，单位：分钟。 |
|V1080Duration|Long|300|全高清通信时长，视频分辨率为1920X1080及以下，单位：分钟。 |
|V360Duration|Long|300|标清通信时长，视频分辨率为640X480及以下，单位：分钟。 |
|V720Duration|Long|200|高清通信时长，视频分辨率为1280X720及以下，单位：分钟。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcDurationData
&AppId=yourAppId
&StartTime=2020-02-04T05:00:00Z
&EndTime=2020-02-04T07:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcDurationDataResponse>
  <RequestId>8D49CBEB-84E5-4847-AD5E-1EE4B235034E</RequestId>
  <DurationDataPerInterval>
        <DurationModule>
              <ContentDuration>0</ContentDuration>
              <V360Duration>0</V360Duration>
              <V720Duration>0</V720Duration>
              <V1080Duration>0</V1080Duration>
              <TimeStamp>2020-02-04T05:00:00Z</TimeStamp>
              <TotalDuration>0</TotalDuration>
              <AudioDuration>0</AudioDuration>
        </DurationModule>
        <DurationModule>
              <ContentDuration>0</ContentDuration>
              <V360Duration>0</V360Duration>
              <V720Duration>0</V720Duration>
              <V1080Duration>0</V1080Duration>
              <TimeStamp>2020-02-04T06:00:00Z</TimeStamp>
              <TotalDuration>0</TotalDuration>
              <AudioDuration>0</AudioDuration>
        </DurationModule>
  </DurationDataPerInterval>
</DescribeRtcDurationDataResponse>
```

`JSON` 格式

```
{
	"RequestId": "8D49CBEB-84E5-4847-AD5E-1EE4B235034E",
	"DurationDataPerInterval": {
		"DurationModule": [
			{
				"ContentDuration": 0,
				"V360Duration": 0,
				"V720Duration": 0,
				"V1080Duration": 0,
				"TimeStamp": "2020-02-04T05:00:00Z",
				"TotalDuration": 0,
				"AudioDuration": 0
			},
			{
				"ContentDuration": 0,
				"V360Duration": 0,
				"V720Duration": 0,
				"V1080Duration": 0,
				"TimeStamp": "2020-02-04T06:00:00Z",
				"TotalDuration": 0,
				"AudioDuration": 0
			}
		]
	}
}
```

