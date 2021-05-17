# DescribeEndPointEventList

调用DescribeEndPointEventList获取端对端用户事件列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeEndPointEventList&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describeEndPointEventList HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615887685|创建频道时间，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615888615|释放频道时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。

 **说明：** 如果传入的频道释放时间超过真实的释放时间，将返回从创建时间开始到真实释放时间之间的数据。 |
|UserIdList|String|Query|是|c906531af5f9\*\*\*\*|用户ID列表，多个用英文逗号（,）分隔。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Nodes|Array of Nodes| |用户基本信息列表。 |
|UserId|String|testuserid|用户ID。 |
|EventDataItems|Array of EventDataItems| |事件数据列表。 |
|Ts|Long|1615887685|第一个事件发生的时间，使用UNIX时间戳表示，单位：秒。 |
|EventList|Array of EventList| |事件列表。 |
|EventName|String|开始发布|事件名称。 |
|EventType|String|USER|事件类型，取值：

 -   **USER**：用户事件。
-   **SYSTEM**：系统事件。 |
|Ts|Long|1615887686|事件发生的时间，使用UNIX时间戳表示，单位：秒。 |
|RequestId|String|3CFF4E0E-4F4D-49B6-B4C9-12C97E2F1ECD|请求ID。 |

## 示例

请求示例

```
POST api/call/describeEndPointEventList?AppId=9qb1****&ChannelId=311&UserIdList=c906531af5f9****&CreatedTs=1615887685&DestroyedTs=1615888615 HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeEndPointEventListResponse>
<code>200</code>
<data>
    <RequestId>3CFF4E0E-4F4D-49B6-B4C9-12C97E2F1ECD</RequestId>
    <Nodes>
        <UserId>c906531af5f92a78</UserId>
        <EventDataItems>
            <EventList>
                <EventType>USER</EventType>
                <EventName>开始发布</EventName>
                <Ts>1615887686</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>加入房间成功</EventName>
                <Ts>1615887686</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流</EventName>
                <Ts>1615887698</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>重新订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流</EventName>
                <Ts>1615887705</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>重新订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流</EventName>
                <Ts>1615887706</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>取消订阅流，发布端User ID：8214cf2fe8ffbdd6</EventName>
                <Ts>1615887707</Ts>
            </EventList>
            <Ts>1615887685</Ts>
        </EventDataItems>
        <EventDataItems>
            <EventList>
                <EventType>USER</EventType>
                <EventName>订阅流，来自User ID：c052a4e5e96134e1 的音频流</EventName>
                <Ts>1615887720</Ts>
            </EventList>
            <EventList>
                <EventType>USER</EventType>
                <EventName>取消订阅流，发布端User ID：c052a4e5e96134e1</EventName>
                <Ts>1615887722</Ts>
            </EventList>
            <Ts>1615887710</Ts>
        </EventDataItems>
    </Nodes>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>3CFF4E0E-4F4D-49B6-B4C9-12C97E2F1ECD</requestId>
<successResponse>true</successResponse>
</DescribeEndPointEventListResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "3CFF4E0E-4F4D-49B6-B4C9-12C97E2F1ECD",
    "Nodes" : [ {
      "UserId" : "c906531af5f92a78",
      "EventDataItems" : [ {
        "EventList" : [ {
          "EventType" : "USER",
          "EventName" : "开始发布",
          "Ts" : 1615887686
        }, {
          "EventType" : "USER",
          "EventName" : "加入房间成功",
          "Ts" : 1615887686
        }, {
          "EventType" : "USER",
          "EventName" : "订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流",
          "Ts" : 1615887698
        }, {
          "EventType" : "USER",
          "EventName" : "重新订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流",
          "Ts" : 1615887705
        }, {
          "EventType" : "USER",
          "EventName" : "重新订阅流，来自User ID：8214cf2fe8ffbdd6 的音频流",
          "Ts" : 1615887706
        }, {
          "EventType" : "USER",
          "EventName" : "取消订阅流，发布端User ID：8214cf2fe8ffbdd6",
          "Ts" : 1615887707
        } ],
        "Ts" : 1615887685
      }, {
        "EventList" : [ {
          "EventType" : "USER",
          "EventName" : "订阅流，来自User ID：c052a4e5e96134e1 的音频流",
          "Ts" : 1615887720
        }, {
          "EventType" : "USER",
          "EventName" : "取消订阅流，发布端User ID：c052a4e5e96134e1",
          "Ts" : 1615887722
        } ],
        "Ts" : 1615887710
      } ]
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "3CFF4E0E-4F4D-49B6-B4C9-12C97E2F1ECD",
  "successResponse" : true
}
```

