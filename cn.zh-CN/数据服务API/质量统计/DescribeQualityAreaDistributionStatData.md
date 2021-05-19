# DescribeQualityAreaDistributionStatData

调用DescribeQualityAreaDistributionStatData获取质量统计的地域分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeQualityAreaDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/quality/describeQualityAreaDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|ParentArea|String|Query|否|中国|父级地区名称，例如：深圳市的父级为广东省。参数为空表示世界范围（国家维度）的统计，例如：中国、英国。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|QualityStatDataList|Array of QualityStatData| |质量分布数据列表。 |
|Name|String|中国\_浙江省|地域名称。 |
|CallDurationRatio|String|0.7959|通话时长占比，用四位小数表示，例如1.0000表示通话时长占比为100%。 |
|JoinChannelSucRate|String|0.9972|加入频道成功率，用四位小数表示。 |
|JoinChannelSucFiveSecRate|String|0.9939|5秒加入频道成功率，用四位小数表示。 |
|AudioSpeakOutDuration|Long|1060|音频首次出声时间，单位：毫秒。 |
|VideoFirstPicDuration|Long|1236|视频首次出图时间，单位：毫秒。 |
|AudioStuckRate|String|0.0025|音频卡顿率，用四位小数表示。 |
|VideoStuckRate|String|0.0104|视频卡顿率，用四位小数表示。 |
|AudioDelay|Long|300|音频延时，单位：毫秒。 |
|VideoDelay|Long|252|视频延时，单位：毫秒。 |
|AudioHighQualityTransmissionRate|String|0.9941|音频优质传输率，用四位小数表示。 |
|VideoHighQualityTransmissionRate|String|0.9978|视频优质传输率，用四位小数表示。 |
|RequestId|String|5295429E-9E9E-4F79-B814-70D71B8554EB|请求ID。 |

## 示例

请求示例

```
POST /api/quality/describeQualityAreaDistributionStatData?StartDate=1615824000&EndDate=1615910399&ParentArea=中国&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeQualityAreaDistributionStatDataResponse>
    <code>200</code>
    <data>
        <RequestId>5295429E-9E9E-4F79-B814-70D71B8554EB</RequestId>
        <QualityStatDataList>
            <AudioStuckRate>0.0025</AudioStuckRate>
            <VideoStuckRate>0.0104</VideoStuckRate>
            <JoinChannelSucRate>0.9972</JoinChannelSucRate>
            <CallDurationRatio>0.7959</CallDurationRatio>
            <VideoHighQualityTransmissionRate>0.9978</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>0.9939</JoinChannelSucFiveSecRate>
            <VideoDelay>252</VideoDelay>
            <AudioDelay>300</AudioDelay>
            <VideoFirstPicDuration>1236</VideoFirstPicDuration>
            <AudioSpeakOutDuration>1060</AudioSpeakOutDuration>
            <AudioHighQualityTransmissionRate>0.9941</AudioHighQualityTransmissionRate>
            <Name>中国_浙江省</Name>
        </QualityStatDataList>
        <QualityStatDataList>
            <AudioStuckRate>0.0041</AudioStuckRate>
            <VideoStuckRate>0.0181</VideoStuckRate>
            <JoinChannelSucRate>1.0000</JoinChannelSucRate>
            <CallDurationRatio>0.1153</CallDurationRatio>
            <VideoHighQualityTransmissionRate>0.9996</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>1.0000</JoinChannelSucFiveSecRate>
            <VideoDelay>221</VideoDelay>
            <AudioDelay>283</AudioDelay>
            <VideoFirstPicDuration>1042</VideoFirstPicDuration>
            <AudioSpeakOutDuration>865</AudioSpeakOutDuration>
            <AudioHighQualityTransmissionRate>0.9965</AudioHighQualityTransmissionRate>
            <Name>中国_北京市</Name>
        </QualityStatDataList>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>5295429E-9E9E-4F79-B814-70D71B8554EB</requestId>
    <successResponse>true</successResponse>
</DescribeQualityAreaDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "5295429E-9E9E-4F79-B814-70D71B8554EB",
    "QualityStatDataList" : [ {
      "AudioStuckRate" : "0.0025",
      "VideoStuckRate" : "0.0104",
      "JoinChannelSucRate" : "0.9972",
      "CallDurationRatio" : "0.7959",
      "VideoHighQualityTransmissionRate" : "0.9978",
      "JoinChannelSucFiveSecRate" : "0.9939",
      "VideoDelay" : 252,
      "AudioDelay" : 300,
      "VideoFirstPicDuration" : 1236,
      "AudioSpeakOutDuration" : 1060,
      "AudioHighQualityTransmissionRate" : "0.9941",
      "Name" : "中国_浙江省"
    }, {
      "AudioStuckRate" : "0.0041",
      "VideoStuckRate" : "0.0181",
      "JoinChannelSucRate" : "1.0000",
      "CallDurationRatio" : "0.1153",
      "VideoHighQualityTransmissionRate" : "0.9996",
      "JoinChannelSucFiveSecRate" : "1.0000",
      "VideoDelay" : 221,
      "AudioDelay" : 283,
      "VideoFirstPicDuration" : 1042,
      "AudioSpeakOutDuration" : 865,
      "AudioHighQualityTransmissionRate" : "0.9965",
      "Name" : "中国_北京市"
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "5295429E-9E9E-4F79-B814-70D71B8554EB",
  "successResponse" : true
}
```

