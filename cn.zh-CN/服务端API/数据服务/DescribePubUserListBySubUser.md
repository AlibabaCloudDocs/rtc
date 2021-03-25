# DescribePubUserListBySubUser

调用DescribePubUserListBySubUser根据订阅端获取通信中发布端用户列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribePubUserListBySubUser&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describePubUserListBySubUser HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615887685|频道创建时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615888615|频道释放时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。 |
|SubUserId|String|Query|是|c906531af5f9\*\*\*\*|订阅端用户ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|SubUserDetail|object| |订阅端用户详细信息。 |
|UserId|String|c906531af5f9\*\*\*\*|用户ID。 |
|Roles|Array of String|SENDER|用户角色，取值：

 -   **SENDER**：发布端。
-   **RECEIVER**：订阅端。 |
|Location|String|浙江省-杭州市|地理位置信息，例如：浙江省-杭州市。 |
|OnlinePeriods|Array of OnlinePeriod| |在线时段信息。 |
|JoinTs|Long|1614936817|加入通话时间，使用UNIX时间戳表示，单位：秒。 |
|LeaveTs|Long|1614936820|离开通话时间，使用UNIX时间戳表示，单位：秒。 |
|CreatedTs|Long|1614936817|第一次加入通话的时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1614936820|最后一次离开通话的时间，使用UNIX时间戳表示，单位：秒。通话未结束时值为0。 |
|OnlineDuration|Long|0|在线时长，单位：秒。 |
|Duration|Long|0|通话时长，首次进入到最后离开，单位：秒。 |
|SdkVersion|String|1.0.0|SDK版本。 |
|Os|String|iOS|操作系统平台，例如iOS、Android等。 |
|Network|String|4G|网络类型，例如WiFi、4G等。 |
|ClientType|String|WEB|端类型，取值：

 -   **WEB**：Web端。
-   **NATIVE**：本地端。 |
|PubUserDetailList|Array of UserDetail| |发布端用户详情信息。 |
|UserId|String|c906531af5f9\*\*\*\*|用户ID。 |
|Roles|Array of String|SENDER|用户角色，取值：

 -   **SENDER**：发起者。
-   **RECEIVER**：接收者。 |
|Location|String|浙江省-杭州市|地理位置信息，例如：浙江省-杭州市。 |
|OnlinePeriods|Array of OnlinePeriod| |在线时段信息。 |
|JoinTs|Long|1615887685|加入通话时间，使用UNIX时间戳表示，单位：秒。 |
|LeaveTs|Long|1614936820|离开通话时间，使用UNIX时间戳表示，单位：秒。 |
|CreatedTs|Long|1615887685|第一次加入通话的时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1615888615|最后一次离开通话的时间，使用UNIX时间戳表示，单位：秒。 |
|OnlineDuration|Long|930|在线时长，单位：秒。 |
|Duration|Long|930|通话时长，首次进入到最后离开，单位：秒。 |
|SdkVersion|String|1.14.7|SDK版本。 |
|Os|String|iOS|操作系统平台，例如iOS、Android等。 |
|Network|String|4G|网络类型，例如WiFi、4G等。 |
|ClientType|String|NATIVE|端类型，取值：

 -   **WEB**：Web端。
-   **NATIVE**：本地端。 |
|CallIdList|Array of String|testcallid|用户通信流的Call ID。 |
|CallStatus|String|OUT|通信状态。取值：

 -   **IN**：进行中。
-   **OUT**：已结束。 |
|RequestId|String|D27DB8B0-73F6-42D0-9AAA-AD77EE3A9B29|请求ID。 |

## 示例

请求示例

```
POST api/call/describePubUserListBySubUser?AppId=9qb1****&ChannelId=311&CreatedTs=1615887685&DestroyedTs=1615888615&SubUserId=c906531af5f9**** HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribePubUserListBySubUserResponse>
<code>200</code>
<data>
    <RequestId>D27DB8B0-73F6-42D0-9AAA-AD77EE3A9B29</RequestId>
    <SubUserDetail>
        <DestroyedTs>1615888615</DestroyedTs>
        <ClientType>WEB</ClientType>
        <Os>Chrome</Os>
        <UserId>c906531af5f92a78</UserId>
        <SdkVersion>1.14.7</SdkVersion>
        <Duration>930</Duration>
        <Roles>SENDER</Roles>
        <CreatedTs>1615887685</CreatedTs>
        <OnlineDuration>930</OnlineDuration>
        <OnlinePeriods>
            <JoinTs>1615887685</JoinTs>
        </OnlinePeriods>
        <Location>浙江省-杭州市</Location>
    </SubUserDetail>
    <CallStatus>OUT</CallStatus>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>D27DB8B0-73F6-42D0-9AAA-AD77EE3A9B29</requestId>
<successResponse>true</successResponse>
</DescribePubUserListBySubUserResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "PubUserDetailList" : [ ],
    "RequestId" : "D27DB8B0-73F6-42D0-9AAA-AD77EE3A9B29",
    "SubUserDetail" : {
      "DestroyedTs" : 1615888615,
      "ClientType" : "WEB",
      "Os" : "Chrome",
      "UserId" : "c906531af5f92a78",
      "SdkVersion" : "1.14.7",
      "Duration" : 930,
      "Roles" : [ "SENDER" ],
      "CreatedTs" : 1615887685,
      "OnlineDuration" : 930,
      "OnlinePeriods" : [ {
        "JoinTs" : 1615887685
      } ],
      "Location" : "浙江省-杭州市"
    },
    "CallStatus" : "OUT"
  },
  "httpStatusCode" : "200",
  "requestId" : "D27DB8B0-73F6-42D0-9AAA-AD77EE3A9B29",
  "successResponse" : true
}
```

