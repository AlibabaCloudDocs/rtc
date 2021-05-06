# SetAppCallbackType

调用SetAppCallbackType设置白板应用的回调类型。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=SetAppCallbackType&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetAppCallbackType|系统规定参数。取值：**SetAppCallbackType**。 |
|AppID|String|是|7mbj\*\*\*\*|白板应用唯一标识符。 |
|AppCallbackType|String|是|userPermissionCallback,whiteBoardProfileCallback,userProfileCallback,hostCheckCallback|白板应用的回调类型，多个使用英文逗号（,）分隔。取值范围如下所示：

 -   userPermissionCallback：用户权限回调。
-   whiteBoardProfileCallback：白板元信息回调。
-   userProfileCallback：用户元信息回调。
-   hostCheckCallback：合法域名校验失败回调。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CFB5E6AA-823B-415B-AA03-4B9892049B68|请求ID。 |
|ResponseSuccess|Boolean|true|请求结果。 |
|ErrorCode|String|null|错误码。 |
|ErrorMsg|String|null|错误信息。 |
|Result|Boolean|true|返回结果。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=SetAppCallbackType
&AppID=7mbj****
&AppCallbackType=userPermissionCallback,whiteBoardProfileCallback,userProfileCallback,hostCheckCallback
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<SetAppCallbackTypeResponse>
    <RequestId>CFB5E6AA-823B-415B-AA03-4B9892049B68</RequestId>
    <ResponseSuccess>true</ResponseSuccess>
    <Result>true</Result>
</SetAppCallbackTypeResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CFB5E6AA-823B-415B-AA03-4B9892049B68",
  "ResponseSuccess" : true,
  "Result" : true
}
```

