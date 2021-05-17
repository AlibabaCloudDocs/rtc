# DescribeChannelOverallData

调用DescribeChannelOverallData查询频道概览数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeChannelOverallData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/channel/describeChannelOverallData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|123333|频道ID。 |
|CreatedTs|Long|Query|是|1615893133|创建频道的时间戳，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615893757|释放频道的时间戳，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。

 **说明：** 如果传入的频道释放时间超过真实的释放时间，将返回从创建时间开始到真实释放时间之间的数据。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MetricDatas|Array of MetricDatas| |指标数据列表。 |
|Type|String|CALL\_QUALITY|指标类型，取值：

 -   **CALL\_QUALITY**：通信质量。
-   **CONN\_NUM**：加入频道成功用时的区间分布。 |
|Nodes|Array of Nodes| |指标趋势图坐标点列表。 |
|X|String|1612418625|指标趋势图中x轴横坐标。当Type=CALL\_QUALITY时，x轴横坐标表示时间戳，当Type=CONN\_NUM时，x轴横坐标取值：

 -   **WITHIN\_FIVE**：5秒内。
-   **FIVE\_TO\_TEN**：5~10秒。
-   **TEN\_TO\_FIFTEEN**：10~15秒。
-   **ABOVE\_FIFTEEN**：15秒以上。
-   **CONN\_FAIL**：连接失败。 |
|Y|String|123|指标趋势图中y轴纵坐标。 |
|Ext|Map| |扩展数据。 |
|OverallData|object| |概览数据。 |
|ConnAvgTime|Float|0.10325|平均通信连接的用时，单位：秒。 |
|FiveSecJoinRate|Float|1.0|5秒内连通成功率，用小数表示，例如1.0表示连通成功率为100%。 |
|TotalAudioStuckRate|Float|0.02|整体音频卡顿率，用小数表示，例如0.02表示音频卡顿率为2%。 |
|TotalVideoStuckRate|Float|0.02|整体视频卡顿率，用小数表示，例如0.02表示视频卡顿率为2%。 |
|TotalVideoVagueRate|Float|0.02|整体视频模糊率，用小数表示，例如0.02表示视频模糊率为2%。 |
|CallInfo|object| |通信基本信息。 |
|AppId|String|9qb1\*\*\*\*|应用ID。 |
|ChannelId|String|123456|频道ID。 |
|CallStatus|String|IN|通信状态，取值：

 -   **IN**：进行中。
-   **OUT**：已结束。 |
|CreatedTs|Long|1615860711|创建通信的时间戳，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1615860811|释放通信的时间戳，使用UNIX时间戳表示，单位：秒。 |
|Duration|Long|100|通信时长，单位：秒。 |
|RequestId|String|C9F1EB03-1B7E-4115-ABFA-CB945B2348E7|请求ID。 |

## 示例

请求示例

```
POST api/channel/describeChannelOverallData?AppId=9qb1****&ChannelId=123333&CreatedTs=1615893133&DestroyedTs=1615893757 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeChannelOverallDataResponse>
<code>200</code>
<data>
    <RequestId>C9F1EB03-1B7E-4115-ABFA-CB945B2348E7</RequestId>
    <OverallData>
        <ConnAvgTime>0.10325</ConnAvgTime>
        <FiveSecJoinRate>1</FiveSecJoinRate>
    </OverallData>
    <MetricDatas>
        <Type>CONN_NUM</Type>
        <Nodes>
            <Ext>
                <num>4</num>
            </Ext>
            <X>WITHIN_FIVE</X>
            <Y>1.0000</Y>
        </Nodes>
        <Nodes>
            <Ext>
                <num>0</num>
            </Ext>
            <X>FIVE_TO_TEN</X>
            <Y>0.0000</Y>
        </Nodes>
        <Nodes>
            <Ext>
                <num>0</num>
            </Ext>
            <X>TEN_TO_FIFTEEN</X>
            <Y>0.0000</Y>
        </Nodes>
        <Nodes>
            <Ext>
                <num>0</num>
            </Ext>
            <X>ABOVE_FIFTEEN</X>
            <Y>0.0000</Y>
        </Nodes>
        <Nodes>
            <Ext>
                <num>0</num>
            </Ext>
            <X>CONN_FAIL</X>
            <Y>0.0000</Y>
        </Nodes>
    </MetricDatas>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>C9F1EB03-1B7E-4115-ABFA-CB945B2348E7</requestId>
<successResponse>true</successResponse>
</DescribeChannelOverallDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "C9F1EB03-1B7E-4115-ABFA-CB945B2348E7",
    "OverallData" : {
      "ConnAvgTime" : 0.10325,
      "FiveSecJoinRate" : 1.0
    },
    "MetricDatas" : [ {
      "Type" : "CONN_NUM",
      "Nodes" : [ {
        "Ext" : {
          "num" : 4
        },
        "X" : "WITHIN_FIVE",
        "Y" : "1.0000"
      }, {
        "Ext" : {
          "num" : 0
        },
        "X" : "FIVE_TO_TEN",
        "Y" : "0.0000"
      }, {
        "Ext" : {
          "num" : 0
        },
        "X" : "TEN_TO_FIFTEEN",
        "Y" : "0.0000"
      }, {
        "Ext" : {
          "num" : 0
        },
        "X" : "ABOVE_FIFTEEN",
        "Y" : "0.0000"
      }, {
        "Ext" : {
          "num" : 0
        },
        "X" : "CONN_FAIL",
        "Y" : "0.0000"
      } ]
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "C9F1EB03-1B7E-4115-ABFA-CB945B2348E7",
  "successResponse" : true
}
```

