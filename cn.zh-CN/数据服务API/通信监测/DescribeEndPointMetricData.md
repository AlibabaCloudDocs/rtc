# DescribeEndPointMetricData

调用DescribeEndPointMetricData获取端对端指标数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeEndPointMetricData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describeEndPointMetricData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615887685|创建频道时间，支持查询最近30天的数据。使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615888615|释放频道时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。

 **说明：** 如果传入的频道释放时间超过真实的释放时间，将返回从创建时间开始到真实释放时间之间的数据，且最多返回最近3个小时的数据。 |
|SubUserId|String|Query|否|testsubuserid|订阅端用户ID。 |
|PubUserId|String|Query|否|c906531af5f9\*\*\*\*|发布端用户ID。

 **说明：** PubUserId和PubCallIdList参数只能二选一输入。 |
|PubCallIdList|String|Query|否|testcall1,testcall2|发布端用户通信流的Call ID，多个用英文逗号（,）分隔。

 **说明：** PubUserId和PubCallIdList参数只能二选一输入。 |
|Metrics|String|Query|是|APP\_CPU,SYSTEM\_CPU|指标枚举列表，多个用英文逗号（,）分隔。 |

指标如下所示：

|名称

|说明 |
|----|----|
|APP\_CPU

|APP占用CPU。 |
|SYSTEM\_CPU

|系统占用CPU。 |
|APP\_MEMORY

|APP占用内存。 |
|SYSTEM\_MEMORY

|系统占用内存。 |
|SYSTEM\_TOTAL\_MEMORY

|系统总内存。 |
|AUDIO\_LOST\_RATE

|音频丢包率。 |
|VIDEO\_LOST\_RATE

|视频丢包率。 |
|AUDIO\_RTT

|音频延时。 |
|VIDEO\_RTT

|视频延时。 |
|AUDIO\_END\_TO\_END\_RTT

|音频端到端延时。 |
|VIDEO\_END\_TO\_END\_RTT

|视频端到端延时。 |
|AUDIO\_BIT\_RATE

|音频码率。 |
|AUDIO\_STUCK

|音频卡顿。 |
|AUDIO\_LEVEL

|音量。 |
|VIDEO\_BIT\_RATE\_CAMERA

|摄像头视频码率。 |
|VIDEO\_BIT\_RATE\_LARGE

|视频码率（大画面）。 |
|VIDEO\_BIT\_RATE\_SMALL

|视频码率（小画面）。 |
|VIDEO\_BIT\_RATE\_SUPER

|视频码率（超大屏幕）。 |
|VIDEO\_BIT\_RATE\_SHARE

|视频码率（屏幕分享）。 |
|VIDEO\_STUCK\_CAMERA

|摄像头视频卡顿。 |
|VIDEO\_STUCK\_LARGE

|视频卡顿（大画面）。 |
|VIDEO\_STUCK\_SMALL

|视频卡顿（小画面）。 |
|VIDEO\_STUCK\_SUPER

|视频卡顿（超大屏幕）。 |
|VIDEO\_STUCK\_SHARE

|视频卡顿（屏幕分享）。 |
|VIDEO\_RESOLUTION\_CAMERA

|摄像头视频分辨率。 |
|VIDEO\_RESOLUTION\_LARGE

|视频分辨率（大画面）。 |
|VIDEO\_RESOLUTION\_SMALL

|视频分辨率（小画面）。 |
|VIDEO\_RESOLUTION\_SUPER

|视频分辨率（超大屏幕）。 |
|VIDEO\_RESOLUTION\_SHARE

|视频分辨率（屏幕分享）。 |
|VIDEO\_FPS\_CAMERA

|摄像头视频帧率。 |
|VIDEO\_FPS\_LARGE

|视频帧率（大画面）。 |
|VIDEO\_FPS\_SMALL

|视频帧率（小画面）。 |
|VIDEO\_FPS\_SUPER

|视频帧率（超大屏幕）。 |
|VIDEO\_FPS\_SHARE

|视频帧率（屏幕分享）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|SubMetrics|Array of MetricDataItem| |订阅端用户指标数据。 |
|Type|String|VIDEO\_STUCK\_CAMERA|订阅端指标，更多信息，请参见请求参数中指标枚举列表。 |
|UserId|String|testuserid1|用户ID。 |
|Nodes|Array of Node| |订阅端指标趋势图坐标点列表。 |
|X|String|1548670257|订阅端指标趋势图中x轴横坐标。 |
|Y|String|230100|订阅端指标趋势图y轴纵坐标。 |
|Ext|Map| |拓展属性。 |
|PubMetrics|Array of MetricDataItem| |发布端用户指标数据。 |
|Type|String|APP\_CPU|发布端指标，更多信息，请参见请求参数中指标枚举列表。 |
|UserId|String|testuserid2|用户ID。 |
|Nodes|Array of Node| |发布端指标趋势图坐标点列表。 |
|X|String|1548670257|发布端指标趋势图中x轴横坐标。 |
|Y|String|230100|发布端指标趋势图中y轴纵坐标。 |
|Ext|Map| |拓展属性。 |
|RequestId|String|478B9DE1-3958-4734-AE4F-534658AD8574|请求ID。 |

## 示例

请求示例

```
POST api/call/describeEndPointMetricData?AppId=9qb1****&ChannelId=311&CreatedTs=1615887685&DestroyedTs=1615888615&Metrics=APP_CPU,SYSTEM_CPU&PubUserId=c906531af5f9**** HTTP/1.1 
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeEndPointMetricDataResponse>
<code>200</code>
<data>
    <RequestId>478B9DE1-3958-4734-AE4F-534658AD8574</RequestId>
    <PubMetrics>
        <Type>APP_CPU</Type>
    </PubMetrics>
    <PubMetrics>
        <Type>SYSTEM_CPU</Type>
    </PubMetrics>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>478B9DE1-3958-4734-AE4F-534658AD8574</requestId>
<successResponse>true</successResponse>
</DescribeEndPointMetricDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "478B9DE1-3958-4734-AE4F-534658AD8574",
    "PubMetrics" : [ {
      "Type" : "APP_CPU",
      "Nodes" : [ ]
    }, {
      "Type" : "SYSTEM_CPU",
      "Nodes" : [ ]
    } ],
    "SubMetrics" : [ ]
  },
  "httpStatusCode" : "200",
  "requestId" : "478B9DE1-3958-4734-AE4F-534658AD8574",
  "successResponse" : true
}
```

