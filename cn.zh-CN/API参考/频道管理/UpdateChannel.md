# UpdateChannel

调用UpdateChannel刷新频道信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=UpdateChannel&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateChannel|操作接口名，系统规定参数，取值：**UpdateChannel**。 |
|AppId|String|是|aoe\*\*\*\*|应用ID，通过控制台开通创建。 |
|ChannelId|String|是|testId|频道ID，仅支持传单个ID。 |
|Nonce|String|是|as213hhd\*\*\*\*|频道原有随机码。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Nonce|String|072a9f56ca9ce380a22f6447f7e\*\*\*\*|刷新频道生成的随机码。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CF8|请求ID。 |
|Timestamp|Integer|1510545933|刷新频道生成的时间戳，有效期48小时。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=UpdateChannel
&AppId=aoe****
&ChannelId=testId
&Nonce=as213hhd****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateChannelResponse>
    <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CF8</RequestId>
    <Nonce>072a9f56ca9ce380a22f6447f7e****</Nonce>
    <Timestamp>1510545933</Timestamp>
</UpdateChannelResponse>
```

`JSON` 格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8",
    "Nonce":"072a9f56ca9ce380a22f6447f7e****",
    "Timestamp":1510545933
}
```

