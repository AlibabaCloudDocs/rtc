# DescribeUsageOsSdkVersionDistributionStatData

调用DescribeUsageOsSdkVersionDistributionStatData获取用量统计中各操作系统及SDK版本的分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeUsageOsSdkVersionDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/usage/describeUsageOsSdkVersionDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|UsageOsSdkVersionStatList|Array of UsageOsSdkVersionStatData| |用量统计中操作系统及SDK版本的数据列表。 |
|Name|String|2.1.2104|SDK版本名称。 |
|Os|String|macOS|操作系统，例如iOS、Android等。 |
|AudioCallDuration|Long|0|音频通话时长，单位：分钟。 |
|VideoCallDuration|Long|1720|视频通话时长，单位：分钟。 |
|TotalCallDuration|Long|1720|总通话时长，单位：分钟。 |
|CallDurationRatio|String|0.0768|通话时长占比，用四位小数表示，例如1.0000表示通话时长占比为100%。 |
|RequestId|String|579EA10B-8B89-449E-88E0-D362C76EAC62|请求ID。 |

## 示例

请求示例

```
POST /api/usage/describeUsageOsSdkVersionDistributionStatData?StartDate=1615824000&EndDate=1615910399&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeUsageOsSdkVersionDistributionStatDataResponse>
    <code>200</code>
    <data>
        <RequestId>579EA10B-8B89-449E-88E0-D362C76EAC62</RequestId>
        <UsageOsSdkVersionStatList>
            <AudioCallDuration>0</AudioCallDuration>
            <TotalCallDuration>1720</TotalCallDuration>
            <CallDurationRatio>0.0768</CallDurationRatio>
            <VideoCallDuration>1720</VideoCallDuration>
            <Os>macOS</Os>
            <Name>2.1.2104</Name>
        </UsageOsSdkVersionStatList>
        <UsageOsSdkVersionStatList>
            <AudioCallDuration>0</AudioCallDuration>
            <TotalCallDuration>1490</TotalCallDuration>
            <CallDurationRatio>0.0665</CallDurationRatio>
            <VideoCallDuration>1490</VideoCallDuration>
            <Os>macOS</Os>
            <Name>1.19.2</Name>
        </UsageOsSdkVersionStatList>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>579EA10B-8B89-449E-88E0-D362C76EAC62</requestId>
    <successResponse>true</successResponse>
</DescribeUsageOsSdkVersionDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "579EA10B-8B89-449E-88E0-D362C76EAC62",
    "UsageOsSdkVersionStatList" : [ {
      "AudioCallDuration" : 0,
      "TotalCallDuration" : 1720,
      "CallDurationRatio" : "0.0768",
      "VideoCallDuration" : 1720,
      "Os" : "macOS",
      "Name" : "2.1.2104"
    }, {
      "AudioCallDuration" : 0,
      "TotalCallDuration" : 1490,
      "CallDurationRatio" : "0.0665",
      "VideoCallDuration" : 1490,
      "Os" : "macOS",
      "Name" : "1.19.2"
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "579EA10B-8B89-449E-88E0-D362C76EAC62",
  "successResponse" : true
}
```

