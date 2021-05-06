# SetUsersPermissions

调用SetUsersPermissions设置白板文档用户的长期权限。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=SetUsersPermissions&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetUsersPermissions|系统规定参数。取值：**SetUsersPermissions**。 |
|UserIds|String|是|100001,100002|需要设置权限的用户ID，多个使用英文逗号（,）分隔，最多30个，每个ID由纯数字组成。 |
|DocKey|String|是|4EZlwmRW0gDG\*\*\*\*|白板文档唯一标识符。 |
|AppID|String|是|7mbj\*\*\*\*|白板应用唯一标识符。 |
|PermissionType|String|否|edit|用户白板权限类型，取值：

 -   **ban**：无权限。
-   **read**：只读。
-   **edit**：读写。 |

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
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=SetUsersPermissions
&UserIds=100001,100002
&DocKey=4EZlwmRW0gDG****
&AppID=7mbj****
&PermissionType=edit
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<SetUsersPermissionsResponse>
    <RequestId>CFB5E6AA-823B-415B-AA03-4B9892049B68</RequestId>
    <ResponseSuccess>true</ResponseSuccess>
    <Result>true</Result>
</SetUsersPermissionsResponse>
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

