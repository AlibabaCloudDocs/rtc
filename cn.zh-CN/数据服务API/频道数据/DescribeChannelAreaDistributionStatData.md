# DescribeChannelAreaDistributionStatData

调用DescribeChannelAreaDistributionStatData获取频道地区分布统计数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeChannelAreaDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/channel/describeChannelAreaDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|pdtk\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|12345|频道ID。 |
|CreatedTs|Long|Query|是|1616125296|频道创建时间，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1616125993|频道释放时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。

 **说明：** 如果传入的频道释放时间超过真实的释放时间，将返回从创建时间开始到真实释放时间之间的数据。 |
|ParentArea|String|Query|否|中国\_浙江省|父级地区名称，例如：深圳市的父级为广东省。参数为空表示世界范围（国家维度）的统计，例如：中国、英国。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AreaStatList|Array of AreaStatData| |地域统计列表。 |
|AreaName|String|中国\_浙江省\_杭州市|地域名称，例如：中国\_浙江省\_杭州市。 |
|CallUserCount|Integer|3|通信人数。 |
|PubUserCount|Integer|2|发布端人数。 |
|SubUserCount|Integer|1|订阅端人数。 |
|HighQualityTransmissionRate|String|0.9999|优质传输率，用小数表示，例如0.9999表示优质传输率为99.99%。 |
|RequestId|String|659D0AE5-B9EC-4878-B297-A2444C9E64D7|请求ID。 |

## 示例

请求示例

```
POST api/channel/describeChannelAreaDistributionStatData?AppId=pdtk****&ChannelId=12345&CreatedTs=1616125296&DestroyedTs=1616125993&ParentArea=中国_浙江省 HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeChannelAreaDistributionStatDataResponse>
<requestId>659D0AE5-B9EC-4878-B297-A2444C9E64D7</requestId>
<code>200</code>
<message/>
<action/>
<apiName/>
<extendedCode/>
<bizCode/>
<httpStatusCode>200</httpStatusCode>
<data>
    <RequestId>659D0AE5-B9EC-4878-B297-A2444C9E64D7</RequestId>
    <AreaStatList>
        <AreaName>中国_浙江省_杭州市</AreaName>
        <CallUserCount>3</CallUserCount>
        <HighQualityTransmissionRate>98.87</HighQualityTransmissionRate>
        <SubUserCount>1</SubUserCount>
        <PubUserCount>2</PubUserCount>
    </AreaStatList>
</data>
<successResponse>true</successResponse>
</DescribeChannelAreaDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "requestId" : "659D0AE5-B9EC-4878-B297-A2444C9E64D7",
  "code" : "200",
  "httpStatusCode" : "200",
  "data" : {
    "RequestId" : "659D0AE5-B9EC-4878-B297-A2444C9E64D7",
    "AreaStatList" : [ {
      "AreaName" : "中国_浙江省_杭州市",
      "CallUserCount" : 3,
      "HighQualityTransmissionRate" : "98.87",
      "SubUserCount" : 1,
      "PubUserCount" : 2
    } ]
  },
  "successResponse" : true
}
```

