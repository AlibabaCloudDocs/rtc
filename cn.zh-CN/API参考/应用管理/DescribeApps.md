# DescribeApps

调用DescribeApps查询应用列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeApps&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|否|DescribeApps|操作接口名，系统规定参数，取值：**DescribeApps**。 |
|AppId|String|否|yourAppId|应用ID，通过控制台创建和查询，仅支持传单个ID。

 默认查询所有应用ID。 |
|Status|String|否|1|状态，默认查询所有状态。

 -   **1**：可用。
-   **2**：停用。
-   **3**：欠费停用。 |
|Order|String|否|asc|排序方式。

 -   **asc**：递增。
-   **desc**（默认值）：递减。 |
|PageNum|Integer|否|1|第几页，取值必须大于**0**。

 默认查询第**1**页。 |
|PageSize|Integer|否|2|每页显示个数，取值必须大于**0**。

 默认为**10**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AppList|Array| |信息列表。 |
|App| | | |
|AppId|String|rgf1\*\*\*\*"|应用ID。 |
|AppName|String|Default AppName|应用名称。 |
|AppType|String|universal|应用类型。

 -   **conference**：会议。
-   **universal**：通用型。 |
|BillType|String|paybyduration|计费方式：**paybyduration**（按时长计费）。 |
|CreateTime|String|2017-08-30 10:47:25.0|创建时间。 |
|ServiceAreas|List|CN|服务区域：CN（中国）。 |
|Status|Integer|1|状态。

 -   **1**：可用。
-   **2**：停用。
-   **3**：欠费停用。 |
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。 |
|TotalNum|Integer|1|返回结果数。 |
|TotalPage|Integer|1|返回分页数。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeApps
&PageNum=1
&PageSize=2
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeAppsResponse>
  <TotalNum>1</TotalNum>
  <TotalPage>1</TotalPage>
  <RequestId>B0A2FCBC-43A4-428F-BC1D-3F4F85837F76</RequestId>
  <AppList>
        <App>
              <Status>1</Status>
              <BillType>paybyduration</BillType>
              <AppId>rgf1****</AppId>
              <CreateTime>2020-01-09T02:02:29Z</CreateTime>
              <ServiceAreas>
                    <ServiceArea>CN</ServiceArea>
              </ServiceAreas>
              <AppType>universal</AppType>
              <AppName>Default AppName</AppName>
        </App>
  </AppList>
</DescribeAppsResponse>
```

`JSON` 格式

```
{
	"TotalNum": 1,
	"TotalPage": 1,
	"RequestId": "B0A2FCBC-43A4-428F-BC1D-3F4F85837F76",
	"AppList": {
		"App": [
			{
				"Status": 1,
				"BillType": "paybyduration",
				"AppId": "rgf1****",
				"CreateTime": "2020-01-09T02:02:29Z",
				"ServiceAreas": {
					"ServiceArea": [
						"CN"
					]
				},
				"AppType": "universal",
				"AppName": "Default AppName"
			}
		]
    }   
}
```

