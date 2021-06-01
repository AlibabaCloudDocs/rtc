# StartWhiteBoardRecording

调用StartWhiteBoardRecording启动白板录制。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=StartWhiteBoardRecording&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartWhiteBoardRecording|系统规定参数。取值：**StartWhiteBoardRecording**。 |
|AppID|String|是|7mbj\*\*\*\*|白板应用唯一标识符。更多信息，请参见[CreateApp](~~204234~~)。 |
|UserId|String|是|123456|启动白板录制的用户ID（客户业务用户），由1~32位大小写字母、数字、下划线、短划线（-）组成。 |
|DocKey|String|是|4EZlwmRW0gDG\*\*\*\*|白板文档唯一标识符。更多信息，请参见[CreateWhiteBoard](~~204299~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|FFE713C6-BBA9-457B-AF9D-F6584279A790|请求ID。 |
|ResponseSuccess|Boolean|true|请求结果。 |
|ErrorCode|String|null|错误码。 |
|ErrorMsg|String|null|错误信息。 |
|Result|Object| |返回结果信息。 |
|RecordId|String|05157a01cb1d4aca97704fc7a473\*\*\*\*|白板录制Session的唯一标识符。 |
|StartTime|Long|1622173517031|录制的开始时间，使用UNIX时间戳表示，单位：秒。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=StartWhiteBoardRecording
&AppID=7mbj****
&UserId=123456
&DocKey=4EZlwmRW0gDG****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<StartWhiteBoardRecordingResponse>
    <RequestId>FFE713C6-BBA9-457B-AF9D-F6584279A790</RequestId>
    <ResponseSuccess>true</ResponseSuccess>
    <ErrorMsg/>
    <ErrorCode/>
    <Result>
        <StartTime>1622173517031</StartTime>
        <RecordId>05157a01cb1d4aca97704fc7a473****</RecordId>
    </Result>
</StartWhiteBoardRecordingResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "FFE713C6-BBA9-457B-AF9D-F6584279A790",
  "ResponseSuccess" : true,
  "ErrorMsg" : "",
  "ErrorCode" : "",
  "Result" : {
    "StartTime" : 1622173517031,
    "RecordId" : "05157a01cb1d4aca97704fc7a473****"
  }
}
```

