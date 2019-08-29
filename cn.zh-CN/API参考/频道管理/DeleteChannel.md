# DeleteChannel {#doc_api_rtc_DeleteChannel .reference}

调用DeleteChannel删除频道。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DeleteChannel&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteChannel|操作接口名，系统规定参数，取值：**DeleteChannel**。

 |
|AppId|String|是|yourAppId|应用ID，通过控制台开通创建。

 |
|ChannelId|String|是|yourChannelId|频道ID，加入的频道。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CF8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com/?Action=DeleteChannel
&AppId=xxx
&ChannelId=xxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteChannelResesponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CF8</RequestId>
</DeleteChannelResesponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

