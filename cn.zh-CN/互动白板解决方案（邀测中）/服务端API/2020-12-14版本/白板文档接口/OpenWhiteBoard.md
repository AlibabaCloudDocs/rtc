# OpenWhiteBoard

调用OpenWhiteBoard打开白板文档。

**说明：** 此接口会通过用户鉴权回调和用户信息回调请求客户服务器，以获取用户权限及用户基本信息，请确保应用回调地址配置无误。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=OpenWhiteBoard&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|OpenWhiteBoard|系统规定参数。取值：**OpenWhiteBoard**。 |
|AppID|String|是|7mbjnzq8|白板应用唯一标识符。更多信息，请参见[CreateApp](~~204234~~)。 |
|UserId|String|是|123456|打开白板的用户ID（客户业务用户），由1~32位大小写字母、数字、下划线、短划线（-）组成。 |
|DocKey|String|是|4EZlwmRW0gDGqxAY|白板文档唯一标识符。更多信息，请参见[CreateWhiteBoard](~~204299~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CE47143D-9700-4756-856A-BB22FEBE4DAE|请求ID。 |
|ResponseSuccess|Boolean|true|请求结果。 |
|ErrorCode|String|null|错误码。 |
|ErrorMsg|String|null|错误信息。 |
|Result|Object| |返回的结果信息。 |
|DocumentAccessInfo|Object| |白板连接信息。 |
|AccessToken|String|qbFPTqipwQZqkGitAoAGbNHuHREmGGPe|连接签名。 |
|CollabHost|String|collab-cn-shanghai.\*\*\*\*.com|白板长连接地址。 |
|Permission|Long|2|权限码。取值：

 -   **0**：无权限。
-   **1**：只读。
-   **2**：读写。 |
|UserInfo|Object| |用户信息。 |
|AvatarUrl|String|http://www.avatarset/\*\*\*\*.jpg|用户头像的URL。 |
|Nick|String|Mary|用户昵称。 |
|NickPinyin|String|Pinyin\_Mary|用户的拼音昵称。 |
|UserId|String|123456|打开白板的用户ID。 |
|WsDomain|String|collab-ws-cn-shanghai.\*\*\*\*.com|高性能长连接服务地址。

 **说明：** 支持Web SDK 0.0.4或以上版本使用。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=OpenWhiteBoard
&AppID=7mbjnzq8
&DocKey=4EZlwmRW0gDGqxAY
&UserId=123456
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<OpenWhiteBoardResponse>
<RequestId>CE47143D-9700-4756-856A-BB22FEBE4DAE</RequestId>
<ResponseSuccess>true</ResponseSuccess>
<Result>
    <DocumentAccessInfo>
        <AccessToken>qbFPTqipwQZqkGitAoAGbNHuHREmGGPe</AccessToken>
        <CollabHost>pre-collab-cn-shanghai.****.com</CollabHost>
        <Permission>2</Permission>
        <UserInfo>
            <AvatarUrl>http://www.avatarset/****.jpg</AvatarUrl>
            <UserId>123456</UserId>
            <Nick>Mary</Nick>
            <NickPinyin>Pinyin_Mary</NickPinyin>
			<WsDomain>collab-ws-cn-shanghai.****.com</WsDomain>
        </UserInfo>
    </DocumentAccessInfo>
</Result>
</OpenWhiteBoardResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CE47143D-9700-4756-856A-BB22FEBE4DAE",
  "ResponseSuccess" : true,
  "Result" : {
    "DocumentAccessInfo" : {
      "AccessToken" : "qbFPTqipwQZqkGitAoAGbNHuHREmGGPe",
      "CollabHost" : "collab-cn-shanghai.****.com",
      "Permission" : 2,
      "UserInfo" : {
        "AvatarUrl" : "http://www.avatarset/****.jpg",
        "UserId" : "123456",
        "Nick" : "Mary",
        "NickPinyin" : "Pinyin_Mary",
        "WsDomain" : "collab-ws-cn-shanghai.****.com"
      }
    }
  }
}
```

