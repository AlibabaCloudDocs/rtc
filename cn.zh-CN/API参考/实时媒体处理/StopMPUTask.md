# StopMPUTask {#reference974 .reference}

调用StopMPUTask停止任务。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：StopMPUTask。|
|AppId|String|是|应用ID，创建应用后生成。|
|TaskId|String|是|任务ID。|

## 返回参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|RequestId|String|是|该条任务请求Id。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=StopMPUTask&AppId=xxxx&TaskId=xxx<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
  "RequestId": "760bad53276431c499e30dc36f6b26be", 
}
```

## 特殊错误码 {#section_9ik_z82_vu9 .section}

|错误ID|错误代码|描述|Http 状态码|语义|
|----|----|--|--------|--|
|0x0702000C|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|0x07020010|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

