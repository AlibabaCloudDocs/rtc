# DescribeRtcDurationData {#reference2076 .reference}

调用DescribeRtcDurationData获取应用在一段时间内的累计通信时长，区分音视频规格进行统计。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRtcDurationData。|
|AppId|String|否|应用id，不填则返回所有AppId的汇总数据。|
|StartTime|String|是|起始时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|EndTime|String|是|结束时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|Interval|Enum|否|时间粒度参数，取值为 3600（小时粒度）或86400（天粒度），默认为 3600。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|
|DurationDataPerInterval|—|通信时长统计数据结构。|
|└TimeStamp|String|时间戳，UTC格式，例如：2018-01-29T00:00:00Z。|
|└TotalDuration|Long|通信总时长，单位：分钟。|
|└AudioDuration|Long|纯音频通信时长，音频为基础规格。|
|└V360Duration|Long|标清通信时长，视频为640X480及以下，音频为基础规格。|
|└V720Duration|Long|高清通信时长，视频为1280X720及以下，音频为基础规格。|
|└V1080Duration|Long|全高清通信时长，视频为1920X1080及以下，音频为基础规格。|
|└ContentDuration|Long|屏幕共享时长，音频为基础规格。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcDurationData&AppId=xxx&StartTime=2018-01-29T00:00:00Z&EndTime=2018-01-30T00:00:00Z&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "DurationDataPerInterval": [
        {
            "TimeStamp": "2018-01-29T00:00:00Z",
            "TotalDuration": 1000,
            "AudioDuration": 200,                    
            "V360Duration": 300,
            "V720Duration": 300,
            "V1080Duration": 300,
            "ContentDuration": 200
        }
    ]
}
```

## 特殊错误码 {#section_s00_1ks_ppi .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|MissingParameter|ClientToken is mandatory for this action.|400|参数缺失。|

