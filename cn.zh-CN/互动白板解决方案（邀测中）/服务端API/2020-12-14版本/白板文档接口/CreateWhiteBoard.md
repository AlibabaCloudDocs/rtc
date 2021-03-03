# CreateWhiteBoard

调用CreateWhiteBoard创建白板文档。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=CreateWhiteBoard&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateWhiteBoard|系统规定参数。取值：**CreateWhiteBoard**。 |
|AppID|String|是|7mbjnzq8|白板应用唯一标识符。更多信息，请参见[CreateApp](~~204234~~)。 |
|UserId|String|是|123456|创建白板的用户ID（客户业务用户），由1~9位纯数字组成。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|null|错误码。 |
|ErrorMsg|String|null|错误信息。 |
|RequestId|String|B29ADDF9-D089-460A-AF7D-BDE5DA112E4E|请求ID。 |
|ResponseSuccess|Boolean|true|请求结果。 |
|Result|Struct| |返回的结果信息。 |
|DocKey|String|4EZlwmRW0gDGqxAY|文档的标识符，由大小写字母和数字组成。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=CreateWhiteBoard
&AppID=7mbjnzq8
&UserId=123456
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateWhiteBoardResponse>
  <RequestId>B29ADDF9-D089-460A-AF7D-BDE5DA112E4E</RequestId>
  <ResponseSuccess>true</ResponseSuccess>
  <Result>
        <DocKey>4EZlwmRW0gDGqxAY</DocKey>
  </Result>
</CreateWhiteBoardResponse>
```

`JSON`格式

```
{
"RequestId":"B29ADDF9-D089-460A-AF7D-BDE5DA112E4E",
"ResponseSuccess":true,
"Result":{
"DocKey":"4EZlwmRW0gDGqxAY"
}
}
```

