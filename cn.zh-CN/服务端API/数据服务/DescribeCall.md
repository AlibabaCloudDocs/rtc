# DescribeCall

调用DescribeCall获取单次通信详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeCall&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describeCall HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|pdtk\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|1230|频道ID。 |
|CreatedTs|Long|Query|是|1616564129|创建频道时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1616564304|释放频道时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。 |
|ExtDataType|String|Query|否|USER\_DURATION\_STAT|查询的扩展。取值：

 **USER\_DURATION\_STAT**：用户时长统计数据类型。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CallInfo|object| |通信基本信息。 |
|AppId|String|pdtk\*\*\*\*|App ID。 |
|ChannelId|String|1230|频道ID。 |
|CallStatus|String|OUT|通信状态。取值：

 -   **IN**：进行中。
-   **OUT**：已结束。 |
|CreatedTs|Long|1616564129|创建通信时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1616564304|释放通信时间，使用UNIX时间戳表示，单位：秒。 |
|Duration|Long|175|通信持续时长，单位：秒。 |
|UserDetailList|Array of UserDetail| |用户详情列表。 |
|UserId|String|29ebdab59ba8\*\*\*\*|用户ID。 |
|Roles|Array of String|SENDER|用户角色，取值：

 -   **SENDER**：发布端。
-   **RECEIVER**：订阅端。 |
|Location|String|浙江省-杭州市|地理位置信息，例如：浙江省-杭州市。 |
|OnlinePeriods|Array of OnlinePeriod| |在线时段信息。 |
|JoinTs|Long|1616564129|加入通话时间，使用UNIX时间戳表示，单位：秒。 |
|LeaveTs|Long|1616564304|离开通话时间，使用UNIX时间戳表示，单位：秒。 |
|CreatedTs|Long|1616564129|第一次加入通话的时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1616564304|最后一次离开通话的时间，使用UNIX时间戳表示，单位：秒。通话未结束时值为0。 |
|OnlineDuration|Long|175|在线时长，单位：秒。 |
|Duration|Long|0|通话时长，首次进入到最后离开，单位：秒。 |
|SdkVersion|String|2.1.2103191|SDK版本。 |
|Os|String|macOS|浏览器或操作系统类型，例如Chrome、iOS、Android等。

 **说明：** 如果客户端为Web，返回浏览器类型；如果客户端为本地Native端，返回操作系统类型。 |
|Network|String|WiFi|网络类型，例如WiFi，4G等。 |
|CallExp|String|GOOD|通话体验，取值：

 -   **GOOD**：优良。
-   **BAD**：欠佳。 |
|DurMetricStatData|object| |时长统计数据。 |
|PubAudio|Long|0|发布音频时长，单位：秒。 |
|SubAudio|Long|0|订阅音频时长，单位：秒。 |
|PubVideo360|Long|0|发布360P视频时长，单位：秒。 |
|SubVideo360|Long|0|订阅360P视频时长时长，单位：秒。 |
|PubVideo720|Long|0|发布720P视频时长时长，单位：秒。 |
|SubVideo720|Long|0|订阅720P视频时长时长，单位：秒。 |
|PubVideo1080|Long|0|发布1080P视频时长时长，单位：秒。 |
|SubVideo1080|Long|0|订阅1080P视频时长时长，单位：秒。 |
|PubVideoScreenShare|Long|0|发布屏幕共享时长，单位：秒。 |
|SubVideoScreenShare|Long|0|订阅屏幕共享时长，单位：秒。 |
|RequestId|String|EC4960AA-A407-4853-975E-D68F253E18FF|请求ID。 |

## 示例

请求示例

