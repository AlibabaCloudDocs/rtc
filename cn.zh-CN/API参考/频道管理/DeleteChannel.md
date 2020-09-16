# DeleteChannel

调用DeleteChannel删除频道。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DeleteChannel&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteChannel|操作接口名，系统规定参数，取值：**DeleteChannel**。 |
|AppId|String|是|eo85xxxx|应用ID，通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|testid|已加入频道的频道ID，仅支持传单个ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CF8|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DeleteChannel
&AppId=eo85xxxx
&ChannelId=testid
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteChannelResesponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CF8</RequestId>
</DeleteChannelResesponse>
```

`JSON` 格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8"
}
```

