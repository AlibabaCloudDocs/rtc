# DescribeQualityOverallData

调用DescribeQualityOverallData获取质量统计的概览数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeQualityOverallData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/quality/describeQualityOverallData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|Types|String|Query|是|JOIN\_CHANNEL\_SUC\_RATE|查询的指标类型，多个用英文逗号（,）分隔。

 -   **JOIN\_CHANNEL\_SUC\_RATE**：加入频道成功率。
-   **JOIN\_CHANNEL\_SUC\_FIVE\_SEC\_RATE**：五秒加入频道成功率。
-   **AUDIO\_SPEAK\_OUT\_DUR**：首次出声时间。
-   **VIDEO\_FIRST\_PIC\_DUR**：首次出图时间。
-   **AUDIO\_STUCK\_RATE**：音频卡顿率。
-   **VIDEO\_STUCK\_RATE**：视频卡顿率。
-   **AUDIO\_DELAY**：音频延时。
-   **AUDIO\_DELAY**：视频延时。
-   **AUDIO\_HIGH\_QUALITY\_TRANSMISSION\_RATE**：音频优质传输率。
-   **VIDEO\_HIGH\_QUALITY\_TRANSMISSION\_RATE**：视频优质传输率。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|QualityOverallData|Array of MetricDataItem| |概览数据列表。 |
|Type|String|JOIN\_CHANNEL\_SUC\_RATE|查询的指标类型。 |
|Nodes|Array of Nodes| |指标趋势图坐标点列表。 |
|X|String|1620144000|指标趋势图中x轴横坐标。 |
|Y|String|1.0000|指标趋势图中y轴纵坐标。 |
|Average|String|0.9967|该指标的平均值。 |
|RequestId|String|4F8EE7C0-5B91-4EEF-AAA3-1C8430F6DB13|请求ID。 |

## 示例

请求示例

```
POST /api/quality/describeQualityOverallData?StartDate=1615824000&EndDate=1615910399&Types=JOIN_CHANNEL_SUC_RATE&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeQualityOverallDataResponse>
    <code>200</code>
    <data>
        <QualityOverallData>
            <Type>JOIN_CHANNEL_SUC_RATE</Type>
            <Average>0.9967</Average>
            <Nodes>
                <X>1620144000</X>
                <Y>1.0000</Y>
            </Nodes>
        </QualityOverallData>
        <QualityOverallData>
            <Type>JOIN_CHANNEL_SUC_FIVE_SEC_RATE</Type>
            <Average>0.9937</Average>
            <Nodes>
                <X>1620144000</X>
                <Y>1.0000</Y>
            </Nodes>
        </QualityOverallData>
        <RequestId>4F8EE7C0-5B91-4EEF-AAA3-1C8430F6DB13</RequestId>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>4F8EE7C0-5B91-4EEF-AAA3-1C8430F6DB13</requestId>
    <successResponse>true</successResponse>
</DescribeQualityOverallDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "QualityOverallData" : [ {
      "Type" : "JOIN_CHANNEL_SUC_RATE",
      "Average" : "0.9967",
      "Nodes" : [ {
        "X" : "1620144000",
        "Y" : "1.0000"
      } ]
    }, {
      "Type" : "JOIN_CHANNEL_SUC_FIVE_SEC_RATE",
      "Average" : "0.9937",
      "Nodes" : [ {
        "X" : "1620144000",
        "Y" : "1.0000"
      } ]
    } ],
    "RequestId" : "4F8EE7C0-5B91-4EEF-AAA3-1C8430F6DB13"
  },
  "httpStatusCode" : "200",
  "requestId" : "4F8EE7C0-5B91-4EEF-AAA3-1C8430F6DB13",
  "successResponse" : true
}
```

