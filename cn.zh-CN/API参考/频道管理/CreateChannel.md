# CreateChannel {#reference1942 .reference}

调用CreateChannel创建频道。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：CreateChannel。|
|AppId|String|是|应用ID，通过控制台开通创建。|
|ChannelId|String|是|频道ID，用户加入的频道。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求ID。|
|ChannelKey|String|创建频道生成的密钥。|
|Nonce|String|创建频道生成的随机码。|
|Timestamp|Long|创建频道生成的时间戳，有效期48小时。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com/?Action=CreateChannel&AppId=xxx&ChannelId=xxx&<公共请求参数>            
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8",
    "ChannelKey":"c0e30f7a49bd198e99f7e5b86dcd2378af9b6exxxx",
    "Nonce":"9f96b47103d087db222a25145e834acf",
    "Timestamp":1520996765
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

## 特殊错误码 {#section_dbm_fik_lot .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|MissingParameter|AppIdis mandatory for this action.|400|AppId缺失。|
|MissingParameter|ChannelIdis mandatory for this action.|400|ChannelId缺失。|
|InvalidAppId.ExceedsMaximum|AppIdshould be less than or equal to 64 bytes.|400|AppId过长。|
|InvalidChannelId.ExceedsMaximum|ChannelIdshould be less than or equal to 64 bytes.|400|ChannelId过长。|
|InvalidAppId.NotFound|AppIdnot found.|404|AppId不存在。|
|InvalidChannel.ExceedsMaximum|channel exceeds the maximum.|500|超过频道数量限制。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