```
POST api/call/describeCall?AppId=pdtk****&ChannelId=1230&CreatedTs=1616564129&DestroyedTs=1616564304 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DscribeCallResponse>
<requestId>EC4960AA-A407-4853-975E-D68F253E18FF</requestId>
<code>200</code>
<message/>
<action/>
<apiName/>
<extendedCode/>
<bizCode/>
<httpStatusCode>200</httpStatusCode>
<data>
    <RequestId>EC4960AA-A407-4853-975E-D68F253E18FF</RequestId>
    <CallInfo>
        <DestroyedTs>1616564304</DestroyedTs>
        <AppId>pdtkb2qy</AppId>
        <CallStatus>OUT</CallStatus>
        <Duration>175</Duration>
        <CreatedTs>1616564129</CreatedTs>
        <ChannelId>1230</ChannelId>
    </CallInfo>
    <UserDetailList>
        <Os>macOS</Os>
        <SdkVersion>2.0.0.210324.dev--release/rtcsdk_v2.0</SdkVersion>
        <Duration>175</Duration>
        <OnlineDuration>175</OnlineDuration>
        <DestroyedTs>1616564304</DestroyedTs>
        <CallExp>GOOD</CallExp>
        <UserId>29ebdab59ba891c3</UserId>
        <Network>WiFi</Network>
        <CreatedTs>1616564129</CreatedTs>
        <OnlinePeriods>
            <LeaveTs>1616564304</LeaveTs>
            <JoinTs>1616564129</JoinTs>
        </OnlinePeriods>
        <Location>浙江省-杭州市</Location>
        <DurMetricStatData/>
    </UserDetailList>
    <UserDetailList>
        <Os>Android</Os>
        <SdkVersion>2.1.2103191</SdkVersion>
        <Duration>112</Duration>
        <OnlineDuration>102</OnlineDuration>
        <DestroyedTs>1616564253</DestroyedTs>
        <CallExp>GOOD</CallExp>
        <UserId>c31b32364ce1</UserId>
        <Network>WiFi</Network>
        <CreatedTs>1616564141</CreatedTs>
        <OnlinePeriods>
            <LeaveTs>1616564207</LeaveTs>
            <JoinTs>1616564141</JoinTs>
        </OnlinePeriods>
        <OnlinePeriods>
            <LeaveTs>1616564253</LeaveTs>
            <JoinTs>1616564217</JoinTs>
        </OnlinePeriods>
        <Location>浙江省-杭州市</Location>
        <DurMetricStatData/>
    </UserDetailList>
</data>
<successResponse>true</successResponse>
</DscribeCallResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "requestId" : "EC4960AA-A407-4853-975E-D68F253E18FF",
  "code" : "200",
  "httpStatusCode" : "200",
  "data" : {
    "RequestId" : "EC4960AA-A407-4853-975E-D68F253E18FF",
    "CallInfo" : {
      "DestroyedTs" : 1616564304,
      "AppId" : "pdtkb2qy",
      "CallStatus" : "OUT",
      "Duration" : 175,
      "CreatedTs" : 1616564129,
      "ChannelId" : "1230"
    },
    "UserDetailList" : [ {
      "Os" : "macOS",
      "SdkVersion" : "2.0.0.210324.dev--release/rtcsdk_v2.0",
      "Duration" : 175,
      "Roles" : [ ],
      "OnlineDuration" : 175,
      "DestroyedTs" : 1616564304,
      "CallExp" : "GOOD",
      "UserId" : "29ebdab59ba891c3",
      "Network" : "WiFi",
      "CreatedTs" : 1616564129,
      "OnlinePeriods" : [ {
        "LeaveTs" : 1616564304,
        "JoinTs" : 1616564129
      } ],
      "Location" : "浙江省-杭州市",
      "DurMetricStatData" : { }
    }, {
      "Os" : "Android",
      "SdkVersion" : "2.1.2103191",
      "Duration" : 112,
      "Roles" : [ ],
      "OnlineDuration" : 102,
      "DestroyedTs" : 1616564253,
      "CallExp" : "GOOD",
      "UserId" : "c31b32364ce1",
      "Network" : "WiFi",
      "CreatedTs" : 1616564141,
      "OnlinePeriods" : [ {
        "LeaveTs" : 1616564207,
        "JoinTs" : 1616564141
      }, {
        "LeaveTs" : 1616564253,
        "JoinTs" : 1616564217
      } ],
      "Location" : "浙江省-杭州市",
      "DurMetricStatData" : { }
    } ]
  },
  "successResponse" : true
}
```

