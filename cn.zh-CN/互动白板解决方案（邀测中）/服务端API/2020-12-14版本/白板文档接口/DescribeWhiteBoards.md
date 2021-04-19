# DescribeWhiteBoards

调用DescribeWhiteBoards分页查询白板文档信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=DescribeWhiteBoards&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeWhiteBoards|系统规定参数。取值：**DescribeWhiteBoards**。 |
|AppID|String|是|7mbj\*\*\*\*|白板文档唯一标识符。获取AppID，请参见[CreateApp](~~204234~~)。 |
|DocStatus|Long|否|1|白板文档状态，参数为空默认查询所有状态。取值：

 -   **1**：启用。
-   **2**：停用。 |
|PageNum|Long|否|1|查询页码，参数为空默认查询第1页。 |
|PageSize|Long|否|10|每页显示个数，参数为空默认显示个数为10。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|FE22D613-D3C6-4A58-87CA-F21FC85AA08E|请求ID。 |
|ResponseSuccess|Boolean|true|调用结果。 |
|ErrorCode|String|null|错误码。 |
|ErrorMsg|String|null|错误信息。 |
|Result|object| |返回的结果信息。 |
|TotalNum|Long|33|文档总个数。 |
|TotalPage|Long|11|文档总页数。 |
|DocList|Array of docList| |文档详情列表。 |
|AppID|String|7mbj\*\*\*\*|白板应用唯一标识符。 |
|DocKey|String|4EZlwmRW0gDG\*\*\*\*|白板文档唯一标识符。 |
|Status|Long|1|白板文档状态。取值：

 -   **1**：启用。
-   **2**：停用。 |
|CreateUserId|String|123456|创建白板的用户ID。 |
|CreateTime|String|2020-04-10 12:20:30.567|白板文档的创建时间。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=DescribeWhiteBoards
&AppID=7mbj****
&DocStatus=1
&PageNum=1
&PageSize=10
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeWhiteBoardsResponse>	
  <RequestId>AEBD21E4-85D7-4B8D-A51E-F9E01AEEB682</RequestId>
	<ResponseSuccess>true</ResponseSuccess>
	<ErrorMsg></ErrorMsg>
	<ErrorCode></ErrorCode>
	<Result>
		<TotalNum>33</TotalNum>
		<TotalPage>11</TotalPage>
		<DocList>
			<Status>1</Status>
			<DocKey>4j7OJzVEKR8J****</DocKey>
			<AppID>p9an****</AppID>
			<CreateTime>2021-04-10 14:22:13.647</CreateTime>
			<CreateUserId>12345601</CreateUserId>
		</DocList>
		<DocList>
			<Status>1</Status>
			<DocKey>XN94MkAb63Bm****</DocKey>
			<AppID>p9an****</AppID>
			<CreateTime>2021-04-12 14:22:21.492</CreateTime>
			<CreateUserId>12345602</CreateUserId>
		</DocList>
		<DocList>
			<Status>1</Status>
			<DocKey>5VLqX472M3Dw****</DocKey>
			<AppID>p9an****</AppID>
			<CreateTime>2021-04-12 15:07:37.069</CreateTime>
			<CreateUserId>12345603</CreateUserId>
		</DocList>
	</Result>
</DescribeWhiteBoardsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "AEBD21E4-85D7-4B8D-A51E-F9E01AEEB682",
  "ResponseSuccess" : true,
  "ErrorMsg" : "",
  "ErrorCode" : "",
  "Result" : {
    "TotalNum" : 33,
    "TotalPage" : 11,
    "DocList" : [ {
      "Status" : 1,
      "DocKey" : "4j7OJzVEKR8J****",
      "AppID" : "p9an****",
      "CreateTime" : "2021-04-10 14:22:13.647",
      "CreateUserId" : "12345601"
    }, {
      "Status" : 1,
      "DocKey" : "XN94MkAb63Bm****",
      "AppID" : "p9an****",
      "CreateTime" : "2021-04-12 14:22:21.492",
      "CreateUserId" : "12345602"
    }, {
      "Status" : 1,
      "DocKey" : "5VLqX472M3Dw****",
      "AppID" : "p9an****",
      "CreateTime" : "2021-04-12 15:07:37.069",
      "CreateUserId" : "12345603"
    } ]
  }
}
```

