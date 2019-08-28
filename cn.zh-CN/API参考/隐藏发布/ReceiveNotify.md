# ReceiveNotify {#doc_api_rtc_ReceiveNotify .reference}

调用ReceiveNotify接收信令回调信息，专有云信令使用通知消息至SaaS服务。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=ReceiveNotify&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ReceiveNotify|操作接口名，系统规定参数，取值：**ReceiveNotify**。

 |
|BizId|String|是|xxx|aliUID。

 |
|Content|String|是|xxx|透明消息。

 |
|ContentType|String|是|xxx|透明消息类型。

 |
|Event|String|是|join|事件类型，包括：**join**、**leave**、**publish**、**unpublish**、**message**。

 |
|TraceId|String|是|xxx|该条任务请求ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|TraceId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|该条任务请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=ReceiveNotify
&TraceId=xxx
&BizId=xxxx
&Event=xxx
&ContentType=xxxx
&Content=xxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ReceiveNotifyResponse>
	  <TraceId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</TraceId>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</ReceiveNotifyResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"TraceId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

