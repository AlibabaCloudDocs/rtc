# CreateEventSubscribe

调用CreateEventSubscribe创建订阅房间消息的回调。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=CreateEventSubscribe&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateEventSubscribe|操作接口名，系统规定参数，取值：**CreateEventSubscribe**。 |
|AppId|String|是|9qb1\*\*\*\*|订阅的应用ID。 |
|CallbackUrl|String|是|http://\*\*\*\*.com/callback|回调地址。回调内容请参见以下回调内容示例。 |
|ClientToken|String|是|123e4567-e89b-12d3-a456-42665544\*\*\*\*|客户端创建订阅的幂等标识。 |
|Events.N|RepeatList|是|ChannelEvent|订阅的事件，取值：

 -   **ChannelEvent**：频道事件。
-   **UserEvent**：频道内用户事件。

 详细信息请参见以下表格说明。 |
|ChannelId|String|否|123333|订阅的频道ID。

 **说明：** 如果Users.N参数不为空，则此参数必填。 |
|Users.N|RepeatList|否|user1|订阅哪些用户的消息，参数为空表示订阅该房间全部用户。 |

## CallBack

RTC通过用户传入的CallbackUrl，回调用户的内容，示例如下所示：

```

Request:

POST /callbackURL

Body
(x-www-form-urlencoded)

"MsgId": "消息id",
"MsgTimestamp": "消息时间",
"SubscribeId": "订阅者ID",
"AppId": "频道应用ID",
"ChannelId": "频道ID",
"Contents": [
    {
        "Event": "UserEvent",
        "UserEvent": {
            "UserId": "参会用户Id",
            "SessionId": "参会用户SessionId",
            "EventTag": "摄像头开启或者关闭: CameraOpen|CameraClose",
            "Timestamp": "事件发生时间戳"
        },
    {
        "Event": "UserEvent",
        "UserEvent": {
            "UserId": "参会用户Id",
            "SessionId": "参会用户SessionId",
            "EventTag": "入会或者离会: Join|Leave",
            "Timestamp": "事件发生时间戳"
        }
    },
    {
        "Event": "ChannelEvent",,
        "ChannelEvent": {
            "EventTag":"会议开启或关闭: Open|Close",
            "Timestamp": "事件发生时间戳"
        }
    }
]

Response 
HTTP STATUS 200

```

## UserEvent用户事件

|参数

|类型

|是否必须

|描述 |
|----|----|------|----|
|UserId

|string

|是

|用户ID。

| |
|SessionId

|string

|是

|用户SessionID。

| |
|EventTag

|string

|是

|事件类型，取值：

 -   **Join**：入会。
-   **Leave**：离会。
-   **CameraOpen**：摄像头开启。
-   **CameraClose**：摄像头关闭。

| |
|Timestamp

|number

|是

|事件发生的时间戳。

| |

## ChannelEvent频道事件

|参数

|类型

|是否必须

|描述 |
|----|----|------|----|
|EventTag

|string

|是

|事件类型，取值：

 -   **Open**：会议开始。
-   **Close**：会议结束。

| |
|Timestamp

|number

|是

|事件发生的时间戳。

|C |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |
|SubscribeId|String|ad53276431c\*\*\*\*|创建的订阅ID。 |

## 示例

请求示例

```
http(s)://rtc.aliyuncs.com/?Action=CreateEventSubscribe
&AppId=9qb1****
&CallbackUrl=http://****.com/callback
&ClientToken=123e4567-e89b-12d3-a456-42665544****
&Events.1=ChannelEvent
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateEventSubscribeResbonse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
  <SubscribeId>ad53276431c499e</SubscribeId>
</CreateEventSubscribeResbonse>
```

`JSON`格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be", 
  "SubscribeId": "ad53276431c499e"
}
```

