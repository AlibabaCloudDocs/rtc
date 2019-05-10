# DescribeRtcUserCntData {#reference1554 .reference}

调用DescribeRtcUserCntData查询应用在一段时间内的活跃用户数，即发生通信的用户终端数。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRtcUserCntData。|
|AppId|String|否|应用id，不填则返回所有AppId的汇总数据。|
|StartTime|String|是|起始时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|EndTime|String|是|结束时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|Interval|Enum|否|时间粒度参数，取值为 3600（小时粒度） 或 86400（天粒度），默认为 3600。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|
|UserCntDataPerInterval|—|活跃用户统计数据结构。|
|└TimeStamp|String|时间戳，UTC格式，例如：2018-01-29T00:00:00Z。|
|└ActiveUserCnt|Long|当前活跃用户数（基于发生通信的用户终端统计）。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcUserCntData&AppId=xxx&StartTime=2018-01-29T00:00:00Z&EndTime=2018-01-30T00:00:00Z&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "UserCntDataPerInterval": [ 
        {  
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveUserCnt": 10
        }
    ]
}
```

## 特殊错误码 {#section_9jo_ubk_owf .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|MissingParameter|ClientToken is mandatory for this action.|400|参数缺失。|

