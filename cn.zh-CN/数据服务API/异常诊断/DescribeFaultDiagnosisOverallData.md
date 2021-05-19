# DescribeFaultDiagnosisOverallData

调用DescribeFaultDiagnosisOverallData获取异常诊断的概览数据。

**说明：** 支持查询最近48小时且查询范围不超过24小时的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeFaultDiagnosisOverallData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/diagnosis/describeFaultDiagnosisOverallData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |
|StartTs|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndTs|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|StatDim|String|Query|是|JOIN\_SLOW\_USER|统计维度，取值：

 -   **JOIN\_SLOW\_USER**：进频道慢人次。
-   **AUDIO\_STUCK\_USER**：音频卡顿用户数。
-   **VIDEO\_STUCK\_USER**：视频卡顿用户数。
-   **VIDEO\_VAGUE\_USER**：视频模糊用户数。
-   **HIGH\_DELAY\_USER**：通话延迟高用户数。
-   **FIRST\_FRAME\_SLOW\_USER**：接收首屏慢人次。

 关于统计维度详情，请参见[异常类型说明](~~217966~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OverallData|Object| |异常诊断的概览数据列表。 |
|FaultUserCount|Integer|3|异常人次或异常用户数。 |
|TotalUserCount|Integer|1027|总人次或总用户数。 |
|FaultUserRatio|Float|0.0029|异常用户总占比。 |
|MetricData|Object| |异常指标数据。 |
|Nodes|Array of Node| |指标趋势图坐标点列表。 |
|X|String|1620725400|指标趋势图中x轴横坐标，单位时间为1分钟。 |
|Y|String|1|指标趋势图中y轴纵坐标。 |
|Ext|Map| |拓展属性。其中，ratio表示单位时间内异常用户占比；totalCount表示单位时间内用户总数。 |
|RequestId|String|1C24B3B5-E41A-45CE-844D-D3C578B97AA6|请求ID。 |

## 示例

请求示例

```
POST /api/diagnosis/describeFaultDiagnosisOverallData?AppId=0rbd****&StartTs=1615824000&EndTs=1615910399&StatDim=JOIN_SLOW_USER HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeFaultDiagnosisOverallDataResponse>
    <code>200</code>
    <data>
        <RequestId>1C24B3B5-E41A-45CE-844D-D3C578B97AA6</RequestId>
        <OverallData>
            <FaultUserCount>3</FaultUserCount>
            <FaultUserRatio>0.0029</FaultUserRatio>
            <TotalUserCount>1027</TotalUserCount>
        </OverallData>
        <MetricData>
            <Nodes>
                <Ext>
                    <totalCount>2</totalCount>
                    <ratio>0.5</ratio>
                </Ext>
                <X>1620725400</X>
                <Y>1</Y>
            </Nodes>
            <Nodes>
                <Ext>
                    <totalCount>1</totalCount>
                    <ratio>1</ratio>
                </Ext>
                <X>1620738780</X>
                <Y>1</Y>
            </Nodes>
            <Nodes>
                <Ext>
                    <totalCount>1</totalCount>
                    <ratio>1</ratio>
                </Ext>
                <X>1620739140</X>
                <Y>1</Y>
            </Nodes>
        </MetricData>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>1C24B3B5-E41A-45CE-844D-D3C578B97AA6</requestId>
    <successResponse>true</successResponse>
</DescribeFaultDiagnosisOverallDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "1C24B3B5-E41A-45CE-844D-D3C578B97AA6",
    "OverallData" : {
      "FaultUserCount" : 3,
      "FaultUserRatio" : 0.0029,
      "TotalUserCount" : 1027
    },
    "MetricData" : {
      "Nodes" : [ {
        "Ext" : {
          "totalCount" : 2,
          "ratio" : "0.5"
        },
        "X" : "1620725400",
        "Y" : "1"
      }, {
        "Ext" : {
          "totalCount" : 1,
          "ratio" : "1"
        },
        "X" : "1620738780",
        "Y" : "1"
      }, {
        "Ext" : {
          "totalCount" : 1,
          "ratio" : "1"
        },
        "X" : "1620739140",
        "Y" : "1"
      } ]
    }
  },
  "httpStatusCode" : "200",
  "requestId" : "1C24B3B5-E41A-45CE-844D-D3C578B97AA6",
  "successResponse" : true
}
```

