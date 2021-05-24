# StopMPUTask

调用StopMPUTask停止任务。

**说明：** 在需要停止旁路直播任务时，您可以主动调用StopMPUTask接口。如果异常未调用StopMPUTask，本次旁路直播任务会在频道中最后一个人离开频道2分钟后自动停止任务。停止后如果需要恢复旁路直播，您需要重新调用StartMPUTask接口。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=StopMPUTask&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StopMPUTask|操作接口名，系统规定参数，取值：**StopMPUTask**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 **说明：** 您可以在[控制台](https://rtc.console.aliyun.com/manage/list#/manage/list)创建和查询。 |
|TaskId|String|是|yourTaskId|任务ID，仅支持传单个ID，可通过[StartMpuTask](~~93183~~)接口设置。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=StopMPUTask
&AppId=yourAppId
&TaskId=yourTaskId
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<StopMPUTaskResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</StopMPUTaskResponse>
```

`JSON`格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be"
}
```

