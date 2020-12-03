# DeleteRecordTemplate

调用DeleteRecordTemplate删除录制配置模板。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DeleteRecordTemplate&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteRecordTemplate|操作接口名，系统规定参数，取值：**DeleteRecordTemplate**。 |
|AppId|String|是|yourAppId|应用ID。通过控制台创建和查询，仅支持传单个ID。 |
|TemplateId|String|是|76dasgb\*\*\*\*|配置模板ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|该条任务请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DeleteRecordTemplate
&AppId=yourAppId
&TemplateId=76dasgb****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteRecordTemplateResponse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</DeleteRecordTemplateResponse>
```

`JSON` 格式

```
{
	"RequestId": "760bad53276431c499e30dc36f6b26be"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/rtc)查看更多错误码。

## 特殊错误码

|错误ID

|错误代码

|描述

|Http 状态码

|语义 |
|------|------|----|----------|----|
|InternalError

|InternalError

|The request processing has failed due to some unknown error, exception or failure.

|500

|内部错误 |

