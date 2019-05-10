# DescribeRtcPeakUserCntData {#reference1710 .reference}

调用DescribeRtcPeakUserCntData查询应用在一段时间内的并发通信峰值，一组“发布-订阅”关系被标记为一次通信。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名。系统规定参数，取值：DescribeRtcPeakUserCntData。|
|AppId|String|否|应用Id。如果不填，则返回所有AppId的汇总数据。|
|StartTime|String|是|起始时间。UTC格式，例如：2018-01-29T00:00:00Z。|
|EndTime|String|是|结束时间。UTC格式，例如：2018-01-29T00:00:00Z。|
|Interval|Enum|否|时间粒度参数。取值为3600（小时粒度）或86400（天粒度），默认值为3600。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|
|PeakUserCntDataPerInterval|—|峰值并发通信统计数据结构。|
|└TimeStamp|String|时间戳。UTC格式，例如：2018-01-29T00:00:00Z。|
|└ActiveUserPeak|Long|峰值时刻的并发通信数。|
|└ActiveUserPeakTime|String|并发通信峰值时刻，UTC格式，例如：2018-01-29T00:00:00Z。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcPeakUserCntData&AppId=xxx&StartTime=2018-01-29T00:00:00Z&EndTime=2018-01-30T00:00:00Z&<公共请求参数>
```

正常返回示例

 `JSON`格式

```language-json
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "PeakUserCntDataPerInterval": [ 
        {  
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveUserPeak": 10,
            "ActiveUserPeakTime": "2018-01-29T00:01:00Z"
        }
    ]
}
```

## 特殊错误码 { .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|服务器内部错误。|
|MissingParameter|ClientToken is mandatory for this action.|400|请求参数缺失。|

