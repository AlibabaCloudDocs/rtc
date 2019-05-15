# UpdateChannel {#reference1888 .reference}

调用UpdateChannel刷新频道信息。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：UpdateChannel。|
|AppId|String|是|应用ID，通过控制台开通创建。|
|ChannelId|String|是|频道ID，用户加入的频道。|
|Nonce|String|是|频道原有随机码。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求ID。|
|Nonce|String|刷新频道生成的随机码。|
|Timestamp|Long|刷新频道生成的时间戳，有效期48小时。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com/?Action=UpdateChannel&AppId=xxx&ChannelId=xxx&Nonce=xxx&<公共请求参数>          
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8",
    "Nonce":"072a9f56ca9ce380a22f6447f7e85fce",
    "Timestamp":1510545933
}          
```

异常返回示例

`JSON`格式

```language-json
{
    "Code":"InternalError",
    "HostId":"rtc.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}     
```

## 特殊错误码 {#section_ms7_z9a_ibn .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|MissingParameter|AppIdis mandatory for this action.|400|AppId缺失。|
|MissingParameter|ChannelIdis mandatory for this action.|400|ChannelId缺失。|
|InvalidAppId.ExceedsMaximum|AppIdshould be less than or equal to 64 bytes.|400|AppId过长。|
|InvalidChannelId.ExceedsMaximum|ChannelId should be less than or equal to 64 bytes.|400|ChannelId过长。|
|InvalidAppId.NotFound|AppIdnot found.|404|AppId不存在。|
|InvalidChannelId.NotFound|ChannelIdnot found.|404|ChannelId不存在。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

