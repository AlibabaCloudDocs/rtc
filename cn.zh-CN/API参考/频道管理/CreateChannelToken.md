# CreateChannelToken {#reference2631 .reference}

调用CreateChannelToken创建频道Token。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：CreateChannelToken。|
|AppId|String|是|应用ID，通过控制台开通创建。|
|ChannelId|String|是|频道ID，用户加入的频道。|
|SessionId|String|是|加入频道会话唯一标识。|
|UId|String|是|用户唯一标识, 由用户生成，保证唯一性。|
|Nonce|String|是|频道随机码。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求ID。|
|ChannelToken|String|频道的签名字符串。|

## 示例 { .section}

请求示例

`JSON`格式

```
https://rtc.aliyuncs.com/?Action=CreateChannelToken&AppId=xxx&ChannelId=xxx&SessionId=xxx&UId=xxx&Nonce=xxx&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8",
    "ChannelToken":"a54d7g3e072a9f56ca9ce347f7e85fce5xxxx"
}
```

异常返回示例

```language-json
{
    "Code":"InternalError",
    "HostId":"rtc.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 特殊错误码 {#section_t28_kk0_t3n .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|MissingParameter|AppIdis mandatory for this action.|400|AppId缺失。|
|MissingParameter|ChannelIdis mandatory for this action.|400|ChannelId缺失。|
|MissingParameter|SessionIdis mandatory for this action.|400|SessionId缺失。|
|MissingParameter|UIdis mandatory for this action.|400|UId缺失。|
|MissingParameter|Nonceis mandatory for this action.|400|Nonce缺失。|
|InvalidAppId.ExceedsMaximum|AppIdshould be less than or equal to 64 bytes.|400|AppId过长。|
|InvalidChannelId.ExceedsMaximum|ChannelIdshould be less than or equal to 64 bytes.|400|ChannelId过长。|
|InvalidChannelId.ExceedsMaximum|SessionIdshould be less than or equal to 32 bytes.|400|SessionId过长。|
|InvalidChannelId.ExceedsMaximum|UId should be less than or equal to 32 bytes.|400|UId过长。|
|InvalidChannelId.ExceedsMaximum|Nonceshould be less than or equal to 64 bytes.|400|Nonce过长。|
|InvalidAppId.NotFound|AppId not found.|404|AppId不存在。|
|InvalidChannelId.NotFound|ChannelId not found.|404|ChannelId不存在。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

