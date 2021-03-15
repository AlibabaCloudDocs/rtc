# DescribeChannelParticipants

调用DescribeChannelParticipants查询频道在线用户列表，不包含详细信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeChannelParticipants&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeChannelParticipants|操作接口名，系统规定参数，取值：**DescribeChannelParticipants**。 |
|AppId|String|是|aec\*\*\*\*|应用ID，可通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|testId|加入的频道，仅支持传单个ID。 |
|Order|String|否|asc|排序方式。

 -   **asc**：递增。
-   **desc**（默认值）：递减。 |
|PageNum|Integer|否|1|第几页，取值：\>**0**。

 默认为1。 |
|PageSize|Integer|否|10|数量，取值：\>**0**。

 默认为10。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。 |
|Timestamp|Integer|1557909133|返回结果时间戳。 |
|TotalNum|Integer|3|返回结果数。 |
|TotalPage|Integer|1|返回分页数。 |
|UserList|List|27f9\*\*\*\*|用户ID列表。 |

## 示例

请求示例

```
https://rtc.aliyuncs.comAction=DescribeChannelParticipants
&AppId=aec****
&ChannelId=testId
&Order=desc
&PageNum=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeChannelParticipantsResponse>
  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
  <Timestamp>1557909133</Timestamp>
  <TotalNum>3</TotalNum>
  <TotalPage>1</TotalPage>
  <UserList>
        <User>27f9****</User>
        <User>bb87****</User>
        <User>df82****</User>
  </UserList>
</DescribeChannelParticipantsResponse>
```

`JSON` 格式

```
{
	"RequestId": "6159ba01-6687-4fb2-a831-f0cd8d188648",
	"Timestamp": 1557909133,
	"TotalNum": 3,
	"TotalPage": 1,
	"UserList": {
		"User": ["27f9****",
			"bb87****",
			"df82****"
		]
	}
}
```

