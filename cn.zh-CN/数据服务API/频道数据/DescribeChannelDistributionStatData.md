# DescribeChannelDistributionStatData

调用DescribeChannelDistributionStatData获取频道分布统计数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeChannelDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/channel/describeChannelDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|123333|频道ID。 |
|CreatedTs|Long|Query|是|1615893133|创建频道的时间戳，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615893757|释放频道的时间戳，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。

 **说明：** 如果传入的频道释放时间超过真实的释放时间，将返回从创建时间开始到真实释放时间之间的数据。 |
|StatDim|String|Query|是|OS|统计维度，取值：

 -   **OS**：按照系统统计。
-   **SDK\_VERSION**：按照SDK版本统计。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|StatList|Array of StatData| |频道分布统计列表。 |
|Name|String|macOS|统计维度。 |
|CallUserCount|Integer|1|通信人数。 |
|CallUserRatio|String|1.0000|通信人数占比，用小数表示，例如1.0000表示通信人数占比为100%。 |
|RequestId|String|4EBB875A-C25F-49DE-8567-F4E226B4AB9D|请求ID。 |

## 示例

请求示例

```
POST api/channel/describeChannelDistributionStatData?AppId=9qb1****&ChannelId=123333&CreatedTs=1615893133&DestroyedTs=1615893757&StatDim=OS HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeChannelDistributionStatDataResponse>
<code>200</code>
<data>
    <StatList>
        <CallUserRatio>0.25</CallUserRatio>
        <CallUserCount>1</CallUserCount>
        <Name>macOS</Name>
    </StatList>
    <StatList>
        <CallUserRatio>0.75</CallUserRatio>
        <CallUserCount>3</CallUserCount>
        <Name>Linux</Name>
    </StatList>
    <RequestId>4EBB875A-C25F-49DE-8567-F4E226B4AB9D</RequestId>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>4EBB875A-C25F-49DE-8567-F4E226B4AB9D</requestId>
<successResponse>true</successResponse>
</DescribeChannelDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "StatList" : [ {
      "CallUserRatio" : "0.25",
      "CallUserCount" : 1,
      "Name" : "macOS"
    }, {
      "CallUserRatio" : "0.75",
      "CallUserCount" : 3,
      "Name" : "Linux"
    } ],
    "RequestId" : "4EBB875A-C25F-49DE-8567-F4E226B4AB9D"
  },
  "httpStatusCode" : "200",
  "requestId" : "4EBB875A-C25F-49DE-8567-F4E226B4AB9D",
  "successResponse" : true
}
```

