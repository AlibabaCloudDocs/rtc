# DescribeUsageAreaDistributionStatData

调用DescribeUsageAreaDistributionStatData获取用量统计的地域分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeUsageAreaDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/usage/describeUsageAreaDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|String|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|String|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|ParentArea|String|Query|否|中国|父级地区名称，例如：深圳市的父级为广东省。参数为空表示世界范围（国家维度）的统计，例如：中国、英国。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|UsageAreaStatList|Array of UsageAreaStatData| |用量统计的地域分布数据列表。 |
|Name|String|中国\_浙江省|地域名称。 |
|AudioCallDuration|Integer|160|音频通话时长，单位：分钟。 |
|VideoCallDuration|Integer|17361|视频通话时长，单位：分钟。 |
|TotalCallDuration|Integer|17521|总通话时长，单位：分钟。 |
|RequestId|String|4473A35B-18C1-4D91-A596-32F99C7D1C8B|请求ID。 |

## 示例

请求示例

```
POST /api/usage/describeUsageAreaDistributionStatData?StartDate=1615824000&EndDate=1615910399&ParentArea=中国&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeUsageAreaDistributionStatDataResponse>
    <code>200</code>
    <data>
        <RequestId>4473A35B-18C1-4D91-A596-32F99C7D1C8B</RequestId>
        <UsageAreaStatList>
            <AudioCallDuration>160</AudioCallDuration>
            <TotalCallDuration>17521</TotalCallDuration>
            <VideoCallDuration>17361</VideoCallDuration>
            <Name>中国_浙江省</Name>
        </UsageAreaStatList>
        <UsageAreaStatList>
            <AudioCallDuration>22</AudioCallDuration>
            <TotalCallDuration>2538</TotalCallDuration>
            <VideoCallDuration>2516</VideoCallDuration>
            <Name>中国_北京市</Name>
        </UsageAreaStatList>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>4473A35B-18C1-4D91-A596-32F99C7D1C8B</requestId>
    <successResponse>true</successResponse>
</DescribeUsageAreaDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "4473A35B-18C1-4D91-A596-32F99C7D1C8B",
    "UsageAreaStatList" : [ {
      "AudioCallDuration" : 160,
      "TotalCallDuration" : 17521,
      "VideoCallDuration" : 17361,
      "Name" : "中国_浙江省"
    }, {
      "AudioCallDuration" : 22,
      "TotalCallDuration" : 2538,
      "VideoCallDuration" : 2516,
      "Name" : "中国_北京市"
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "4473A35B-18C1-4D91-A596-32F99C7D1C8B",
  "successResponse" : true
}
```

