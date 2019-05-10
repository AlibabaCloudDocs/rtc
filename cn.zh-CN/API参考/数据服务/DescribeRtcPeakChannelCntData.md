# DescribeRtcPeakChannelCntData {#reference1710 .reference}

调用DescribeRtcPeakChannelCntData查询应用在一段时间内的并发频道峰值数量。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRtcPeakChannelCntData。|
|AppId|String|否|应用id，不填则返回所有AppId的汇总数据。|
|StartTime|String|是|起始时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|EndTime|String|是|结束时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|Interval|Enum|否|时间粒度参数，取值为 3600（小时粒度） 或 86400（天粒度），默认为 3600。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|
|PeakChannelCntDataPerInterval|—|并发频道峰值数据结构。|
|└TimeStamp|String|时间戳，UTC格式，例如：2018-01-29T00:00:00Z。|
|└ActiveChannelPeak|Long|并发频道峰值数量。|
|└ActiveChannelPeakTime|String|峰值时刻，UTC格式，例如：2018-01-29T00:00:00Z。|

## 示例 { .section}

请求示例

``` {#codeblock_dpy_jh1_6gi}
https://rtc.aliyuncs.com?Action=DescribeRtcPeakChannelCntData&AppId=xxx&StartTime=2018-01-29T00:00:00Z&EndTime=2018-01-30T00:00:00Z&<公共请求参数>
```

正常返回示例

`JSON`格式

``` {#codeblock_ccu_wbb_7t4}
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "PeakChannelCntDataPerInterval": [ 
        {  
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveChannelPeak": 10,
            "ActiveChannelPeakTime": "2018-01-29T00:01:00Z"
        }
    ]
}    
```

## 特殊错误码 {#section_mve_6c1_thf .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|MissingParameter|ClientToken is mandatory for this action.|400|参数缺失。|

