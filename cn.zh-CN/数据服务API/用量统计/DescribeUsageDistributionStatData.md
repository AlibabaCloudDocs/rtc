# DescribeUsageDistributionStatData

调用DescribeUsageDistributionStatData获取用量统计的分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeUsageDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/usage/describeUsageDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|StatDim|String|Query|是|CHANNEL\_ONLINE|统计维度，取值：

 -   **CHANNEL\_ONLINE**：按照频道在线人数统计。
-   **NETWORK**：按照网络类型统计。
-   **OS**：按照系统类型统计。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|UsageStatList|Array of UsageStatData| |用量统计数据列表。 |
|Name|String|ONE\_TO\_FIVE|统计维度，取值：

 -   当StatDim为CHANNEL\_ONLINE时，取值：**ONE\_TO\_FIVE**（1~5人）、**SIX\_TO\_TEN**（6~10人）、**ELEVEN\_TO\_TWENTY**（11~20人）、**TWENTY\_ONE\_TO\_FIFTY**（21~50人）、**ABOVE\_FIFTY**（50人以上）。
-   当StatDim为NETWORK时，取值：**WiFi**、**4G**等。
-   当StatDim为OS时，取值：**iOS**、**Android**等。 |
|AudioCallDuration|Long|408|音频通话时长，单位：分钟。 |
|VideoCallDuration|Long|45556|视频通话时长，单位：分钟。 |
|TotalCallDuration|Long|45964|总通话时长，单位：分钟。 |
|CallDurationRatio|String|0.9782|通话时长占比，用四位小数表示，例如1.0000表示通话时长占比为100%。 |
|RequestId|String|AAF6805E-D9DF-43E4-B94A-396A7EF69A0A|请求ID。 |

## 示例

请求示例

```
POST /api/usage/describeUsageDistributionStatData?StartDate=1615824000&EndDate=1615910399&StatDim=CHANNEL_ONLINE&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeUsageDistributionStatDataResponse>
    <code>200</code>
    <data>
        <UsageStatList>
            <AudioCallDuration>408</AudioCallDuration>
            <TotalCallDuration>45964</TotalCallDuration>
            <CallDurationRatio>0.9782</CallDurationRatio>
            <VideoCallDuration>45556</VideoCallDuration>
            <Name>ONE_TO_FIVE</Name>
        </UsageStatList>
        <UsageStatList>
            <AudioCallDuration>0</AudioCallDuration>
            <TotalCallDuration>1025</TotalCallDuration>
            <CallDurationRatio>0.0218</CallDurationRatio>
            <VideoCallDuration>1025</VideoCallDuration>
            <Name>SIX_TO_TEN</Name>
        </UsageStatList>
        <RequestId>AAF6805E-D9DF-43E4-B94A-396A7EF69A0A</RequestId>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>AAF6805E-D9DF-43E4-B94A-396A7EF69A0A</requestId>
    <successResponse>true</successResponse>
</DescribeUsageDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "UsageStatList" : [ {
      "AudioCallDuration" : 408,
      "TotalCallDuration" : 45964,
      "CallDurationRatio" : "0.9782",
      "VideoCallDuration" : 45556,
      "Name" : "ONE_TO_FIVE"
    }, {
      "AudioCallDuration" : 0,
      "TotalCallDuration" : 1025,
      "CallDurationRatio" : "0.0218",
      "VideoCallDuration" : 1025,
      "Name" : "SIX_TO_TEN"
    } ],
    "RequestId" : "AAF6805E-D9DF-43E4-B94A-396A7EF69A0A"
  },
  "httpStatusCode" : "200",
  "requestId" : "AAF6805E-D9DF-43E4-B94A-396A7EF69A0A",
  "successResponse" : true
}
```

