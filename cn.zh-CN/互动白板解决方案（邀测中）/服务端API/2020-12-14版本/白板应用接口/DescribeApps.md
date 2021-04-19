# DescribeApps

调用DescribeApps分页查询白板应用信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc-white-board&api=DescribeApps&type=RPC&version=2020-12-14)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeApps|系统规定参数。取值：**DescribeApps**。 |
|AppID|String|否|7mbj\*\*\*\*|白板应用唯一标识符，参数为空默认查询所有应用ID。获取AppID，请参见[CreateApp](~~204234~~)。 |
|AppStatus|Long|否|1|白板应用状态，参数为空默认查询所有状态。取值：

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
|TotalNum|Long|15|应用总个数。 |
|TotalPage|Long|5|应用总页数。 |
|AppList|Array of appList| |应用详情列表。 |
|AppID|String|7mbj\*\*\*\*|白板应用唯一标识符。 |
|AppName|String|my\_white\_board|白板应用名称。 |
|Status|Long|1|白板应用状态。取值：

 -   **1**：启用。
-   **2**：停用。 |
|CallbackUrl|String|http://www.example.com/callback|白板应用回调地址URL。 |
|DomainNames|String|www.example1.com,www.example2.com|合法域名列表，多个使用英文逗号\(,\)分隔。 |
|CreateTime|String|2020-04-10 12:20:30.567|白板应用的创建时间。 |

## 示例

请求示例

```
http(s)://rtc-white-board.cn-shanghai.aliyuncs.com/?Action=DescribeApps
&AppID=7mbj****
&AppStatus=1
&PageNum=1
&PageSize=10
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeAppsResponse>
	<RequestId>29D20DA7-985D-425E-89BD-26594D327DCC</RequestId>
	<ResponseSuccess>true</ResponseSuccess>
	<ErrorMsg></ErrorMsg>
	<ErrorCode></ErrorCode>
	<Result>
		<TotalNum>15</TotalNum>
		<TotalPage>5</TotalPage>
		<AppList>
			<CallbackUrl>http://www.example.com/callback</CallbackUrl>
			<Status>1</Status>
			<AppID>zt87****</AppID>
			<CreateTime>2021-04-10 16:10:57.217</CreateTime>
			<DomainNames>www.example1.com,www.example2.com</DomainNames>
			<AppName>我的APP1</AppName>
		</AppList>
		<AppList>
			<CallbackUrl>http://www.example.com/callback</CallbackUrl>
			<Status>1</Status>
			<AppID>sf1g****</AppID>
			<CreateTime>2021-04-12 15:29:27.315</CreateTime>
			<DomainNames>www.example1.com,www.example2.com</DomainNames>
			<AppName>我的APP2</AppName>
		</AppList>
		<AppList>
			<CallbackUrl>http://www.example.com/callback</CallbackUrl>
			<Status>1</Status>
			<AppID>5s77****</AppID>
			<CreateTime>2021-04-12 17:00:39.325</CreateTime>
			<DomainNames>www.example1.com,www.example2.com</DomainNames>
			<AppName>我的APP3</AppName>
		</AppList>
	</Result>
</DescribeAppsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "29D20DA7-985D-425E-89BD-26594D327DCC",
  "ResponseSuccess" : true,
  "ErrorMsg" : "",
  "ErrorCode" : "",
  "Result" : {
    "TotalNum" : 15,
    "TotalPage" : 5,
    "AppList" : [ {
      "CallbackUrl" : "http://www.example.com/callback",
      "Status" : 1,
      "AppID" : "zt87****",
      "CreateTime" : "2021-04-10 16:10:57.217",
      "DomainNames" : "www.example1.com,www.example2.com",
      "AppName" : "我的APP1"
    }, {
      "CallbackUrl" : "http://www.example.com/callback",
      "Status" : 1,
      "AppID" : "sf1g****",
      "CreateTime" : "2021-04-12 15:29:27.315",
      "DomainNames" : "www.example1.com,www.example2.com",
      "AppName" : "我的APP2"
    }, {
      "CallbackUrl" : "http://www.example.com/callback",
      "Status" : 1,
      "AppID" : "5s77****",
      "CreateTime" : "2021-04-12 17:00:39.325",
      "DomainNames" : "www.example1.com,www.example2.com",
      "AppName" : "我的APP3"
    } ]
  }
}
```

