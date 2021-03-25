# DescribeRtcChannels

调用DescribeRtcChannels获取频道通信记录列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannels&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannels|操作接口名。系统规定参数，取值：**DescribeRtcChannels**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|StartTime|String|是|2018-01-29T05:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|是|2018-01-29T06:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。 |
|ChannelId|String|否|yourChannelId|频道ID，仅支持传单个ID。 |
|PageSize|Integer|否|10|每页显示数量。默认为**10**，取值范围：**5**~**20**。 |
|PageNo|Integer|否|1|页码。默认值**1**，取值范围：**0**~**3000**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Channels|Array of Channel| |频道列表。 |
|ChannelId|String|yourChannelId|频道ID。 |
|EndTime|String|2018-01-29T06:00:00Z|频道结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|Finished|Boolean|true|频道是否已经结束。取值：

 -   **true**：已经结束。
-   **false**：还未结束。 |
|StartTime|String|2018-01-29T05:00:00Z|频道开始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|PageSize|Long|10|每页显示数量。 |
|PageNo|Long|0|页码。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|TotalCnt|Long|1000|总页数。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcChannels
&AppId=yourAppId
&StartTime=2018-01-29T05:00:00Z
&EndTime=2018-01-29T06:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelsResponse>
  <TotalCnt>1000</TotalCnt>
  <PageSize>10</PageSize>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
  <PageNo>0</PageNo>
  <Channels>
        <StartTime>2018-01-29T05:00:00Z</StartTime>
        <Finished>true</Finished>
        <EndTime>2018-01-29T06:00:00Z</EndTime>
        <ChannelId>yourChannelId</ChannelId>
  </Channels>
</DescribeRtcChannelsResponse>
```

`JSON` 格式

```
{"TotalCnt":"1000",
"PageSize":"10",
"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"PageNo":"0",
"Channels":[{
    "StartTime":"2018-01-29T05:00:00Z",
    "Finished":"true",
    "EndTime":"2018-01-29T06:00:00Z",
    "ChannelId":"yourChannelId"
    }]
}
```

