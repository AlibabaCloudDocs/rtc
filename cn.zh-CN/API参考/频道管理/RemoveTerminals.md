# RemoveTerminals

调用RemoveTerminals将指定终端用户从频道踢出。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=RemoveTerminals&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveTerminals|操作接口名，系统规定参数，取值：**RemoveTerminals**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 可通过控制台创建和查询。 |
|ChannelId|String|是|yourChannelId|已加入的频道ID，仅支持传单个ID。 |
|TerminalIds.N|RepeatList|是|1811xxxx|UserID（用户ID）列表，多个用逗号（,）分隔。N的取值：**1**~**30**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|Terminals|Array of Terminal| |用户ID信息列表。 |
|Terminal| | | |
|Code|Integer|0|状态码，成功返回0，失败返回错误码描述。 |
|Id|String|1811xxxx|用户ID。 |
|Message|String|Success|删除终端操作结果。取值：

 -   Success：成功。
-   Failed：失败。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=RemoveTerminals
&ChannelId=yourChannelId
&Terminals.1=1811xxxx
&AppId=yourAppId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<RemoveTerminalsResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <Terminals>
		    <Id>1811xxxx</Id>
		    <Code>0</Code>
		    <Message>Success</Message>
	  </Terminals>
	  <Terminals>
		    <Id>1811xxxx</Id>
		    <Code>0</Code>
		    <Message>Success</Message>
	  </Terminals>
</RemoveTerminalsResponse>
```

`JSON` 格式

```
{
   "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
   "Terminals":[
      {
         "Id":"1811xxxx",
         "Code":0,
         "Message":"Success"
      },
      {
         "Id":"1811xxxx",
         "Code":0,
         "Message":"Success"
      }
   ]
}
```

