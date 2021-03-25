# GetMPUTaskStatus

调用GetMPUTaskStatus获取任务状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=GetMPUTaskStatus&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetMPUTaskStatus|操作接口名，系统规定参数，取值：**GetMPUTaskStatus**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|TaskId|String|是|yourTaskId|任务ID，仅支持传单个ID，通过[StartMpuTask](~~93183~~)设置。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |
|Status|Integer|0|任务的状态ID。

 -   **0**：等待channel开始。

**说明：** 30天内没有启动任务，任务将自动停止。

-   **1**：任务运行中 。
-   **2**：任务已停止 。
-   **3**：用户停止任务。
-   **4**：Channel已停止。
-   **5**：CDN网络问题，直播停止。
-   **6**：直播URL问题，直播停止。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=GetMPUTaskStatus
&AppId=yourAppId
&TaskId=yourTaskId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetMPUTaskStatusResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
	  <Status>0</Status>
</GetMPUTaskStatusResponse>
```

`JSON` 格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be", 
  "Status":0
}
```

