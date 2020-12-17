# DescribeRtcChannelDetail

调用DescribeRtcChannelDetail获取频道详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelDetail&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelDetail|操作接口名，系统规定参数，取值：**DescribeRtcChannelDetail**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|ChannelId|String|是|yourChannelId|频道ID。默认返回所有频道ID。 |
|StartTime|String|是|2020-02-04T05:00:00Z|查询数据起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|EndTime|String|是|2020-02-04T06:00:00Z|查询数据结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 结束时间需大于起始时间。结束时间和开始时间之差不能超过1天。 |
|PageNo|Integer|否|1|页码。默认为**1**，取值范围：**0**~**300**。 |
|PageSize|Integer|否|10|每页显示数量。默认为**10**，取值范围：**5**~**20**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|频道ID。 |
|ChannelInfo|Array of Detail| |频道信息。 |
|DeviceType|String|OPPO R11|设备类型。 |
|JoinTime|String|2020-02-04T05:00:00Z|用户入会时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|LeaveTime|String|2020-02-04T06:00:00Z|用户离会时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|OS|String|android|操作系统。 |
|Platform|String|android 8.1.0|平台信息。 |
|SdkVersion|String|1.17.21.2008144|SDK版本。 |
|Sid|String|pOkV7Nfyt7AcCCZwYbyIMjDKvWzR\*\*\*\*|Session ID，用户每一次入会会产生一个全局唯一的Session ID。 |
|Uid|String|28719cc0134711ebaba349c4b5d3\*\*\*\*|参会者ID。 |
|PageNo|Long|0|页码。 |
|PageSize|Long|10|每页显示数量。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|TotalCnt|Long|20|总页数。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeRtcChannelDetail
&AppId=yourAppId
&ChannelId=yourChannelId
&StartTime=2020-02-04T05:00:00Z
&EndTime=2020-02-04T06:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelDetailResponse>
  <TotalCnt>20</TotalCnt>
  <PageSize>10</PageSize>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
  <PageNo>0</PageNo>
  <ChannelInfo>
        <DeviceType>OPPO R11</DeviceType>
        <Uid>28719cc0134711ebaba349c4b5d3****</Uid>
        <LeaveTime>2020-02-04T06:00:00Z</LeaveTime>
        <OS>android</OS>
        <Platform>android 8.1.0</Platform>
        <SdkVersion>1.17.21.2008144</SdkVersion>
        <JoinTime>2020-02-04T05:00:00Z</JoinTime>
        <Sid>pOkV7Nfyt7AcCCZwYbyIMjDKvWzR****</Sid>
  </ChannelInfo>
  <ChannelId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</ChannelId>
</DescribeRtcChannelDetailResponse>
```

`JSON` 格式

```
{"TotalCnt":"20",
"PageSize":"10",
"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"PageNo":"0",
"ChannelInfo":[{
    "DeviceType":"OPPO R11",
    "Uid":"28719cc0134711ebaba349c4b5d3****",
    "LeaveTime":"2020-02-04T06:00:00Z",
    "OS":"android",
    "Platform":"android 8.1.0",
    "SdkVersion":"1.17.21.2008144",
    "JoinTime":"2020-02-04T05:00:00Z",
    "Sid":"pOkV7Nfyt7AcCCZwYbyIMjDKvWzR****"
    }],
    "ChannelId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"}
```

