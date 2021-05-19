# DescribeQualityDistributionStatData

调用DescribeQualityDistributionStatData获取质量统计的分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeQualityDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/quality/describeQualityDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|StatDim|String|Query|是|CHANNEL\_ONLINE|统计维度，取值：

 -   **CHANNEL\_ONLINE**：按照频道在线人数统计。
-   **NETWORK**：按照网络类型统计。
-   **OS**：按照系统类型统计。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|QualityStatDataList|Array of QualityStatData| |质量统计数据列表。 |
|Name|String|WiFi|统计维度，取值：

 -   当StatDim为CHANNELONLINE时，取值：**ONE\_TO\_FIVE**（1~5人）、**SIX\_TO\_TEN**（6~10人）、**ELEVEN\_TO\_TWENTY**（11~20人）、**TWENTYONE\_TO\_FIFTY**（21~50人）、**ABOVE\_FIFTY**（50人以上）。
-   当StatDim为NETWORK时，取值：**WiFi**、**4G**等。
-   当StatDim为OS时，取值：**iOS**、**Android**等。 |
|CallDurationRatio|String|0.8366|通话时长占比，用四位小数表示，例如1.0000表示通话时长占比为100%。 |
|JoinChannelSucRate|String|0.9966|加入频道成功率，用四位小数表示。 |
|JoinChannelSucFiveSecRate|String|0.9920|5秒加入频道成功率，用四位小数表示。 |
|AudioSpeakOutDuration|Long|1546|音频首次出声时间，单位：毫秒。 |
|VideoFirstPicDuration|Long|1677|视频首次出图时间，单位：毫秒。 |
|AudioStuckRate|String|0.0049|音频卡顿率，用四位小数表示。 |
|VideoStuckRate|String|0.0137|视频卡顿率，用四位小数表示。 |
|AudioDelay|Long|464|音频延时，单位：毫秒。 |
|VideoDelay|Long|403|视频延时，单位：毫秒。 |
|AudioHighQualityTransmissionRate|String|0.9941|音频优质传输率，用四位小数表示。 |
|VideoHighQualityTransmissionRate|String|0.9974|视频优质传输率，用四位小数表示。 |
|RequestId|String|2D9B00C1-1BA9-4388-9CC1-91F1A933262D|请求ID。 |

## 示例

请求示例

```
POST /api/quality/describeQualityDistributionStatData?StartDate=1615824000&EndDate=1615910399&StatDim=CHANNEL_ONLINE&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeQualityDistributionStatDataResponse>
    <code>200</code>
    <data>
        <RequestId>2D9B00C1-1BA9-4388-9CC1-91F1A933262D</RequestId>
        <QualityStatDataList>
            <AudioStuckRate>0.0049</AudioStuckRate>
            <VideoStuckRate>0.0137</VideoStuckRate>
            <JoinChannelSucRate>0.9966</JoinChannelSucRate>
            <CallDurationRatio>0.8366</CallDurationRatio>
            <VideoHighQualityTransmissionRate>0.9974</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>0.9920</JoinChannelSucFiveSecRate>
            <VideoDelay>403</VideoDelay>
            <AudioDelay>464</AudioDelay>
            <VideoFirstPicDuration>1677</VideoFirstPicDuration>
            <AudioSpeakOutDuration>1546</AudioSpeakOutDuration>
            <AudioHighQualityTransmissionRate>0.9941</AudioHighQualityTransmissionRate>
            <Name>WiFi</Name>
        </QualityStatDataList>
        <QualityStatDataList>
            <AudioStuckRate>0.0039</AudioStuckRate>
            <VideoStuckRate>0.0166</VideoStuckRate>
            <JoinChannelSucRate>1.0000</JoinChannelSucRate>
            <CallDurationRatio>0.1399</CallDurationRatio>
            <VideoHighQualityTransmissionRate>0.9933</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>1.0000</JoinChannelSucFiveSecRate>
            <VideoDelay>266</VideoDelay>
            <AudioDelay>311</AudioDelay>
            <VideoFirstPicDuration>1181</VideoFirstPicDuration>
            <AudioSpeakOutDuration>888</AudioSpeakOutDuration>
            <AudioHighQualityTransmissionRate>0.9898</AudioHighQualityTransmissionRate>
            <Name>UNKNOWN</Name>
        </QualityStatDataList>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>2D9B00C1-1BA9-4388-9CC1-91F1A933262D</requestId>
    <successResponse>true</successResponse>
</DescribeQualityDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "2D9B00C1-1BA9-4388-9CC1-91F1A933262D",
    "QualityStatDataList" : [ {
      "AudioStuckRate" : "0.0049",
      "VideoStuckRate" : "0.0137",
      "JoinChannelSucRate" : "0.9966",
      "CallDurationRatio" : "0.8366",
      "VideoHighQualityTransmissionRate" : "0.9974",
      "JoinChannelSucFiveSecRate" : "0.9920",
      "VideoDelay" : 403,
      "AudioDelay" : 464,
      "VideoFirstPicDuration" : 1677,
      "AudioSpeakOutDuration" : 1546,
      "AudioHighQualityTransmissionRate" : "0.9941",
      "Name" : "WiFi"
    }, {
      "AudioStuckRate" : "0.0039",
      "VideoStuckRate" : "0.0166",
      "JoinChannelSucRate" : "1.0000",
      "CallDurationRatio" : "0.1399",
      "VideoHighQualityTransmissionRate" : "0.9933",
      "JoinChannelSucFiveSecRate" : "1.0000",
      "VideoDelay" : 266,
      "AudioDelay" : 311,
      "VideoFirstPicDuration" : 1181,
      "AudioSpeakOutDuration" : 888,
      "AudioHighQualityTransmissionRate" : "0.9898",
      "Name" : "UNKNOWN"
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "2D9B00C1-1BA9-4388-9CC1-91F1A933262D",
  "successResponse" : true
}
```

