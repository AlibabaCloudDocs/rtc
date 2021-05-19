# DescribeQualityOsSdkVersionDistributionStatData

调用DescribeQualityOsSdkVersionDistributionStatData获取质量统计中各操作系统及SDK版本的分布数据。

**说明：**

-   支持查询最近365天（不包含查询当天）任意范围的数据。
-   如果查询范围小于24小时，则按小时统计查询的数据；如果查询范围大于或等于24小时，则按天统计查询的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeQualityOsSdkVersionDistributionStatData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/quality/describeQualityOsSdkVersionDistributionStatData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|StartDate|Long|Query|是|1615824000|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndDate|Long|Query|是|1615910399|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|QualityOsSdkVersionStatDataList|Array of QualityStatData| |质量统计中操作系统及SDK版本的数据列表。 |
|Name|String|2.1.21041618553512|SDK版本名称。 |
|Os|String|macOS|操作系统，例如iOS、Android等。 |
|CallDurationRatio|String|0.0768|通话时长占比，用四位小数表示，例如1.0000表示通话时长占比为100%。 |
|JoinChannelSucRate|String|1.0000|加入频道成功率，用四位小数表示。 |
|JoinChannelSucFiveSecRate|String|1.0000|5秒加入频道成功率，用四位小数表示。 |
|AudioSpeakOutDuration|Long|550|音频首次出声时间，单位：毫秒。 |
|VideoFirstPicDuration|Long|631|视频首次出图时间，单位：毫秒。 |
|AudioStuckRate|String|0.0007|音频卡顿率，用四位小数表示。 |
|VideoStuckRate|String|0.0002|视频卡顿率，用四位小数表示。 |
|AudioDelay|Long|260|音频延时，单位：毫秒。 |
|VideoDelay|Long|241|视频延时，单位：毫秒。 |
|AudioHighQualityTransmissionRate|String|0.9969|音频优质传输率，用四位小数表示。 |
|VideoHighQualityTransmissionRate|String|0.9992|视频优质传输率，用四位小数表示。 |
|RequestId|String|250069CD-B97C-46D8-9F9F-716D0D8A7E86|请求ID。 |

## 示例

请求示例

```
POST /api/quality/describeQualityOsSdkVersionDistributionStatData?StartDate=1615824000&EndDate=1615910399&AppId=0rbd**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeQualityOsSdkVersionDistributionStatDataResponse>
    <code>200</code>
    <data>
        <QualityOsSdkVersionStatDataList>
            <AudioStuckRate>0.0007</AudioStuckRate>
            <VideoStuckRate>0.0002</VideoStuckRate>
            <CallDurationRatio>0.0768</CallDurationRatio>
            <Os>macOS</Os>
            <VideoHighQualityTransmissionRate>0.9992</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>1.0000</JoinChannelSucFiveSecRate>
            <VideoDelay>241</VideoDelay>
            <AudioDelay>260</AudioDelay>
            <AudioSpeakOutDuration>550</AudioSpeakOutDuration>
            <Name>2.1.21041618553512</Name>
            <JoinChannelSucRate>1.0000</JoinChannelSucRate>
            <VideoFirstPicDuration>631</VideoFirstPicDuration>
            <AudioHighQualityTransmissionRate>0.9969</AudioHighQualityTransmissionRate>
        </QualityOsSdkVersionStatDataList>
        <QualityOsSdkVersionStatDataList>
            <AudioStuckRate>0.0028</AudioStuckRate>
            <VideoStuckRate>0.0244</VideoStuckRate>
            <CallDurationRatio>0.0665</CallDurationRatio>
            <Os>macOS</Os>
            <VideoHighQualityTransmissionRate>0.9984</VideoHighQualityTransmissionRate>
            <JoinChannelSucFiveSecRate>1.0000</JoinChannelSucFiveSecRate>
            <VideoDelay>253</VideoDelay>
            <AudioDelay>276</AudioDelay>
            <AudioSpeakOutDuration>679</AudioSpeakOutDuration>
            <Name>1.19.2.2012071</Name>
            <JoinChannelSucRate>1.0000</JoinChannelSucRate>
            <VideoFirstPicDuration>904</VideoFirstPicDuration>
            <AudioHighQualityTransmissionRate>0.9934</AudioHighQualityTransmissionRate>
        </QualityOsSdkVersionStatDataList>
        <RequestId>250069CD-B97C-46D8-9F9F-716D0D8A7E86</RequestId>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>250069CD-B97C-46D8-9F9F-716D0D8A7E86</requestId>
    <successResponse>true</successResponse>
</DescribeQualityOsSdkVersionDistributionStatDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "QualityOsSdkVersionStatDataList" : [ {
      "AudioStuckRate" : "0.0007",
      "VideoStuckRate" : "0.0002",
      "CallDurationRatio" : "0.0768",
      "Os" : "macOS",
      "VideoHighQualityTransmissionRate" : "0.9992",
      "JoinChannelSucFiveSecRate" : "1.0000",
      "VideoDelay" : 241,
      "AudioDelay" : 260,
      "AudioSpeakOutDuration" : 550,
      "Name" : "2.1.21041618553512",
      "JoinChannelSucRate" : "1.0000",
      "VideoFirstPicDuration" : 631,
      "AudioHighQualityTransmissionRate" : "0.9969"
    }, {
      "AudioStuckRate" : "0.0028",
      "VideoStuckRate" : "0.0244",
      "CallDurationRatio" : "0.0665",
      "Os" : "macOS",
      "VideoHighQualityTransmissionRate" : "0.9984",
      "JoinChannelSucFiveSecRate" : "1.0000",
      "VideoDelay" : 253,
      "AudioDelay" : 276,
      "AudioSpeakOutDuration" : 679,
      "Name" : "1.19.2.2012071",
      "JoinChannelSucRate" : "1.0000",
      "VideoFirstPicDuration" : 904,
      "AudioHighQualityTransmissionRate" : "0.9934"
    } ],
    "RequestId" : "250069CD-B97C-46D8-9F9F-716D0D8A7E86"
  },
  "httpStatusCode" : "200",
  "requestId" : "250069CD-B97C-46D8-9F9F-716D0D8A7E86",
  "successResponse" : true
}
```

