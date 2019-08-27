# DescribeChannelParticipants {#doc_api_rtc_DescribeChannelParticipants .reference}

调用DescribeChannelParticipants查询频道在线用户列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeChannelParticipants&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeChannelParticipants|操作接口名，系统规定参数，取值：**DescribeChannelParticipants**。

 |
|AppId|String|是|sad123|应用ID。

 |
|ChannelId|String|是|123|用户加入的频道。

 |
|Order|String|否|asc|不输入该参数默认为**desc**取最近记录。

 -   递增：**asc**。
-   递减：**desc**。

 |
|PageNum|Integer|否|1|不输入默认1页, 必须大于0。

 |
|PageSize|Integer|否|10|不输入如默认为10， 必须大于0。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。

 |
|Timestamp|Integer|1557909133|返回结果时间戳。

 |
|TotalNum|Integer|3|返回结果数。

 |
|TotalPage|Integer|1|返回分页数。

 |
|UserList| |27f91ecf|用户ID列表。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.comAction=DescribeChannelParticipants
&AppId=xxx
&ChannelId=xxx
&Order=desc
&PageNum=1
&PageSize=2
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeChannelParticipantsResponse>
	  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
	  <Timestamp>1557909133</Timestamp>
	  <TotalNum>3</TotalNum>
	  <TotalPage>1</TotalPage>
	  <UserList>27f91ecf</UserList>
	  <UserList>bb874474</UserList>
	  <UserList>df82298d</UserList>
</DescribeChannelParticipantsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":1,
	"UserList":[
		"27f91ecf",
		"bb874474",
		"df82298d"
	],
	"TotalNum":3,
	"RequestId":"6159ba01-6687-4fb2-a831-f0cd8d188648",
	"Timestamp":1557909133
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

