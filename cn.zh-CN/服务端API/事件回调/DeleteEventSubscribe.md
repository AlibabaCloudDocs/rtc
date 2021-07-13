# DeleteEventSubscribe

调用DeleteEventSubscribe删除订阅房间消息的回调。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DeleteEventSubscribe&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteEventSubscribe|操作接口名，系统规定参数，取值：**DeleteEventSubscribe**。 |
|AppId|String|是|9qb1\*\*\*\*|应用ID。 |
|SubscribeId|String|是|ad53276431c\*\*\*\*|订阅ID。更多信息，请参见[CreateEventSubscribe](~~274447~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
http(s)://rtc.aliyuncs.com/?Action=DeleteEventSubscribe
&AppId=9qb1****
&SubscribeId=ad53276431c****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteEventSubscribeResponse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</DeleteEventSubscribeResponse>
```

`JSON`格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be" 
}
```

