# GetMPUTaskStatus {#doc_api_rtc_GetMPUTaskStatus .reference}

调用GetMPUTaskStatus获取任务状态。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=GetMPUTaskStatus&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetMPUTaskStatus|操作接口名，系统规定参数，取值：**GetMPUTaskStatus**。

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
|Status|Integer|0|任务的状态ID：

 -   **0**：等待channel开始。
-   **1**：任务运行中 。
-   **2**：任务已停止 。
-   **3**：用户停止任务。
-   **4**：Channel已停止。
-   **5**：CDN网络问题，直播停止。
-   **6**：直播URL问题，直播停止。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=GetMPUTaskStatus
&AppId=xxxx
&ChannelId=xxx
&TaskId=xxx<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetMPUTaskStatusResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
	  <Status>0</Status>
</GetMPUTaskStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Status":0,
	"RequestId":"760bad53276431c499e30dc36f6b26be"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

