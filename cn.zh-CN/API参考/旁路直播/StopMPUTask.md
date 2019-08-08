# StopMPUTask {#doc_api_rtc_StopMPUTask .reference}

调用StopMPUTask停止任务。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=StopMPUTask&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StopMPUTask|操作接口名，系统规定参数，取值：**StopMPUTask**。

 |
|AppId|String|是|yourAppId|应用ID，创建应用后生成。

 |
|TaskId|String|是|yourTaskId|任务ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=StopMPUTask
&AppId=xxxx
&TaskId=xxx<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StopMPUTaskResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</StopMPUTaskResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"760bad53276431c499e30dc36f6b26be"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

