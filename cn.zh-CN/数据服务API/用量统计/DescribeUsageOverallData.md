# DescribeUsageOverallData

调用DescribeUsageOverallData获取用量统计的概览数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeUsageOverallData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/usage/describeUsageOverallData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|Types|String|Query|是|ONLINE\_USER\_PEAK|查询的指标类型，多个用英文逗号（,）分隔。取值：

 -   **TOTAL\_CALL\_DURATION**：总时长。
-   **VIDEO\_CALL\_DURATION**：视频通信时长。
-   **AUDIO\_CALL\_DURATION**：音频通信时长。
-   **CALL\_CHANNEL\_COUNT**：通信频道数。
-   **HIGHLY\_CONCURRENT\_CHANNEL\_COUNT**：高并发通信频道数。
-   **CHANNEL\_CONCURRENT\_PEAK**：并发频道数峰值。
-   **ONLINE\_USER\_PEAK**：在线人数峰值。
-   **TOTAL\_CALL\_USER**：累计通话人数。
-   **TOTAL\_INOUT\_NUM**：累计进出人次。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|UsageOverallData|Array of MetricDataItem| |用量的概览数据列表。 |
|Type|String|VIDEO\_CALL\_DURATION|查询的指标类型。 |
|Nodes|Array of Nodes| |指标趋势图坐标点列表。 |
|X|String|1620144000|指标趋势图中x轴横坐标。 |
|Y|String|64|指标趋势图中y轴纵坐标。 |
|RequestId|String|51E9F79B-A198-43F0-8E24-1322FAB1E244|请求ID。 |

## 示例

请求示例

```
POST /api/usage/describeUsageOverallData?StartDate=1615824000&EndDate=1615910399&Types=ONLINE_USER_PEAK&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeUsageOverallDataResponse>
    <code>200</code>
    <data>
        <RequestId>51E9F79B-A198-43F0-8E24-1322FAB1E244</RequestId>
        <UsageOverallData>
            <Type>VIDEO_CALL_DURATION</Type>
            <Nodes>
                <X>1620144000</X>
                <Y>64</Y>
            </Nodes>
        </UsageOverallData>
        <UsageOverallData>
            <Type>TOTAL_CALL_DURATION</Type>
            <Nodes>
                <X>1620144000</X>
                <Y>64</Y>
            </Nodes>
        </UsageOverallData>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>51E9F79B-A198-43F0-8E24-1322FAB1E244</requestId>
    <successResponse>true</successResponse>
</DescribeUsageOverallDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "51E9F79B-A198-43F0-8E24-1322FAB1E244",
    "UsageOverallData" : [ {
      "Type" : "VIDEO_CALL_DURATION",
      "Nodes" : [ {
        "X" : "1620144000",
        "Y" : "64"
      } ]
    }, {
      "Type" : "TOTAL_CALL_DURATION",
      "Nodes" : [ {
        "X" : "1620144000",
        "Y" : "64"
      } ]
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "51E9F79B-A198-43F0-8E24-1322FAB1E244",
  "successResponse" : true
}
```

