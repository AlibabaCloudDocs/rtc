# DescribeCallList

调用DescribeCallList分页查询时间范围内创建的通信信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeCallList&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describeCallList HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|StartTs|Long|Query|是|1615806196|查询的开始时间，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|EndTs|Long|Query|是|1615892596|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|ChannelId|String|Query|否|311|频道ID。 |
|UserId|String|Query|否|c906531af5f9\*\*\*\*|查询对应此用户ID的通信信息。 |
|CallStatus|String|Query|否|OUT|通信状态。取值：

 -   **IN**：进行中。
-   **OUT**：已结束。 |
|OrderBy|String|Query|否|BAD\_EXP\_USER\_COUNT\_DESC|排序字段。取值：

 -   **BAD\_EXP\_USER\_COUNT\_DESC**：按体验欠佳人数降序。
-   **BAD\_EXP\_USER\_COUNT\_ASC**：按体验欠佳人数升序 |
|QueryMode|String|Query|否|ALL|查询模式。取值：

 -   **ALL**：全部通话。
-   **FOLLOW**：关注通话。 |
|PageNo|Integer|Query|是|1|页码。 |
|PageSize|Integer|Query|是|10|每页数量。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNo|Integer|2|页码。 |
|PageSize|Integer|10|每页数量。 |
|TotalCnt|Integer|20|总数量。 |
|CallList|Array of CallListItem| |通信列表。 |
|AppId|String|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|904|频道ID。 |
|CallStatus|String|OUT|通信状态。 |
|CreatedTs|Long|1615885823|通信的创建时间戳，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1615886028|通信的释放时间戳，使用UNIX时间戳表示，单位：秒。 |
|Duration|Long|205|通信持续时长，单位：秒。 |
|UserCnt|Integer|2|通信用户数。 |
|BadExpUserCnt|Integer|0|通信体验差的用户数。 |
|RequestId|String|231470C1-ACFB-4C9F-844F-4CFE1E3804C5|请求ID。 |

## 示例

请求示例

```
POST api/call/describeCallList?AppId=9qb1****&StartTs=1615806196&EndTs=1615892596&PageNo=1&PageSize=10 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeCallListResponse>
<code>200</code>
<data>
    <CallList>
        <DestroyedTs>1615886028</DestroyedTs>
        <AppId>9qb1****</AppId>
        <BadExpUserCnt>0</BadExpUserCnt>
        <CallStatus>OUT</CallStatus>
        <Duration>205</Duration>
        <CreatedTs>1615885823</CreatedTs>
        <ChannelId>904</ChannelId>
        <UserCnt>2</UserCnt>
    </CallList>
    <CallList>
        <DestroyedTs>1615885133</DestroyedTs>
        <AppId>9qb1****</AppId>
        <BadExpUserCnt>0</BadExpUserCnt>
        <CallStatus>OUT</CallStatus>
        <Duration>845</Duration>
        <CreatedTs>1615884288</CreatedTs>
        <ChannelId>903</ChannelId>
        <UserCnt>11</UserCnt>
    </CallList>
    <RequestId>D8DFED63-7754-4CD6-95B6-9DB46A6578E0</RequestId>
    <TotalCnt>90</TotalCnt>
    <PageSize>10</PageSize>
    <PageNo>1</PageNo>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>D8DFED63-7754-4CD6-95B6-9DB46A6578E0</requestId>
<successResponse>true</successResponse>
</DescribeCallListResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "CallList" : [ {
      "DestroyedTs" : 1615886028,
      "AppId" : "9qb1****",
      "BadExpUserCnt" : 0,
      "CallStatus" : "OUT",
      "Duration" : 205,
      "CreatedTs" : 1615885823,
      "ChannelId" : "904",
      "UserCnt" : 2
    }, {
      "DestroyedTs" : 1615885133,
      "AppId" : "9qb1****",
      "BadExpUserCnt" : 0,
      "CallStatus" : "OUT",
      "Duration" : 845,
      "CreatedTs" : 1615884288,
      "ChannelId" : "903",
      "UserCnt" : 11
    } ],
    "RequestId" : "D8DFED63-7754-4CD6-95B6-9DB46A6578E0",
    "TotalCnt" : 90,
    "PageSize" : 10,
    "PageNo" : 1
  },
  "httpStatusCode" : "200",
  "requestId" : "D8DFED63-7754-4CD6-95B6-9DB46A6578E0",
  "successResponse" : true
}
```

