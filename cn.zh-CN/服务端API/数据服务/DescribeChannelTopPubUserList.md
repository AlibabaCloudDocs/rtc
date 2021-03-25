# DescribeChannelTopPubUserList

调用DescribeChannelTopPubUserList获取频道内发布端的用户列表（按用户在线时长降序）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeChannelTopPubUserList&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/channel/describeChannelTopPubUserList HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615893133|创建频道的时间戳，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615893757|释放频道的时间戳，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TopPubUserDetailList|Array of UserDetail| |发布端的用户列表。 |
|UserId|String|d58e3582\*\*\*\*|用户ID。 |
|Location|String|上海市-上海市|地域位置，例如：浙江省-杭州市。 |
|OnlinePeriods|Array of OnlinePeriod| |在线时段信息。 |
|JoinTs|Long|1615893327|加入通话时间，使用UNIX时间戳表示，单位：秒。 |
|LeaveTs|Long|1615893442|离开通话时间，使用UNIX时间戳表示，单位：秒。 |
|CreatedTs|Long|1615893327|第一次加入通话的时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1615893442|最后一次离开通话的时间，使用UNIX时间戳表示，单位：秒。通话未结束时值为0。 |
|OnlineDuration|Long|115|通信时长，单位：秒。 |
|Duration|Long|115|总时长，单位：秒。 |
|RequestId|String|3024CAAA-962D-459F-871B-C263841F264A|请求ID。 |

## 示例

请求示例

```
POST api/channel/describeChannelTopPubUserList?AppId=9qb1****&ChannelId=123333&CreatedTs=1615893133&DestroyedTs=1615893757 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeChannelTopPubUserListResponse>
<code>200</code>
<data>
    <TopPubUserDetailList>
        <DestroyedTs>1615893757</DestroyedTs>
        <UserId>d58e3582****</UserId>
        <Duration>616</Duration>
        <CreatedTs>1615893141</CreatedTs>
        <OnlineDuration>616</OnlineDuration>
        <OnlinePeriods>
            <JoinTs>1615893141</JoinTs>
        </OnlinePeriods>
        <Location>上海市-上海市</Location>
    </TopPubUserDetailList>
    <TopPubUserDetailList>
        <DestroyedTs>1615893442</DestroyedTs>
        <UserId>6af2a3b1bd5a****</UserId>
        <Duration>115</Duration>
        <CreatedTs>1615893327</CreatedTs>
        <OnlineDuration>115</OnlineDuration>
        <OnlinePeriods>
            <LeaveTs>1615893442</LeaveTs>
            <JoinTs>1615893327</JoinTs>
        </OnlinePeriods>
        <Location>上海市-上海市</Location>
    </TopPubUserDetailList>
    <RequestId>3024CAAA-962D-459F-871B-C263841F264A</RequestId>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>3024CAAA-962D-459F-871B-C263841F264A</requestId>
<successResponse>true</successResponse>
</DescribeChannelTopPubUserListResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "TopPubUserDetailList" : [ {
      "DestroyedTs" : 1615893757,
      "UserId" : "d58e3582****",
      "Duration" : 616,
      "CreatedTs" : 1615893141,
      "OnlineDuration" : 616,
      "OnlinePeriods" : [ {
        "JoinTs" : 1615893141
      } ],
      "Location" : "上海市-上海市"
    }, {
      "DestroyedTs" : 1615893442,
      "UserId" : "6af2a3b1bd5a****",
      "Duration" : 115,
      "CreatedTs" : 1615893327,
      "OnlineDuration" : 115,
      "OnlinePeriods" : [ {
        "LeaveTs" : 1615893442,
        "JoinTs" : 1615893327
      } ],
      "Location" : "上海市-上海市"
    } ],
    "RequestId" : "3024CAAA-962D-459F-871B-C263841F264A"
  },
  "httpStatusCode" : "200",
  "requestId" : "3024CAAA-962D-459F-871B-C263841F264A",
  "successResponse" : true
}
```

