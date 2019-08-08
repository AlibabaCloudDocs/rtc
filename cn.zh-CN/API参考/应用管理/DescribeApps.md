# DescribeApps {#doc_api_rtc_DescribeApps .reference}

调用DescribeApps查询应用列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeApps&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|否|DescribeApps|操作接口名，系统规定参数，取值：**DescribeApps**。

 |
|AppId|String|否|yourAppId|应用ID，通过控制台开通创建，长度最大8个字节，不填则返回该用户下所有应用信息。

 |
|Order|String|否|asc|不填则默认desc取最近记录：

 -   **asc**：递增。
-   **desc**：递减。

 |
|PageNum|Integer|否|1|不填则默认**1**页，取值必须大于**0**。

 |
|PageSize|Integer|否|2|不填则默认为**10**， 取值必须大于**0**。

 |
|Status|String|否|1|状态：

 -   **1**：可用。
-   **2**：停用。
-   **3**：欠费停用。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AppList| | |信息列表。

 |
|AppId|String|yourAppId|应用ID。

 |
|AppName|String|abc|应用名称。

 |
|AppType|String|conference|应用类型。conference：会议；universal：通用型。

 |
|BillType|String|payByDuration|按时长计费：payByDuration。

 |
|CreateTime|String|2017-08-30 10:47:25.0|创建时间。

 |
|ServiceAreas| |\[\\"CN\\"\]|服务地区。

 |
|Status|Integer|1|状态：

 -   1：可用。
-   2：停用。
    -   3：欠费停用。

 |
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|该条任务请求ID。

 |
|TotalNum|Integer|2|返回结果数。

 |
|TotalPage|Integer|1|返回分页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=DescribeApps
&PageNum=1
&PageSize=2
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAppsResponse>
	  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
	  <TotalNum>2</TotalNum>
	  <TotalPage>1</TotalPage>
	  <AppList>
		    <Status>1</Status>
		    <AppName>coco-conf</AppName>
		    <CreateTime>2017-08-30 10:47:25.0</CreateTime>
		    <AppId>af2ace82-dc55-40b1-9fa3-688787214b1d</AppId>
		    <ServiceAreas>["CN"]</ServiceAreas>
		    <AppType>universal</AppType>
		    <BillType>payByDuration</BillType>
	  </AppList>
</DescribeAppsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":1,
	"AppList":[
		{
			"ServiceAreas":"[\"CN\"]",
			"Status":1,
			"CreateTime":"2017-08-30 10:47:25.0",
			"AppId":"af2ace82-dc55-40b1-9fa3-688787214b1d",
			"AppName":"coco-conf",
			"BillType":"payByDuration",
			"AppType":"universal"
		}
	],
	"TotalNum":2,
	"RequestId":"6159ba01-6687-4fb2-a831-f0cd8d188648"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

