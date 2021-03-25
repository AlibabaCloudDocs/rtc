# DescribeChannelUserMetrics

调用DescribeChannelUserMetrics查询频道概览中的用户数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeChannelUserMetrics&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/channel/describeChannelUserMetrics HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|123333|频道ID。 |
|CreatedTs|Long|Query|是|1615893133|频道的创建时间戳，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615893757|频道的释放时间戳，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MetricDatas|Array of MetricDatas| |指标数据列表。 |
|Type|String|ALL\_NUM|指标类型，取值：

 -   **ALL\_NUM**：单位时间内的用户数量。
-   **PUB\_NUM**：单位时间内发布端的用户数量。
-   **SUB\_NUM**：单位时间内订阅端的用户数量。
-   **JOIN\_FAIL\_NUM**：单位时间内加入频道异常的用户数量。
-   **BAD\_EXP\_NUM**：单位时间内通信体验异常的用户数量。 |
|Nodes|Array of Nodes| |指标趋势图坐标点列表。 |
|X|String|1612418625|指标趋势图中x轴横坐标。 |
|Y|String|123|指标趋势图中y轴纵坐标。 |
|Ext|Map| |拓展属性。 |
|OverallData|object| |概览数据。 |
|TotalUserNum|Long|4|累计用户数量。 |
|TotalPubUserNum|Long|4|累计发布端用户数量。 |
|TotalSubUserNum|Long|1|累计订阅端用户数量。 |
|TotalJoinFailNum|Long|0|累计加入频道异常用户数量。 |
|TotalBadExpNum|Long|0|累计通信体验异常用户数量。 |
|RequestId|String|F10D39C3-B58B-4A74-89B5-34162BA121E7|请求ID。 |

## 示例

请求示例

```
POST api/channel/describeChannelUserMetrics?AppId=9qb1****&ChannelId=123333&CreatedTs=1615893133&DestroyedTs=1615893757 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeChannelUserMetricsResponse>
<code>200</code>
<data>
    <RequestId>F10D39C3-B58B-4A74-89B5-34162BA121E7</RequestId>
    <OverallData>
        <TotalBadExpNum>0</TotalBadExpNum>
        <TotalPubUserNum>4</TotalPubUserNum>
        <TotalJoinFailNum>0</TotalJoinFailNum>
        <TotalUserNum>4</TotalUserNum>
        <TotalSubUserNum>1</TotalSubUserNum>
    </OverallData>
    <MetricDatas>
        <Type>ALL_NUM</Type>
        <Nodes>
            <X>1615893133</X>
            <Y>1</Y>
        </Nodes>
        <Nodes>
            <X>1615893139</X>
            <Y>2</Y>
        </Nodes>
        <Nodes>
            <X>1615893757</X>
        </Nodes>
    </MetricDatas>
    <MetricDatas>
        <Type>JOIN_FAIL_NUM</Type>
        <Nodes>
            <X>1615893133</X>
            <Y>0</Y>
        </Nodes>
        <Nodes>
            <X>1615893289</X>
            <Y>0</Y>
        </Nodes>
        <Nodes>
            <X>1615893601</X>
            <Y>0</Y>
        </Nodes>
        <Nodes>
            <X>1615893757</X>
            <Y>0</Y>
        </Nodes>
    </MetricDatas>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>F10D39C3-B58B-4A74-89B5-34162BA121E7</requestId>
<successResponse>true</successResponse>
</DescribeChannelUserMetricsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "F10D39C3-B58B-4A74-89B5-34162BA121E7",
    "OverallData" : {
      "TotalBadExpNum" : 0,
      "TotalPubUserNum" : 4,
      "TotalJoinFailNum" : 0,
      "TotalUserNum" : 4,
      "TotalSubUserNum" : 1
    },
    "MetricDatas" : [ {
      "Type" : "ALL_NUM",
      "Nodes" : [ {
        "X" : "1615893133",
        "Y" : "1"
      }, {
        "X" : "1615893139",
        "Y" : "2"
      }, {
        "X" : "1615893757"
      } ]
    }, {
      "Type" : "JOIN_FAIL_NUM",
      "Nodes" : [ {
        "X" : "1615893133",
        "Y" : "0"
      }, {
        "X" : "1615893289",
        "Y" : "0"
      }, {
        "X" : "1615893601",
        "Y" : "0"
      }, {
        "X" : "1615893757",
        "Y" : "0"
      } ]
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "F10D39C3-B58B-4A74-89B5-34162BA121E7",
  "successResponse" : true
}
```

