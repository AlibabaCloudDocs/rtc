# DescribeFaultDiagnosisFactorDistributionStat

调用DescribeFaultDiagnosisFactorDistributionStat获取异常诊断的影响因素分布。

**说明：** 支持查询最近48小时且查询范围不超过24小时的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeFaultDiagnosisFactorDistributionStat&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/diagnosis/describeFaultDiagnosisFactorDistributionStat HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |
|StartTs|Long|Query|是|1615806196|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndTs|Long|Query|是|1615892596|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|StatList|Array of FactorData| |影响因素分布统计数据。 |
|FactorId|String|UNKNOWN|影响因素ID，取值：

 -   **1**：发布端网络差。
-   **2**：订阅端网络差。
-   **3**：发布端设备性能差。
-   **4**：发布端关闭摄像头。
-   **5**：发布端切到后台运行。
-   **UNKNOWN**：未知。 |
|UserCount|Integer|449|影响用户数。 |
|UserRatio|Float|0.9239|影响用户占比。 |
|RequestId|String|D5220A80-94A3-4C3E-B0BC-DD914FB46BE4|请求ID。 |

## 示例

请求示例

```
POST /api/diagnosis/describeFaultDiagnosisFactorDistributionStat?AppId=0rbd****&StartTs=1615806196&EndTs=1615892596 HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeFaultDiagnosisFactorDistributionStatResponse>
    <code>200</code>
    <data>
        <StatList>
            <UserCount>449</UserCount>
            <FactorId>UNKNOWN</FactorId>
            <UserRatio>0.9239</UserRatio>
        </StatList>
        <StatList>
            <UserCount>30</UserCount>
            <FactorId>1</FactorId>
            <UserRatio>0.0617</UserRatio>
        </StatList>
        <StatList>
            <UserCount>4</UserCount>
            <FactorId>4</FactorId>
            <UserRatio>0.0082</UserRatio>
        </StatList>
        <StatList>
            <UserCount>2</UserCount>
            <FactorId>2</FactorId>
            <UserRatio>0.0041</UserRatio>
        </StatList>
        <StatList>
            <UserCount>1</UserCount>
            <FactorId>5</FactorId>
            <UserRatio>0.0021</UserRatio>
        </StatList>
        <RequestId>D5220A80-94A3-4C3E-B0BC-DD914FB46BE4</RequestId>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>D5220A80-94A3-4C3E-B0BC-DD914FB46BE4</requestId>
    <successResponse>true</successResponse>
</DescribeFaultDiagnosisFactorDistributionStatResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "StatList" : [ {
      "UserCount" : 449,
      "FactorId" : "UNKNOWN",
      "UserRatio" : 0.9239
    }, {
      "UserCount" : 30,
      "FactorId" : "1",
      "UserRatio" : 0.0617
    }, {
      "UserCount" : 4,
      "FactorId" : "4",
      "UserRatio" : 0.0082
    }, {
      "UserCount" : 2,
      "FactorId" : "2",
      "UserRatio" : 0.0041
    }, {
      "UserCount" : 1,
      "FactorId" : "5",
      "UserRatio" : 0.0021
    } ],
    "RequestId" : "D5220A80-94A3-4C3E-B0BC-DD914FB46BE4"
  },
  "httpStatusCode" : "200",
  "requestId" : "D5220A80-94A3-4C3E-B0BC-DD914FB46BE4",
  "successResponse" : true
}
```

